---
title: DacpGetModuleAddress::Request, metoda
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress::Request Method
helpviewer.keywords:
- DacpGetModuleAddress::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 1755526636bed6d78663112e4c2ad5ab7c3f731c
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860835"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="ea902-102">DacpGetModuleAddress::Request, metoda</span><span class="sxs-lookup"><span data-stu-id="ea902-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="ea902-103">Wykonuje żądanie wypełnienia struktury z danej struktury środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ea902-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="ea902-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea902-104">Syntax</span></span>

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="ea902-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea902-105">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="ea902-106">podczas Wskaźnik do modułu danych inicjatora.</span><span class="sxs-lookup"><span data-stu-id="ea902-106">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="ea902-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ea902-107">Remarks</span></span>

<span data-ttu-id="ea902-108">Ta struktura jest w czasie wykonywania i nie jest udostępniana za pomocą żadnych plików nagłówkowych ani bibliotek.</span><span class="sxs-lookup"><span data-stu-id="ea902-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="ea902-109">Aby go użyć, najprostszym sposobem jest naśladowanie implementacji:</span><span class="sxs-lookup"><span data-stu-id="ea902-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="ea902-110">Zwróć wartość uzyskaną z wywołania `Request` metody dla `IXCLRDataModule*` parametru o następujących parametrach:`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="ea902-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>

## <a name="requirements"></a><span data-ttu-id="ea902-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ea902-111">Requirements</span></span>

<span data-ttu-id="ea902-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md)</span><span class="sxs-lookup"><span data-stu-id="ea902-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md)</span></span>\
<span data-ttu-id="ea902-113">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="ea902-113">**Header:** None\</span></span>
<span data-ttu-id="ea902-114">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="ea902-114">**Library:** None\</span></span>
<span data-ttu-id="ea902-115">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ea902-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ea902-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea902-116">See also</span></span>

- [<span data-ttu-id="ea902-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="ea902-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="ea902-118">DacpGetModuleAddress, struktura</span><span class="sxs-lookup"><span data-stu-id="ea902-118">DacpGetModuleAddress structure</span></span>](dacpgetmoduleaddress-structure.md)
