# Encryptor
An Encrypt/Decrypt algorithm in lib.<br/>
C# only(yet).<br/>
It can't be broke by Known-plaintext attack and Chosen-plaintext attack.(if full power method is used).<br/>
it can take up to years for a brute-force attack to break an encryted string.(if used with the recommend options).<br/>
The main class is System.Security.EncryptString<br/>
I have made the algorithm to be only one method for each action either encrypt or decrypt.<br/>
IMPORTANT NOTE : This lib is for free use, so if you like it, Please donate.<br/>
# The EncryptString(main class in the lib) class contains <br/>
*******************************************************************************************************************************
public String Encrypt(String data, Encoding encoding);

public String Encrypt(String data, Encoding encoding, string password);

public String Encrypt(String data, Encoding encoding, string password, string password2);

public String Encrypt(String data, Encoding encoding, string password, string password2, System.Security.encryption.CryptoTypes cryptoTypes, bool destroyBase);

public String Encrypt(String data, Encoding encoding, string password, string password2, System.Security.encryption.CryptoTypes cryptoTypes, bool destroyBase, bool destroyChars);

public String Encrypt(String data, Encoding encoding, string password, string password2, string password3, System.Security.encryption.CryptoTypes cryptoTypes, bool destroyBase, bool destroyChars, bool destroyBasePassword)//destroyBasePassword since version 1.3

public string Decrypt(string data, Encoding encoding);

public string Decrypt(string data, Encoding encoding, string password);

public string Decrypt(string data, Encoding encoding, string password, string password2);

public string Decrypt(string data, Encoding encoding, string password, string password2, System.Security.encryption.CryptoTypes cryptoTypes, bool BaseDestroyed);

public string Decrypt(string data, Encoding encoding, string password, string password2, System.Security.encryption.CryptoTypes cryptoTypes, bool BaseDestroyed, bool CharsDestroyed);

public string Decrypt(string data, Encoding encoding, string password, string password2, string password3, System.Security.encryption.CryptoTypes cryptoTypes, bool BaseDestroyed, bool CharsDestroyed, bool destroyBasePassword)

******************************************************************************************************************************

Each of the above methods returns a string either encrypted or decrypted depends on the method used.
The methods is sorted from low to high security. With each variable passes to the method, the security increases as the bounders for a guesser program can be greater to be guessed.

lets take the simplest method which is Encrypt(String data, Encoding encoding)

   using System.Security;<br/>
   using System.Text;<br/>
   
   string text = "A simple text";
   
   EncryptString myEncryptor = new EncryptString();//creating instance to main class
   
   string encryptedText = myEncryptor.Encrypt(text, Encoding.ASCII);<br/>
   //any encoding will work actually, but MUST be the same encoding to use while decypting.
   
   Console.WriteLine(encryptedText + "\n" + "\n");
   
   string decryptedText = myEncryptor.Decrypt(encryptedText, Encoding.ASCII);<br/>
   Console.WriteLine(decryptedText);<br/>
   OUTPUT : QaKLWaDLWaKLQaDLQaKLQaDLQaKLWaDLQaKLQaDLQaKLQaDLQaKLQaKLWaDLRaKLQaDLQaKLQaDLtaKLQaDLQaKLQaDLQaKLQaDLQaKLQaDLWaKLWaKLeaDLeaKLQaKLWaDLQaKLWaDLWaKLQaKLQaDLQaKLQaDLWaKLWaDLQaKLQaDLQaKLQaDLeaKLQaDLWaKLWaDLQaKLWaDLQaKLQaKLWaDLQaKLQaDLQaKLWaDLQaKLQaDLQaKLQaDLRaKLWaKLQaDLQaKLQaDLQaKLWaDLQaKLWaDLWaKLQaDLWaKLQaKLeaDLQaKLQaDLQaKLQaDLQaKLWaDLWaKLeaDLQaKLWaDLeaKLQaDLQaKLQaKLQaDLWaKLWaDLQaKLQaDLQaKLWaDLeaKLWaDLWaKLWaDLQaKLWaDLQaKLQaKLWaDLeaKLQaDLQaKLQaKLQaDLtaKLQaDLWaKLRaDLQaKLQaDLWaKLRaDLQaKLQaDL[BE]
   
