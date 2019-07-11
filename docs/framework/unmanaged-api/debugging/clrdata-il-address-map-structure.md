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
ms.openlocfilehash: 2f34ae3e6687027aeb75e7ea169487fc8cbda466
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741035"
---
# <a name="clrdatailaddressmap-structure"></a><span data-ttu-id="d09d7-102">CLRDATA_IL_ADDRESS_MAP Structure</span><span class="sxs-lookup"><span data-stu-id="d09d7-102">CLRDATA_IL_ADDRESS_MAP Structure</span></span>

<span data-ttu-id="d09d7-103">Definiuje mapowanie adresu IL.</span><span class="sxs-lookup"><span data-stu-id="d09d7-103">Defines an IL to address mapping.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="d09d7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d09d7-104">Syntax</span></span>

```cpp
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a><span data-ttu-id="d09d7-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d09d7-105">Members</span></span>

| <span data-ttu-id="d09d7-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="d09d7-106">Member</span></span>         | <span data-ttu-id="d09d7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d09d7-107">Description</span></span>                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | <span data-ttu-id="d09d7-108">Przesunięcie IL dla zakresu adresów zawarte</span><span class="sxs-lookup"><span data-stu-id="d09d7-108">IL offset for the contained address range</span></span>              |
| `startAddress` | <span data-ttu-id="d09d7-109">Adres początkowy zakresu.</span><span class="sxs-lookup"><span data-stu-id="d09d7-109">The start address of the range.</span></span>                        |
| `endAddress`   | <span data-ttu-id="d09d7-110">Adres końcowy zakresu.</span><span class="sxs-lookup"><span data-stu-id="d09d7-110">The end address of the range.</span></span>                          |
| `type`         | <span data-ttu-id="d09d7-111">Typ danych.</span><span class="sxs-lookup"><span data-stu-id="d09d7-111">The type of the data.</span></span> <span data-ttu-id="d09d7-112">Ta wartość nie jest obecnie używana</span><span class="sxs-lookup"><span data-stu-id="d09d7-112">This value is currently not used</span></span> |

## <a name="remarks"></a><span data-ttu-id="d09d7-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d09d7-113">Remarks</span></span>

<span data-ttu-id="d09d7-114">Ta struktura znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="d09d7-114">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="d09d7-115">Aby go użyć, definiują strukturę zgodnie z powyższym opisem gdzie `CLRDATA_ADDRESS` jest 64-bitowej nieoznaczonej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="d09d7-115">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="d09d7-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d09d7-116">Requirements</span></span>

<span data-ttu-id="d09d7-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d09d7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="d09d7-118">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="d09d7-118">**Header:** None</span></span>  
<span data-ttu-id="d09d7-119">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="d09d7-119">**Library:** None</span></span>   
<span data-ttu-id="d09d7-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d09d7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="d09d7-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d09d7-121">See also</span></span>

- [<span data-ttu-id="d09d7-122">Wyliczenie CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="d09d7-122">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="d09d7-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="d09d7-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="d09d7-124">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="d09d7-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
