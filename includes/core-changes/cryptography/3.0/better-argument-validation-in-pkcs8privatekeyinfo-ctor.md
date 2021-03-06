---
ms.openlocfilehash: 32030698c12de87daef5e1d8851a0f55ec36d688
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721421"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a>Lepsza weryfikacja argumentów w konstruktorze Pkcs8PrivateKeyInfo

Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9, `Pkcs8PrivateKeyInfo` Konstruktor sprawdza poprawność `algorithmParameters` parametru jako pojedynczej wartości zakodowanej przez funkcję.

#### <a name="change-description"></a>Zmień opis

Przed uruchomieniem programu .NET Core 3,0 w wersji zapoznawczej 9 [ `Pkcs8PrivateKeyInfo` Konstruktor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) nie sprawdza poprawności `algorithmParameters` argumentu.  Gdy ten argument reprezentuje nieprawidłową wartość, Konstruktor powiedzie się, ale wywołanie dowolnych <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A> metod,, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A> lub <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> może zgłosić <xref:System.ArgumentException> dla argumentu, który nie zaakceptował ( `preEncodedValue` ) lub <xref:System.Security.Cryptography.CryptographicException> .

W przypadku uruchomienia z programem .NET Core 3,0 przed zainstalowaniem wersji zapoznawczej 9 Poniższy kod zgłasza wyjątek tylko wtedy, gdy <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> Metoda jest wywoływana:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9, argument jest weryfikowany w konstruktorze, a nieprawidłowa wartość powoduje, że metoda zgłasza <xref:System.Security.Cryptography.CryptographicException> . Ta zmiana przenosi wyjątek bliżej źródła błędu danych. Przykład:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 9

#### <a name="recommended-action"></a>Zalecana akcja

Upewnij się, że `algorithmParameters` podane są tylko prawidłowe wartości lub że wywołania `Pkcs8PrivateKeyInfo` testu konstruktora dla obu <xref:System.ArgumentException> i w <xref:System.Security.Cryptography.CryptographicException> razie potrzeby obsługi wyjątków.

#### <a name="category"></a>Kategoria

Kryptografia

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- [Konstruktor Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