A simple text
   
********************************************************************************************************************************   

It's so simple yet, so strong. but this was actually a weak method. let's add more variables to make it stronger :

   using System.Security;<br/>
   using System.Text;<br/>
   
   string text = "A simple text";
   
   EncryptString myEncryptor = new EncryptString();//creating instance to main class
   
   string encryptedText = myEncryptor.Encrypt(text, Encoding.ASCII, "123456789", "AnY PaSSwOrd Will WoRk");<br/>
   
   //Any encoding will work actually, but MUST be the same encoding to use while decypting.<br/>
   //Password 1 MUST BE 9 character in length. <br/>
   //Password 2 can be anything, but as you know "size matters" the "longer" password the "Harder" it becomes harder to be guessed.<br/>
   
   Console.WriteLine(encryptedText + "\n" + "\n");
   
   string decryptedText = myEncryptor.Decrypt(encryptedText, Encoding.ASCII, "123456789", "AnY PaSSwOrd Will WoRk");
   //Anything used while encrypting, MUST be used while decrypting.<br/>
   Console.WriteLine(decryptedText);<br/>
   
   OUTPUT : 
   2aKL2aDL4aKL1aKL2aDL3aKL1aDL1aKL1aKL1aDL1aKL1aDL2aKL1aDL1aKL1aKL1aDL1aKL2aDL2aKL1aDL2aKL3aDL2aKL1aDL1aKL1aDL1aKL1aDL1aKL1aDL2aKL1aKL1aDL2aKL2aDL1aKL1aDL1aKL3aDL2aKL2aDL1aKL2aDL4aKL1aDL2aKL2aDL1aKL1aDL1aKL1aDL1aKL1aDL2aKL2aDL2aKL1aKL1aDL2aKL1aDL2aKL1aDL1aKL1aDL2aKL1aDL3aKL1aKL1aDL1aKL1aDL2aKL2aDL2aKL1aDL1aKL4aDL2aKL2aDL1aKL3aDL1aKL1aDL3aKL2aDL1aKL1aKL2aDL1aKL3aDL1aKL2aKL2aDL1aKL3aDL1aKL2aDL1aKL1aDL3aKL1aKL1aDL1aKL1aDL3aKL1aDL1aKL2aDL2aKL3aDL2aKL4aDL1aKL1aDL2aKL4aDL1aKL1aDL[BE]
   
A simple text
   
