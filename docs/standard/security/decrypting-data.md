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
# <a name="decrypting-data"></a><span data-ttu-id="cec83-102">Odszyfrowywanie danych</span><span class="sxs-lookup"><span data-stu-id="cec83-102">Decrypting Data</span></span>

<span data-ttu-id="cec83-103">Odszyfrowywanie jest odwrotną operacją szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="cec83-103">Decryption is the reverse operation of encryption.</span></span> <span data-ttu-id="cec83-104">W przypadku szyfrowania klucza tajnego należy znać zarówno klucz, jak i IV, które były używane do szyfrowania danych.</span><span class="sxs-lookup"><span data-stu-id="cec83-104">For secret-key encryption, you must know both the key and IV that were used to encrypt the data.</span></span> <span data-ttu-id="cec83-105">W przypadku szyfrowania klucza publicznego należy znać klucz publiczny (Jeśli dane zostały zaszyfrowane przy użyciu klucza prywatnego) lub klucza prywatnego (Jeśli dane zostały zaszyfrowane przy użyciu klucza publicznego).</span><span class="sxs-lookup"><span data-stu-id="cec83-105">For public-key encryption, you must know either the public key (if the data was encrypted using the private key) or the private key (if the data was encrypted using the public key).</span></span>

## <a name="symmetric-decryption"></a><span data-ttu-id="cec83-106">Odszyfrowywanie symetryczne</span><span class="sxs-lookup"><span data-stu-id="cec83-106">Symmetric Decryption</span></span>

<span data-ttu-id="cec83-107">Odszyfrowywanie danych szyfrowanych za pomocą algorytmów symetrycznych jest podobne do procesu używanego do szyfrowania danych za pomocą algorytmów symetrycznych.</span><span class="sxs-lookup"><span data-stu-id="cec83-107">The decryption of data encrypted with symmetric algorithms is similar to the process used to encrypt data with symmetric algorithms.</span></span> <span data-ttu-id="cec83-108">Klasa <xref:System.Security.Cryptography.CryptoStream> jest używana z symetrycznymi klasami kryptografii udostępnianymi przez .NET Framework do odszyfrowywania danych odczytanych z dowolnego zarządzanego obiektu strumienia.</span><span class="sxs-lookup"><span data-stu-id="cec83-108">The <xref:System.Security.Cryptography.CryptoStream> class is used with symmetric cryptography classes provided by the .NET Framework to decrypt data read from any managed stream object.</span></span>

<span data-ttu-id="cec83-109">Poniższy przykład ilustruje sposób tworzenia nowego wystąpienia klasy <xref:System.Security.Cryptography.RijndaelManaged> i używania go do wykonania odszyfrowywania na obiekcie <xref:System.Security.Cryptography.CryptoStream>.</span><span class="sxs-lookup"><span data-stu-id="cec83-109">The following example illustrates how to create a new instance of the <xref:System.Security.Cryptography.RijndaelManaged> class and use it to perform decryption on a <xref:System.Security.Cryptography.CryptoStream> object.</span></span> <span data-ttu-id="cec83-110">Ten przykład najpierw tworzy nowe wystąpienie klasy **RijndaelManaged** .</span><span class="sxs-lookup"><span data-stu-id="cec83-110">This example first creates a new instance of the **RijndaelManaged** class.</span></span> <span data-ttu-id="cec83-111">Następnie tworzy obiekt **CryptoStream** i inicjuje go do wartości strumienia zarządzanego o nazwie `myStream`.</span><span class="sxs-lookup"><span data-stu-id="cec83-111">Next it creates a **CryptoStream** object and initializes it to the value of a managed stream called `myStream`.</span></span> <span data-ttu-id="cec83-112">Następnie Metoda **odszyfrowania** z klasy **RijndaelManaged** jest przenoszona z tego samego klucza i IV, który był używany do szyfrowania, a następnie jest przenoszona do konstruktora **CryptoStream** .</span><span class="sxs-lookup"><span data-stu-id="cec83-112">Next, the **CreateDecryptor** method from the **RijndaelManaged** class is passed the same key and IV that was used for encryption and is then passed to the **CryptoStream** constructor.</span></span> <span data-ttu-id="cec83-113">Na koniec Wyliczenie **CryptoStreamMode. Read** jest przesyłane do konstruktora **CryptoStream** w celu określenia dostępu do odczytu strumienia.</span><span class="sxs-lookup"><span data-stu-id="cec83-113">Finally, the **CryptoStreamMode.Read** enumeration is passed to the **CryptoStream** constructor to specify read access to the stream.</span></span>

```vb
Dim rmCrypto As New RijndaelManaged()
Dim cryptStream As New CryptoStream(myStream, rmCrypto.CreateDecryptor(rmCrypto.Key, rmCrypto.IV), CryptoStreamMode.Read)
```

```csharp
RijndaelManaged rmCrypto = new RijndaelManaged();
CryptoStream cryptStream = new CryptoStream(myStream, rmCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read);
```

