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
ms.openlocfilehash: 8eb841b4c4f06a3932805ae6222bdd693def5ea0
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274312"
---
# <a name="clrdata_address_range-structure"></a><span data-ttu-id="a068a-102">CLRDATA_ADDRESS_RANGE, struktura</span><span class="sxs-lookup"><span data-stu-id="a068a-102">CLRDATA_ADDRESS_RANGE Structure</span></span>

<span data-ttu-id="a068a-103">Definiuje zakres adresów.</span><span class="sxs-lookup"><span data-stu-id="a068a-103">Defines an address range.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="a068a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a068a-104">Syntax</span></span>

```cpp
typedef struct
{
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
} CLRDATA_ADDRESS_RANGE;
```

## <a name="members"></a><span data-ttu-id="a068a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a068a-105">Members</span></span>

| <span data-ttu-id="a068a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a068a-106">Member</span></span>         | <span data-ttu-id="a068a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a068a-107">Description</span></span>                     |
| -------------- | ------------------------------- |
| `startAddress` | <span data-ttu-id="a068a-108">Adres początkowy zakresu.</span><span class="sxs-lookup"><span data-stu-id="a068a-108">The start address of the range.</span></span> |
| `endAddress`   | <span data-ttu-id="a068a-109">Adres końcowy zakresu.</span><span class="sxs-lookup"><span data-stu-id="a068a-109">The end address of the range.</span></span>   |

## <a name="remarks"></a><span data-ttu-id="a068a-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a068a-110">Remarks</span></span>

<span data-ttu-id="a068a-111">Ta struktura jest w czasie wykonywania i nie jest udostępniana za pomocą żadnych plików nagłówkowych ani bibliotek.</span><span class="sxs-lookup"><span data-stu-id="a068a-111">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="a068a-112">Aby go użyć, Zdefiniuj strukturę jak określono powyżej, gdzie `CLRDATA_ADDRESS` jest 64-bitową liczbą całkowitą bez znaku.</span><span class="sxs-lookup"><span data-stu-id="a068a-112">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="a068a-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a068a-113">Requirements</span></span>

<span data-ttu-id="a068a-114">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a068a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="a068a-115">**Nagłówki** Brak</span><span class="sxs-lookup"><span data-stu-id="a068a-115">**Header:** None</span></span>  
<span data-ttu-id="a068a-116">**Biblioteki** Brak</span><span class="sxs-lookup"><span data-stu-id="a068a-116">**Library:** None</span></span>  
<span data-ttu-id="a068a-117">**.NET Framework wersje:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a068a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a068a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a068a-118">See also</span></span>

- [<span data-ttu-id="a068a-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="a068a-119">Debugging</span></span>](index.md)
- [<span data-ttu-id="a068a-120">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="a068a-120">Debugging Structures</span></span>](debugging-structures.md)
