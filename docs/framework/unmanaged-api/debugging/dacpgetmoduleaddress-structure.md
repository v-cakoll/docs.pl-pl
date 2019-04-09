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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104113"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="87765-102">DacpGetModuleAddress Structure</span><span class="sxs-lookup"><span data-stu-id="87765-102">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="87765-103">Definiuje kontener dla żądania adres modułu.</span><span class="sxs-lookup"><span data-stu-id="87765-103">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="87765-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="87765-104">Syntax</span></span>

```
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="87765-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="87765-105">Members</span></span>

| <span data-ttu-id="87765-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="87765-106">Member</span></span>      | <span data-ttu-id="87765-107">Opis</span><span class="sxs-lookup"><span data-stu-id="87765-107">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="87765-108">Wskaźnik do modułu.</span><span class="sxs-lookup"><span data-stu-id="87765-108">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="87765-109">Metody</span><span class="sxs-lookup"><span data-stu-id="87765-109">Methods</span></span>

| <span data-ttu-id="87765-110">Metoda</span><span class="sxs-lookup"><span data-stu-id="87765-110">Method</span></span>                                                                                               | <span data-ttu-id="87765-111">Opis</span><span class="sxs-lookup"><span data-stu-id="87765-111">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="87765-112">Request</span><span class="sxs-lookup"><span data-stu-id="87765-112">Request</span></span>](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="87765-113">Wykonuje żądanie, aby wypełnić struktury ze struktury danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="87765-113">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="87765-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87765-114">Remarks</span></span>

<span data-ttu-id="87765-115">Ta struktura znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="87765-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="87765-116">Aby go użyć, definiują strukturę zgodnie z powyższym opisem gdzie `CLRDATA_ADDRESS` jest 64-bitowej nieoznaczonej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="87765-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="87765-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="87765-117">Requirements</span></span>
<span data-ttu-id="87765-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87765-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="87765-119">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="87765-119">**Header:** None</span></span>  
<span data-ttu-id="87765-120">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="87765-120">**Library:** None</span></span>  
**<span data-ttu-id="87765-121">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="87765-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a><span data-ttu-id="87765-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87765-122">See also</span></span>

- [<span data-ttu-id="87765-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="87765-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="87765-124">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="87765-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
