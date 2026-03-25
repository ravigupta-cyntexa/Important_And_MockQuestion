## Question 1:-
Insert Parent and Child in One DML Statement 
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
