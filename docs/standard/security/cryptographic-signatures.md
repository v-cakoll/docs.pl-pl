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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: de64af1a4617af39b0ef8e054292a402d6a145e6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350456"
---
# <a name="cryptographic-signatures"></a><span data-ttu-id="95c0c-102">Podpisy kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="95c0c-102">Cryptographic Signatures</span></span>

<span data-ttu-id="95c0c-103">Kryptograficzne podpisy cyfrowe korzystają z algorytmów kluczy publicznych w celu zapewnienia integralności danych.</span><span class="sxs-lookup"><span data-stu-id="95c0c-103">Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="95c0c-104">Po podpisaniu danych za pomocą podpisu cyfrowego ktoś inny może zweryfikować podpis i może udowodnić, że dane pochodzą od Ciebie i nie zostały zmienione po podpisaniu.</span><span class="sxs-lookup"><span data-stu-id="95c0c-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="95c0c-105">Aby uzyskać więcej informacji na temat podpisów cyfrowych, zobacz [usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="95c0c-105">For more information about digital signatures, see [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md).</span></span>

<span data-ttu-id="95c0c-106">W tym temacie wyjaśniono, jak generować i weryfikować podpisy cyfrowe przy użyciu klas w przestrzeni nazw <xref:System.Security.Cryptography?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="95c0c-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>

## <a name="generating-signatures"></a><span data-ttu-id="95c0c-107">Generowanie podpisów</span><span class="sxs-lookup"><span data-stu-id="95c0c-107">Generating Signatures</span></span>

<span data-ttu-id="95c0c-108">Podpisy cyfrowe są zwykle stosowane do wartości skrótu, które reprezentują większe dane.</span><span class="sxs-lookup"><span data-stu-id="95c0c-108">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="95c0c-109">Poniższy przykład stosuje podpis cyfrowy do wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="95c0c-109">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="95c0c-110">Najpierw tworzone jest nowe wystąpienie klasy <xref:System.Security.Cryptography.RSACryptoServiceProvider>, aby wygenerować parę kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="95c0c-110">First, a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="95c0c-111">Następnie <xref:System.Security.Cryptography.RSACryptoServiceProvider> jest przenoszona do nowego wystąpienia klasy <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>.</span><span class="sxs-lookup"><span data-stu-id="95c0c-111">Next, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="95c0c-112">Spowoduje to przeniesienie klucza prywatnego do <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, co w rzeczywistości wykonuje podpis cyfrowy.</span><span class="sxs-lookup"><span data-stu-id="95c0c-112">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="95c0c-113">Przed podpisaniem kodu skrótu należy określić algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="95c0c-113">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="95c0c-114">W tym przykładzie zastosowano algorytm SHA1.</span><span class="sxs-lookup"><span data-stu-id="95c0c-114">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="95c0c-115">Na koniec Metoda <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> jest wywoływana w celu przeprowadzenia podpisywania.</span><span class="sxs-lookup"><span data-stu-id="95c0c-115">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>

<span data-ttu-id="95c0c-116">Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256ą lub lepszą.</span><span class="sxs-lookup"><span data-stu-id="95c0c-116">Due to collision problems with SHA1, Microsoft recommends SHA256 or better.</span></span>

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

### <a name="signing-xml-files"></a><span data-ttu-id="95c0c-117">Podpisywanie plików XML</span><span class="sxs-lookup"><span data-stu-id="95c0c-117">Signing XML Files</span></span>

<span data-ttu-id="95c0c-118">.NET Framework zapewnia <xref:System.Security.Cryptography.Xml> przestrzeni nazw, co umożliwia podpisywanie kodu XML.</span><span class="sxs-lookup"><span data-stu-id="95c0c-118">The .NET Framework provides the <xref:System.Security.Cryptography.Xml> namespace, which enables you sign XML.</span></span> <span data-ttu-id="95c0c-119">Podpisywanie kodu XML jest ważne, gdy chcesz sprawdzić, czy dane XML pochodzą z określonego źródła.</span><span class="sxs-lookup"><span data-stu-id="95c0c-119">Signing XML is important when you want to verify that the XML originates from a certain source.</span></span> <span data-ttu-id="95c0c-120">Jeśli na przykład korzystasz z usługi notowań giełdowych korzystającej z kodu XML, możesz sprawdzić źródło kodu XML, jeśli jest on podpisany.</span><span class="sxs-lookup"><span data-stu-id="95c0c-120">For example, if you are using a stock quote service that uses XML, you can verify the source of the XML if it is signed.</span></span>

