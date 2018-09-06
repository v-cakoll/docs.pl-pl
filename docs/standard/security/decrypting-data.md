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
ms.openlocfilehash: b3e48d5a088fc6cff3dbdaaa77e6fa561c33f400
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865524"
---
# <a name="decrypting-data"></a>Odszyfrowywanie danych
Odszyfrowywanie jest odwrotna operacji szyfrowania. Klucz tajny szyfrowania musisz wiedzieć, zarówno klucz, jak i IV, które były używane do szyfrowania danych. Do szyfrowania klucza publicznego należy znać klucza publicznego (jeśli zostały zaszyfrowane przy użyciu klucza prywatnego) lub klucza prywatnego (jeśli zostały zaszyfrowane przy użyciu klucza publicznego).  
  
## <a name="symmetric-decryption"></a>Odszyfrowanie symetryczne  
 Odszyfrowywanie danych zaszyfrowanych przy użyciu algorytmów symetrycznych jest podobny do procesu, używany do szyfrowania danych przy użyciu algorytmów symetrycznych. <xref:System.Security.Cryptography.CryptoStream> Klasa jest używana z klasami Kryptografia symetryczna dostarczane przez program .NET Framework do odszyfrowania danych odczytanych z dowolnego obiektu zarządzanego strumienia.  
  
 Poniższy przykład ilustruje sposób tworzenia nowego wystąpienia <xref:System.Security.Cryptography.RijndaelManaged> klasy i użyć go do przeprowadzania odszyfrowywania <xref:System.Security.Cryptography.CryptoStream> obiektu. W tym przykładzie najpierw tworzy nowe wystąpienie klasy **RijndaelManaged** klasy. Następnie tworzy **CryptoStream** obiektu i inicjuje ją na wartość zarządzany strumień o nazwie `MyStream`. Następnie **CreateDecryptor** metody z **RijndaelManaged** klasy jest przekazywany w ten sam klucz i IV, który został użyty do szyfrowania i jest następnie przekazywany do **CryptoStream** Konstruktor. Na koniec **CryptoStreamMode.Read** wyliczenia jest przekazywany do **CryptoStream** konstruktora, aby określić strumień do odczytu.  
  
```vb  
Dim RMCrypto As New RijndaelManaged()  
Dim CryptStream As New CryptoStream(MyStream, RMCrypto.CreateDecryptor(RMCrypto.Key, RMCrypto.IV), CryptoStreamMode.Read)  
```  
  
```csharp  
RijndaelManaged RMCrypto = new RijndaelManaged();  
CryptoStream CryptStream = new CryptoStream(MyStream, RMCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read);  
```  
  
 Poniższy przykład pokazuje cały proces tworzenia strumienia, odszyfrowywania strumienia, odczytywania ze strumienia i zamyka strumieni. A <xref:System.Net.Sockets.TcpListener> tworzony jest obiekt, który inicjuje strumień sieciowych po nawiązaniu połączenia z obiektem nasłuchiwania. Strumień sieciowych jest odszyfrowywany za pomocą **CryptoStream** klasy i **RijndaelManaged** klasy. W tym przykładzie przyjęto założenie, że klucza i wartości IV mają została pomyślnie przeniesiona lub wcześniej uzgodnione. Kod potrzebny do szyfrowania i przenieść te wartości nie są wyświetlane.  
  
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
  
 Do działania poprzedniego przykładu należy dokonać szyfrowanego połączenia do odbiornika. Połączenia należy użyć tego samego klucza, IV i algorytm używany w odbiornika. Jeśli takie połączenie, komunikat jest odszyfrowywany i wyświetlana w konsoli.  
  
## <a name="asymmetric-decryption"></a>Odszyfrowanie asymetryczne  
 Zazwyczaj strona (strona: A) generuje zarówno klucz publiczny i prywatny, a przechowuje klucz w pamięci lub w kontenerze kluczy kryptograficznych.  Innych firm, następnie wysyła klucz publiczny do innej strony (strona B).  Przy użyciu klucza publicznego, strona B szyfruje dane i wysyła dane do firmy A.  Po otrzymaniu danych, A strona odszyfrowuje je przy użyciu klucza prywatnego, który odpowiada.  Odszyfrowywanie zakończą się pomyślnie, tylko wtedy, gdy strona A używa klucza prywatnego, który odnosi się do klucza publicznego, który B innych firm używane do szyfrowania danych.  
  
 Aby uzyskać informacje na temat przechowywania klucza asymetrycznego, w bezpiecznej kontenera kluczy kryptograficznych i jak można później pobrać klucza asymetrycznego, zobacz [jak: Store Asymmetric Keys in a Key Container](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).  
  
 Poniższy przykład ilustruje odszyfrowywania dwie tablice bajtów reprezentujących klucz symetryczny i IV.  Aby uzyskać informacje dotyczące można wyodrębnić klucza publicznego asymetrycznego z <xref:System.Security.Cryptography.RSACryptoServiceProvider> obiekt w formacie, który umożliwia łatwe wysyłanie do innej, zobacz [szyfrowania danych](../../../docs/standard/security/encrypting-data.md).  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Generowanie kluczy szyfrowania i odszyfrowywania](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
- [Szyfrowanie danych](../../../docs/standard/security/encrypting-data.md)  
- [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)
