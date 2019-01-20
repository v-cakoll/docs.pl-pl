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
ms.openlocfilehash: 86a51605ad8ea8b394c5b8a5961f32e96baf9e58
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416162"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="b0e03-102">DacpGetModuleAddress::Request Method</span><span class="sxs-lookup"><span data-stu-id="b0e03-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="b0e03-103">Wykonuje żądanie, aby wypełnić struktury ze struktury danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b0e03-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="b0e03-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0e03-104">Syntax</span></span>

```
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

### <a name="parameters"></a><span data-ttu-id="b0e03-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0e03-105">Parameters</span></span>

<span data-ttu-id="b0e03-106">`pDataModule` [in] Wskaźnik do modułu danych inicjatora.</span><span class="sxs-lookup"><span data-stu-id="b0e03-106">`pDataModule` [in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="b0e03-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0e03-107">Remarks</span></span>

<span data-ttu-id="b0e03-108">Ta struktura znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="b0e03-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="b0e03-109">Aby go użyć, najprostszym sposobem jest naśladować wdrożenia:</span><span class="sxs-lookup"><span data-stu-id="b0e03-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="b0e03-110">Zwraca wartość uzyskany z wywołania `Request` metody `IXCLRDataModule*` parametru z następującymi parametrami: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="b0e03-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>


## <a name="requirements"></a><span data-ttu-id="b0e03-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0e03-111">Requirements</span></span>

<span data-ttu-id="b0e03-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0e03-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="b0e03-113">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="b0e03-113">**Header:** None</span></span>     
<span data-ttu-id="b0e03-114">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="b0e03-114">**Library:** None</span></span>  
<span data-ttu-id="b0e03-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b0e03-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b0e03-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0e03-116">See Also</span></span>

- [<span data-ttu-id="b0e03-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b0e03-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="b0e03-118">DacpGetModuleAddress Interface</span><span class="sxs-lookup"><span data-stu-id="b0e03-118">DacpGetModuleAddress Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md)
