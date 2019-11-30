---
ms.openlocfilehash: a9b6af31b68c25ab58c52757f48ed23cca3f5a35
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567986"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a><span data-ttu-id="7b121-101">Lepsza weryfikacja argumentów w konstruktorze Pkcs8PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="7b121-101">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>

<span data-ttu-id="7b121-102">Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9, Konstruktor `Pkcs8PrivateKeyInfo` sprawdza poprawność parametru `algorithmParameters` jako pojedynczej wartości zakodowanej przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="7b121-102">Starting with .NET Core 3.0 Preview 9, the `Pkcs8PrivateKeyInfo` constructor validates the `algorithmParameters` parameter as a single BER-encoded value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7b121-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="7b121-103">Change description</span></span>

<span data-ttu-id="7b121-104">Przed uruchomieniem programu .NET Core 3,0 w wersji zapoznawczej 9 [konstruktor`Pkcs8PrivateKeyInfo`](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) nie potwierdził argumentu `algorithmParameters`.</span><span class="sxs-lookup"><span data-stu-id="7b121-104">Before .NET Core 3.0 Preview 9, the [`Pkcs8PrivateKeyInfo` constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) did not validate the `algorithmParameters` argument.</span></span>  <span data-ttu-id="7b121-105">Gdy ten argument reprezentuje nieprawidłową wartość, Konstruktor powiedzie się, ale wywołanie dowolnej metody <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>lub <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> spowoduje zgłoszenie <xref:System.ArgumentException> argumentu, który nie zaakceptował (`preEncodedValue`) ani <xref:System.Security.Cryptography.CryptographicException>.</span><span class="sxs-lookup"><span data-stu-id="7b121-105">When this argument represented an invalid value, the constructor would succeed, but a call to any of the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, or <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> methods would throw either an <xref:System.ArgumentException> for an argument they did not accept (`preEncodedValue`) or a <xref:System.Security.Cryptography.CryptographicException>.</span></span>

<span data-ttu-id="7b121-106">W przypadku uruchomienia z programem .NET Core 3,0 przed zainstalowaniem wersji zapoznawczej 9 Poniższy kod zgłasza wyjątek tylko wtedy, gdy wywoływana jest metoda <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>:</span><span class="sxs-lookup"><span data-stu-id="7b121-106">If run with .NET Core 3.0 before Preview 9, the following code throws an exception only when the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> method is called:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

<span data-ttu-id="7b121-107">Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9, argument jest weryfikowany w konstruktorze, a nieprawidłowa wartość powoduje, że metoda zgłasza <xref:System.Security.Cryptography.CryptographicException>.</span><span class="sxs-lookup"><span data-stu-id="7b121-107">Starting with .NET Core 3.0 Preview 9, the argument is validated in the constructor, and an invalid value results in the method throwing a <xref:System.Security.Cryptography.CryptographicException>.</span></span> <span data-ttu-id="7b121-108">Ta zmiana przenosi wyjątek bliżej źródła błędu danych.</span><span class="sxs-lookup"><span data-stu-id="7b121-108">This change moves the exception closer to the source of the data error.</span></span> <span data-ttu-id="7b121-109">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="7b121-109">For example:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a><span data-ttu-id="7b121-110">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="7b121-110">Version introduced</span></span>

<span data-ttu-id="7b121-111">3,0 wersja zapoznawcza 9</span><span class="sxs-lookup"><span data-stu-id="7b121-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7b121-112">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="7b121-112">Recommended action</span></span>

<span data-ttu-id="7b121-113">Upewnij się, że podane są tylko prawidłowe wartości `algorithmParameters` lub że wywołania testu konstruktora `Pkcs8PrivateKeyInfo` dla obydwu <xref:System.ArgumentException> i <xref:System.Security.Cryptography.CryptographicException>, jeśli jest wymagana obsługa wyjątków.</span><span class="sxs-lookup"><span data-stu-id="7b121-113">Ensure that only valid `algorithmParameters` values are provided, or that calls to the `Pkcs8PrivateKeyInfo` constructor test for both <xref:System.ArgumentException> and <xref:System.Security.Cryptography.CryptographicException> if exception handling is desired.</span></span>

### <a name="category"></a><span data-ttu-id="7b121-114">Kategoria</span><span class="sxs-lookup"><span data-stu-id="7b121-114">Category</span></span>

<span data-ttu-id="7b121-115">Kryptografia</span><span class="sxs-lookup"><span data-stu-id="7b121-115">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="7b121-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="7b121-116">Affected APIs</span></span>

- <span data-ttu-id="7b121-117">[Konstruktor Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span><span class="sxs-lookup"><span data-stu-id="7b121-117">[Pkcs8PrivateKeyInfo constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span></span>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean))

-->
