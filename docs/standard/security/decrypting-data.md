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
ms.openlocfilehash: 37194380d9f08d328f836bcb8648772348958768
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706243"
---
# <a name="decrypting-data"></a>Odszyfrowywanie danych

Odszyfrowywanie jest odwrotną operacją szyfrowania. W przypadku szyfrowania klucza tajnego należy znać zarówno klucz, jak i IV, które były używane do szyfrowania danych. W przypadku szyfrowania klucza publicznego należy znać klucz publiczny (Jeśli dane zostały zaszyfrowane przy użyciu klucza prywatnego) lub klucza prywatnego (Jeśli dane zostały zaszyfrowane przy użyciu klucza publicznego).

## <a name="symmetric-decryption"></a>Odszyfrowywanie symetryczne

Odszyfrowywanie danych szyfrowanych za pomocą algorytmów symetrycznych jest podobne do procesu używanego do szyfrowania danych za pomocą algorytmów symetrycznych. Klasa <xref:System.Security.Cryptography.CryptoStream> jest używana z symetrycznymi klasami kryptografii udostępnianymi przez .NET Framework do odszyfrowywania danych odczytanych z dowolnego zarządzanego obiektu strumienia.

Poniższy przykład ilustruje sposób tworzenia nowego wystąpienia klasy <xref:System.Security.Cryptography.RijndaelManaged> i używania go do wykonania odszyfrowywania na obiekcie <xref:System.Security.Cryptography.CryptoStream>. Ten przykład najpierw tworzy nowe wystąpienie klasy **RijndaelManaged** . Następnie tworzy obiekt **CryptoStream** i inicjuje go do wartości strumienia zarządzanego o nazwie `myStream`. Następnie Metoda **odszyfrowania** z klasy **RijndaelManaged** jest przenoszona z tego samego klucza i IV, który był używany do szyfrowania, a następnie jest przenoszona do konstruktora **CryptoStream** . Na koniec Wyliczenie **CryptoStreamMode. Read** jest przesyłane do konstruktora **CryptoStream** w celu określenia dostępu do odczytu strumienia.

```vb
Dim rmCrypto As New RijndaelManaged()
Dim cryptStream As New CryptoStream(myStream, rmCrypto.CreateDecryptor(rmCrypto.Key, rmCrypto.IV), CryptoStreamMode.Read)
```

```csharp
RijndaelManaged rmCrypto = new RijndaelManaged();
CryptoStream cryptStream = new CryptoStream(myStream, rmCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read);
```

Poniższy przykład pokazuje cały proces tworzenia strumienia, odszyfrowywania strumienia, odczytywania ze strumienia i zamykania strumieni. Tworzony jest obiekt <xref:System.Net.Sockets.TcpListener>, który inicjuje strumień sieciowy w przypadku nawiązania połączenia z obiektem nasłuchiwania. Strumień sieciowy zostaje następnie odszyfrowany przy użyciu klasy **CryptoStream** i klasy **RijndaelManaged** . W tym przykładzie przyjęto założenie, że wartości key i IV zostały pomyślnie przeniesione lub wcześniej uzgodnione. Nie jest wyświetlany kod wymagany do szyfrowania i transferu tych wartości.

```vb
Imports System.IO
Imports System.Net
Imports System.Net.Sockets
Imports System.Security.Cryptography
Imports System.Threading

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
using System.IO;
using System.Net;
using System.Net.Sockets;
using System.Security.Cryptography;
using System.Threading;

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

Aby powyższy przykład działał, należy nawiązać połączenie szyfrowane z odbiornikiem. Połączenie musi używać tego samego klucza, IV i algorytmu, który jest używany w odbiorniku. Jeśli takie połączenie jest nawiązywane, komunikat jest odszyfrowywany i wyświetlany w konsoli programu.

## <a name="asymmetric-decryption"></a>Odszyfrowywanie asymetryczne

Zazwyczaj strona (Strona A) generuje zarówno klucz publiczny, jak i prywatny, a klucz jest przechowywany w pamięci lub w kontenerze kluczy kryptograficznych. Następnie firma A następnie wysyła klucz publiczny do innej strony (strona B). Przy użyciu klucza publicznego Strona B szyfruje dane i wysyła je z powrotem do strony A. Po odebraniu danych firma odszyfruje je przy użyciu klucza prywatnego, który odpowiada. Odszyfrowywanie powiedzie się tylko wtedy, gdy strona A używa klucza prywatnego, który odpowiada stronie klucza publicznego, który jest używany do szyfrowania danych.

Aby uzyskać informacje na temat sposobu przechowywania klucza asymetrycznego w bezpiecznym kontenerze kluczy kryptograficznych i sposobie późniejszego pobierania klucza asymetrycznego, zobacz [How to: Store asymetryczne klucze w kontenerze kluczy](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).

Poniższy przykład ilustruje odszyfrowywanie dwóch tablic bajtów reprezentujących klucz symetryczny i IV. Aby uzyskać informacje na temat sposobu wyodrębniania asymetrycznego klucza publicznego z obiektu <xref:System.Security.Cryptography.RSACryptoServiceProvider> w formacie, który można łatwo przesłać do innej firmy, zobacz temat [szyfrowanie danych](../../../docs/standard/security/encrypting-data.md).

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
