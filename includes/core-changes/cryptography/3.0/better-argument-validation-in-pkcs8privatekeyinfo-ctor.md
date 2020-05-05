---
ms.openlocfilehash: 8d3a8712528d2d35c706cc26b8c388b65d6ad506
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449227"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a><span data-ttu-id="29631-101">Lepsza weryfikacja argumentów w konstruktorze Pkcs8PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="29631-101">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>

<span data-ttu-id="29631-102">Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9 `Pkcs8PrivateKeyInfo` , `algorithmParameters` Konstruktor sprawdza poprawność parametru jako pojedynczej wartości zakodowanej przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="29631-102">Starting with .NET Core 3.0 Preview 9, the `Pkcs8PrivateKeyInfo` constructor validates the `algorithmParameters` parameter as a single BER-encoded value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="29631-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="29631-103">Change description</span></span>

<span data-ttu-id="29631-104">Przed uruchomieniem programu .NET Core 3,0 w wersji zapoznawczej 9 `algorithmParameters` [ `Pkcs8PrivateKeyInfo` Konstruktor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) nie sprawdza poprawności argumentu.</span><span class="sxs-lookup"><span data-stu-id="29631-104">Before .NET Core 3.0 Preview 9, the [`Pkcs8PrivateKeyInfo` constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) did not validate the `algorithmParameters` argument.</span></span>  <span data-ttu-id="29631-105">Gdy ten argument reprezentuje nieprawidłową wartość, Konstruktor powiedzie się <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, ale wywołanie dowolnych metod,, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A> <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>lub <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> może zgłosić <xref:System.ArgumentException> dla argumentu, który nie zaakceptował (`preEncodedValue`) lub. <xref:System.Security.Cryptography.CryptographicException></span><span class="sxs-lookup"><span data-stu-id="29631-105">When this argument represented an invalid value, the constructor would succeed, but a call to any of the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, or <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> methods would throw either an <xref:System.ArgumentException> for an argument they did not accept (`preEncodedValue`) or a <xref:System.Security.Cryptography.CryptographicException>.</span></span>

<span data-ttu-id="29631-106">W przypadku uruchomienia z programem .NET Core 3,0 przed zainstalowaniem wersji zapoznawczej 9 Poniższy kod <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> zgłasza wyjątek tylko wtedy, gdy metoda jest wywoływana:</span><span class="sxs-lookup"><span data-stu-id="29631-106">If run with .NET Core 3.0 before Preview 9, the following code throws an exception only when the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> method is called:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

<span data-ttu-id="29631-107">Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9, argument jest weryfikowany w konstruktorze, a nieprawidłowa wartość powoduje, <xref:System.Security.Cryptography.CryptographicException>że metoda zgłasza.</span><span class="sxs-lookup"><span data-stu-id="29631-107">Starting with .NET Core 3.0 Preview 9, the argument is validated in the constructor, and an invalid value results in the method throwing a <xref:System.Security.Cryptography.CryptographicException>.</span></span> <span data-ttu-id="29631-108">Ta zmiana przenosi wyjątek bliżej źródła błędu danych.</span><span class="sxs-lookup"><span data-stu-id="29631-108">This change moves the exception closer to the source of the data error.</span></span> <span data-ttu-id="29631-109">Przykład:</span><span class="sxs-lookup"><span data-stu-id="29631-109">For example:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a><span data-ttu-id="29631-110">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="29631-110">Version introduced</span></span>

<span data-ttu-id="29631-111">3,0 wersja zapoznawcza 9</span><span class="sxs-lookup"><span data-stu-id="29631-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="29631-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="29631-112">Recommended action</span></span>

<span data-ttu-id="29631-113">Upewnij się, że `algorithmParameters` podane są tylko prawidłowe wartości lub że wywołania testu `Pkcs8PrivateKeyInfo` konstruktora dla obu <xref:System.ArgumentException> i <xref:System.Security.Cryptography.CryptographicException> w razie potrzeby obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="29631-113">Ensure that only valid `algorithmParameters` values are provided, or that calls to the `Pkcs8PrivateKeyInfo` constructor test for both <xref:System.ArgumentException> and <xref:System.Security.Cryptography.CryptographicException> if exception handling is desired.</span></span>

### <a name="category"></a><span data-ttu-id="29631-114">Kategoria</span><span class="sxs-lookup"><span data-stu-id="29631-114">Category</span></span>

<span data-ttu-id="29631-115">Kryptografia</span><span class="sxs-lookup"><span data-stu-id="29631-115">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="29631-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="29631-116">Affected APIs</span></span>

- <span data-ttu-id="29631-117">[Konstruktor Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span><span class="sxs-lookup"><span data-stu-id="29631-117">[Pkcs8PrivateKeyInfo constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span></span>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
