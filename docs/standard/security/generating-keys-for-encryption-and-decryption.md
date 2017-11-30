---
title: Generowanie kluczy szyfrowania i odszyfrowywania
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
- keys, encryption and decryption
- keys, asymmetric
- keys, symmetric
- encryption [.NET Framework], keys
- symmetric keys
- asymmetric keys [.NET Framework]
- cryptography [.NET Framework], keys
ms.assetid: c197dfc9-a453-4226-898d-37a16638056e
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0b40e09a9a2c534d3376fa6930d8166591873a0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="generating-keys-for-encryption-and-decryption"></a>Generowanie kluczy szyfrowania i odszyfrowywania
Tworzenie i zarządzanie kluczami jest ważnym elementem procesu szyfrowania. Symetryczne algorytmy wymaga utworzenia klucza i wektor inicjowania (IV). Klucz musi być trzymane w każdy, kto powinien nie odszyfrowania danych. IV musi być tajny, ale powinny być zmieniane dla każdej sesji. Asymetryczne algorytmy wymaga utworzenia klucz publiczny i klucz prywatny. Klucz publiczny mogą być ujawniane innym osobom, gdy klucz prywatny musi znane tylko przez strony, która będzie odszyfrować dane zaszyfrowane przy użyciu klucza publicznego. W tej sekcji opisano, jak do generowania i zarządzania kluczami zarówno symetrycznego i asymetryczne algorytmy.  
  
## <a name="symmetric-keys"></a>Klucze symetryczne  
 Klasy szyfrowania symetrycznego dostarczonych przez program .NET Framework wymaga klucza i nowy wektor inicjowania (IV) do szyfrowania i odszyfrowywania danych. Podczas tworzenia nowego wystąpienia jednego z zarządzanych za pomocą konstruktora domyślnego symetrycznego klas kryptograficznych klucza i IV są tworzone automatycznie. Każda osoba, która pozwala na odszyfrowywanie danych musi posiadać ten sam klucz i IV i korzystać z tego samego algorytmu. Ogólnie rzecz biorąc dla każdej sesji powinien zostać utworzony nowy klucz i IV, a klucz ani IV powinny być przechowywane do wykorzystania w późniejszym sesji.  
  
 Do komunikacji klucza symetrycznego i IV strona zdalna, czy zwykle szyfrowania symetrycznego klucza przy użyciu szyfrowanie asymetryczne. Przesyłania tego klucza przez niezabezpieczonej sieci bez szyfrowania jest niebezpieczne, ponieważ każdy użytkownik, który przechwytuje klucza i IV odszyfrować danych. Aby uzyskać więcej informacji na temat wymiany danych przy użyciu szyfrowania, zobacz [tworzenie schematu kryptograficznego](../../../docs/standard/security/creating-a-cryptographic-scheme.md).  
  
 W poniższym przykładzie pokazano tworzenie nowego wystąpienia <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> klasa implementująca algorytmu TripleDES.  
  
```vb  
Dim TDES As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider TDES = new TripleDESCryptoServiceProvider();  
```  
  
 Po wykonaniu poprzednich kodu nowy klucz i IV były generowane i umieszczane w **klucza** i **IV** właściwości, odpowiednio.  
  
 Czasami może być konieczne do wygenerowania wielu kluczy. W takiej sytuacji można tworzyć nowe wystąpienie klasy, która implementuje algorytmu symetrycznego i utworzyć nowy klucz i IV przez wywołanie metody **GenerateKey** i **GenerateIV** metody. Poniższy przykładowy kod ilustruje sposób tworzenia nowych kluczy i wektory inicjacji po dokonaniu nowe wystąpienie klasy asymetrycznego kryptograficznych.  
  
```vb  
Dim TDES As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
TDES.GenerateIV()  
TDES.GenerateKey()  
```  
  
```csharp  
TripleDESCryptoServiceProvider TDES = new TripleDESCryptoServiceProvider();  
TDES.GenerateIV();  
TDES.GenerateKey();  
```  
  
 Po wykonaniu poprzedni kod klucza i IV są generowane podczas nowe wystąpienie klasy **TripleDESCryptoServiceProvider** staje się. Inny klucz i IV są tworzone, gdy **GenerateKey** i **GenerateIV** metody są wywoływane.  
  
## <a name="asymmetric-keys"></a>Klucze asymetryczne  
 Platforma .NET Framework zapewnia <xref:System.Security.Cryptography.RSACryptoServiceProvider> i <xref:System.Security.Cryptography.DSACryptoServiceProvider> klasy dla szyfrowanie asymetryczne. Te klasy utworzyć pary kluczy publiczny/prywatny, używając domyślnego konstruktora do utworzenia nowego wystąpienia. Klucze asymetryczne można przechowywane do wykorzystania w wiele sesji lub wygenerowany dla tylko jednej sesji. Gdy klucz publiczny mogą być udostępniane ogólnie rzecz biorąc, klucz prywatny powinien ściśle chroniony.  
  
 Pary kluczy publiczny/prywatny jest generowany, gdy tworzone jest nowe wystąpienie klasy algorytmu asymetrycznego. Po utworzeniu nowego wystąpienia klasy, informacje o kluczu można wyodrębnić przy użyciu jednej z dwóch metod:  
  
-   <xref:System.Security.Cryptography.RSA.ToXmlString%2A> Metody, która zwraca informacje o kluczu reprezentację XML.  
  
-   <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> Metody, która zwraca <xref:System.Security.Cryptography.RSAParameters> struktury, która przechowuje informacje o kluczu.  
  
 Obie metody zaakceptuj wartość logiczną wskazującą, czy zwracać tylko informacje o kluczu publicznym, czy zwracać zarówno klucz publiczny i informacje klucza prywatnego. **RSACryptoServiceProvider** klasy mogą być inicjowane w wartości **RSAParameters** struktury przy użyciu <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> metody.  
  
 Prywatne klucze asymetryczne nigdy nie powinny być przechowywane, dosłownego wyrażenia lub w postaci zwykłego tekstu na komputerze lokalnym. Jeśli musisz przechować klucz prywatny, należy użyć kontenera kluczy. Aby uzyskać więcej informacji na temat sposobu przechowywania klucza prywatnego w kontenerze kluczy, zobacz [porady: przechowywanie kluczy asymetrycznych w kontenerze klucza](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).  
  
 Poniższy przykład kodu tworzy nowe wystąpienie klasy **RSACryptoServiceProvider** klasy, tworzenie pary kluczy publiczny/prywatny i zapisuje informacje o kluczu publicznym do **RSAParameters** struktury.  
  
```vb  
'Generate a public/private key pair.  
Dim RSA as RSACryptoServiceProvider = new RSACryptoServiceProvider()  
'Save the public key information to an RSAParameters structure.  
Dim RSAKeyInfo As RSAParameters = RSA.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
//Save the public key information to an RSAParameters structure.  
RSAParameters RSAKeyInfo = RSA.ExportParameters(false);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Szyfrowanie danych](../../../docs/standard/security/encrypting-data.md)  
 [Odszyfrowywanie danych](../../../docs/standard/security/decrypting-data.md)  
 [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)  
 [Porady: przechowywanie kluczy asymetrycznych w kontenerze kluczy](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md)
