## Question 1:-
Insert Parent and Child in One DML Statement using External ID
```
public class AccountContactcreate {
    public static void mymethod(){
        ///creating obj the Accocunt record instance
        
        Account accref=new Account(Name='Iishan Singh',Ext_ID__c='SAP213459786');

        /// new contact record 
        Contact newcon=new Contact(FirstName='Isihan', LastName='Coontact', Email='hjjobfweufwf@gmail.com');

         // referencing the Account to this contact that we want to create with External_ID 
        newcon.Account=new Account(Ext_ID__c='SAP213459786');
        
        
        Database.insert(new list<sobject>{accref,newcon});
        System.debug(newcon);
        
    }
}
```

## Question 2
create function to delete the dublicate records 

```
List<Contact> conList = [SELECT Name FROM Contact];
Map<String, ID> mMap = new Map<String, ID>();
for(Contact c: conList)
{
	mMap.put(c.Name, c.Id);
}
List<Contact> delList = new List<Contact>();
Set<String> sSet = mMap.keySet();
Set<ID> uniqSet = new Set<ID>();
for(String s: sSet)
{
	uniqSet.add(mMap.get(s));
}
for(Contact c1: conList)
{
	if(!uniqSet.contains(c1.Id))
		delList.add(c1);
		
}
delete delList;

```

## Question 3


