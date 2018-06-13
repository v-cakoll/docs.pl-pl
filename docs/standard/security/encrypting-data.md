---
title: Szyfrowanie danych
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET Framework], symmetric
- symmetric encryption
- cryptography [.NET Framework], asymmetric
- asymmetric encryption
ms.assetid: 7ecce51f-db5f-4bd4-9321-cceb6fcb2a77
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 39dd7bfe4e5dd3405e24bf044723dbd92ccc65a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589831"
---
# <a name="encrypting-data"></a>Szyfrowanie danych
Szyfrowanie symetryczne i szyfrowanie asymetryczne są wykonywane przy użyciu różnych procesów. Szyfrowanie symetryczne odbywa się na strumienie i dlatego jest przydatne do szyfrowania dużych ilości danych. Szyfrowanie asymetryczne odbywa się na niewielką liczbę bajtów i dlatego jest użyteczna tylko w przypadku niewielkich ilości danych.  
  
## <a name="symmetric-encryption"></a>Szyfrowanie symetryczne  
 Klasy zarządzane Kryptografia symetryczna są używane z klasy specjalne strumienia o nazwie <xref:System.Security.Cryptography.CryptoStream> który szyfruje dane odczytane w strumieniu. **CryptoStream** klasy jest inicjowany z klasy zarządzanego strumienia, klasa implementuje <xref:System.Security.Cryptography.ICryptoTransform> interfejsu (utworzone z klasy, która implementuje algorytm kryptograficzny), a <xref:System.Security.Cryptography.CryptoStreamMode> wyliczenie który Opisuje typ dostępu mogą **CryptoStream**. **CryptoStream** klasy mogą być inicjowane przy użyciu dowolnej klasy, która jest pochodną <xref:System.IO.Stream> klasy, w tym <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, i <xref:System.Net.Sockets.NetworkStream>. Korzystanie z tych klas, można wykonać szyfrowania symetrycznego na różnych obiektów strumienia.  
  
 Poniższy przykład przedstawia sposób utworzyć nowe wystąpienie klasy <xref:System.Security.Cryptography.RijndaelManaged> klasy, która implementuje algorytmu szyfrowania Rijndael i umożliwia szyfrowanie na **CryptoStream** klasy. W tym przykładzie **CryptoStream** jest inicjowany z obiektu strumienia, nazywany `MyStream` które może być dowolnego typu zarządzanego strumienia. **CreateEncryptor** metody z **RijndaelManaged** klasy jest przekazywany klucza i IV, które są używane do szyfrowania. W takim przypadku wygenerowany domyślny klucz i IV z `RMCrypto` są używane. Na koniec **CryptoStreamMode.Write** jest przekazywana, określając dostęp do zapisu do strumienia.  
  
```vb  
Dim RMCrypto As New RijndaelManaged()  
Dim CryptStream As New CryptoStream(MyStream, RMCrypto.CreateEncryptor(RMCrypto.Key, RMCrypto.IV), CryptoStreamMode.Write)  
```  
  
```csharp  
RijndaelManaged RMCrypto = new RijndaelManaged();  
CryptoStream CryptStream = new CryptoStream(MyStream, RMCrypto.CreateEncryptor(), CryptoStreamMode.Write);  
```  
  
 Po wykonaniu tego kodu, wszystkie dane zapisane **CryptoStream** obiektu jest szyfrowana przy użyciu algorytmu Rijndael.  
  
 Poniższy przykład przedstawia cały proces tworzenia strumienia, szyfrowania strumień zapisu do strumienia i zamknięcie strumienia. W tym przykładzie tworzy strumień sieci, który jest szyfrowana przy użyciu **CryptoStream** klasy i **RijndaelManaged** klasy. Komunikat jest zapisywane do strumienia zaszyfrowanych z <xref:System.IO.StreamWriter> klasy.  
  
> [!NOTE]
>  W tym przykładzie służy również do zapisu do pliku. Aby to zrobić, należy usunąć <xref:System.Net.Sockets.TcpClient> odwołania oraz Zastąp <xref:System.Net.Sockets.NetworkStream> z <xref:System.IO.FileStream>.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Security.Cryptography  
Imports System.Net.Sockets  
  
