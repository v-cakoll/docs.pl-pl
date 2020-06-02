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
ms.openlocfilehash: 3230836b93ea191e5de27717a918038f2f8dead6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288358"
---
# <a name="encrypting-data"></a>Szyfrowanie danych
Szyfrowanie symetryczne i szyfrowanie asymetryczne są wykonywane przy użyciu różnych procesów. Szyfrowanie symetryczne jest wykonywane na strumieniach i dlatego jest przydatne do szyfrowania dużych ilości danych. Szyfrowanie asymetryczne jest wykonywane w niewielkiej liczbie bajtów i dlatego jest przydatne tylko w przypadku małych ilości danych.  
  
## <a name="symmetric-encryption"></a>Szyfrowanie symetryczne  
 Zarządzane klasy kryptografii symetrycznej są używane z specjalną klasą strumienia o nazwie a <xref:System.Security.Cryptography.CryptoStream> , która szyfruje dane odczytane do strumienia. Klasa **CryptoStream** została zainicjowana za pomocą zarządzanej klasy strumienia, Klasa implementuje <xref:System.Security.Cryptography.ICryptoTransform> interfejs (utworzony z klasy implementującej algorytm kryptograficzny) i <xref:System.Security.Cryptography.CryptoStreamMode> Wyliczenie, które opisuje typ dostępu, który jest dozwolony dla **CryptoStream**. Klasę **CryptoStream** można zainicjować przy użyciu dowolnej klasy, która dziedziczy z <xref:System.IO.Stream> klasy, w tym <xref:System.IO.FileStream> , <xref:System.IO.MemoryStream> , i <xref:System.Net.Sockets.NetworkStream> . Za pomocą tych klas można wykonać szyfrowanie symetryczne na różnych obiektach strumienia.  
  
 Poniższy przykład ilustruje, jak utworzyć nowe wystąpienie <xref:System.Security.Cryptography.RijndaelManaged> klasy, która implementuje algorytm szyfrowania Rijndael, i użyć go do wykonania szyfrowania klasy **CryptoStream** . W tym przykładzie **CryptoStream** jest inicjowany przy użyciu obiektu Stream o nazwie `myStream` , który może być dowolnym typem strumienia zarządzanego. Metoda **coclass** z klasy **RijndaelManaged** jest przenoszona z klucza i IV, który jest używany do szyfrowania. W takim przypadku użyto klucza domyślnego i dodatku IV wygenerowanego z `rmCrypto` . Na koniec **CryptoStreamMode. Write** jest przenoszona, określając dostęp do zapisu w strumieniu.  
  
```vb  
Dim rmCrypto As New RijndaelManaged()  
Dim cryptStream As New CryptoStream(myStream, rmCrypto.CreateEncryptor(rmCrypto.Key, rmCrypto.IV), CryptoStreamMode.Write)  
```  
  
```csharp  
RijndaelManaged rmCrypto = new RijndaelManaged();  
CryptoStream cryptStream = new CryptoStream(myStream, rmCrypto.CreateEncryptor(), CryptoStreamMode.Write);  
```  
  
 Po wykonaniu tego kodu wszystkie dane zapisywane w obiekcie **CryptoStream** są szyfrowane przy użyciu algorytmu Rijndael.  
  
 Poniższy przykład pokazuje cały proces tworzenia strumienia, szyfrowania strumienia, zapisywania do strumienia i zamykania strumienia. W tym przykładzie tworzony jest strumień sieciowy szyfrowany przy użyciu klasy **CryptoStream** i klasy **RijndaelManaged** . Wiadomość jest zapisywana w zaszyfrowanym strumieniu z <xref:System.IO.StreamWriter> klasą.  
  
