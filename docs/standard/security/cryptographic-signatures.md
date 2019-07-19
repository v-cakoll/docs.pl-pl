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
ms.openlocfilehash: 862d520073dde1b935510bc7c68782c1204c6111
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331651"
---
# <a name="cryptographic-signatures"></a>Podpisy kryptograficzne

<a name="top"></a>Kryptograficzne podpisy cyfrowe korzystają z algorytmów kluczy publicznych w celu zapewnienia integralności danych. Po podpisaniu danych za pomocą podpisu cyfrowego ktoś inny może zweryfikować podpis i może udowodnić, że dane pochodzą od Ciebie i nie zostały zmienione po podpisaniu. Aby uzyskać więcej informacji na temat podpisów cyfrowych, zobacz [usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md).

W tym temacie wyjaśniono, jak generować i weryfikować podpisy cyfrowe przy <xref:System.Security.Cryptography?displayProperty=nameWithType> użyciu klas w przestrzeni nazw.

- [Generowanie podpisów](#generate)

- [Weryfikowanie podpisów](#verify)

<a name="generate"></a>

## <a name="generating-signatures"></a>Generowanie podpisów

Podpisy cyfrowe są zwykle stosowane do wartości skrótu, które reprezentują większe dane. Poniższy przykład stosuje podpis cyfrowy do wartości skrótu. Najpierw tworzone jest nowe wystąpienie <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy w celu wygenerowania pary kluczy publicznych/prywatnych. Następnie jest przenoszona do nowego wystąpienia <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> klasy. <xref:System.Security.Cryptography.RSACryptoServiceProvider> Spowoduje to przeniesienie klucza prywatnego do programu <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, co w rzeczywistości wykonuje podpis cyfrowy. Przed podpisaniem kodu skrótu należy określić algorytm wyznaczania wartości skrótu. W tym przykładzie zastosowano algorytm SHA1. Na koniec Metoda jest wywoływana w celu przeprowadzenia podpisywania. <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A>

Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256ą lub lepszą.

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

### <a name="signing-xml-files"></a>Podpisywanie plików XML

.NET Framework udostępnia <xref:System.Security.Cryptography.Xml> przestrzeń nazw, co umożliwia podpisywanie kodu XML. Podpisywanie kodu XML jest ważne, gdy chcesz sprawdzić, czy dane XML pochodzą z określonego źródła. Jeśli na przykład korzystasz z usługi notowań giełdowych korzystającej z kodu XML, możesz sprawdzić źródło kodu XML, jeśli jest on podpisany.

Klasy w tej przestrzeni nazw są zgodne ze [składnią podpisu XML i zaleceniem do przetwarzania](https://www.w3.org/TR/xmldsig-core/) z organizacja World Wide Web Consortium.

[Powrót do początku](#top)

<a name="verify"></a>

## <a name="verifying-signatures"></a>Weryfikowanie podpisów

Aby sprawdzić, czy dane zostały podpisane przez określoną stronę, musisz dysponować następującymi informacjami:

- Klucz publiczny podmiotu, który podpisał dane.

- Podpis cyfrowy.

- Dane, które zostały podpisane.

- Algorytm wyznaczania wartości skrótu używany przez program podpisujący.

Aby sprawdzić podpis podpisany przez <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> klasę, <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> Użyj klasy. <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> Klasa musi być dostarczona z kluczem publicznym osoby podpisującej. Do określenia klucza publicznego potrzebne będą wartości z modułu i wykładnika. (Strona, która wygenerowała parę kluczy publiczny/prywatny powinna podawać te wartości). Najpierw Utwórz <xref:System.Security.Cryptography.RSACryptoServiceProvider> obiekt przechowujący klucz publiczny, który będzie weryfikować podpis, a następnie <xref:System.Security.Cryptography.RSAParameters> zainicjuj strukturę do wartości modulo i wykładnik, które określają klucz publiczny.

Poniższy kod przedstawia tworzenie <xref:System.Security.Cryptography.RSAParameters> struktury. Właściwość jest ustawiona na wartość tablicy bajtowej o nazwie `modulusData` i `Exponent` właściwość jest ustawiona na wartość tablicy bajtowej o nazwie `exponentData`. `Modulus`

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

Po utworzeniu <xref:System.Security.Cryptography.RSAParameters> obiektu można zainicjować nowe wystąpienie <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy do wartości określonych w <xref:System.Security.Cryptography.RSAParameters>. To z kolei jest przekazywane do konstruktora elementu <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> , aby przenieść klucz. <xref:System.Security.Cryptography.RSACryptoServiceProvider>

Poniższy przykład ilustruje ten proces. W tym przykładzie `hashValue` i `signedHashValue` są tablicami bajtów dostarczanych przez stronę zdalną. Strona zdalna podpisała `hashValue` przy użyciu algorytmu SHA1, generując podpis `signedHashValue`cyfrowy. Metoda weryfikuje, czy podpis cyfrowy jest prawidłowy i został użyty do `hashValue`podpisania. <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType>

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

W tym fragmencie kodu zostanie wyświetlony`The signature is valid`element "", jeśli sygnatura jest`The signature is not valid`prawidłowa i "", jeśli nie jest.

## <a name="see-also"></a>Zobacz także

- [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)
