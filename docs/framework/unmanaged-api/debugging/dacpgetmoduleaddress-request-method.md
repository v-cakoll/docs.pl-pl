---
title: DacpGetModuleAddress::Request Method
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
ms.openlocfilehash: 298620092c37b2c02332e9135f73584272e326bd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111686"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="0ff1f-102">DacpGetModuleAddress::Request Method</span><span class="sxs-lookup"><span data-stu-id="0ff1f-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="0ff1f-103">Wykonuje żądanie, aby wypełnić struktury ze struktury danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="0ff1f-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="0ff1f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ff1f-104">Syntax</span></span>

```
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="0ff1f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ff1f-105">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="0ff1f-106">[in] Wskaźnik do modułu danych inicjatora.</span><span class="sxs-lookup"><span data-stu-id="0ff1f-106">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="0ff1f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ff1f-107">Remarks</span></span>

<span data-ttu-id="0ff1f-108">Ta struktura znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="0ff1f-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="0ff1f-109">Aby go użyć, najprostszym sposobem jest naśladować wdrożenia:</span><span class="sxs-lookup"><span data-stu-id="0ff1f-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="0ff1f-110">Zwraca wartość uzyskany z wywołania `Request` metody `IXCLRDataModule*` parametru z następującymi parametrami: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="0ff1f-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>

## <a name="requirements"></a><span data-ttu-id="0ff1f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0ff1f-111">Requirements</span></span>

<span data-ttu-id="0ff1f-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ff1f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="0ff1f-113">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="0ff1f-113">**Header:** None</span></span>     
<span data-ttu-id="0ff1f-114">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="0ff1f-114">**Library:** None</span></span>  
<span data-ttu-id="0ff1f-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0ff1f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="0ff1f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ff1f-116">See also</span></span>

- [<span data-ttu-id="0ff1f-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="0ff1f-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="0ff1f-118">DacpGetModuleAddress Interface</span><span class="sxs-lookup"><span data-stu-id="0ff1f-118">DacpGetModuleAddress Interface</span></span>](dacpgetmoduleaddress-structure.md)