<span data-ttu-id="cec83-114">Poniższy przykład pokazuje cały proces tworzenia strumienia, odszyfrowywania strumienia, odczytywania ze strumienia i zamykania strumieni.</span><span class="sxs-lookup"><span data-stu-id="cec83-114">The following example shows the entire process of creating a stream, decrypting the stream, reading from the stream, and closing the streams.</span></span> <span data-ttu-id="cec83-115">Tworzony jest obiekt <xref:System.Net.Sockets.TcpListener>, który inicjuje strumień sieciowy w przypadku nawiązania połączenia z obiektem nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="cec83-115">A <xref:System.Net.Sockets.TcpListener> object is created that initializes a network stream when a connection to the listening object is made.</span></span> <span data-ttu-id="cec83-116">Strumień sieciowy zostaje następnie odszyfrowany przy użyciu klasy **CryptoStream** i klasy **RijndaelManaged** .</span><span class="sxs-lookup"><span data-stu-id="cec83-116">The network stream is then decrypted using the **CryptoStream** class and the **RijndaelManaged** class.</span></span> <span data-ttu-id="cec83-117">W tym przykładzie przyjęto założenie, że wartości key i IV zostały pomyślnie przeniesione lub wcześniej uzgodnione.</span><span class="sxs-lookup"><span data-stu-id="cec83-117">This example assumes that the key and IV values have been either successfully transferred or previously agreed upon.</span></span> <span data-ttu-id="cec83-118">Nie jest wyświetlany kod wymagany do szyfrowania i transferu tych wartości.</span><span class="sxs-lookup"><span data-stu-id="cec83-118">It does not show the code needed to encrypt and transfer these values.</span></span>

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

<span data-ttu-id="cec83-119">Aby powyższy przykład działał, należy nawiązać połączenie szyfrowane z odbiornikiem.</span><span class="sxs-lookup"><span data-stu-id="cec83-119">For the previous sample to work, an encrypted connection must be made to the listener.</span></span> <span data-ttu-id="cec83-120">Połączenie musi używać tego samego klucza, IV i algorytmu, który jest używany w odbiorniku.</span><span class="sxs-lookup"><span data-stu-id="cec83-120">The connection must use the same key, IV, and algorithm used in the listener.</span></span> <span data-ttu-id="cec83-121">Jeśli takie połączenie jest nawiązywane, komunikat jest odszyfrowywany i wyświetlany w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="cec83-121">If such a connection is made, the message is decrypted and displayed to the console.</span></span>

## <a name="asymmetric-decryption"></a><span data-ttu-id="cec83-122">Odszyfrowywanie asymetryczne</span><span class="sxs-lookup"><span data-stu-id="cec83-122">Asymmetric Decryption</span></span>

<span data-ttu-id="cec83-123">Zazwyczaj strona (Strona A) generuje zarówno klucz publiczny, jak i prywatny, a klucz jest przechowywany w pamięci lub w kontenerze kluczy kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="cec83-123">Typically, a party (party A) generates both a public and private key and stores the key either in memory or in a cryptographic key container.</span></span> <span data-ttu-id="cec83-124">Następnie firma A następnie wysyła klucz publiczny do innej strony (strona B).</span><span class="sxs-lookup"><span data-stu-id="cec83-124">Party A then sends the public key to another party (party B).</span></span> <span data-ttu-id="cec83-125">Przy użyciu klucza publicznego Strona B szyfruje dane i wysyła je z powrotem do strony A. Po odebraniu danych firma odszyfruje je przy użyciu klucza prywatnego, który odpowiada.</span><span class="sxs-lookup"><span data-stu-id="cec83-125">Using the public key, party B encrypts data and sends the data back to party A. After receiving the data, party A decrypts it using the private key that corresponds.</span></span> <span data-ttu-id="cec83-126">Odszyfrowywanie powiedzie się tylko wtedy, gdy strona A używa klucza prywatnego, który odpowiada stronie klucza publicznego, który jest używany do szyfrowania danych.</span><span class="sxs-lookup"><span data-stu-id="cec83-126">Decryption will be successful only if party A uses the private key that corresponds to the public key Party B used to encrypt the data.</span></span>

<span data-ttu-id="cec83-127">Aby uzyskać informacje na temat sposobu przechowywania klucza asymetrycznego w bezpiecznym kontenerze kluczy kryptograficznych i sposobie późniejszego pobierania klucza asymetrycznego, zobacz [How to: Store asymetryczne klucze w kontenerze kluczy](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="cec83-127">For information on how to store an asymmetric key in secure cryptographic key container and how to later retrieve the asymmetric key, see [How to: Store Asymmetric Keys in a Key Container](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>

<span data-ttu-id="cec83-128">Poniższy przykład ilustruje odszyfrowywanie dwóch tablic bajtów reprezentujących klucz symetryczny i IV.</span><span class="sxs-lookup"><span data-stu-id="cec83-128">The following example illustrates the decryption of two arrays of bytes that represent a symmetric key and IV.</span></span> <span data-ttu-id="cec83-129">Aby uzyskać informacje na temat sposobu wyodrębniania asymetrycznego klucza publicznego z obiektu <xref:System.Security.Cryptography.RSACryptoServiceProvider> w formacie, który można łatwo przesłać do innej firmy, zobacz temat [szyfrowanie danych](../../../docs/standard/security/encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="cec83-129">For information on how to extract the asymmetric public key from the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object in a format that you can easily send to a third party, see [Encrypting Data](../../../docs/standard/security/encrypting-data.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cec83-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cec83-130">See also</span></span>

- [<span data-ttu-id="cec83-131">Generowanie kluczy szyfrowania i odszyfrowywania</span><span class="sxs-lookup"><span data-stu-id="cec83-131">Generating Keys for Encryption and Decryption</span></span>](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="cec83-132">Szyfrowanie danych</span><span class="sxs-lookup"><span data-stu-id="cec83-132">Encrypting Data</span></span>](../../../docs/standard/security/encrypting-data.md)
- [<span data-ttu-id="cec83-133">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="cec83-133">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
