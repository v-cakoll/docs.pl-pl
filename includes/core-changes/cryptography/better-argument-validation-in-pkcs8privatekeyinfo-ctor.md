---
ms.openlocfilehash: a9b6af31b68c25ab58c52757f48ed23cca3f5a35
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71263306"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a><span data-ttu-id="69dd9-101">Lepsza weryfikacja argumentów w konstruktorze Pkcs8PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="69dd9-101">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>

<span data-ttu-id="69dd9-102">Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9 `Pkcs8PrivateKeyInfo` , `algorithmParameters` Konstruktor sprawdza poprawność parametru jako pojedynczej wartości zakodowanej przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="69dd9-102">Starting with .NET Core 3.0 Preview 9, the `Pkcs8PrivateKeyInfo` constructor validates the `algorithmParameters` parameter as a single BER-encoded value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="69dd9-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="69dd9-103">Change description</span></span>

<span data-ttu-id="69dd9-104">Przed uruchomieniem programu .NET Core 3,0 w [ `Pkcs8PrivateKeyInfo` ](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) wersji zapoznawczej 9 `algorithmParameters` Konstruktor nie sprawdza poprawności argumentu.</span><span class="sxs-lookup"><span data-stu-id="69dd9-104">Before .NET Core 3.0 Preview 9, the [`Pkcs8PrivateKeyInfo` constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) did not validate the `algorithmParameters` argument.</span></span>  <span data-ttu-id="69dd9-105">Gdy ten argument <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>reprezentuje nieprawidłową wartość, Konstruktor powiedzie się, ale wywołanie dowolnych metod,, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A> <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>lub <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> może zgłosić <xref:System.ArgumentException> dla argumentu, który nie zaakceptował (`preEncodedValue`) <xref:System.Security.Cryptography.CryptographicException>lub.</span><span class="sxs-lookup"><span data-stu-id="69dd9-105">When this argument represented an invalid value, the constructor would succeed, but a call to any of the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, or <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> methods would throw either an <xref:System.ArgumentException> for an argument they did not accept (`preEncodedValue`) or a <xref:System.Security.Cryptography.CryptographicException>.</span></span>

<span data-ttu-id="69dd9-106">W przypadku uruchomienia z programem .NET Core 3,0 przed zainstalowaniem wersji zapoznawczej 9 Poniższy kod <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> zgłasza wyjątek tylko wtedy, gdy metoda jest wywoływana:</span><span class="sxs-lookup"><span data-stu-id="69dd9-106">If run with .NET Core 3.0 before Preview 9, the following code throws an exception only when the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> method is called:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

<span data-ttu-id="69dd9-107">Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9, argument jest weryfikowany w konstruktorze, a nieprawidłowa wartość powoduje, <xref:System.Security.Cryptography.CryptographicException>że metoda zgłasza.</span><span class="sxs-lookup"><span data-stu-id="69dd9-107">Starting with .NET Core 3.0 Preview 9, the argument is validated in the constructor, and an invalid value results in the method throwing a <xref:System.Security.Cryptography.CryptographicException>.</span></span> <span data-ttu-id="69dd9-108">Ta zmiana przenosi wyjątek bliżej źródła błędu danych.</span><span class="sxs-lookup"><span data-stu-id="69dd9-108">This change moves the exception closer to the source of the data error.</span></span> <span data-ttu-id="69dd9-109">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="69dd9-109">For example:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a><span data-ttu-id="69dd9-110">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="69dd9-110">Version introduced</span></span>

<span data-ttu-id="69dd9-111">3,0 wersja zapoznawcza 9</span><span class="sxs-lookup"><span data-stu-id="69dd9-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="69dd9-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="69dd9-112">Recommended action</span></span>

<span data-ttu-id="69dd9-113">Upewnij się, że `algorithmParameters` podane są tylko prawidłowe wartości lub że wywołania `Pkcs8PrivateKeyInfo` testu konstruktora dla obu <xref:System.ArgumentException> i <xref:System.Security.Cryptography.CryptographicException> w razie potrzeby obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="69dd9-113">Ensure that only valid `algorithmParameters` values are provided, or that calls to the `Pkcs8PrivateKeyInfo` constructor test for both <xref:System.ArgumentException> and <xref:System.Security.Cryptography.CryptographicException> if exception handling is desired.</span></span>

### <a name="category"></a><span data-ttu-id="69dd9-114">Kategoria</span><span class="sxs-lookup"><span data-stu-id="69dd9-114">Category</span></span>

<span data-ttu-id="69dd9-115">Cryptography</span><span class="sxs-lookup"><span data-stu-id="69dd9-115">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="69dd9-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="69dd9-116">Affected APIs</span></span>

- <span data-ttu-id="69dd9-117">[Konstruktor Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span><span class="sxs-lookup"><span data-stu-id="69dd9-117">[Pkcs8PrivateKeyInfo constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span></span>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean))

-->
