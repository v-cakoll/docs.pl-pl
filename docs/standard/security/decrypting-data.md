---
title: Odszyfrowywanie danych
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [.NET Framework], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d0aefcc61a9ce283f1230cd44ffae549725bb15f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="decrypting-data"></a>Odszyfrowywanie danych
Odszyfrowywanie jest odwrotnej operacji szyfrowania. Do szyfrowania klucza tajnego musisz znać klucz i IV, które były używane do szyfrowania danych. Do szyfrowania klucza publicznego musisz znać klucza publicznego (jeśli zostały zaszyfrowane przy użyciu klucza prywatnego) lub klucza prywatnego (jeśli zostały zaszyfrowane za pomocą klucza publicznego).  
  
## <a name="symmetric-decryption"></a>Odszyfrowanie symetryczne  
 Odszyfrowywanie danych zaszyfrowanych za pomocą symetryczne algorytmy jest podobny do procesu używany do szyfrowania danych za pomocą symetryczne algorytmy. <xref:System.Security.Cryptography.CryptoStream> Klasa jest używana z klasami Kryptografia symetryczna dostarczane przez program .NET Framework, aby odszyfrować dane z dowolnych obiektów zarządzanych strumień do odczytu.  
  
 Poniższy przykład przedstawia sposób utworzyć nowe wystąpienie klasy <xref:System.Security.Cryptography.RijndaelManaged> klasy i używać go do odszyfrowywania na <xref:System.Security.Cryptography.CryptoStream> obiektu. W tym przykładzie najpierw tworzy nowe wystąpienie klasy **RijndaelManaged** klasy. Następnie tworzy **CryptoStream** obiekt i inicjuje wartość zarządzanego strumienia mu `MyStream`. Następnie **CreateDecryptor** metody z **RijndaelManaged** klasy jest przekazywany ten sam klucz i IV, który był używany do szyfrowania i są następnie przekazywane do **CryptoStream** Konstruktor. Na koniec **CryptoStreamMode.Read** wyliczenie jest przekazywana do **CryptoStream** konstruktora, aby określić dostęp do odczytu do strumienia.  
  
```vb  
Dim RMCrypto As New RijndaelManaged()  
Dim CryptStream As New CryptoStream(MyStream, RMCrypto.CreateDecryptor(RMCrypto.Key, RMCrypto.IV), CryptoStreamMode.Read)  
```  
  
```csharp  
RijndaelManaged RMCrypto = new RijndaelManaged();  
CryptoStream CryptStream = new CryptoStream(MyStream, RMCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read);  
```  
  
 Poniższy przykład przedstawia cały proces tworzenia strumienia, odszyfrowywania strumień odczytu ze strumienia i zamykania strumieni. A <xref:System.Net.Sockets.TcpListener> tworzony jest obiekt, który inicjuje strumienia sieci, gdy nawiązuje połączenie z obiektem nasłuchiwania. Strumień sieciowych jest odszyfrowywany za pomocą **CryptoStream** klasy i **RijndaelManaged** klasy. W tym przykładzie przyjęto założenie, że klucza i wartości IV ma została pomyślnie przeniesiona lub wcześniej uzgodnione. Kod wymagane do szyfrowania i przesyłania tych wartości nie są wyświetlane.  
  
