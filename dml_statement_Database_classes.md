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

Bulk Lead Conversion whose name start with a

```
   public static void LeadConversion(){
          List<Lead> leadList=[select name from Lead where name like 'sh%' ];
          List<Database.leadConvert>needtoConvert=new List<Database.leadConvert>();
          try{
              for(Lead le:leadList){
              Database.leadConvert lc=new Database.leadConvert();
              lc.setLeadId(le.id);
              LeadStatus convertStatus = [SELECT Id, ApiName FROM LeadStatus WHERE IsConverted=true LIMIT 1];
              lc.setConvertedStatus(convertStatus.ApiName);
              lc.setOwnerId(UserInfo.getUserId());
              needtoConvert.add(lc);
                  
              }
              
          }catch(Exception e){
              System.debug(e.getMessage());
          }
          
        
        Database.leadConvertResult[] leadcresult=DataBase.convertLead(needtoConvert);
    }
```
