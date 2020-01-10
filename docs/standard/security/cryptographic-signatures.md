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
ms.openlocfilehash: 1de6b3f2eb30df270339910e7b8287101bde65ca
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706256"
---
# <a name="cryptographic-signatures"></a>Podpisy kryptograficzne

Kryptograficzne podpisy cyfrowe korzystają z algorytmów kluczy publicznych w celu zapewnienia integralności danych. Po podpisaniu danych za pomocą podpisu cyfrowego ktoś inny może zweryfikować podpis i może udowodnić, że dane pochodzą od Ciebie i nie zostały zmienione po podpisaniu. Aby uzyskać więcej informacji na temat podpisów cyfrowych, zobacz [usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md).

W tym temacie wyjaśniono, jak generować i weryfikować podpisy cyfrowe przy użyciu klas w przestrzeni nazw <xref:System.Security.Cryptography?displayProperty=nameWithType>.

## <a name="generating-signatures"></a>Generowanie podpisów

Podpisy cyfrowe są zwykle stosowane do wartości skrótu, które reprezentują większe dane. Poniższy przykład stosuje podpis cyfrowy do wartości skrótu. Najpierw tworzone jest nowe wystąpienie klasy <xref:System.Security.Cryptography.RSACryptoServiceProvider>, aby wygenerować parę kluczy publiczny/prywatny. Następnie <xref:System.Security.Cryptography.RSACryptoServiceProvider> jest przenoszona do nowego wystąpienia klasy <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>. Spowoduje to przeniesienie klucza prywatnego do <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, co w rzeczywistości wykonuje podpis cyfrowy. Przed podpisaniem kodu skrótu należy określić algorytm wyznaczania wartości skrótu. W tym przykładzie zastosowano algorytm SHA1. Na koniec Metoda <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> jest wywoływana w celu przeprowadzenia podpisywania.

Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256ą lub lepszą.

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

### <a name="signing-xml-files"></a>Podpisywanie plików XML

.NET Framework zapewnia <xref:System.Security.Cryptography.Xml> przestrzeni nazw, co umożliwia podpisywanie kodu XML. Podpisywanie kodu XML jest ważne, gdy chcesz sprawdzić, czy dane XML pochodzą z określonego źródła. Jeśli na przykład korzystasz z usługi notowań giełdowych korzystającej z kodu XML, możesz sprawdzić źródło kodu XML, jeśli jest on podpisany.

Klasy w tej przestrzeni nazw są zgodne ze [składnią podpisu XML i zaleceniem do przetwarzania](https://www.w3.org/TR/xmldsig-core/) z organizacja World Wide Web Consortium.

## <a name="verifying-signatures"></a>Weryfikowanie podpisów

Aby sprawdzić, czy dane zostały podpisane przez określoną stronę, musisz dysponować następującymi informacjami:

- Klucz publiczny podmiotu, który podpisał dane.

- Podpis cyfrowy.

- Dane, które zostały podpisane.

- Algorytm wyznaczania wartości skrótu używany przez program podpisujący.

Aby sprawdzić podpis podpisany przez klasę <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, użyj klasy <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter>. Klasa <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> musi być dostarczona z kluczem publicznym osoby podpisującej. Do określenia klucza publicznego potrzebne będą wartości z modułu i wykładnika. (Strona, która wygenerowała parę kluczy publiczny/prywatny powinna podawać te wartości). Najpierw Utwórz obiekt <xref:System.Security.Cryptography.RSACryptoServiceProvider>, aby pomieścić klucz publiczny, który sprawdzi podpis, a następnie zainicjuj strukturę <xref:System.Security.Cryptography.RSAParameters> do wartości moduł i wykładnik, które określają klucz publiczny.

Poniższy kod przedstawia tworzenie struktury <xref:System.Security.Cryptography.RSAParameters>. Właściwość `Modulus` jest ustawiona na wartość tablicy bajtowej o nazwie `modulusData` i Właściwość `Exponent` jest ustawiona na wartość tablicy bajtowej o nazwie `exponentData`.

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

Po utworzeniu obiektu <xref:System.Security.Cryptography.RSAParameters> można zainicjować nowe wystąpienie klasy <xref:System.Security.Cryptography.RSACryptoServiceProvider> do wartości określonych w <xref:System.Security.Cryptography.RSAParameters>. <xref:System.Security.Cryptography.RSACryptoServiceProvider> jest z kolei przekazywana do konstruktora <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> w celu przetransferowania klucza.

Poniższy przykład ilustruje ten proces. W tym przykładzie `hashValue` i `signedHashValue` to tablice bajtów dostarczone przez stronę zdalną. Strona zdalna podpisała `hashValue` przy użyciu algorytmu SHA1, generując `signedHashValue`podpis cyfrowy. Metoda <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> sprawdza, czy podpis cyfrowy jest prawidłowy i został użyty do podpisywania `hashValue`.

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

Ten fragment kodu będzie wyświetlał "`The signature is valid`", jeśli sygnatura jest prawidłowa i "`The signature is not valid`", jeśli nie jest.

## <a name="see-also"></a>Zobacz także

- [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)
