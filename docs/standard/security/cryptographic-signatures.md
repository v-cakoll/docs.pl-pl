---
title: Podpisy kryptograficzne
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- digital signatures
- cryptography [.NET Framework], signatures
- digital signatures, XML signing
- signatures, cryptographic
- digital signatures, generating
- verifying signatures
- generating signatures
- digital signatures, about
- encryption [.NET Framework], signatures
- security [.NET Framework], signatures
- XML signing
- digital signatures, verifying
- signing XML
ms.assetid: aa87cb7f-e608-4a81-948b-c9b8a1225783
ms.openlocfilehash: 9e69578ceffeeacb73cf059f5b577fe7c137b599
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288397"
---
# <a name="cryptographic-signatures"></a><span data-ttu-id="ad84f-102">Podpisy kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="ad84f-102">Cryptographic Signatures</span></span>

<span data-ttu-id="ad84f-103">Kryptograficzne podpisy cyfrowe korzystają z algorytmów kluczy publicznych w celu zapewnienia integralności danych.</span><span class="sxs-lookup"><span data-stu-id="ad84f-103">Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="ad84f-104">Po podpisaniu danych za pomocą podpisu cyfrowego ktoś inny może zweryfikować podpis i może udowodnić, że dane pochodzą od Ciebie i nie zostały zmienione po podpisaniu.</span><span class="sxs-lookup"><span data-stu-id="ad84f-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="ad84f-105">Aby uzyskać więcej informacji na temat podpisów cyfrowych, zobacz [usługi kryptograficzne](cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="ad84f-105">For more information about digital signatures, see [Cryptographic Services](cryptographic-services.md).</span></span>

<span data-ttu-id="ad84f-106">W tym temacie wyjaśniono, jak generować i weryfikować podpisy cyfrowe przy użyciu klas w <xref:System.Security.Cryptography?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ad84f-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>

## <a name="generating-signatures"></a><span data-ttu-id="ad84f-107">Generowanie podpisów</span><span class="sxs-lookup"><span data-stu-id="ad84f-107">Generating Signatures</span></span>

<span data-ttu-id="ad84f-108">Podpisy cyfrowe są zwykle stosowane do wartości skrótu, które reprezentują większe dane.</span><span class="sxs-lookup"><span data-stu-id="ad84f-108">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="ad84f-109">Poniższy przykład stosuje podpis cyfrowy do wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="ad84f-109">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="ad84f-110">Najpierw tworzone jest nowe wystąpienie <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy w celu wygenerowania pary kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="ad84f-110">First, a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="ad84f-111">Następnie <xref:System.Security.Cryptography.RSACryptoServiceProvider> jest przenoszona do nowego wystąpienia <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> klasy.</span><span class="sxs-lookup"><span data-stu-id="ad84f-111">Next, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="ad84f-112">Spowoduje to przeniesienie klucza prywatnego do programu <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> , co w rzeczywistości wykonuje podpis cyfrowy.</span><span class="sxs-lookup"><span data-stu-id="ad84f-112">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="ad84f-113">Przed podpisaniem kodu skrótu należy określić algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="ad84f-113">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="ad84f-114">W tym przykładzie zastosowano algorytm SHA1.</span><span class="sxs-lookup"><span data-stu-id="ad84f-114">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="ad84f-115">Na koniec <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> Metoda jest wywoływana w celu przeprowadzenia podpisywania.</span><span class="sxs-lookup"><span data-stu-id="ad84f-115">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>

<span data-ttu-id="ad84f-116">Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256ą lub lepszą.</span><span class="sxs-lookup"><span data-stu-id="ad84f-116">Due to collision problems with SHA1, Microsoft recommends SHA256 or better.</span></span>

```vb
Imports System.Security.Cryptography

Module Module1
    Sub Main()
        'The hash value to sign.
        Dim hashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135}

        'The value to hold the signed value.
        Dim signedHashValue() As Byte

        'Generate a public/private key pair.
        Dim rsa As New RSACryptoServiceProvider()

        'Create an RSAPKCS1SignatureFormatter object and pass it
        'the RSACryptoServiceProvider to transfer the private key.
        Dim rsaFormatter As New RSAPKCS1SignatureFormatter(rsa)

        'Set the hash algorithm to SHA1.
        rsaFormatter.SetHashAlgorithm("SHA1")

        'Create a signature for hashValue and assign it to
        'signedHashValue.
        signedHashValue = rsaFormatter.CreateSignature(hashValue)
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
      //The hash value to sign.
      byte[] hashValue = {59,4,248,102,77,97,142,201,210,12,224,93,25,41,100,197,213,134,130,135};

      //The value to hold the signed value.
      byte[] signedHashValue;

      //Generate a public/private key pair.
      RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();

      //Create an RSAPKCS1SignatureFormatter object and pass it the
      //RSACryptoServiceProvider to transfer the private key.
      RSAPKCS1SignatureFormatter rsaFormatter = new RSAPKCS1SignatureFormatter(rsa);

      //Set the hash algorithm to SHA1.
      rsaFormatter.SetHashAlgorithm("SHA1");

      //Create a signature for hashValue and assign it to
      //signedHashValue.
      signedHashValue = rsaFormatter.CreateSignature(hashValue);
   }
}
```

