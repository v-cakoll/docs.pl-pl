---
title: DacpGetModuleAddress Structure
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress Structure
helpviewer.keywords:
- DacpGetModuleAddress Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: cbea6c0562c68ae5d18247dc97bc53eb9dfbfd7e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104113"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="fa0f0-102">DacpGetModuleAddress Structure</span><span class="sxs-lookup"><span data-stu-id="fa0f0-102">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="fa0f0-103">Definiuje kontener dla żądania adres modułu.</span><span class="sxs-lookup"><span data-stu-id="fa0f0-103">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="fa0f0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fa0f0-104">Syntax</span></span>

```
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="fa0f0-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="fa0f0-105">Members</span></span>

| <span data-ttu-id="fa0f0-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="fa0f0-106">Member</span></span>      | <span data-ttu-id="fa0f0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fa0f0-107">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="fa0f0-108">Wskaźnik do modułu.</span><span class="sxs-lookup"><span data-stu-id="fa0f0-108">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="fa0f0-109">Metody</span><span class="sxs-lookup"><span data-stu-id="fa0f0-109">Methods</span></span>

| <span data-ttu-id="fa0f0-110">Metoda</span><span class="sxs-lookup"><span data-stu-id="fa0f0-110">Method</span></span>                                                                                               | <span data-ttu-id="fa0f0-111">Opis</span><span class="sxs-lookup"><span data-stu-id="fa0f0-111">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="fa0f0-112">Żądanie</span><span class="sxs-lookup"><span data-stu-id="fa0f0-112">Request</span></span>](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="fa0f0-113">Wykonuje żądanie, aby wypełnić struktury ze struktury danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="fa0f0-113">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="fa0f0-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fa0f0-114">Remarks</span></span>

<span data-ttu-id="fa0f0-115">Ta struktura znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="fa0f0-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="fa0f0-116">Aby go użyć, definiują strukturę zgodnie z powyższym opisem gdzie `CLRDATA_ADDRESS` jest 64-bitowej nieoznaczonej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="fa0f0-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="fa0f0-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fa0f0-117">Requirements</span></span>
<span data-ttu-id="fa0f0-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa0f0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="fa0f0-119">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="fa0f0-119">**Header:** None</span></span>  
<span data-ttu-id="fa0f0-120">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="fa0f0-120">**Library:** None</span></span>  
<span data-ttu-id="fa0f0-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fa0f0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="fa0f0-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa0f0-122">See also</span></span>

- [<span data-ttu-id="fa0f0-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="fa0f0-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="fa0f0-124">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="fa0f0-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
