---
title: CLRDATA_ADDRESS_RANGE, struktura
ms.date: 01/16/2019
api.name:
- CLRDATA_ADDRESS_RANGE Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_ADDRESS_RANGE Structure
helpviewer.keywords:
- CLRDATA_ADDRESS_RANGE Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: afcb4e642c9b54107423f7474771fdc28cde709e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741015"
---
# <a name="clrdataaddressrange-structure"></a><span data-ttu-id="7bdba-102">CLRDATA_ADDRESS_RANGE, struktura</span><span class="sxs-lookup"><span data-stu-id="7bdba-102">CLRDATA_ADDRESS_RANGE Structure</span></span>

<span data-ttu-id="7bdba-103">Definiuje zakres adresów.</span><span class="sxs-lookup"><span data-stu-id="7bdba-103">Defines an address range.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="7bdba-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7bdba-104">Syntax</span></span>

```cpp
typedef struct
{
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
} CLRDATA_ADDRESS_RANGE;
```

## <a name="members"></a><span data-ttu-id="7bdba-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="7bdba-105">Members</span></span>

| <span data-ttu-id="7bdba-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="7bdba-106">Member</span></span>         | <span data-ttu-id="7bdba-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7bdba-107">Description</span></span>                     |
| -------------- | ------------------------------- |
| `startAddress` | <span data-ttu-id="7bdba-108">Adres początkowy zakresu.</span><span class="sxs-lookup"><span data-stu-id="7bdba-108">The start address of the range.</span></span> |
| `endAddress`   | <span data-ttu-id="7bdba-109">Adres końcowy zakresu.</span><span class="sxs-lookup"><span data-stu-id="7bdba-109">The end address of the range.</span></span>   |

## <a name="remarks"></a><span data-ttu-id="7bdba-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7bdba-110">Remarks</span></span>

<span data-ttu-id="7bdba-111">Ta struktura znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="7bdba-111">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="7bdba-112">Aby go użyć, definiują strukturę zgodnie z powyższym opisem gdzie `CLRDATA_ADDRESS` jest 64-bitowej nieoznaczonej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="7bdba-112">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="7bdba-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7bdba-113">Requirements</span></span>

<span data-ttu-id="7bdba-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bdba-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="7bdba-115">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="7bdba-115">**Header:** None</span></span>  
<span data-ttu-id="7bdba-116">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="7bdba-116">**Library:** None</span></span>  
<span data-ttu-id="7bdba-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7bdba-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="7bdba-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7bdba-118">See also</span></span>

- [<span data-ttu-id="7bdba-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="7bdba-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="7bdba-120">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="7bdba-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
