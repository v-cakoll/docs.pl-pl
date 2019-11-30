---
ms.openlocfilehash: a9b6af31b68c25ab58c52757f48ed23cca3f5a35
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567986"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a>Lepsza weryfikacja argumentów w konstruktorze Pkcs8PrivateKeyInfo

Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9, Konstruktor `Pkcs8PrivateKeyInfo` sprawdza poprawność parametru `algorithmParameters` jako pojedynczej wartości zakodowanej przez funkcję.

#### <a name="change-description"></a>Zmień opis

Przed uruchomieniem programu .NET Core 3,0 w wersji zapoznawczej 9 [konstruktor`Pkcs8PrivateKeyInfo`](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) nie potwierdził argumentu `algorithmParameters`.  Gdy ten argument reprezentuje nieprawidłową wartość, Konstruktor powiedzie się, ale wywołanie dowolnej metody <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>lub <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> spowoduje zgłoszenie <xref:System.ArgumentException> argumentu, który nie zaakceptował (`preEncodedValue`) ani <xref:System.Security.Cryptography.CryptographicException>.

W przypadku uruchomienia z programem .NET Core 3,0 przed zainstalowaniem wersji zapoznawczej 9 Poniższy kod zgłasza wyjątek tylko wtedy, gdy wywoływana jest metoda <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9, argument jest weryfikowany w konstruktorze, a nieprawidłowa wartość powoduje, że metoda zgłasza <xref:System.Security.Cryptography.CryptographicException>. Ta zmiana przenosi wyjątek bliżej źródła błędu danych. Na przykład:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 9

#### <a name="recommended-action"></a>Zalecane działanie

Upewnij się, że podane są tylko prawidłowe wartości `algorithmParameters` lub że wywołania testu konstruktora `Pkcs8PrivateKeyInfo` dla obydwu <xref:System.ArgumentException> i <xref:System.Security.Cryptography.CryptographicException>, jeśli jest wymagana obsługa wyjątków.

### <a name="category"></a>Kategoria

Kryptografia

### <a name="affected-apis"></a>Dotyczy interfejsów API

- [Konstruktor Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean))

-->