> [!NOTE]
> Tego przykładu można również użyć do zapisu w pliku. Aby to zrobić, Usuń <xref:System.Net.Sockets.TcpClient> odwołanie i Zastąp <xref:System.Net.Sockets.NetworkStream> element elementem <xref:System.IO.FileStream> .  
  
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
      Dim tcp As New TcpClient("localhost", 11000)  
  
      'Create a network stream from the TCP connection.
      Dim netStream As NetworkStream = tcp.GetStream()  
  
      'Create a new instance of the RijndaelManaged class  
      'and encrypt the stream.  
      Dim rmCrypto As New RijndaelManaged()  
  
            Dim key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
            Dim iv As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
  
      'Create a CryptoStream, pass it the NetworkStream, and encrypt
      'it with the Rijndael class.  
      Dim cryptStream As New CryptoStream(netStream, rmCrypto.CreateEncryptor(key, iv), CryptoStreamMode.Write)  
  
      'Create a StreamWriter for easy writing to the
      'network stream.  
      Dim sWriter As New StreamWriter(cryptStream)  
  
      'Write to the stream.  
      sWriter.WriteLine("Hello World!")  
  
      'Inform the user that the message was written  
      'to the stream.  
      Console.WriteLine("The message was sent.")  
  
      'Close all the connections.  
      sWriter.Close()  
      cryptStream.Close()  
      netStream.Close()  
      tcp.Close()  
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
         TcpClient tcp = new TcpClient("localhost",11000);  
  
         //Create a network stream from the TCP connection.
         NetworkStream netStream = tcp.GetStream();  
  
         //Create a new instance of the RijndaelManaged class  
         // and encrypt the stream.  
         RijndaelManaged rmCrypto = new RijndaelManaged();  
  
         byte[] key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
         byte[] iv = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
  
         //Create a CryptoStream, pass it the NetworkStream, and encrypt
         //it with the Rijndael class.  
         CryptoStream cryptStream = new CryptoStream(netStream,
         rmCrypto.CreateEncryptor(key, iv),
         CryptoStreamMode.Write);  
  
         //Create a StreamWriter for easy writing to the
         //network stream.  
         StreamWriter sWriter = new StreamWriter(cryptStream);  
  
         //Write to the stream.  
         sWriter.WriteLine("Hello World!");  
  
         //Inform the user that the message was written  
         //to the stream.  
         Console.WriteLine("The message was sent.");  
  
         //Close all the connections.  
         sWriter.Close();  
         cryptStream.Close();  
         netStream.Close();  
         tcp.Close();  
      }  
      catch  
      {  
         //Inform the user that an exception was raised.  
         Console.WriteLine("The connection failed.");  
      }  
   }  
}  
```  
  
 Aby można było pomyślnie wykonać poprzedni przykład, musi istnieć proces nasłuchiwania na adresie IP i numer portu określony w <xref:System.Net.Sockets.TcpClient> klasie. Jeśli istnieje proces nasłuchiwania, kod nawiąże połączenie z procesem nasłuchiwania, szyfruje strumień przy użyciu algorytmu symetrycznego Rijndael i pisze "Hello world!" do strumienia. Jeśli kod powiedzie się, w konsoli zostanie wyświetlony następujący tekst:  
  
```console  
The message was sent.  
```  
  
 Jeśli jednak nie zostanie znaleziony żaden proces nasłuchujący lub wystąpił wyjątek, kod wyświetla następujący tekst w konsoli programu:  
  
```console  
The connection failed.  
```  
  
## <a name="asymmetric-encryption"></a>Szyfrowanie asymetryczne  
 Algorytmy asymetryczne są zwykle używane do szyfrowania małych ilości danych, takich jak szyfrowanie klucza symetrycznego i IV. Zazwyczaj pojedyncze wykonywanie szyfrowania asymetrycznego używa klucza publicznego wygenerowanego przez inną firmę. W <xref:System.Security.Cryptography.RSACryptoServiceProvider> tym celu Klasa jest udostępniana przez .NET Framework.  
  
 Poniższy przykład używa informacji o kluczu publicznym do szyfrowania klucza symetrycznego i IV. Są inicjowane dwubajtowe tablice reprezentujące klucz publiczny strony trzeciej. <xref:System.Security.Cryptography.RSAParameters>Obiekt jest zainicjowany do tych wartości. Następnie obiekt **RSAParameters** (wraz z kluczem publicznym, który reprezentuje) jest importowany do **RSACryptoServiceProvider** przy użyciu <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> metody. Na koniec klucz prywatny i IV tworzony przez <xref:System.Security.Cryptography.RijndaelManaged> klasę są szyfrowane. Ten przykład wymaga, aby systemy miały zainstalowane szyfrowanie 128-bitowe.  
  
```vb  
Imports System  
Imports System.Security.Cryptography  
  
Module Module1  
  
    Sub Main()  
        'Initialize the byte arrays to the public key information.  
      Dim publicKey As Byte() =  {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19,202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147}  
  
        Dim exponent As Byte() = {1, 0, 1}  
  
        'Create values to store encrypted symmetric keys.  
        Dim encryptedSymmetricKey() As Byte  
        Dim encryptedSymmetricIV() As Byte  
  
        'Create a new instance of the RSACryptoServiceProvider class.  
        Dim rsa As New RSACryptoServiceProvider()  
  
        'Create a new instance of the RSAParameters structure.  
        Dim rsaKeyInfo As New RSAParameters()  
  
        'Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = publicKey  
        rsaKeyInfo.Exponent = exponent  
  
        'Import key parameters into rsa.  
        rsa.ImportParameters(rsaKeyInfo)  
  
        'Create a new instance of the RijndaelManaged class.  
        Dim RM As New RijndaelManaged()  
  
        'Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(RM.Key, False)  
        encryptedSymmetricIV = rsa.Encrypt(RM.IV, False)  
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
      byte[] publicKey = {214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56,  
            74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222,  
            207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175,  
            108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194,  
            240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139,  
            168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171,  
            38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93,  
            106,99,179,68,175,211,164,116,64,148,226,254,172,147};  
  
      byte[] exponent = {1,0,1};  
  
      //Create values to store encrypted symmetric keys.  
      byte[] encryptedSymmetricKey;  
      byte[] encryptedSymmetricIV;  
  
      //Create a new instance of the RSACryptoServiceProvider class.  
      RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();  
  
      //Create a new instance of the RSAParameters structure.  
      RSAParameters rsaKeyInfo = new RSAParameters();  
  
      //Set rsaKeyInfo to the public key values.
      rsaKeyInfo.Modulus = publicKey;  
      rsaKeyInfo.Exponent = exponent;  
  
      //Import key parameters into RSA.  
      rsa.ImportParameters(rsaKeyInfo);  
  
      //Create a new instance of the RijndaelManaged class.  
      RijndaelManaged rm = new RijndaelManaged();  
  
      //Encrypt the symmetric key and IV.  
      encryptedSymmetricKey = rsa.Encrypt(rm.Key, false);  
      encryptedSymmetricIV = rsa.Encrypt(rm.IV, false);  
   }  
}  
```  
  
## <a name="see-also"></a>Zobacz także

- [Generowanie kluczy szyfrowania i odszyfrowywania](generating-keys-for-encryption-and-decryption.md)
- [Odszyfrowywanie danych](decrypting-data.md)
- [Usługi kryptograficzne](cryptographic-services.md)
