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
ms.openlocfilehash: 3aac7e24fa9cd03350aebf5f441063bcedfaed04
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644771"
---
# <a name="clrdatailaddressmap-structure"></a><span data-ttu-id="1c06f-102">CLRDATA_IL_ADDRESS_MAP Structure</span><span class="sxs-lookup"><span data-stu-id="1c06f-102">CLRDATA_IL_ADDRESS_MAP Structure</span></span>

<span data-ttu-id="1c06f-103">Definiuje mapowanie adresu IL.</span><span class="sxs-lookup"><span data-stu-id="1c06f-103">Defines an IL to address mapping.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="1c06f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c06f-104">Syntax</span></span>

```
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a><span data-ttu-id="1c06f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="1c06f-105">Members</span></span>

| <span data-ttu-id="1c06f-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="1c06f-106">Member</span></span>         | <span data-ttu-id="1c06f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1c06f-107">Description</span></span>                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | <span data-ttu-id="1c06f-108">Przesunięcie IL dla zakresu adresów zawarte</span><span class="sxs-lookup"><span data-stu-id="1c06f-108">IL offset for the contained address range</span></span>              |
| `startAddress` | <span data-ttu-id="1c06f-109">Adres początkowy zakresu.</span><span class="sxs-lookup"><span data-stu-id="1c06f-109">The start address of the range.</span></span>                        |
| `endAddress`   | <span data-ttu-id="1c06f-110">Adres końcowy zakresu.</span><span class="sxs-lookup"><span data-stu-id="1c06f-110">The end address of the range.</span></span>                          |
| `type`         | <span data-ttu-id="1c06f-111">Typ danych.</span><span class="sxs-lookup"><span data-stu-id="1c06f-111">The type of the data.</span></span> <span data-ttu-id="1c06f-112">Ta wartość nie jest obecnie używana</span><span class="sxs-lookup"><span data-stu-id="1c06f-112">This value is currently not used</span></span> |

## <a name="remarks"></a><span data-ttu-id="1c06f-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c06f-113">Remarks</span></span>

<span data-ttu-id="1c06f-114">Ta struktura znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="1c06f-114">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="1c06f-115">Aby go użyć, definiują strukturę zgodnie z powyższym opisem gdzie `CLRDATA_ADDRESS` jest 64-bitowej nieoznaczonej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="1c06f-115">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="1c06f-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c06f-116">Requirements</span></span>

<span data-ttu-id="1c06f-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c06f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="1c06f-118">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="1c06f-118">**Header:** None</span></span>  
<span data-ttu-id="1c06f-119">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="1c06f-119">**Library:** None</span></span>   
<span data-ttu-id="1c06f-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1c06f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="1c06f-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c06f-121">See also</span></span>

- [<span data-ttu-id="1c06f-122">Wyliczenie CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="1c06f-122">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="1c06f-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="1c06f-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="1c06f-124">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="1c06f-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
