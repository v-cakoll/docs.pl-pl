---
ms.openlocfilehash: 8d3a8712528d2d35c706cc26b8c388b65d6ad506
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449227"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a><span data-ttu-id="66158-101">Lepsza weryfikacja argumentu w konstruktorze Pkcs8PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="66158-101">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>

<span data-ttu-id="66158-102">Począwszy od .NET Core 3.0 Preview 9, `Pkcs8PrivateKeyInfo` konstruktor sprawdza poprawność parametru `algorithmParameters` jako pojedynczą wartość zakodowaną przez BER.</span><span class="sxs-lookup"><span data-stu-id="66158-102">Starting with .NET Core 3.0 Preview 9, the `Pkcs8PrivateKeyInfo` constructor validates the `algorithmParameters` parameter as a single BER-encoded value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="66158-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="66158-103">Change description</span></span>

<span data-ttu-id="66158-104">Przed .NET Core 3.0 Preview 9 [ `Pkcs8PrivateKeyInfo` konstruktor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) nie sprawdzał poprawności argumentu. `algorithmParameters`</span><span class="sxs-lookup"><span data-stu-id="66158-104">Before .NET Core 3.0 Preview 9, the [`Pkcs8PrivateKeyInfo` constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) did not validate the `algorithmParameters` argument.</span></span>  <span data-ttu-id="66158-105">Gdy ten argument reprezentował nieprawidłową wartość, konstruktor zakończy się <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>pomyślnie, ale wywołanie dowolnej z , , lub <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A> <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> metod będzie rzucać <xref:System.ArgumentException> za argument, którego nie zaakceptował (`preEncodedValue`) lub . <xref:System.Security.Cryptography.CryptographicException></span><span class="sxs-lookup"><span data-stu-id="66158-105">When this argument represented an invalid value, the constructor would succeed, but a call to any of the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, or <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> methods would throw either an <xref:System.ArgumentException> for an argument they did not accept (`preEncodedValue`) or a <xref:System.Security.Cryptography.CryptographicException>.</span></span>

<span data-ttu-id="66158-106">Jeśli uruchom z .NET Core 3.0 przed podglądem 9, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> następujący kod zgłasza wyjątek tylko wtedy, gdy metoda jest wywoływana:</span><span class="sxs-lookup"><span data-stu-id="66158-106">If run with .NET Core 3.0 before Preview 9, the following code throws an exception only when the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> method is called:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

<span data-ttu-id="66158-107">Począwszy od .NET Core 3.0 Preview 9, argument jest sprawdzany w konstruktorze, <xref:System.Security.Cryptography.CryptographicException>a nieprawidłowa wartość powoduje metodę wyrzucającą .</span><span class="sxs-lookup"><span data-stu-id="66158-107">Starting with .NET Core 3.0 Preview 9, the argument is validated in the constructor, and an invalid value results in the method throwing a <xref:System.Security.Cryptography.CryptographicException>.</span></span> <span data-ttu-id="66158-108">Ta zmiana przenosi wyjątek bliżej źródła błędu danych.</span><span class="sxs-lookup"><span data-stu-id="66158-108">This change moves the exception closer to the source of the data error.</span></span> <span data-ttu-id="66158-109">Przykład:</span><span class="sxs-lookup"><span data-stu-id="66158-109">For example:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a><span data-ttu-id="66158-110">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="66158-110">Version introduced</span></span>

<span data-ttu-id="66158-111">3.0 Podgląd 9</span><span class="sxs-lookup"><span data-stu-id="66158-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="66158-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="66158-112">Recommended action</span></span>

<span data-ttu-id="66158-113">Upewnij się, `algorithmParameters` że podano tylko prawidłowe `Pkcs8PrivateKeyInfo` wartości lub że <xref:System.ArgumentException> <xref:System.Security.Cryptography.CryptographicException> wywołuje test konstruktora dla obu i jeśli obsługa wyjątków jest pożądane.</span><span class="sxs-lookup"><span data-stu-id="66158-113">Ensure that only valid `algorithmParameters` values are provided, or that calls to the `Pkcs8PrivateKeyInfo` constructor test for both <xref:System.ArgumentException> and <xref:System.Security.Cryptography.CryptographicException> if exception handling is desired.</span></span>

### <a name="category"></a><span data-ttu-id="66158-114">Kategoria</span><span class="sxs-lookup"><span data-stu-id="66158-114">Category</span></span>

<span data-ttu-id="66158-115">Kryptografia</span><span class="sxs-lookup"><span data-stu-id="66158-115">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="66158-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="66158-116">Affected APIs</span></span>

- <span data-ttu-id="66158-117">[Konstruktor Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span><span class="sxs-lookup"><span data-stu-id="66158-117">[Pkcs8PrivateKeyInfo constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span></span>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
