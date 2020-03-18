---
ms.openlocfilehash: 8d3a8712528d2d35c706cc26b8c388b65d6ad506
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449227"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a>Lepsza weryfikacja argumentu w konstruktorze Pkcs8PrivateKeyInfo

Począwszy od .NET Core 3.0 Preview 9, `Pkcs8PrivateKeyInfo` konstruktor sprawdza poprawność parametru `algorithmParameters` jako pojedynczą wartość zakodowaną przez BER.

#### <a name="change-description"></a>Zmień opis

Przed .NET Core 3.0 Preview 9 [ `Pkcs8PrivateKeyInfo` konstruktor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) nie sprawdzał poprawności argumentu. `algorithmParameters`  Gdy ten argument reprezentował nieprawidłową wartość, konstruktor zakończy się <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>pomyślnie, ale wywołanie dowolnej z , , lub <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A> <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> metod będzie rzucać <xref:System.ArgumentException> za argument, którego nie zaakceptował (`preEncodedValue`) lub . <xref:System.Security.Cryptography.CryptographicException>

Jeśli uruchom z .NET Core 3.0 przed podglądem 9, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> następujący kod zgłasza wyjątek tylko wtedy, gdy metoda jest wywoływana:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

Począwszy od .NET Core 3.0 Preview 9, argument jest sprawdzany w konstruktorze, <xref:System.Security.Cryptography.CryptographicException>a nieprawidłowa wartość powoduje metodę wyrzucającą . Ta zmiana przenosi wyjątek bliżej źródła błędu danych. Przykład:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0 Podgląd 9

#### <a name="recommended-action"></a>Zalecana akcja

Upewnij się, `algorithmParameters` że podano tylko prawidłowe `Pkcs8PrivateKeyInfo` wartości lub że <xref:System.ArgumentException> <xref:System.Security.Cryptography.CryptographicException> wywołuje test konstruktora dla obu i jeśli obsługa wyjątków jest pożądane.

### <a name="category"></a>Kategoria

Kryptografia

### <a name="affected-apis"></a>Dotyczy interfejsów API

- [Konstruktor Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