### <a name="signing-xml-files"></a><span data-ttu-id="ad84f-117">Podpisywanie plików XML</span><span class="sxs-lookup"><span data-stu-id="ad84f-117">Signing XML Files</span></span>

<span data-ttu-id="ad84f-118">.NET Framework udostępnia <xref:System.Security.Cryptography.Xml> przestrzeń nazw, co umożliwia podpisywanie kodu XML.</span><span class="sxs-lookup"><span data-stu-id="ad84f-118">The .NET Framework provides the <xref:System.Security.Cryptography.Xml> namespace, which enables you sign XML.</span></span> <span data-ttu-id="ad84f-119">Podpisywanie kodu XML jest ważne, gdy chcesz sprawdzić, czy dane XML pochodzą z określonego źródła.</span><span class="sxs-lookup"><span data-stu-id="ad84f-119">Signing XML is important when you want to verify that the XML originates from a certain source.</span></span> <span data-ttu-id="ad84f-120">Jeśli na przykład korzystasz z usługi notowań giełdowych korzystającej z kodu XML, możesz sprawdzić źródło kodu XML, jeśli jest on podpisany.</span><span class="sxs-lookup"><span data-stu-id="ad84f-120">For example, if you are using a stock quote service that uses XML, you can verify the source of the XML if it is signed.</span></span>

