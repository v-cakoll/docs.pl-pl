---
ms.openlocfilehash: 8d3a8712528d2d35c706cc26b8c388b65d6ad506
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449227"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a>Lepsza weryfikacja argumentów w konstruktorze Pkcs8PrivateKeyInfo

Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9 `Pkcs8PrivateKeyInfo` , `algorithmParameters` Konstruktor sprawdza poprawność parametru jako pojedynczej wartości zakodowanej przez funkcję.

#### <a name="change-description"></a>Zmień opis

Przed uruchomieniem programu .NET Core 3,0 w wersji zapoznawczej 9 `algorithmParameters` [ `Pkcs8PrivateKeyInfo` Konstruktor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) nie sprawdza poprawności argumentu.  Gdy ten argument reprezentuje nieprawidłową wartość, Konstruktor powiedzie się <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, ale wywołanie dowolnych metod,, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A> <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>lub <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> może zgłosić <xref:System.ArgumentException> dla argumentu, który nie zaakceptował (`preEncodedValue`) lub. <xref:System.Security.Cryptography.CryptographicException>

W przypadku uruchomienia z programem .NET Core 3,0 przed zainstalowaniem wersji zapoznawczej 9 Poniższy kod <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> zgłasza wyjątek tylko wtedy, gdy metoda jest wywoływana:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9, argument jest weryfikowany w konstruktorze, a nieprawidłowa wartość powoduje, <xref:System.Security.Cryptography.CryptographicException>że metoda zgłasza. Ta zmiana przenosi wyjątek bliżej źródła błędu danych. Przykład:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 9

#### <a name="recommended-action"></a>Zalecana akcja

Upewnij się, że `algorithmParameters` podane są tylko prawidłowe wartości lub że wywołania testu `Pkcs8PrivateKeyInfo` konstruktora dla obu <xref:System.ArgumentException> i <xref:System.Security.Cryptography.CryptographicException> w razie potrzeby obsługi wyjątków.

### <a name="category"></a>Kategoria

Kryptografia

### <a name="affected-apis"></a>Dotyczy interfejsów API

- [Konstruktor Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
