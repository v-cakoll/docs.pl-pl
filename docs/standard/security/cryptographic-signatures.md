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
ms.openlocfilehash: 15fd79a1289bd54b81db551abbdfcd63deef3e24
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710306"
---
# <a name="cryptographic-signatures"></a><span data-ttu-id="1eb6b-102">Podpisy kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="1eb6b-102">Cryptographic Signatures</span></span>

<a name="top"></a> <span data-ttu-id="1eb6b-103">Podpisy cyfrowe kryptograficzne umożliwia algorytmy kluczy publicznych zapewniają integralność danych.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-103">Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="1eb6b-104">Po zalogowaniu danych przy użyciu podpisu cyfrowego, ktoś inny może zweryfikować podpisu, a można udowodnić, że dane pochodzą od użytkownika oraz nie została zmodyfikowana po użytkownik zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="1eb6b-105">Aby uzyskać więcej informacji na temat podpisów cyfrowych, zobacz [usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="1eb6b-105">For more information about digital signatures, see [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md).</span></span>

<span data-ttu-id="1eb6b-106">W tym temacie opisano sposób rejestrowania i weryfikowania podpisów cyfrowych przy użyciu klas w <xref:System.Security.Cryptography?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>

- [<span data-ttu-id="1eb6b-107">Generowanie podpisów</span><span class="sxs-lookup"><span data-stu-id="1eb6b-107">Generating Signatures</span></span>](#generate)

- [<span data-ttu-id="1eb6b-108">Weryfikowanie podpisów</span><span class="sxs-lookup"><span data-stu-id="1eb6b-108">Verifying Signatures</span></span>](#verify)

<a name="generate"></a>

## <a name="generating-signatures"></a><span data-ttu-id="1eb6b-109">Generowanie podpisów</span><span class="sxs-lookup"><span data-stu-id="1eb6b-109">Generating Signatures</span></span>

<span data-ttu-id="1eb6b-110">Podpisy cyfrowe są zazwyczaj stosowane do wartości skrótu, które reprezentują więcej danych.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-110">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="1eb6b-111">Poniższy przykład dotyczy wartości skrótu podpisu cyfrowego.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-111">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="1eb6b-112">Po pierwsze, nowe wystąpienie klasy <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasa została utworzona, można wygenerować pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-112">First, a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="1eb6b-113">Następnie <xref:System.Security.Cryptography.RSACryptoServiceProvider> jest przekazywany do nowego wystąpienia <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> klasy.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-113">Next, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="1eb6b-114">To przesłanie klucza prywatnego <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, który wykonuje cyfrowego podpisywania.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-114">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="1eb6b-115">Przed zarejestrowaniem skrótu, należy określić algorytm wyznaczania wartości skrótu do użycia.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-115">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="1eb6b-116">W tym przykładzie użyto algorytmu SHA1.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-116">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="1eb6b-117">Na koniec <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> metoda jest wywoływana w celu wykonania podpisywania.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-117">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>

```vb
Imports System
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

### <a name="signing-xml-files"></a><span data-ttu-id="1eb6b-118">Podpisywanie plików XML</span><span class="sxs-lookup"><span data-stu-id="1eb6b-118">Signing XML Files</span></span>

<span data-ttu-id="1eb6b-119">Program .NET Framework oferuje <xref:System.Security.Cryptography.Xml> przestrzeni nazw, co pozwala zarejestrować XML.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-119">The .NET Framework provides the <xref:System.Security.Cryptography.Xml> namespace, which enables you sign XML.</span></span> <span data-ttu-id="1eb6b-120">Podpisywanie XML jest ważne w przypadku, gdy chcesz zweryfikować, że plik XML pochodzi z danego źródła.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-120">Signing XML is important when you want to verify that the XML originates from a certain source.</span></span> <span data-ttu-id="1eb6b-121">Na przykład jeśli używasz usługi notowań giełdowych, który używa XML możesz zweryfikować źródła XML jest podpisany.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-121">For example, if you are using a stock quote service that uses XML, you can verify the source of the XML if it is signed.</span></span>

<span data-ttu-id="1eb6b-122">Postępuj zgodnie z klas w tej przestrzeni nazw [zalecenie składni XML podpisu i przetwarzanie](https://www.w3.org/TR/xmldsig-core/) z konsorcjum World Wide Web.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-122">The classes in this namespace follow the [XML-Signature Syntax and Processing recommendation](https://www.w3.org/TR/xmldsig-core/) from the World Wide Web Consortium.</span></span>

[<span data-ttu-id="1eb6b-123">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="1eb6b-123">Back to top</span></span>](#top)

<a name="verify"></a>

## <a name="verifying-signatures"></a><span data-ttu-id="1eb6b-124">Weryfikowanie podpisów</span><span class="sxs-lookup"><span data-stu-id="1eb6b-124">Verifying Signatures</span></span>

<span data-ttu-id="1eb6b-125">Aby sprawdzić, czy dane został podpisany przez określoną stronę, musisz mieć następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="1eb6b-125">To verify that data was signed by a particular party, you must have the following information:</span></span>

- <span data-ttu-id="1eb6b-126">Klucz publiczny w innej firmy, który podpisał danych.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-126">The public key of the party that signed the data.</span></span>

- <span data-ttu-id="1eb6b-127">Podpis cyfrowy.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-127">The digital signature.</span></span>

- <span data-ttu-id="1eb6b-128">Dane, który został podpisany.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-128">The data that was signed.</span></span>

- <span data-ttu-id="1eb6b-129">Algorytm skrótu używany przez osoby podpisującej.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-129">The hash algorithm used by the signer.</span></span>

<span data-ttu-id="1eb6b-130">Aby zweryfikować podpisu, który został podpisany przez <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> klasy, należy użyć <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> klasy.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-130">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="1eb6b-131"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> Klasa musi być podany klucz publiczny podpisu.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-131">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="1eb6b-132">Konieczne będzie wartości moduł i wykładnik, do określenia klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-132">You will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="1eb6b-133">(Strona, która wygenerowała pary kluczy publiczny/prywatny podać te wartości.) Najpierw utwórz <xref:System.Security.Cryptography.RSACryptoServiceProvider> obiekt do przechowywania klucza publicznego, zweryfikować podpisu, a następnie zainicjuj <xref:System.Security.Cryptography.RSAParameters> struktury wyznaczanie modułu i wykładnik wartości, które określają klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-133">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>

<span data-ttu-id="1eb6b-134">Poniższy kod ilustruje tworzenie <xref:System.Security.Cryptography.RSAParameters> struktury.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-134">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="1eb6b-135">`Modulus` Właściwości ustawiono wartość tablicy typu byte o nazwie `modulusData` i `Exponent` właściwości ustawiono wartość tablicy typu byte o nazwie `exponentData`.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-135">The `Modulus` property is set to the value of a byte array called `modulusData` and the `Exponent` property is set to the value of a byte array called `exponentData`.</span></span>

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

<span data-ttu-id="1eb6b-136">Po utworzeniu <xref:System.Security.Cryptography.RSAParameters> obiektu można zainicjować nowe wystąpienie klasy <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy wartościom określonym w <xref:System.Security.Cryptography.RSAParameters>.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-136">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="1eb6b-137"><xref:System.Security.Cryptography.RSACryptoServiceProvider> z kolei przekazany do konstruktora obiektu <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> celu przeniesienia klucza.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-137">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>

<span data-ttu-id="1eb6b-138">Poniższy przykład ilustruje ten proces.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-138">The following example illustrates this process.</span></span> <span data-ttu-id="1eb6b-139">W tym przykładzie `hashValue` i `signedHashValue` to tablice bajtów dostarczonym przez firmę zdalnego.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-139">In this example, `hashValue` and `signedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="1eb6b-140">Strona zdalna została podpisana `hashValue` przy użyciu algorytmu SHA1, tworzenie podpis cyfrowy `signedHashValue`.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-140">The remote party has signed the `hashValue` using the SHA1 algorithm, producing the digital signature `signedHashValue`.</span></span> <span data-ttu-id="1eb6b-141"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> Metoda sprawdza, czy podpis cyfrowy jest prawidłowa i czy został użyty do podpisania `hashValue`.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-141">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `hashValue`.</span></span>

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

<span data-ttu-id="1eb6b-142">Ten fragment kodu będą wyświetlane "`The signature is valid`" Jeśli podpis jest prawidłowy i "`The signature is not valid`" Jeśli nie jest.</span><span class="sxs-lookup"><span data-stu-id="1eb6b-142">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>

## <a name="see-also"></a><span data-ttu-id="1eb6b-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1eb6b-143">See also</span></span>

- [<span data-ttu-id="1eb6b-144">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="1eb6b-144">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