********************************************************************************************************************************   
  It's not that hard to understand, yet so strong. but this was actually a not full security and not to be considered weak.   let's add more variables to make it stronger :

   using System.Security;<br/>
   using System.Text;<br/>
   
   string text = "A simple text";
   
   EncryptString myEncryptor = new EncryptString();//creating instance to main class
   <br/>
   //Full power method.<br/>
   
   string encryptedText = myEncryptor.Encrypt(text, Encoding.Unicode, "123456789", "AnY PaSSwOrd Will WoRk", "AnY PaSSwOrd Will WoRk aGain", encryption.CryptoTypes.encTypeTripleDES, true, true, true);
  
   //If you used third extra security feat., it's preferred to use UTF-* or Unicode as your encoding.<br/>
   //Password 1 MUST BE 9 character in length. <br/>
   //Password 2 can be anything, but as you know "size matters" the "longer" password the "Harder" it becomes to be guessed.<br/>
   //Password 3 can be anything, but as you know "size matters" the "longer" password the "Harder" it becomes to be guessed.<br/>
   //encryption.CryptoTypes is an enum that contains most known algorithms. it merges my algorithm with the most known algorithms to make it nearly impossible or as we should say might endup taking too too long to be breakable.<br/>
   //the boolen variable tells the algorithim to use the extra security feature which destroys the base text.<br/>
   //the second boolen variable tells the algorithim to use the extra sec. feat. which destroys the original text using the password.<br/>
   //the third boolen variable tells the algorithm to use the extra third feat. which destroys the original base using the password. so now the base is destroyed twice using two diffrent algorithms<br/>
   //ofcourse you can use the extra features or not as you wish, but remember to be the same when decrypting.<br/>
   
   WriteLine(encryptedText + "\n" + "\n");<br/>
   
   string decryptedText = myEncryptor.Decrypt(encryptedText, Encoding.Unicode, "123456789", "AnY PaSSwOrd Will WoRk", "AnY PaSSwOrd Will WoRk aGain", encryption.CryptoTypes.encTypeTripleDES, true, true, true);<br/>
   
   //anything used while encrypting, MUST be used while decrypting.<br/>
   Console.WriteLine(decryptedText);<br/>
   <br/>
   OUTPUT :  
   
   1aDL1aKL3aDL1aKL2aDL8aKL1aDL1aKL1aDL2aKL2aDL1aKL8aKL1aKL1aDL1aKL1aDL2aKL1aDL1aKL8aKL1aDL6aKL1aDL8aKL1aDL1aKL1aDL3aKL2aDL8aKL2aDL2aKL2aDL1aKL1aDL8aKL1aDL1aKL1aDL1aKL1aDL3aKL8aKL3aDL2aKL1aDL2aKL8aKL1aDL2aKL1aDL1aKL3aDL8aKL2aDL5aKL1aDL8aKL2aDL1aKL1aDL1aKL1aDL2aKL8aKL1aDL3aKL4aDL8aKL2aDL2aKL1aDL1aKL1aDL1aKL8aKL2aDL4aKL1aDL1aKL8aKL1aDL1aKL1aDL1aKL3aDL1aKL8aKL2aDL2aKL2aDL1aKL1aDL8aKL1aDL4aKL3aDL8aKL1aDL3aKL3aDL1aKL8aKL1aDL1aKL3aDL1aKL1aDL1aKL8aKL1aDL3aKL1aDL1aKL1aDL1aKL8aKL2aDL1aKL2aDL3aKL8aKL1aKL2aDL1aKL1aDL3aKL8aKL2aDL2aKL1aDL3aKL8aKL1aDL1aKL1aDL5aKL8aKL2aDL1aKL2aDL1aKL1aDL1aKL8aKL1aDL1aKL3aDL1aKL1aDL1aKL8aKL2aDL1aKL1aDL1aKL1aDL2aKL8aKL1aDL1aKL1aDL1aKL3aDL1aKL8aKL2aDL4aKL2aDL8aKL1aDL3aKL1aDL1aKL2aDL8aKL1aKL1aDL1aKL1aDL3aKL1aDL8aKL1aDL1aKL3aDL1aKL2aDL8aKL1aDL1aKL3aDL1aKL2aDL8aKL1aDL1aKL1aDL1aKL1aDL3aKL8aKL1aDL1aKL1aDL1aKL1aDL1aKL2aDL8aKL2aDL3aKL1aDL1aKL1aDL8aKL1aDL5aKL1aDL1aKL8aKL3aDL2aKL3aDL8aKL2aDL1aKL1aDL2aKL1aDL1aKL8aKL1aDL2aKL2aDL2aKL1aDL8aKL1aDL1aKL1aDL2aKL1aDL1aKL1aDL8aKL1aDL1aKL2aDL2aKL2aDL8aKL1aDL2aKL3aDL2aKL8aKL1aDL1aKL1aDL1aKL1aDL2aKL1aDL8aKL[BE]
   
A simple text 
   
********************************************************************************************************************************   
Illegal characters to use in password 1 : K, D, T, L, [,], B, E <br/>
password 2 can be anything.<br/>

# Error list 
_______________________________________
*
    * Error 101 = not a valid or modified encrypted string                                                                                                                             *
    * Error 102 = Illegal character used as a password1 character                                                                                                           * 
    * Error 103 = Password1 can be ONLY nine characters. not more or less                                                                                                  *
    * Error 104 = not a valid or modified encrypted string                                                                                                                             *
    * Error 105 = not a valid or modified encrypted string
*
    * Error 106 = not a valid or modified encrypted string                                                                                     *
    * Error 107 = not a valid or modified encrypted string                                                                                      *
    * Error 108 = not a valid or modified encrypted string                                                                                      *
    * "?" character that represented alot in a decrypted string is because, eather the password2 is wrong or the text       isn't encrypted with extra function 2 and decrypted using extra function 2
********************************************************************************************************************************
