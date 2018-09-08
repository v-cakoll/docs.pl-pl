---
title: Generowanie kluczy szyfrowania i odszyfrowywania
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 839a04d8a06e782582705cf0d9ad92d2e2df6af6
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135409"
---
# <a name="generating-keys-for-encryption-and-decryption"></a>Generowanie kluczy szyfrowania i odszyfrowywania
Tworzenie i zarządzanie kluczami jest ważną częścią procesu szyfrowania. Symetryczne algorytmy wymaga utworzenia klucza i wektor inicjowania (IV). Klucz musi trzymane w tajemnicy każdy, kto powinien nie odszyfrowania danych. IV nie muszą być wpisu tajnego, ale powinna zostać zmieniona dla każdej sesji. Asymetryczne algorytmy wymagają utworzenia klucza publicznego i prywatnego klucza. Klucz publiczny mogą być ujawniane dla każdego, kto, gdy klucz prywatny musi znane tylko przez strony, która spowoduje odszyfrowanie dane zaszyfrowane przy użyciu klucza publicznego. W tej sekcji opisano sposób generowania i zarządzania kluczami symetrycznego i asymetrycznych algorytmów.  
  
## <a name="symmetric-keys"></a>Klucze symetryczne  
 Klasy szyfrowania symetrycznego, dostarczanych przez .NET Framework wymaga klucza i nowy wektor inicjowania (IV) do szyfrowania i odszyfrowywania danych. Zawsze, gdy tworzysz nowe wystąpienie jednego z zarządzanego symetrycznego klas kryptograficznych przy użyciu domyślnego konstruktora, nowy klucz i IV są tworzone automatycznie. Każda osoba, dzięki czemu można odszyfrować danych muszą posiadać ten sam klucz i IV i używać tego samego algorytmu. Ogólnie rzecz biorąc dla każdej sesji powinien zostać utworzony nowy klucz i IV, a klucz ani IV powinny być przechowywane do użytku w sesji nowsze.  
  
 Do przekazywania klucza symetrycznego i IV zdalnego innych firm, będzie zazwyczaj szyfrowania klucza symetrycznego za pomocą asymetrycznych. Wysyłanie klucz za pośrednictwem niezabezpieczonej sieci bez szyfrowania stanowi zagrożenie, ponieważ każdy, kto przechwytuje klucz i IV odszyfrować danych. Aby uzyskać więcej informacji na temat wymiana danych przy użyciu szyfrowania, zobacz [tworzenie schematu kryptograficznego](../../../docs/standard/security/creating-a-cryptographic-scheme.md).  
  
 W poniższym przykładzie pokazano tworzenie nowego wystąpienia <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> klasę, która implementuje algorytm TripleDES.  
  
```vb  
Dim TDES As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider TDES = new TripleDESCryptoServiceProvider();  
```  
  
 Jeśli poprzedni kod jest wykonywany, nowy klucz i IV są generowane i umieszczane w **klucz** i **IV** właściwości, odpowiednio.  
  
 Czasami może być konieczne generowania wielu kluczy. W takiej sytuacji można utworzyć nowe wystąpienie klasy, która implementuje algorytm symetryczny i utworzyć nowy klucz i IV przez wywołanie metody **do generowania kluczy** i **GenerateIV** metody. Poniższy przykładowy kod przedstawia sposób tworzenia nowych kluczy i wektory, po dokonaniu nowe wystąpienie klasy kryptograficznych asymetrycznego.  
  
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
  
 Po poprzednim kodzie jest wykonywana, klucza i IV są generowane podczas nowe wystąpienie klasy **TripleDESCryptoServiceProvider** wykonano. Inny klucz i IV są tworzone, gdy **do generowania kluczy** i **GenerateIV** metody są wywoływane.  
  
## <a name="asymmetric-keys"></a>Klucze asymetryczne  
 Program .NET Framework oferuje <xref:System.Security.Cryptography.RSACryptoServiceProvider> i <xref:System.Security.Cryptography.DSACryptoServiceProvider> klasy dla szyfrowanie asymetryczne. W ramach tych zajęć utworzyć parę kluczy publiczny/prywatny, używając domyślnego konstruktora do utworzenia nowego wystąpienia. Klucze asymetryczne może przechowywane do użytku w wielu sesjach lub generowane dla tylko jednej sesji. Podczas gdy klucz publiczny może być ogólnie dostępne, klucz prywatny powinny być ściśle chronione podobnie.  
  
 Pary kluczy publiczny/prywatny jest generowany, gdy tworzone jest nowe wystąpienie klasy algorytmu asymetrycznego. Po utworzeniu nowe wystąpienie klasy informacje o kluczu można wyodrębnić przy użyciu jednej z dwóch metod:  
  
-   <xref:System.Security.Cryptography.RSA.ToXmlString%2A> Metody, która zwraca informacje o kluczu Reprezentacja XML.  
  
-   <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> Metody, która zwraca <xref:System.Security.Cryptography.RSAParameters> strukturę, która przechowuje informacje o kluczu.  
  
 Obie metody zaakceptuj wartość logiczna, która wskazuje, czy zwracać tylko informacje o kluczu publicznym lub w celu zwrócenia zarówno klucz publiczny, jak i informacje klucza prywatnego. **RSACryptoServiceProvider** klasy mogą być inicjowane na wartość **RSAParameters** struktury za pomocą <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> metody.  
  
 Klucze asymetryczne prywatnej nigdy nie powinny być przechowywane, verbatim lub w postaci zwykłego tekstu, na komputerze lokalnym. Jeśli musisz przechować klucz prywatny, należy użyć kontenera kluczy. Aby uzyskać więcej informacji na temat sposobu przechowywać klucz prywatny w kontenerze kluczy, zobacz [jak: Store Asymmetric Keys in a Key Container](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).  
  
 Poniższy przykład kodu tworzy nowe wystąpienie klasy **RSACryptoServiceProvider** klasy, tworząc parę kluczy publiczny/prywatny, a następnie zapisuje informacje o kluczu publicznym do **RSAParameters** struktury.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Szyfrowanie danych](../../../docs/standard/security/encrypting-data.md)  
- [Odszyfrowywanie danych](../../../docs/standard/security/decrypting-data.md)  
- [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)  
- [Instrukcje: przechowywanie kluczy asymetrycznych w kontenerze kluczy](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md)
