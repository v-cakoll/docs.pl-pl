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
ms.openlocfilehash: ca9ce04e9a4770d46f88e10785f4dafd044c9212
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416102"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="67761-102">DacpGetModuleAddress Structure</span><span class="sxs-lookup"><span data-stu-id="67761-102">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="67761-103">Definiuje kontener dla żądania adres modułu.</span><span class="sxs-lookup"><span data-stu-id="67761-103">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="67761-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="67761-104">Syntax</span></span>

```
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="67761-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="67761-105">Members</span></span>

| <span data-ttu-id="67761-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="67761-106">Member</span></span>      | <span data-ttu-id="67761-107">Opis</span><span class="sxs-lookup"><span data-stu-id="67761-107">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="67761-108">Wskaźnik do modułu.</span><span class="sxs-lookup"><span data-stu-id="67761-108">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="67761-109">Metody</span><span class="sxs-lookup"><span data-stu-id="67761-109">Methods</span></span>

| <span data-ttu-id="67761-110">Metoda</span><span class="sxs-lookup"><span data-stu-id="67761-110">Method</span></span>                                                                                               | <span data-ttu-id="67761-111">Opis</span><span class="sxs-lookup"><span data-stu-id="67761-111">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="67761-112">Żądanie</span><span class="sxs-lookup"><span data-stu-id="67761-112">Request</span></span>](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="67761-113">Wykonuje żądanie, aby wypełnić struktury ze struktury danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="67761-113">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="67761-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="67761-114">Remarks</span></span>

<span data-ttu-id="67761-115">Ta struktura znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="67761-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="67761-116">Aby go użyć, definiują strukturę zgodnie z powyższym opisem gdzie `CLRDATA_ADDRESS` jest 64-bitowej nieoznaczonej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="67761-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="67761-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="67761-117">Requirements</span></span>
<span data-ttu-id="67761-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67761-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="67761-119">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="67761-119">**Header:** None</span></span>  
<span data-ttu-id="67761-120">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="67761-120">**Library:** None</span></span>  
<span data-ttu-id="67761-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="67761-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="67761-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="67761-122">See Also</span></span>
- [<span data-ttu-id="67761-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="67761-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="67761-124">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="67761-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)