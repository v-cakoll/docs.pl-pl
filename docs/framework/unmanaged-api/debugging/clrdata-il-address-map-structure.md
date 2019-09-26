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
ms.openlocfilehash: 3f6928832d822422177ebd7def142422953468a0
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274294"
---
# <a name="clrdata_il_address_map-structure"></a><span data-ttu-id="f6992-102">CLRDATA_IL_ADDRESS_MAP Structure</span><span class="sxs-lookup"><span data-stu-id="f6992-102">CLRDATA_IL_ADDRESS_MAP Structure</span></span>

<span data-ttu-id="f6992-103">Definiuje mapowanie IL to Address.</span><span class="sxs-lookup"><span data-stu-id="f6992-103">Defines an IL to address mapping.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="f6992-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6992-104">Syntax</span></span>

```cpp
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a><span data-ttu-id="f6992-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f6992-105">Members</span></span>

| <span data-ttu-id="f6992-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="f6992-106">Member</span></span>         | <span data-ttu-id="f6992-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f6992-107">Description</span></span>                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | <span data-ttu-id="f6992-108">Przesunięcie IL dla zawartego zakresu adresów</span><span class="sxs-lookup"><span data-stu-id="f6992-108">IL offset for the contained address range</span></span>              |
| `startAddress` | <span data-ttu-id="f6992-109">Adres początkowy zakresu.</span><span class="sxs-lookup"><span data-stu-id="f6992-109">The start address of the range.</span></span>                        |
| `endAddress`   | <span data-ttu-id="f6992-110">Adres końcowy zakresu.</span><span class="sxs-lookup"><span data-stu-id="f6992-110">The end address of the range.</span></span>                          |
| `type`         | <span data-ttu-id="f6992-111">Typ danych.</span><span class="sxs-lookup"><span data-stu-id="f6992-111">The type of the data.</span></span> <span data-ttu-id="f6992-112">Ta wartość nie jest obecnie używana</span><span class="sxs-lookup"><span data-stu-id="f6992-112">This value is currently not used</span></span> |

## <a name="remarks"></a><span data-ttu-id="f6992-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f6992-113">Remarks</span></span>

<span data-ttu-id="f6992-114">Ta struktura jest w czasie wykonywania i nie jest udostępniana za pomocą żadnych plików nagłówkowych ani bibliotek.</span><span class="sxs-lookup"><span data-stu-id="f6992-114">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="f6992-115">Aby go użyć, Zdefiniuj strukturę jak określono powyżej, gdzie `CLRDATA_ADDRESS` jest 64-bitową liczbą całkowitą bez znaku.</span><span class="sxs-lookup"><span data-stu-id="f6992-115">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="f6992-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f6992-116">Requirements</span></span>

<span data-ttu-id="f6992-117">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6992-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="f6992-118">**Nagłówki** Brak</span><span class="sxs-lookup"><span data-stu-id="f6992-118">**Header:** None</span></span>  
<span data-ttu-id="f6992-119">**Biblioteki** Brak</span><span class="sxs-lookup"><span data-stu-id="f6992-119">**Library:** None</span></span>   
<span data-ttu-id="f6992-120">**.NET Framework wersje:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f6992-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="f6992-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6992-121">See also</span></span>

- [<span data-ttu-id="f6992-122">CLRDataSourceType, Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="f6992-122">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="f6992-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="f6992-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="f6992-124">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="f6992-124">Debugging Structures</span></span>](debugging-structures.md)