<span data-ttu-id="95c0c-121">Klasy w tej przestrzeni nazw są zgodne ze [składnią podpisu XML i zaleceniem do przetwarzania](https://www.w3.org/TR/xmldsig-core/) z organizacja World Wide Web Consortium.</span><span class="sxs-lookup"><span data-stu-id="95c0c-121">The classes in this namespace follow the [XML-Signature Syntax and Processing recommendation](https://www.w3.org/TR/xmldsig-core/) from the World Wide Web Consortium.</span></span>

## <a name="verifying-signatures"></a><span data-ttu-id="95c0c-122">Weryfikowanie podpisów</span><span class="sxs-lookup"><span data-stu-id="95c0c-122">Verifying Signatures</span></span>

<span data-ttu-id="95c0c-123">Aby sprawdzić, czy dane zostały podpisane przez określoną stronę, musisz dysponować następującymi informacjami:</span><span class="sxs-lookup"><span data-stu-id="95c0c-123">To verify that data was signed by a particular party, you must have the following information:</span></span>

- <span data-ttu-id="95c0c-124">Klucz publiczny podmiotu, który podpisał dane.</span><span class="sxs-lookup"><span data-stu-id="95c0c-124">The public key of the party that signed the data.</span></span>

- <span data-ttu-id="95c0c-125">Podpis cyfrowy.</span><span class="sxs-lookup"><span data-stu-id="95c0c-125">The digital signature.</span></span>

- <span data-ttu-id="95c0c-126">Dane, które zostały podpisane.</span><span class="sxs-lookup"><span data-stu-id="95c0c-126">The data that was signed.</span></span>

- <span data-ttu-id="95c0c-127">Algorytm wyznaczania wartości skrótu używany przez program podpisujący.</span><span class="sxs-lookup"><span data-stu-id="95c0c-127">The hash algorithm used by the signer.</span></span>

<span data-ttu-id="95c0c-128">Aby sprawdzić podpis podpisany przez klasę <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, użyj klasy <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter>.</span><span class="sxs-lookup"><span data-stu-id="95c0c-128">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="95c0c-129">Klasa <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> musi być dostarczona z kluczem publicznym osoby podpisującej.</span><span class="sxs-lookup"><span data-stu-id="95c0c-129">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="95c0c-130">Do określenia klucza publicznego potrzebne będą wartości z modułu i wykładnika.</span><span class="sxs-lookup"><span data-stu-id="95c0c-130">You will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="95c0c-131">(Strona, która wygenerowała parę kluczy publiczny/prywatny powinna podawać te wartości). Najpierw Utwórz obiekt <xref:System.Security.Cryptography.RSACryptoServiceProvider>, aby pomieścić klucz publiczny, który sprawdzi podpis, a następnie zainicjuj strukturę <xref:System.Security.Cryptography.RSAParameters> do wartości moduł i wykładnik, które określają klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="95c0c-131">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>

<span data-ttu-id="95c0c-132">Poniższy kod przedstawia tworzenie struktury <xref:System.Security.Cryptography.RSAParameters>.</span><span class="sxs-lookup"><span data-stu-id="95c0c-132">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="95c0c-133">Właściwość `Modulus` jest ustawiona na wartość tablicy bajtowej o nazwie `modulusData` i Właściwość `Exponent` jest ustawiona na wartość tablicy bajtowej o nazwie `exponentData`.</span><span class="sxs-lookup"><span data-stu-id="95c0c-133">The `Modulus` property is set to the value of a byte array called `modulusData` and the `Exponent` property is set to the value of a byte array called `exponentData`.</span></span>

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

<span data-ttu-id="95c0c-134">Po utworzeniu obiektu <xref:System.Security.Cryptography.RSAParameters> można zainicjować nowe wystąpienie klasy <xref:System.Security.Cryptography.RSACryptoServiceProvider> do wartości określonych w <xref:System.Security.Cryptography.RSAParameters>.</span><span class="sxs-lookup"><span data-stu-id="95c0c-134">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="95c0c-135"><xref:System.Security.Cryptography.RSACryptoServiceProvider> jest z kolei przekazywana do konstruktora <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> w celu przetransferowania klucza.</span><span class="sxs-lookup"><span data-stu-id="95c0c-135">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>

<span data-ttu-id="95c0c-136">Poniższy przykład ilustruje ten proces.</span><span class="sxs-lookup"><span data-stu-id="95c0c-136">The following example illustrates this process.</span></span> <span data-ttu-id="95c0c-137">W tym przykładzie `hashValue` i `signedHashValue` to tablice bajtów dostarczone przez stronę zdalną.</span><span class="sxs-lookup"><span data-stu-id="95c0c-137">In this example, `hashValue` and `signedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="95c0c-138">Strona zdalna podpisała `hashValue` przy użyciu algorytmu SHA1, generując `signedHashValue`podpis cyfrowy.</span><span class="sxs-lookup"><span data-stu-id="95c0c-138">The remote party has signed the `hashValue` using the SHA1 algorithm, producing the digital signature `signedHashValue`.</span></span> <span data-ttu-id="95c0c-139">Metoda <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> sprawdza, czy podpis cyfrowy jest prawidłowy i został użyty do podpisywania `hashValue`.</span><span class="sxs-lookup"><span data-stu-id="95c0c-139">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `hashValue`.</span></span>

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

<span data-ttu-id="95c0c-140">Ten fragment kodu będzie wyświetlał "`The signature is valid`", jeśli sygnatura jest prawidłowa i "`The signature is not valid`", jeśli nie jest.</span><span class="sxs-lookup"><span data-stu-id="95c0c-140">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>

## <a name="see-also"></a><span data-ttu-id="95c0c-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95c0c-141">See also</span></span>

- [<span data-ttu-id="95c0c-142">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="95c0c-142">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
