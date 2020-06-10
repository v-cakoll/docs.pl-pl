---
title: Generowanie kluczy szyfrowania i odszyfrowywania
description: Informacje na temat tworzenia kluczy symetrycznych i asymetrycznych na potrzeby szyfrowania i odszyfrowywania w programie .NET oraz zarządzania nimi.
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: f8c3633d18e200037235502487d0d91d42083241
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84661812"
---
# <a name="generating-keys-for-encryption-and-decryption"></a>Generowanie kluczy szyfrowania i odszyfrowywania
Tworzenie kluczy i zarządzanie nimi jest ważną częścią procesu kryptograficznego. Algorytmy symetryczne wymagają utworzenia klucza i wektora inicjalizacji (IV). Klucz musi być poufny dla każdego, kto nie powinien odszyfrować danych. IV nie musi być tajny, ale powinien zostać zmieniony dla każdej sesji. Algorytmy asymetryczne wymagają utworzenia klucza publicznego i klucza prywatnego. Klucz publiczny może być publiczny dla każdej osoby, natomiast klucz prywatny musi być znany tylko przez osobę, która będzie odszyfrować dane zaszyfrowane za pomocą klucza publicznego. W tej sekcji opisano, jak generować klucze dla algorytmów symetrycznych i asymetrycznych oraz zarządzać nimi.  
  
## <a name="symmetric-keys"></a>Klucze symetryczne  
 Klasy szyfrowania symetrycznego dostarczane przez .NET Framework wymagają klucza i nowego wektora inicjalizacji (IV) do szyfrowania i odszyfrowywania danych. Za każdym razem, gdy tworzysz nowe wystąpienie jednej z zarządzanych symetrycznych klas kryptograficznych przy użyciu konstruktora bez parametrów, nowy klucz i IV są tworzone automatycznie. Każda osoba, która zezwoli na odszyfrowanie danych, musi mieć ten sam klucz i IV i korzystać z tego samego algorytmu. Ogólnie rzecz biorąc, należy utworzyć nowy klucz i IV dla każdej sesji, a klucz i IV nie powinny być przechowywane do użytku w późniejszej sesji.  
  
 Aby przekazać klucz symetryczny i IV do strony zdalnej, zazwyczaj należy zaszyfrować klucz symetryczny przy użyciu szyfrowania asymetrycznego. Wysyłanie klucza w niezabezpieczonej sieci bez szyfrowania jest niebezpieczne, ponieważ każdy z nich przechwytuje klucz i IV może odszyfrować dane. Aby uzyskać więcej informacji na temat wymiany danych przy użyciu szyfrowania, zobacz [Tworzenie schematu kryptograficznego](creating-a-cryptographic-scheme.md).  
  
 Poniższy przykład pokazuje, jak utworzyć nowe wystąpienie <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> klasy implementującej algorytm TripleDES.  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
```  
  
 Gdy poprzedni kod jest wykonywany, nowy klucz i IV są generowane i umieszczane odpowiednio w właściwościach **Key** i **IV** .  
  
 Czasami może być konieczne wygenerowanie wielu kluczy. W takiej sytuacji można utworzyć nowe wystąpienie klasy implementującej algorytm symetryczny, a następnie utworzyć nowy klucz i IV, wywołując metody **do generowania kluczy** i **GenerateIV** . Poniższy przykład kodu ilustruje sposób tworzenia nowych kluczy i użycie japońskich ideograficznych po wykonaniu nowego wystąpienia symetrycznej klasy kryptograficznej.  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
tdes.GenerateIV()  
tdes.GenerateKey()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
tdes.GenerateIV();  
tdes.GenerateKey();  
```  
  
 Gdy poprzedni kod jest wykonywany, klucz i IV są generowane, gdy tworzone jest nowe wystąpienie **TripleDESCryptoServiceProvider** . Po wywołaniu metod **do generowania kluczy** i **GenerateIV** są tworzone inne klucze i IV.  
  
## <a name="asymmetric-keys"></a>Klucze asymetryczne  
 .NET Framework zawiera <xref:System.Security.Cryptography.RSACryptoServiceProvider> <xref:System.Security.Cryptography.DSACryptoServiceProvider> klasy i dla szyfrowania asymetrycznego. Te klasy tworzą parę kluczy publiczny/prywatny, gdy do utworzenia nowego wystąpienia jest używany Konstruktor bez parametrów. Klucze asymetryczne mogą być przechowywane do użytku w wielu sesjach lub generowane tylko dla jednej sesji. Chociaż klucz publiczny można ogólnie udostępnić, klucz prywatny powinien być ściśle chroniony.  
  
 Para kluczy publiczny/prywatny jest generowana za każdym razem, gdy tworzone jest nowe wystąpienie klasy algorytmu asymetrycznego. Po utworzeniu nowego wystąpienia klasy informacje o kluczach można wyodrębnić przy użyciu jednej z dwóch metod:  
  
- <xref:System.Security.Cryptography.RSA.ToXmlString%2A>Metoda, która zwraca reprezentację XML informacji o kluczu.  
  
- <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A>Metoda, która zwraca <xref:System.Security.Cryptography.RSAParameters> strukturę, która zawiera informacje o kluczu.  
  
 Obie metody akceptują wartość logiczną, która wskazuje, czy zwrócić tylko informacje o kluczu publicznym, czy zwrócić zarówno klucz publiczny, jak i informacje o kluczu prywatnym. Klasa **RSACryptoServiceProvider** może zostać zainicjowana do wartości struktury **RSAParameters** przy użyciu <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> metody.  
  
 Asymetryczne klucze prywatne nigdy nie powinny być przechowywane Verbatim ani w postaci zwykłego tekstu na komputerze lokalnym. Jeśli musisz przechować klucz prywatny, należy użyć kontenera kluczy. Aby uzyskać więcej informacji o tym, jak przechowywać klucz prywatny w kontenerze kluczy, zobacz [jak: przechowywanie kluczy asymetrycznych w kontenerze kluczy](how-to-store-asymmetric-keys-in-a-key-container.md).  
  
 Poniższy przykład kodu tworzy nowe wystąpienie klasy **RSACryptoServiceProvider** , tworząc parę kluczy publiczny/prywatny i zapisuje informacje o kluczu publicznym do struktury **RSAParameters** .  
  
```vb  
'Generate a public/private key pair.  
Dim rsa as RSACryptoServiceProvider = new RSACryptoServiceProvider()  
'Save the public key information to an RSAParameters structure.  
Dim rsaKeyInfo As RSAParameters = rsa.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();  
//Save the public key information to an RSAParameters structure.  
RSAParameters rsaKeyInfo = rsa.ExportParameters(false);  
```  
  
## <a name="see-also"></a>Zobacz także

- [Szyfrowanie danych](encrypting-data.md)
- [Odszyfrowywanie danych](decrypting-data.md)
- [Usługi kryptograficzne](cryptographic-services.md)
- [Instrukcje: przechowywanie kluczy asymetrycznych w kontenerze kluczy](how-to-store-asymmetric-keys-in-a-key-container.md)
