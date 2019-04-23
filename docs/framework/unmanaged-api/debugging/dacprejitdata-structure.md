---
title: DacpReJitData, struktura
ms.date: 02/01/2019
api.name:
- DacpReJitData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpReJitData Structure
helpviewer.keywords:
- DacpReJitData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: a2850add9acb2f7c5297ac6956e349c9277be291
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122801"
---
# <a name="dacprejitdata-structure"></a><span data-ttu-id="ceaad-102">DacpReJitData, struktura</span><span class="sxs-lookup"><span data-stu-id="ceaad-102">DacpReJitData Structure</span></span>

<span data-ttu-id="ceaad-103">Definiuje podstawowe informacje o danej metody Instrumentacji profilera.</span><span class="sxs-lookup"><span data-stu-id="ceaad-103">Defines the basic information about a given profiler-instrumented method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="ceaad-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ceaad-104">Syntax</span></span>

```
struct MSLAYOUT DacpReJitData
{
    enum Flags
    {
        kUnknown,
        kRequested,
        kActive,
        kReverted,
    };

    CLRDATA_ADDRESS                 rejitID;
    Flags                           flags;
    CLRDATA_ADDRESS                 NativeCodeAddr;
};
```

## <a name="members"></a><span data-ttu-id="ceaad-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ceaad-105">Members</span></span>

| <span data-ttu-id="ceaad-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ceaad-106">Member</span></span>           | <span data-ttu-id="ceaad-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ceaad-107">Description</span></span>                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | <span data-ttu-id="ceaad-108">Numer poprawki ReJit dla metody.</span><span class="sxs-lookup"><span data-stu-id="ceaad-108">The ReJit revision number for a method.</span></span>                                                          |
| `flags`          | <span data-ttu-id="ceaad-109">Flaga wskazująca bieżący stan metody ReJit instrumentacji dla danej wersji.</span><span class="sxs-lookup"><span data-stu-id="ceaad-109">A flag indicating the current state of the method's ReJit instrumentation for the given version.</span></span> |
| `NativeCodeAddr` | <span data-ttu-id="ceaad-110">Adres podstawowy implementacji rejitted metody.</span><span class="sxs-lookup"><span data-stu-id="ceaad-110">The base address of the method's rejitted implementation.</span></span>                                         |

## <a name="remarks"></a><span data-ttu-id="ceaad-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ceaad-111">Remarks</span></span>

<span data-ttu-id="ceaad-112">Ta struktura znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="ceaad-112">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="ceaad-113">Aby go użyć, definiują strukturę, jak określono powyżej.</span><span class="sxs-lookup"><span data-stu-id="ceaad-113">To use it, define the structure as specified above.</span></span> <span data-ttu-id="ceaad-114">Struktura również musi być zdefiniowane przy użyciu `ms_struct` pakowania, jeśli nie za pomocą kompilatorów Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ceaad-114">The structure must also be defined using `ms_struct` packing if not using the Microsoft compilers.</span></span>

## <a name="requirements"></a><span data-ttu-id="ceaad-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ceaad-115">Requirements</span></span>
<span data-ttu-id="ceaad-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ceaad-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ceaad-117">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="ceaad-117">**Header:** None</span></span>  
<span data-ttu-id="ceaad-118">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="ceaad-118">**Library:** None</span></span>  
<span data-ttu-id="ceaad-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ceaad-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="ceaad-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ceaad-120">See also</span></span>

- [<span data-ttu-id="ceaad-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="ceaad-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="ceaad-122">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="ceaad-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