Module Module1  
Sub Main()  
   Try  
      'Create a TCP connection to a listening TCP process.  
      'Use "localhost" to specify the current computer or  
      'replace "localhost" with the IP address of the   
      'listening process.   
      Dim TCP As New TcpClient("localhost", 11000)  
  
      'Create a network stream from the TCP connection.   
      Dim NetStream As NetworkStream = TCP.GetStream()  
  
      'Create a new instance of the RijndaelManaged class  
      'and encrypt the stream.  
      Dim RMCrypto As New RijndaelManaged()  
  
            Dim Key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
            Dim IV As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
  
      'Create a CryptoStream, pass it the NetworkStream, and encrypt   
      'it with the Rijndael class.  
      Dim CryptStream As New CryptoStream(NetStream, RMCrypto.CreateEncryptor(Key, IV), CryptoStreamMode.Write)  
  
      'Create a StreamWriter for easy writing to the   
      'network stream.  
      Dim SWriter As New StreamWriter(CryptStream)  
  
      'Write to the stream.  
      SWriter.WriteLine("Hello World!")  
  
      'Inform the user that the message was written  
      'to the stream.  
      Console.WriteLine("The message was sent.")  
  
      'Close all the connections.  
      SWriter.Close()  
      CryptStream.Close()  
      NetStream.Close()  
      TCP.Close()  
   Catch  
      'Inform the user that an exception was raised.  
      Console.WriteLine("The connection failed.")  
   End Try  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Security.Cryptography;  
using System.Net.Sockets;  
  
public class main  
{  
   public static void Main(string[] args)  
   {  
      try  
      {  
         //Create a TCP connection to a listening TCP process.  
         //Use "localhost" to specify the current computer or  
         //replace "localhost" with the IP address of the   
         //listening process.    
         TcpClient TCP = new TcpClient("localhost",11000);  
  
         //Create a network stream from the TCP connection.   
         NetworkStream NetStream = TCP.GetStream();  
  
         //Create a new instance of the RijndaelManaged class  
         // and encrypt the stream.  
         RijndaelManaged RMCrypto = new RijndaelManaged();  
  
         byte[] Key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
         byte[] IV = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
  
         //Create a CryptoStream, pass it the NetworkStream, and encrypt   
         //it with the Rijndael class.  
         CryptoStream CryptStream = new CryptoStream(NetStream,   
         RMCrypto.CreateEncryptor(Key, IV),     
         CryptoStreamMode.Write);  
  
         //Create a StreamWriter for easy writing to the   
         //network stream.  
         StreamWriter SWriter = new StreamWriter(CryptStream);  
  
         //Write to the stream.  
         SWriter.WriteLine("Hello World!");  
  
         //Inform the user that the message was written  
         //to the stream.  
         Console.WriteLine("The message was sent.");  
  
         //Close all the connections.  
         SWriter.Close();  
         CryptStream.Close();  
         NetStream.Close();  
         TCP.Close();  
      }  
      catch  
      {  
         //Inform the user that an exception was raised.  
         Console.WriteLine("The connection failed.");  
      }  
   }  
}  
```  
  
 W poprzednim przykładzie się pomyślnie, musi być procesem nasłuchiwanie na adresie IP i numer portu określone w <xref:System.Net.Sockets.TcpClient> klasy. Jeśli istnieje proces nasłuchiwania, kod będzie połączyć się z procesem nasłuchiwania, szyfrowania przy użyciu algorytmu symetrycznego Rijndael strumienia i zapisać "Witaj świecie!" w strumieniu. Jeśli kod zakończy się pomyślnie, wyświetla następujący tekst do konsoli:  
  
```  
The message was sent.  
```  
  
 Jednak jeśli nie znaleziono żadnych nasłuchiwania procesu lub zgłoszony wyjątek, kod wyświetla następujący tekst do konsoli:  
  
```  
The connection failed.  
```  
  
## <a name="asymmetric-encryption"></a>Szyfrowanie asymetryczne  
 Asymetryczne algorytmy są zazwyczaj używany do szyfrowania niewielkich ilości danych, takimi jak szyfrowanie klucza symetrycznego i IV. Zazwyczaj poszczególnych wykonuje szyfrowanie asymetryczne używa klucza publicznego, generowane przez inną firmę. <xref:System.Security.Cryptography.RSACryptoServiceProvider> Klasy podano w tym celu w programie .NET Framework.  
  
 W poniższym przykładzie użyto informacje o kluczu publicznym do szyfrowania klucza symetrycznego i IV. Tablice typu byte dwóch są inicjowane reprezentujących klucza publicznego innej firmy. <xref:System.Security.Cryptography.RSAParameters> Obiekt został zainicjowany tych wartości. Następnie **RSAParameters** obiektu (wraz z klucza publicznego, który reprezentuje) jest importowany do **RSACryptoServiceProvider** przy użyciu <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> metody. Na koniec klucza prywatnego i IV utworzonych przez <xref:System.Security.Cryptography.RijndaelManaged> klasy są szyfrowane. W tym przykładzie wymaga 128-bitowe szyfrowanie zainstalowane.  
  
```vb  
Imports System  
Imports System.Security.Cryptography  
  
