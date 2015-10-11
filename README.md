# JavaCreditCardClass
My first class usage in java

public class CreditCard {

    // instance fields
	
    /**
     * each CreditCard instance should have
     * a unique card number
     */
    private int cardNumber;
    private String cardHolder;
    private double currentBalance;
    private double creditLimit;
    
    public static final String POUND = java.util.Currency.getInstance("GBP").getSymbol(java.util.Locale.UK);
    // static fields
    
    static int nextID = 0;
    
    // accessor methods

    public int getCardNumber() {
        return this.cardNumber;
    }
    public String getCardHolder() {
    	return this.cardHolder;
    }
    public double getCurrentBalance() {
    	return this.currentBalance;
    }
    public double getCreditLimit() {
    	return this.creditLimit;
    }
    
    public void setCardHolder(String accountHolder){	
    
    this.cardHolder = accountHolder;
    
    }
    public boolean equals(CreditCard s1, CreditCard s2){

    	if(s1.getCardNumber()==s2.getCardNumber()){
    		return true;
    	}else{
    		return false;
    	}
    }
    
    public String toString(){
    	
    	return String.format("cHolder: %s,cNumber: %d, cBalance: %s%.2f, cLimit: %s%.2f.", 
    			getCardHolder(),getCardNumber(),POUND,getCurrentBalance(),POUND,getCreditLimit());
    }
    
    CreditCard(){
    	this.cardNumber = CreditCard.nextID++;
    	this.currentBalance = 0.00;
    	this.creditLimit = 500.00;
    }
    
    CreditCard(String accountHolder, double creditLimit){
    	
    	this.creditLimit = creditLimit;
    	this.cardHolder = accountHolder;
    	this.cardNumber = CreditCard.nextID++;
    	this.currentBalance =0.00;
    	
    }
    
    // other methods
    
    public boolean charge(double amount){
    	
    	if(amount>getCreditLimit()){
    		return false;
    	
    	}else if(amount<=0.00){
    		return false;
    	}else if(getCurrentBalance()+amount>getCreditLimit()){
    		return false;
    	}else{
    		this.currentBalance += amount;
   		 	return true;
    	}
    }
    
    public boolean makePayment(double amount){
    	
    	if(amount>getCurrentBalance()){
    		return false;
    		
    	}else if(amount <= 0.00){
    		return false;
    		
    	}else{
    		this.currentBalance -=amount;
    		return true;
    	}
    }
    
    public boolean setCreditLimit(double creditLimit){
    	
    	if(creditLimit<0.00){
    		return false;
    	}else if(creditLimit<getCurrentBalance()){
    		return false;
    	}else{
    		this.creditLimit = creditLimit;
    		return true;
    	}
    }   
}
