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
ms.openlocfilehash: 3f9d83a0edb6dc2261931e422b0ae4c735d2e0d1
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086099"
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
        Dim HashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135}  
  
        'The value to hold the signed value.  
        Dim SignedHashValue() As Byte  
  
        'Generate a public/private key pair.  
        Dim RSA As New RSACryptoServiceProvider()  
  
        'Create an RSAPKCS1SignatureFormatter object and pass it   
        'the RSACryptoServiceProvider to transfer the private key.  
        Dim RSAFormatter As New RSAPKCS1SignatureFormatter(RSA)  
  
        'Set the hash algorithm to SHA1.  
        RSAFormatter.SetHashAlgorithm("SHA1")  
  
        'Create a signature for HashValue and assign it to   
        'SignedHashValue.  
        SignedHashValue = RSAFormatter.CreateSignature(HashValue)  
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
      byte[] HashValue = {59,4,248,102,77,97,142,201,210,12,224,93,25,41,100,197,213,134,130,135};  
  
      //The value to hold the signed value.  
      byte[] SignedHashValue;  
  
      //Generate a public/private key pair.  
      RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
  
      //Create an RSAPKCS1SignatureFormatter object and pass it the   
      //RSACryptoServiceProvider to transfer the private key.  
      RSAPKCS1SignatureFormatter RSAFormatter = new RSAPKCS1SignatureFormatter(RSA);  
  
      //Set the hash algorithm to SHA1.  
      RSAFormatter.SetHashAlgorithm("SHA1");  
  
      //Create a signature for HashValue and assign it to   
      //SignedHashValue.  
      SignedHashValue = RSAFormatter.CreateSignature(HashValue);  
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
  
 Poniższy kod ilustruje tworzenie <xref:System.Security.Cryptography.RSAParameters> struktury. `Modulus` Właściwości ustawiono wartość tablicy typu byte o nazwie `ModulusData` i `Exponent` właściwości ustawiono wartość tablicy typu byte o nazwie `ExponentData`.  
  
```vb  
Dim RSAKeyInfo As RSAParameters  
RSAKeyInfo.Modulus = ModulusData  
RSAKeyInfo.Exponent = ExponentData  
```  
  
```csharp  
RSAParameters RSAKeyInfo;  
RSAKeyInfo.Modulus = ModulusData;  
RSAKeyInfo.Exponent = ExponentData;  
```  
  
 Po utworzeniu <xref:System.Security.Cryptography.RSAParameters> obiektu można zainicjować nowe wystąpienie klasy <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy wartościom określonym w <xref:System.Security.Cryptography.RSAParameters>. <xref:System.Security.Cryptography.RSACryptoServiceProvider> z kolei przekazany do konstruktora obiektu <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> celu przeniesienia klucza.  
  
 Poniższy przykład ilustruje ten proces. W tym przykładzie `HashValue` i `SignedHashValue` to tablice bajtów dostarczonym przez firmę zdalnego. Strona zdalna została podpisana `HashValue` przy użyciu algorytmu SHA1, tworzenie podpis cyfrowy `SignedHashValue`. Program  
  
 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> metoda sprawdza, czy podpis cyfrowy jest prawidłowa i czy został użyty do podpisania `HashValue`.  
  
```vb  
Dim RSA As New RSACryptoServiceProvider()  
RSA.ImportParameters(RSAKeyInfo)  
Dim RSADeformatter As New RSAPKCS1SignatureDeformatter(RSA)  
RSADeformatter.SetHashAlgorithm("SHA1")  
If RSADeformatter.VerifySignature(HashValue, SignedHashValue) Then  
   Console.WriteLine("The signature is valid.")  
Else  
   Console.WriteLine("The signture is not valid.")  
End If  
```  
  
```csharp  
RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
RSA.ImportParameters(RSAKeyInfo);  
RSAPKCS1SignatureDeformatter RSADeformatter = new RSAPKCS1SignatureDeformatter(RSA);  
RSADeformatter.SetHashAlgorithm("SHA1");  
if(RSADeformatter.VerifySignature(HashValue, SignedHashValue))  
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
