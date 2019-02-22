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
ms.openlocfilehash: 314c8b7268549380143a608bb423f849ad0bb64c
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583276"
---
# <a name="cryptographic-signatures"></a>Podpisy kryptograficzne
<a name="top"></a> Podpisy cyfrowe kryptograficzne umożliwia algorytmy kluczy publicznych zapewniają integralność danych. Po zalogowaniu danych przy użyciu podpisu cyfrowego, ktoś inny może zweryfikować podpisu, a można udowodnić, że dane pochodzą od użytkownika oraz nie została zmodyfikowana po użytkownik zarejestrowany. Aby uzyskać więcej informacji na temat podpisów cyfrowych, zobacz [usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md).  
  
 W tym temacie opisano sposób rejestrowania i weryfikowania podpisów cyfrowych przy użyciu klas w <xref:System.Security.Cryptography?displayProperty=nameWithType> przestrzeni nazw.  
  
-   [Generowanie podpisów](#generate)  
  
-   [Weryfikowanie podpisów](#verify)  
  
<a name="generate"></a>   
## <a name="generating-signatures"></a>Generowanie podpisów  
 Podpisy cyfrowe są zazwyczaj stosowane do wartości skrótu, które reprezentują więcej danych. Poniższy przykład dotyczy wartości skrótu podpisu cyfrowego. Po pierwsze, nowe wystąpienie klasy <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasa została utworzona, można wygenerować pary kluczy publiczny/prywatny. Następnie <xref:System.Security.Cryptography.RSACryptoServiceProvider> jest przekazywany do nowego wystąpienia <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> klasy. To przesłanie klucza prywatnego <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, który wykonuje cyfrowego podpisywania. Przed zarejestrowaniem skrótu, należy określić algorytm wyznaczania wartości skrótu do użycia. W tym przykładzie użyto algorytmu SHA1. Na koniec <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> metoda jest wywoływana w celu wykonania podpisywania.  
  
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
  
using System;  
using System.Security.Cryptography;  
```  
  
```csharp  
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
 Program .NET Framework oferuje <xref:System.Security.Cryptography.Xml> przestrzeni nazw, co pozwala zarejestrować XML. Podpisywanie XML jest ważne w przypadku, gdy chcesz zweryfikować, że plik XML pochodzi z danego źródła. Na przykład jeśli używasz usługi notowań giełdowych, który używa XML możesz zweryfikować źródła XML jest podpisany.  
  
 Postępuj zgodnie z klas w tej przestrzeni nazw [zalecenie składni XML podpisu i przetwarzanie](https://www.w3.org/TR/xmldsig-core/) z konsorcjum World Wide Web.  
  
 [Powrót do początku](#top)  
  
<a name="verify"></a>   
## <a name="verifying-signatures"></a>Weryfikowanie podpisów  
 Aby sprawdzić, czy dane został podpisany przez określoną stronę, musisz mieć następujące informacje:  
  
-   Klucz publiczny w innej firmy, który podpisał danych.  
  
-   Podpis cyfrowy.  
  
-   Dane, który został podpisany.  
  
-   Algorytm skrótu używany przez osoby podpisującej.  
  
 Aby zweryfikować podpisu, który został podpisany przez <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> klasy, należy użyć <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> klasy. <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> Klasa musi być podany klucz publiczny podpisu. Konieczne będzie wartości moduł i wykładnik, do określenia klucza publicznego. (Strona, która wygenerowała pary kluczy publiczny/prywatny podać te wartości.) Najpierw utwórz <xref:System.Security.Cryptography.RSACryptoServiceProvider> obiekt do przechowywania klucza publicznego, zweryfikować podpisu, a następnie zainicjuj <xref:System.Security.Cryptography.RSAParameters> struktury wyznaczanie modułu i wykładnik wartości, które określają klucz publiczny.  
  
 Poniższy kod ilustruje tworzenie <xref:System.Security.Cryptography.RSAParameters> struktury. `Modulus` Właściwości ustawiono wartość tablicy typu byte o nazwie `modulusData` i `Exponent` właściwości ustawiono wartość tablicy typu byte o nazwie `exponentData`.  
  
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
  
 Po utworzeniu <xref:System.Security.Cryptography.RSAParameters> obiektu można zainicjować nowe wystąpienie klasy <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy wartościom określonym w <xref:System.Security.Cryptography.RSAParameters>. <xref:System.Security.Cryptography.RSACryptoServiceProvider> z kolei przekazany do konstruktora obiektu <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> celu przeniesienia klucza.  
  
 Poniższy przykład ilustruje ten proces. W tym przykładzie `hashValue` i `signedHashValue` to tablice bajtów dostarczonym przez firmę zdalnego. Strona zdalna została podpisana `hashValue` przy użyciu algorytmu SHA1, tworzenie podpis cyfrowy `signedHashValue`. Program  
  
 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> metoda sprawdza, czy podpis cyfrowy jest prawidłowa i czy został użyty do podpisania `hashValue`.  
  
```vb  
Dim rsa As New RSACryptoServiceProvider()  
rsa.ImportParameters(rsaKeyInfo)  
Dim rsaDeformatter As New RSAPKCS1SignatureDeformatter(rsa)  
rsaDeformatter.SetHashAlgorithm("SHA1")  
If rsaDeformatter.VerifySignature(hashValue, signedHashValue) Then  
   Console.WriteLine("The signature is valid.")  
Else  
   Console.WriteLine("The signture is not valid.")  
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
  
 Ten fragment kodu będą wyświetlane "`The signature is valid`" Jeśli podpis jest prawidłowy i "`The signature is not valid`" Jeśli nie jest.  
  
## <a name="see-also"></a>Zobacz także

- [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)