```vb  
Imports System  
Imports System.Net.Sockets  
Imports System.Threading  
Imports System.IO  
Imports System.Net  
Imports System.Security.Cryptography  
  
Module Module1  
    Sub Main()  
            'The key and IV must be the same values that were used  
            'to encrypt the stream.    
            Dim Key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
            Dim IV As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
        Try  
            'Initialize a TCPListener on port 11000  
            'using the current IP address.  
            Dim TCPListen As New TcpListener(IPAddress.Any, 11000)  
  
            'Start the listener.  
            TCPListen.Start()  
  
            'Check for a connection every five seconds.  
            While Not TCPListen.Pending()  
                Console.WriteLine("Still listening. Will try in 5 seconds.")  
  
                Thread.Sleep(5000)  
            End While  
  
            'Accept the client if one is found.  
            Dim TCP As TcpClient = TCPListen.AcceptTcpClient()  
  
            'Create a network stream from the connection.  
            Dim NetStream As NetworkStream = TCP.GetStream()  
  
            'Create a new instance of the RijndaelManaged class  
            'and decrypt the stream.  
            Dim RMCrypto As New RijndaelManaged()  
  
            'Create an instance of the CryptoStream class, pass it the NetworkStream, and decrypt   
            'it with the Rijndael class using the key and IV.  
            Dim CryptStream As New CryptoStream(NetStream, RMCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read)  
  
            'Read the stream.  
            Dim SReader As New StreamReader(CryptStream)  
  
            'Display the message.  
            Console.WriteLine("The decrypted original message: {0}", SReader.ReadToEnd())  
  
            'Close the streams.  
            SReader.Close()  
            NetStream.Close()  
            TCP.Close()  
            'Catch any exceptions.   
        Catch  
            Console.WriteLine("The Listener Failed.")  
        End Try  
    End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Net.Sockets;  
using System.Threading;  
using System.IO;  
using System.Net;  
using System.Security.Cryptography;  
  
class Class1  
{  
   static void Main(string[] args)  
   {  
      //The key and IV must be the same values that were used  
      //to encrypt the stream.    
      byte[] Key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
      byte[] IV = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
      try  
      {  
         //Initialize a TCPListener on port 11000  
         //using the current IP address.  
         TcpListener TCPListen = new TcpListener(IPAdress.Any, 11000);  
  
         //Start the listener.  
         TCPListen.Start();  
  
         //Check for a connection every five seconds.  
         while(!TCPListen.Pending())  
         {  
            Console.WriteLine("Still listening. Will try in 5 seconds.");  
            Thread.Sleep(5000);  
         }  
  
         //Accept the client if one is found.  
         TcpClient TCP = TCPListen.AcceptTcpClient();  
  
         //Create a network stream from the connection.  
         NetworkStream NetStream = TCP.GetStream();  
  
         //Create a new instance of the RijndaelManaged class  
         // and decrypt the stream.  
         RijndaelManaged RMCrypto = new RijndaelManaged();  
  
         //Create a CryptoStream, pass it the NetworkStream, and decrypt   
         //it with the Rijndael class using the key and IV.  
         CryptoStream CryptStream = new CryptoStream(NetStream,   
            RMCrypto.CreateDecryptor(Key, IV),   
            CryptoStreamMode.Read);  
  
         //Read the stream.  
         StreamReader SReader = new StreamReader(CryptStream);  
  
         //Display the message.  
         Console.WriteLine("The decrypted original message: {0}", SReader.ReadToEnd());  
  
         //Close the streams.  
         SReader.Close();  
         NetStream.Close();  
         TCP.Close();  
      }  
      //Catch any exceptions.   
      catch  
      {  
         Console.WriteLine("The Listener Failed.");  
      }  
   }  
}  
```  
  
 Dla powyższego przykładu pracy zaszyfrowanego połączenia muszą być wprowadzane do odbiornika. Połączenie musi używać tego samego klucza, IV i algorytm używany w odbiornika. Jeśli takie połączenie zostanie nawiązane, wiadomość jest odszyfrowywany i wyświetlane w konsoli.  
  
## <a name="asymmetric-decryption"></a>Odszyfrowanie asymetryczne  
 Zwykle firmy (strona A) generuje zarówno klucz publiczny i prywatny i przechowuje klucz w pamięci lub w kontenerze kluczy kryptograficznych.  Strona, następnie wysyła klucza publicznego do innej strony (strona B).  Za pomocą klucza publicznego, strona B dane są szyfrowane i wysyła dane do firmy A.  Po odebraniu danych, A strona odszyfrowuje ją przy użyciu klucza prywatnego, który odpowiada.  Odszyfrowywanie zakończy się pomyślnie, tylko wtedy, gdy strona A używa klucza prywatnego, który odpowiada klucza publicznego, który strona B używany do szyfrowania danych.  
  
 Aby uzyskać informacje dotyczące sposobu przechowywania klucza asymetrycznego bezpiecznego kontenera kluczy kryptograficznych i jak później pobrać klucza asymetrycznego, zobacz [porady: przechowywanie kluczy asymetrycznych w kontenerze klucza](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).  
  
 Poniższy przykład przedstawia odszyfrowywanie dwie tablice bajtów reprezentujących klucza symetrycznego i IV.  Aby uzyskać informacje dotyczące wyodrębniania publicznego klucza asymetrycznego z <xref:System.Security.Cryptography.RSACryptoServiceProvider> obiektu w formacie, który umożliwia łatwe wysyłanie do innej firmy, zobacz [szyfrowania danych](../../../docs/standard/security/encrypting-data.md).  
  
```vb  
'Create a new instance of the RSACryptoServiceProvider class.  
Dim RSA As New RSACryptoServiceProvider()  
  
' Export the public key information and send it to a third party.  
' Wait for the third party to encrypt some data and send it back.  
  
'Decrypt the symmetric key and IV.  
SymmetricKey = RSA.Decrypt(EncryptedSymmetricKey, False)  
SymmetricIV = RSA.Decrypt(EncryptedSymmetricIV, False)  
```  
  
```csharp  
//Create a new instance of the RSACryptoServiceProvider class.  
RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
  
// Export the public key information and send it to a third party.  
// Wait for the third party to encrypt some data and send it back.  
  
//Decrypt the symmetric key and IV.  
SymmetricKey = RSA.Decrypt( EncryptedSymmetricKey, false);  
SymmetricIV = RSA.Decrypt( EncryptedSymmetricIV , false);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Generowanie kluczy szyfrowania i odszyfrowywania](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
 [Szyfrowanie danych](../../../docs/standard/security/encrypting-data.md)  
 [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)
