---
title: CLRDATA_IL_ADDRESS_MAP, struktura
ms.date: 01/16/2019
api.name:
- CLRDATA_IL_ADDRESS_MAP Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure
helpviewer.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: e680a7a0dc3209d1988f6c84be0864572a74b3a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179378"
---
# <a name="clrdata_il_address_map-structure"></a><span data-ttu-id="3e9ed-102">CLRDATA_IL_ADDRESS_MAP, struktura</span><span class="sxs-lookup"><span data-stu-id="3e9ed-102">CLRDATA_IL_ADDRESS_MAP Structure</span></span>

<span data-ttu-id="3e9ed-103">Definiuje mapowanie IL do adresów.</span><span class="sxs-lookup"><span data-stu-id="3e9ed-103">Defines an IL to address mapping.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="3e9ed-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e9ed-104">Syntax</span></span>

```cpp
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a><span data-ttu-id="3e9ed-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3e9ed-105">Members</span></span>

| <span data-ttu-id="3e9ed-106">Członek</span><span class="sxs-lookup"><span data-stu-id="3e9ed-106">Member</span></span>         | <span data-ttu-id="3e9ed-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3e9ed-107">Description</span></span>                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | <span data-ttu-id="3e9ed-108">Przesunięcie IL dla zamkniętego zakresu adresów</span><span class="sxs-lookup"><span data-stu-id="3e9ed-108">IL offset for the contained address range</span></span>              |
| `startAddress` | <span data-ttu-id="3e9ed-109">Adres początkowy zakresu.</span><span class="sxs-lookup"><span data-stu-id="3e9ed-109">The start address of the range.</span></span>                        |
| `endAddress`   | <span data-ttu-id="3e9ed-110">Adres końcowy zakresu.</span><span class="sxs-lookup"><span data-stu-id="3e9ed-110">The end address of the range.</span></span>                          |
| `type`         | <span data-ttu-id="3e9ed-111">Typ danych.</span><span class="sxs-lookup"><span data-stu-id="3e9ed-111">The type of the data.</span></span> <span data-ttu-id="3e9ed-112">Ta wartość nie jest obecnie używana</span><span class="sxs-lookup"><span data-stu-id="3e9ed-112">This value is currently not used</span></span> |

## <a name="remarks"></a><span data-ttu-id="3e9ed-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3e9ed-113">Remarks</span></span>

<span data-ttu-id="3e9ed-114">Ta struktura znajduje się wewnątrz środowiska wykonawczego i nie jest narażona za pośrednictwem żadnych nagłówków lub plików biblioteki.</span><span class="sxs-lookup"><span data-stu-id="3e9ed-114">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="3e9ed-115">Aby go użyć, zdefiniuj `CLRDATA_ADDRESS` strukturę określoną powyżej, gdzie jest 64-bitową niepodpisaną całkowitej liczby.</span><span class="sxs-lookup"><span data-stu-id="3e9ed-115">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="3e9ed-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3e9ed-116">Requirements</span></span>

<span data-ttu-id="3e9ed-117">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e9ed-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="3e9ed-118">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="3e9ed-118">**Header:** None</span></span>  
<span data-ttu-id="3e9ed-119">**Biblioteka:** Brak **wersji programu .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3e9ed-119">**Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="3e9ed-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e9ed-120">See also</span></span>

- [<span data-ttu-id="3e9ed-121">Wyliczanie CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="3e9ed-121">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="3e9ed-122">Debugging</span><span class="sxs-lookup"><span data-stu-id="3e9ed-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="3e9ed-123">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="3e9ed-123">Debugging Structures</span></span>](debugging-structures.md)
