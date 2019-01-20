---
title: CLRDATA_IL_ADDRESS_MAP Structure
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
ms.openlocfilehash: 94ebef007cf2893b63383aa4657d382728d3c759
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416103"
---
# <a name="clrdatailaddressmap-structure"></a><span data-ttu-id="62e2b-102">CLRDATA_IL_ADDRESS_MAP Structure</span><span class="sxs-lookup"><span data-stu-id="62e2b-102">CLRDATA_IL_ADDRESS_MAP Structure</span></span>

<span data-ttu-id="62e2b-103">Definiuje mapowanie adresu IL.</span><span class="sxs-lookup"><span data-stu-id="62e2b-103">Defines an IL to address mapping.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="62e2b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="62e2b-104">Syntax</span></span>

```
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a><span data-ttu-id="62e2b-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="62e2b-105">Members</span></span>

| <span data-ttu-id="62e2b-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="62e2b-106">Member</span></span>         | <span data-ttu-id="62e2b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="62e2b-107">Description</span></span>                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | <span data-ttu-id="62e2b-108">Przesunięcie IL dla zakresu adresów zawarte</span><span class="sxs-lookup"><span data-stu-id="62e2b-108">IL offset for the contained address range</span></span>              |
| `startAddress` | <span data-ttu-id="62e2b-109">Adres początkowy zakresu.</span><span class="sxs-lookup"><span data-stu-id="62e2b-109">The start address of the range.</span></span>                        |
| `endAddress`   | <span data-ttu-id="62e2b-110">Adres końcowy zakresu.</span><span class="sxs-lookup"><span data-stu-id="62e2b-110">The end address of the range.</span></span>                          |
| `type`         | <span data-ttu-id="62e2b-111">Typ danych.</span><span class="sxs-lookup"><span data-stu-id="62e2b-111">The type of the data.</span></span> <span data-ttu-id="62e2b-112">Ta wartość nie jest obecnie używana</span><span class="sxs-lookup"><span data-stu-id="62e2b-112">This value is currently not used</span></span> |

## <a name="remarks"></a><span data-ttu-id="62e2b-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62e2b-113">Remarks</span></span>

<span data-ttu-id="62e2b-114">Ta struktura znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="62e2b-114">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="62e2b-115">Aby go użyć, definiują strukturę zgodnie z powyższym opisem gdzie `CLRDATA_ADDRESS` jest 64-bitowej nieoznaczonej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="62e2b-115">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="62e2b-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62e2b-116">Requirements</span></span>

<span data-ttu-id="62e2b-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62e2b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="62e2b-118">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="62e2b-118">**Header:** None</span></span>  
<span data-ttu-id="62e2b-119">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="62e2b-119">**Library:** None</span></span>   
<span data-ttu-id="62e2b-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="62e2b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="62e2b-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62e2b-121">See Also</span></span>

- [<span data-ttu-id="62e2b-122">Wyliczenie CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="62e2b-122">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="62e2b-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="62e2b-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="62e2b-124">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="62e2b-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
