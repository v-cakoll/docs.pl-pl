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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f857f773f02da25fe6650000be777b8290f5af91
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274061"
---
# <a name="cor_field-structure"></a><span data-ttu-id="ee6e2-102">COR_FIELD — Struktura</span><span class="sxs-lookup"><span data-stu-id="ee6e2-102">COR_FIELD Structure</span></span>
<span data-ttu-id="ee6e2-103">Zawiera informacje dotyczące pola w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="ee6e2-103">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee6e2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee6e2-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="ee6e2-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ee6e2-105">Members</span></span>  
  
|<span data-ttu-id="ee6e2-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ee6e2-106">Member</span></span>|<span data-ttu-id="ee6e2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ee6e2-107">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="ee6e2-108">`mdFieldDef` Token, który może służyć do uzyskiwania informacji o polu.</span><span class="sxs-lookup"><span data-stu-id="ee6e2-108">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="ee6e2-109">Przesunięcie, w bajtach, do danych pola w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="ee6e2-109">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="ee6e2-110">Wartość [COR_TYPEID](cor-typeid-structure.md) , która identyfikuje typ tego pola.</span><span class="sxs-lookup"><span data-stu-id="ee6e2-110">A [COR_TYPEID](cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="ee6e2-111">Wartość wyliczenia CorElementType —, która wskazuje typ pola.</span><span class="sxs-lookup"><span data-stu-id="ee6e2-111">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee6e2-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee6e2-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee6e2-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ee6e2-113">Requirements</span></span>  
 <span data-ttu-id="ee6e2-114">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee6e2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee6e2-115">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee6e2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee6e2-116">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee6e2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee6e2-117">**.NET Framework wersje:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee6e2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee6e2-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee6e2-118">See also</span></span>

- [<span data-ttu-id="ee6e2-119">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="ee6e2-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="ee6e2-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="ee6e2-120">Debugging</span></span>](index.md)