Module Module1  
  
    Sub Main()  
        'Initialize the byte arrays to the public key information.  
      Dim PublicKey As Byte() =  {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19,202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147}  
  
        Dim Exponent As Byte() = {1, 0, 1}  
  
        'Create values to store encrypted symmetric keys.  
        Dim EncryptedSymmetricKey() As Byte  
        Dim EncryptedSymmetricIV() As Byte  
  
        'Create a new instance of the RSACryptoServiceProvider class.  
        Dim RSA As New RSACryptoServiceProvider()  
  
        'Create a new instance of the RSAParameters structure.  
        Dim RSAKeyInfo As New RSAParameters()  
  
        'Set RSAKeyInfo to the public key values.   
        RSAKeyInfo.Modulus = PublicKey  
        RSAKeyInfo.Exponent = Exponent  
  
        'Import key parameters into RSA.  
        RSA.ImportParameters(RSAKeyInfo)  
  
        'Create a new instance of the RijndaelManaged class.  
        Dim RM As New RijndaelManaged()  
  
        'Encrypt the symmetric key and IV.  
        EncryptedSymmetricKey = RSA.Encrypt(RM.Key, False)  
        EncryptedSymmetricIV = RSA.Encrypt(RM.IV, False)  
    End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using System.Security.Cryptography;  
  
class Class1  
{  
   static void Main()  
   {  
      //Initialize the byte arrays to the public key information.  
      byte[] PublicKey = {214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56,  
            74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222,  
            207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175,  
            108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194,  
            240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139,  
            168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171,  
            38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93,  
            106,99,179,68,175,211,164,116,64,148,226,254,172,147};  
  
      byte[] Exponent = {1,0,1};  
  
      //Create values to store encrypted symmetric keys.  
      byte[] EncryptedSymmetricKey;  
      byte[] EncryptedSymmetricIV;  
  
      //Create a new instance of the RSACryptoServiceProvider class.  
      RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
  
      //Create a new instance of the RSAParameters structure.  
      RSAParameters RSAKeyInfo = new RSAParameters();  
  
      //Set RSAKeyInfo to the public key values.   
      RSAKeyInfo.Modulus = PublicKey;  
      RSAKeyInfo.Exponent = Exponent;  
  
      //Import key parameters into RSA.  
      RSA.ImportParameters(RSAKeyInfo);  
  
      //Create a new instance of the RijndaelManaged class.  
      RijndaelManaged RM = new RijndaelManaged();  
  
      //Encrypt the symmetric key and IV.  
      EncryptedSymmetricKey = RSA.Encrypt(RM.Key, false);  
      EncryptedSymmetricIV = RSA.Encrypt(RM.IV, false);  
   }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Generowanie kluczy szyfrowania i odszyfrowywania](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
 [Odszyfrowywanie danych](../../../docs/standard/security/decrypting-data.md)  
 [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)
