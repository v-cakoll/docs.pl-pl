---
title: Odszyfrowywanie danych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [.NET Framework], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6f2ffaeeb8a92dd7ab16b4ba233196230b595af2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="decrypting-data"></a><span data-ttu-id="fa6ba-102">Odszyfrowywanie danych</span><span class="sxs-lookup"><span data-stu-id="fa6ba-102">Decrypting Data</span></span>
<span data-ttu-id="fa6ba-103">Odszyfrowywanie jest odwrotnej operacji szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="fa6ba-103">Decryption is the reverse operation of encryption.</span></span> <span data-ttu-id="fa6ba-104">Do szyfrowania klucza tajnego musisz znać klucz i IV, które były używane do szyfrowania danych.</span><span class="sxs-lookup"><span data-stu-id="fa6ba-104">For secret-key encryption, you must know both the key and IV that were used to encrypt the data.</span></span> <span data-ttu-id="fa6ba-105">Do szyfrowania klucza publicznego musisz znać klucza publicznego (jeśli zostały zaszyfrowane przy użyciu klucza prywatnego) lub klucza prywatnego (jeśli zostały zaszyfrowane za pomocą klucza publicznego).</span><span class="sxs-lookup"><span data-stu-id="fa6ba-105">For public-key encryption, you must know either the public key (if the data was encrypted using the private key) or the private key (if the data was encrypted using the public key).</span></span>  
  
## <a name="symmetric-decryption"></a><span data-ttu-id="fa6ba-106">Odszyfrowanie symetryczne</span><span class="sxs-lookup"><span data-stu-id="fa6ba-106">Symmetric Decryption</span></span>  
 <span data-ttu-id="fa6ba-107">Odszyfrowywanie danych zaszyfrowanych za pomocą symetryczne algorytmy jest podobny do procesu używany do szyfrowania danych za pomocą symetryczne algorytmy.</span><span class="sxs-lookup"><span data-stu-id="fa6ba-107">The decryption of data encrypted with symmetric algorithms is similar to the process used to encrypt data with symmetric algorithms.</span></span> <span data-ttu-id="fa6ba-108"><xref:System.Security.Cryptography.CryptoStream> Klasa jest używana z klasami Kryptografia symetryczna dostarczane przez program .NET Framework, aby odszyfrować dane z dowolnych obiektów zarządzanych strumień do odczytu.</span><span class="sxs-lookup"><span data-stu-id="fa6ba-108">The <xref:System.Security.Cryptography.CryptoStream> class is used with symmetric cryptography classes provided by the .NET Framework to decrypt data read from any managed stream object.</span></span>  
  
 <span data-ttu-id="fa6ba-109">Poniższy przykład przedstawia sposób utworzyć nowe wystąpienie klasy <xref:System.Security.Cryptography.RijndaelManaged> klasy i używać go do odszyfrowywania na <xref:System.Security.Cryptography.CryptoStream> obiektu.</span><span class="sxs-lookup"><span data-stu-id="fa6ba-109">The following example illustrates how to create a new instance of the <xref:System.Security.Cryptography.RijndaelManaged> class and use it to perform decryption on a <xref:System.Security.Cryptography.CryptoStream> object.</span></span> <span data-ttu-id="fa6ba-110">W tym przykładzie najpierw tworzy nowe wystąpienie klasy **RijndaelManaged** klasy.</span><span class="sxs-lookup"><span data-stu-id="fa6ba-110">This example first creates a new instance of the **RijndaelManaged** class.</span></span> <span data-ttu-id="fa6ba-111">Następnie tworzy **CryptoStream** obiekt i inicjuje wartość zarządzanego strumienia mu `MyStream`.</span><span class="sxs-lookup"><span data-stu-id="fa6ba-111">Next it creates a **CryptoStream** object and initializes it to the value of a managed stream called `MyStream`.</span></span> <span data-ttu-id="fa6ba-112">Następnie **CreateDecryptor** metody z **RijndaelManaged** klasy jest przekazywany ten sam klucz i IV, który był używany do szyfrowania i są następnie przekazywane do **CryptoStream** Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="fa6ba-112">Next, the **CreateDecryptor** method from the **RijndaelManaged** class is passed the same key and IV that was used for encryption and is then passed to the **CryptoStream** constructor.</span></span> <span data-ttu-id="fa6ba-113">Na koniec **CryptoStreamMode.Read** wyliczenie jest przekazywana do **CryptoStream** konstruktora, aby określić dostęp do odczytu do strumienia.</span><span class="sxs-lookup"><span data-stu-id="fa6ba-113">Finally, the **CryptoStreamMode.Read** enumeration is passed to the **CryptoStream** constructor to specify read access to the stream.</span></span>  
  
```vb  
Dim RMCrypto As New RijndaelManaged()  
Dim CryptStream As New CryptoStream(MyStream, RMCrypto.CreateDecryptor(RMCrypto.Key, RMCrypto.IV), CryptoStreamMode.Read)  
```  
  
