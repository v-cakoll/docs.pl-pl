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
ms.openlocfilehash: 691041632312bf8ac7c82a11724dcd725e14a420
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59231061"
---
# <a name="corfield-structure"></a><span data-ttu-id="e5f5e-102">COR_FIELD — Struktura</span><span class="sxs-lookup"><span data-stu-id="e5f5e-102">COR_FIELD Structure</span></span>
<span data-ttu-id="e5f5e-103">Zawiera informacje dotyczące pól w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="e5f5e-103">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5f5e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5f5e-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="e5f5e-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e5f5e-105">Members</span></span>  
  
|<span data-ttu-id="e5f5e-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e5f5e-106">Member</span></span>|<span data-ttu-id="e5f5e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e5f5e-107">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="e5f5e-108">`mdFieldDef` Token, którego można uzyskać informacji o polu.</span><span class="sxs-lookup"><span data-stu-id="e5f5e-108">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="e5f5e-109">Przesunięcie w bajtach, do pola danych w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="e5f5e-109">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="e5f5e-110">A [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) wartość, która identyfikuje typ tego pola.</span><span class="sxs-lookup"><span data-stu-id="e5f5e-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="e5f5e-111">Corelementtype — wartość wyliczenia, który wskazuje typ pola.</span><span class="sxs-lookup"><span data-stu-id="e5f5e-111">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5f5e-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5f5e-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5f5e-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5f5e-113">Requirements</span></span>  
 <span data-ttu-id="e5f5e-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5f5e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5f5e-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5f5e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5f5e-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5f5e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5f5e-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5f5e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5f5e-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5f5e-118">See also</span></span>

- [<span data-ttu-id="e5f5e-119">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="e5f5e-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="e5f5e-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="e5f5e-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
