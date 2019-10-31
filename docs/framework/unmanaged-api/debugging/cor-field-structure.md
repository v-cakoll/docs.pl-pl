---
title: COR_FIELD — Struktura
ms.date: 03/30/2017
api_name:
- COR_FIELD
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_FIELD
helpviewer_keywords:
- COR_FIELD structure [.NET Framework debugging]
ms.assetid: c0822423-a9df-4961-950d-50dcc152f863
topic_type:
- apiref
ms.openlocfilehash: 78e34d9d33d34047e3ebd2effb4894bc7b709585
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132356"
---
# <a name="cor_field-structure"></a><span data-ttu-id="e849c-102">COR_FIELD — Struktura</span><span class="sxs-lookup"><span data-stu-id="e849c-102">COR_FIELD Structure</span></span>
<span data-ttu-id="e849c-103">Zawiera informacje dotyczące pola w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="e849c-103">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e849c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e849c-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="e849c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e849c-105">Members</span></span>  
  
|<span data-ttu-id="e849c-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e849c-106">Member</span></span>|<span data-ttu-id="e849c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e849c-107">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="e849c-108">Token `mdFieldDef`, który może służyć do uzyskiwania informacji o polu.</span><span class="sxs-lookup"><span data-stu-id="e849c-108">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="e849c-109">Przesunięcie, w bajtach, do danych pola w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="e849c-109">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="e849c-110">Wartość [COR_TYPEID](cor-typeid-structure.md) , która identyfikuje typ tego pola.</span><span class="sxs-lookup"><span data-stu-id="e849c-110">A [COR_TYPEID](cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="e849c-111">Wartość wyliczenia CorElementType —, która wskazuje typ pola.</span><span class="sxs-lookup"><span data-stu-id="e849c-111">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e849c-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e849c-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e849c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e849c-113">Requirements</span></span>  
 <span data-ttu-id="e849c-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e849c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e849c-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e849c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e849c-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e849c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e849c-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e849c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e849c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e849c-118">See also</span></span>

- [<span data-ttu-id="e849c-119">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="e849c-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="e849c-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="e849c-120">Debugging</span></span>](index.md)
