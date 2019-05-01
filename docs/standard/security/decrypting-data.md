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
ms.openlocfilehash: 4cf0ffae2c5803324d4941581855d5dc10224e07
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795229"
---
# <a name="decrypting-data"></a>Odszyfrowywanie danych

Odszyfrowywanie jest odwrotna operacji szyfrowania. Klucz tajny szyfrowania musisz wiedzieć, zarówno klucz, jak i IV, które były używane do szyfrowania danych. Do szyfrowania klucza publicznego należy znać klucza publicznego (jeśli zostały zaszyfrowane przy użyciu klucza prywatnego) lub klucza prywatnego (jeśli zostały zaszyfrowane przy użyciu klucza publicznego).

## <a name="symmetric-decryption"></a>Odszyfrowanie symetryczne

Odszyfrowywanie danych zaszyfrowanych przy użyciu algorytmów symetrycznych jest podobny do procesu, używany do szyfrowania danych przy użyciu algorytmów symetrycznych. <xref:System.Security.Cryptography.CryptoStream> Klasa jest używana z klasami Kryptografia symetryczna dostarczane przez program .NET Framework do odszyfrowania danych odczytanych z dowolnego obiektu zarządzanego strumienia.

Poniższy przykład ilustruje sposób tworzenia nowego wystąpienia <xref:System.Security.Cryptography.RijndaelManaged> klasy i użyć go do przeprowadzania odszyfrowywania <xref:System.Security.Cryptography.CryptoStream> obiektu. W tym przykładzie najpierw tworzy nowe wystąpienie klasy **RijndaelManaged** klasy. Następnie tworzy **CryptoStream** obiektu i inicjuje ją na wartość zarządzany strumień o nazwie `myStream`. Następnie **CreateDecryptor** metody z **RijndaelManaged** klasy jest przekazywany w ten sam klucz i IV, który został użyty do szyfrowania i jest następnie przekazywany do **CryptoStream** Konstruktor. Na koniec **CryptoStreamMode.Read** wyliczenia jest przekazywany do **CryptoStream** konstruktora, aby określić strumień do odczytu.

```vb
Dim rmCrypto As New RijndaelManaged()
Dim cryptStream As New CryptoStream(myStream, rmCrypto.CreateDecryptor(rmCrypto.Key, rmCrypto.IV), CryptoStreamMode.Read)
```

```csharp
RijndaelManaged rmCrypto = new RijndaelManaged();
CryptoStream cryptStream = new CryptoStream(myStream, rmCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read);
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
            Dim key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}
            Dim iv As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}
        Try
            'Initialize a TCPListener on port 11000
            'using the current IP address.
            Dim tcpListen As New TcpListener(IPAddress.Any, 11000)

            'Start the listener.
            tcpListen.Start()

            'Check for a connection every five seconds.
            While Not tcpListen.Pending()
                Console.WriteLine("Still listening. Will try in 5 seconds.")

                Thread.Sleep(5000)
            End While

            'Accept the client if one is found.
            Dim tcp As TcpClient = tcpListen.AcceptTcpClient()

            'Create a network stream from the connection.
            Dim netStream As NetworkStream = tcp.GetStream()

            'Create a new instance of the RijndaelManaged class
            'and decrypt the stream.
            Dim rmCrypto As New RijndaelManaged()

            'Create an instance of the CryptoStream class, pass it the NetworkStream, and decrypt
            'it with the Rijndael class using the key and IV.
            Dim cryptStream As New CryptoStream(netStream, rmCrypto.CreateDecryptor(key, iv), CryptoStreamMode.Read)

            'Read the stream.
            Dim sReader As New StreamReader(cryptStream)

            'Display the message.
            Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd())

            'Close the streams.
            sReader.Close()
            netStream.Close()
            tcp.Close()
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
      byte[] key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};
      byte[] iv = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};
      try
      {
         //Initialize a TCPListener on port 11000
         //using the current IP address.
         TcpListener tcpListen = new TcpListener(IPAddress.Any, 11000);

         //Start the listener.
         tcpListen.Start();

         //Check for a connection every five seconds.
         while(!tcpListen.Pending())
         {
            Console.WriteLine("Still listening. Will try in 5 seconds.");
            Thread.Sleep(5000);
         }

         //Accept the client if one is found.
         TcpClient tcp = tcpListen.AcceptTcpClient();

         //Create a network stream from the connection.
         NetworkStream netStream = tcp.GetStream();

         //Create a new instance of the RijndaelManaged class
         // and decrypt the stream.
         RijndaelManaged rmCrypto = new RijndaelManaged();

         //Create a CryptoStream, pass it the NetworkStream, and decrypt
         //it with the Rijndael class using the key and IV.
         CryptoStream cryptStream = new CryptoStream(netStream,
            rmCrypto.CreateDecryptor(key, iv),
            CryptoStreamMode.Read);

         //Read the stream.
         StreamReader sReader = new StreamReader(cryptStream);

         //Display the message.
         Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd());

         //Close the streams.
         sReader.Close();
         netStream.Close();
         tcp.Close();
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

Zazwyczaj strona (strona: A) generuje zarówno klucz publiczny i prywatny, a przechowuje klucz w pamięci lub w kontenerze kluczy kryptograficznych. Innych firm, następnie wysyła klucz publiczny do innej strony (strona B). Przy użyciu klucza publicznego, strona B szyfruje dane i wysyła dane do firmy A. Po otrzymaniu danych, A strona odszyfrowuje je przy użyciu klucza prywatnego, który odpowiada. Odszyfrowywanie zakończą się pomyślnie, tylko wtedy, gdy strona A używa klucza prywatnego, który odnosi się do klucza publicznego, który B innych firm używane do szyfrowania danych.

Aby uzyskać informacje na temat przechowywania klucza asymetrycznego, w bezpiecznej kontenera kluczy kryptograficznych i jak można później pobrać klucza asymetrycznego, zobacz [jak: Store kluczy asymetrycznych w kontenerze kluczy](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).

Poniższy przykład ilustruje odszyfrowywania dwie tablice bajtów reprezentujących klucz symetryczny i IV. Aby uzyskać informacje dotyczące można wyodrębnić klucza publicznego asymetrycznego z <xref:System.Security.Cryptography.RSACryptoServiceProvider> obiekt w formacie, który umożliwia łatwe wysyłanie do innej, zobacz [szyfrowania danych](../../../docs/standard/security/encrypting-data.md).

```vb
'Create a new instance of the RSACryptoServiceProvider class.
Dim rsa As New RSACryptoServiceProvider()

' Export the public key information and send it to a third party.
' Wait for the third party to encrypt some data and send it back.

'Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, False)
symmetricIV = rsa.Decrypt(encryptedSymmetricIV, False)
```

```csharp
//Create a new instance of the RSACryptoServiceProvider class.
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();

// Export the public key information and send it to a third party.
// Wait for the third party to encrypt some data and send it back.

//Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, false);
symmetricIV = rsa.Decrypt(encryptedSymmetricIV , false);
```

## <a name="see-also"></a>Zobacz także

- [Generowanie kluczy szyfrowania i odszyfrowywania](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)
- [Szyfrowanie danych](../../../docs/standard/security/encrypting-data.md)
- [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)