<span data-ttu-id="ad84f-121">Klasy w tej przestrzeni nazw są zgodne ze [składnią podpisu XML i zaleceniem do przetwarzania](https://www.w3.org/TR/xmldsig-core/) z organizacja World Wide Web Consortium.</span><span class="sxs-lookup"><span data-stu-id="ad84f-121">The classes in this namespace follow the [XML-Signature Syntax and Processing recommendation](https://www.w3.org/TR/xmldsig-core/) from the World Wide Web Consortium.</span></span>

## <a name="verifying-signatures"></a><span data-ttu-id="ad84f-122">Weryfikowanie podpisów</span><span class="sxs-lookup"><span data-stu-id="ad84f-122">Verifying Signatures</span></span>

<span data-ttu-id="ad84f-123">Aby sprawdzić, czy dane zostały podpisane przez określoną stronę, musisz dysponować następującymi informacjami:</span><span class="sxs-lookup"><span data-stu-id="ad84f-123">To verify that data was signed by a particular party, you must have the following information:</span></span>

- <span data-ttu-id="ad84f-124">Klucz publiczny podmiotu, który podpisał dane.</span><span class="sxs-lookup"><span data-stu-id="ad84f-124">The public key of the party that signed the data.</span></span>

- <span data-ttu-id="ad84f-125">Podpis cyfrowy.</span><span class="sxs-lookup"><span data-stu-id="ad84f-125">The digital signature.</span></span>

- <span data-ttu-id="ad84f-126">Dane, które zostały podpisane.</span><span class="sxs-lookup"><span data-stu-id="ad84f-126">The data that was signed.</span></span>

- <span data-ttu-id="ad84f-127">Algorytm wyznaczania wartości skrótu używany przez program podpisujący.</span><span class="sxs-lookup"><span data-stu-id="ad84f-127">The hash algorithm used by the signer.</span></span>

<span data-ttu-id="ad84f-128">Aby sprawdzić podpis podpisany przez <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> klasę, użyj <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> klasy.</span><span class="sxs-lookup"><span data-stu-id="ad84f-128">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="ad84f-129"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter>Klasa musi być dostarczona z kluczem publicznym osoby podpisującej.</span><span class="sxs-lookup"><span data-stu-id="ad84f-129">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="ad84f-130">Do określenia klucza publicznego potrzebne będą wartości z modułu i wykładnika.</span><span class="sxs-lookup"><span data-stu-id="ad84f-130">You will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="ad84f-131">(Strona, która wygenerowała parę kluczy publiczny/prywatny powinna podawać te wartości). Najpierw Utwórz <xref:System.Security.Cryptography.RSACryptoServiceProvider> obiekt przechowujący klucz publiczny, który będzie weryfikować podpis, a następnie zainicjuj <xref:System.Security.Cryptography.RSAParameters> strukturę do wartości modulo i wykładnik, które określają klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="ad84f-131">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>

<span data-ttu-id="ad84f-132">Poniższy kod przedstawia tworzenie <xref:System.Security.Cryptography.RSAParameters> struktury.</span><span class="sxs-lookup"><span data-stu-id="ad84f-132">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="ad84f-133">`Modulus`Właściwość jest ustawiona na wartość tablicy bajtowej o nazwie `modulusData` i `Exponent` Właściwość jest ustawiona na wartość tablicy bajtowej o nazwie `exponentData` .</span><span class="sxs-lookup"><span data-stu-id="ad84f-133">The `Modulus` property is set to the value of a byte array called `modulusData` and the `Exponent` property is set to the value of a byte array called `exponentData`.</span></span>

```vb
Dim rsaKeyInfo As RSAParameters
rsaKeyInfo.Modulus = modulusData
rsaKeyInfo.Exponent = exponentData
```

```csharp
RSAParameters rsaKeyInfo;
rsaKeyInfo.Modulus = modulusData;
rsaKeyInfo.Exponent = exponentData;
```

<span data-ttu-id="ad84f-134">Po utworzeniu <xref:System.Security.Cryptography.RSAParameters> obiektu można zainicjować nowe wystąpienie <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy do wartości określonych w <xref:System.Security.Cryptography.RSAParameters> .</span><span class="sxs-lookup"><span data-stu-id="ad84f-134">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="ad84f-135"><xref:System.Security.Cryptography.RSACryptoServiceProvider>To z kolei jest przekazywane do konstruktora elementu, <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> Aby przenieść klucz.</span><span class="sxs-lookup"><span data-stu-id="ad84f-135">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>

<span data-ttu-id="ad84f-136">Poniższy przykład ilustruje ten proces.</span><span class="sxs-lookup"><span data-stu-id="ad84f-136">The following example illustrates this process.</span></span> <span data-ttu-id="ad84f-137">W tym przykładzie `hashValue` i `signedHashValue` są tablicami bajtów dostarczanych przez stronę zdalną.</span><span class="sxs-lookup"><span data-stu-id="ad84f-137">In this example, `hashValue` and `signedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="ad84f-138">Strona zdalna podpisała `hashValue` przy użyciu algorytmu SHA1, generując podpis cyfrowy `signedHashValue` .</span><span class="sxs-lookup"><span data-stu-id="ad84f-138">The remote party has signed the `hashValue` using the SHA1 algorithm, producing the digital signature `signedHashValue`.</span></span> <span data-ttu-id="ad84f-139"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType>Metoda weryfikuje, czy podpis cyfrowy jest prawidłowy i został użyty do podpisania `hashValue` .</span><span class="sxs-lookup"><span data-stu-id="ad84f-139">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `hashValue`.</span></span>

```vb
Dim rsa As New RSACryptoServiceProvider()
rsa.ImportParameters(rsaKeyInfo)
Dim rsaDeformatter As New RSAPKCS1SignatureDeformatter(rsa)
rsaDeformatter.SetHashAlgorithm("SHA1")
If rsaDeformatter.VerifySignature(hashValue, signedHashValue) Then
   Console.WriteLine("The signature is valid.")
Else
   Console.WriteLine("The signature is not valid.")
End If
```

```csharp
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();
rsa.ImportParameters(rsaKeyInfo);
RSAPKCS1SignatureDeformatter rsaDeformatter = new RSAPKCS1SignatureDeformatter(rsa);
rsaDeformatter.SetHashAlgorithm("SHA1");
if(rsaDeformatter.VerifySignature(hashValue, signedHashValue))
{
   Console.WriteLine("The signature is valid.");
}
else
{
   Console.WriteLine("The signature is not valid.");
}
```

<span data-ttu-id="ad84f-140">W tym fragmencie kodu zostanie wyświetlony element " `The signature is valid` ", jeśli sygnatura jest prawidłowa i " `The signature is not valid` ", jeśli nie jest.</span><span class="sxs-lookup"><span data-stu-id="ad84f-140">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad84f-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad84f-141">See also</span></span>

- [<span data-ttu-id="ad84f-142">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="ad84f-142">Cryptographic Services</span></span>](cryptographic-services.md)
