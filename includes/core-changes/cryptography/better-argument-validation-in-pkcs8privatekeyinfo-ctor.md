---
ms.openlocfilehash: f72a9f60d0adcace2df6f1761940f8d8cd33d3af
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119290"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a>Lepsza weryfikacja argumentów w konstruktorze Pkcs8PrivateKeyInfo

Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9 `Pkcs8PrivateKeyInfo` , `algorithmParameters` Konstruktor sprawdza poprawność parametru jako pojedynczej wartości zakodowanej przez funkcję. 

#### <a name="change-description"></a>Zmień opis

Przed uruchomieniem programu .NET Core 3,0 w [ `Pkcs8PrivateKeyInfo` ](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) wersji zapoznawczej 9 `algorithmParameters` Konstruktor nie sprawdza poprawności argumentu.  Gdy ten argument <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>reprezentuje nieprawidłową wartość, Konstruktor powiedzie się, ale wywołanie dowolnych metod,, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A> <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>lub <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> może zgłosić <xref:System.ArgumentException> dla argumentu, który nie zaakceptował (`preEncodedValue`) <xref:System.Security.Cryptography.CryptographicException>lub.

W przypadku uruchomienia z programem .NET Core 3,0 przed zainstalowaniem wersji zapoznawczej 9 Poniższy kod <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> zgłasza wyjątek tylko wtedy, gdy metoda jest wywoływana:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9, argument jest weryfikowany w konstruktorze, a nieprawidłowa wartość powoduje, <xref:System.Security.Cryptography.CryptographicException>że metoda zgłasza. Ta zmiana przenosi wyjątek bliżej źródła błędu danych. Na przykład:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 9

#### <a name="recommended-action"></a>Zalecana akcja

Upewnij się, że `algorithmParameters` podane są tylko prawidłowe wartości lub że wywołania `Pkcs8PrivateKeyInfo` testu konstruktora dla obu <xref:System.ArgumentException> i <xref:System.Security.Cryptography.CryptographicException> w razie potrzeby obsługi wyjątków.

### <a name="category"></a>Kategoria

Cryptography

### <a name="affected-apis"></a>Dotyczy interfejsów API

- [Konstruktor Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean))

-->