```csharp  
RijndaelManaged RMCrypto = new RijndaelManaged();  
CryptoStream CryptStream = new CryptoStream(MyStream, RMCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read);  
```  
  
 <span data-ttu-id="fa6ba-114">Poniższy przykład przedstawia cały proces tworzenia strumienia, odszyfrowywania strumień odczytu ze strumienia i zamykania strumieni.</span><span class="sxs-lookup"><span data-stu-id="fa6ba-114">The following example shows the entire process of creating a stream, decrypting the stream, reading from the stream, and closing the streams.</span></span> <span data-ttu-id="fa6ba-115">A <xref:System.Net.Sockets.TcpListener> tworzony jest obiekt, który inicjuje strumienia sieci, gdy nawiązuje połączenie z obiektem nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="fa6ba-115">A <xref:System.Net.Sockets.TcpListener> object is created that initializes a network stream when a connection to the listening object is made.</span></span> <span data-ttu-id="fa6ba-116">Strumień sieciowych jest odszyfrowywany za pomocą **CryptoStream** klasy i **RijndaelManaged** klasy.</span><span class="sxs-lookup"><span data-stu-id="fa6ba-116">The network stream is then decrypted using the **CryptoStream** class and the **RijndaelManaged** class.</span></span> <span data-ttu-id="fa6ba-117">W tym przykładzie przyjęto założenie, że klucza i wartości IV ma została pomyślnie przeniesiona lub wcześniej uzgodnione.</span><span class="sxs-lookup"><span data-stu-id="fa6ba-117">This example assumes that the key and IV values have been either successfully transferred or previously agreed upon.</span></span> <span data-ttu-id="fa6ba-118">Kod wymagane do szyfrowania i przesyłania tych wartości nie są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="fa6ba-118">It does not show the code needed to encrypt and transfer these values.</span></span>  
  
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
  
 <span data-ttu-id="fa6ba-119">Dla powyższego przykładu pracy zaszyfrowanego połączenia muszą być wprowadzane do odbiornika.</span><span class="sxs-lookup"><span data-stu-id="fa6ba-119">For the previous sample to work, an encrypted connection must be made to the listener.</span></span> <span data-ttu-id="fa6ba-120">Połączenie musi używać tego samego klucza, IV i algorytm używany w odbiornika.</span><span class="sxs-lookup"><span data-stu-id="fa6ba-120">The connection must use the same key, IV, and algorithm used in the listener.</span></span> <span data-ttu-id="fa6ba-121">Jeśli takie połączenie zostanie nawiązane, wiadomość jest odszyfrowywany i wyświetlane w konsoli.</span><span class="sxs-lookup"><span data-stu-id="fa6ba-121">If such a connection is made, the message is decrypted and displayed to the console.</span></span>  
  
## <a name="asymmetric-decryption"></a><span data-ttu-id="fa6ba-122">Odszyfrowanie asymetryczne</span><span class="sxs-lookup"><span data-stu-id="fa6ba-122">Asymmetric Decryption</span></span>  
 <span data-ttu-id="fa6ba-123">Zwykle firmy (strona A) generuje zarówno klucz publiczny i prywatny i przechowuje klucz w pamięci lub w kontenerze kluczy kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="fa6ba-123">Typically, a party (party A) generates both a public and private key and stores the key either in memory or in a cryptographic key container.</span></span>  <span data-ttu-id="fa6ba-124">Strona, następnie wysyła klucza publicznego do innej strony (strona B).</span><span class="sxs-lookup"><span data-stu-id="fa6ba-124">Party A then sends the public key to another party (party B).</span></span>  <span data-ttu-id="fa6ba-125">Za pomocą klucza publicznego, strona B dane są szyfrowane i wysyła dane do firmy A.  Po odebraniu danych, A strona odszyfrowuje ją przy użyciu klucza prywatnego, który odpowiada.</span><span class="sxs-lookup"><span data-stu-id="fa6ba-125">Using the public key, party B encrypts data and sends the data back to party A.  After receiving the data, party A decrypts it using the private key that corresponds.</span></span>  <span data-ttu-id="fa6ba-126">Odszyfrowywanie zakończy się pomyślnie, tylko wtedy, gdy strona A używa klucza prywatnego, który odpowiada klucza publicznego, który strona B używany do szyfrowania danych.</span><span class="sxs-lookup"><span data-stu-id="fa6ba-126">Decryption will be successful only if party A uses the private key that corresponds to the public key Party B used to encrypt the data.</span></span>  
  
 <span data-ttu-id="fa6ba-127">Aby uzyskać informacje dotyczące sposobu przechowywania klucza asymetrycznego bezpiecznego kontenera kluczy kryptograficznych i jak później pobrać klucza asymetrycznego, zobacz [porady: przechowywanie kluczy asymetrycznych w kontenerze klucza](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="fa6ba-127">For information on how to store an asymmetric key in secure cryptographic key container and how to later retrieve the asymmetric key, see [How to: Store Asymmetric Keys in a Key Container](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="fa6ba-128">Poniższy przykład przedstawia odszyfrowywanie dwie tablice bajtów reprezentujących klucza symetrycznego i IV.</span><span class="sxs-lookup"><span data-stu-id="fa6ba-128">The following example illustrates the decryption of two arrays of bytes that represent a symmetric key and IV.</span></span>  <span data-ttu-id="fa6ba-129">Aby uzyskać informacje dotyczące wyodrębniania publicznego klucza asymetrycznego z <xref:System.Security.Cryptography.RSACryptoServiceProvider> obiektu w formacie, który umożliwia łatwe wysyłanie do innej firmy, zobacz [szyfrowania danych](../../../docs/standard/security/encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="fa6ba-129">For information on how to extract the asymmetric public key from the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object in a format that you can easily send to a third party, see [Encrypting Data](../../../docs/standard/security/encrypting-data.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fa6ba-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa6ba-130">See Also</span></span>  
 [<span data-ttu-id="fa6ba-131">Generowanie kluczy szyfrowania i odszyfrowywania</span><span class="sxs-lookup"><span data-stu-id="fa6ba-131">Generating Keys for Encryption and Decryption</span></span>](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
 [<span data-ttu-id="fa6ba-132">Szyfrowanie danych</span><span class="sxs-lookup"><span data-stu-id="fa6ba-132">Encrypting Data</span></span>](../../../docs/standard/security/encrypting-data.md)  
 [<span data-ttu-id="fa6ba-133">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="fa6ba-133">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
