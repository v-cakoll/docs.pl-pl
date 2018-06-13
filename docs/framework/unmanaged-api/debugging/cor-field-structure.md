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
ms.openlocfilehash: 0898936665b3b337f2fd4e4d53bcc9f6071469b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405362"
---
# <a name="corfield-structure"></a><span data-ttu-id="31630-102">COR_FIELD — Struktura</span><span class="sxs-lookup"><span data-stu-id="31630-102">COR_FIELD Structure</span></span>
<span data-ttu-id="31630-103">Zawiera informacje dotyczące pola w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="31630-103">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31630-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="31630-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="31630-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="31630-105">Members</span></span>  
  
|<span data-ttu-id="31630-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="31630-106">Member</span></span>|<span data-ttu-id="31630-107">Opis</span><span class="sxs-lookup"><span data-stu-id="31630-107">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="31630-108">`mdFieldDef` Token, który może służyć do pobrania informacji z pola.</span><span class="sxs-lookup"><span data-stu-id="31630-108">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="31630-109">Przesunięcie w bajtach, aby dane pola w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="31630-109">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="31630-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) wartość, która identyfikuje typu tego pola.</span><span class="sxs-lookup"><span data-stu-id="31630-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="31630-111">Wartość wyliczenia CorElementType, który wskazuje typ pola.</span><span class="sxs-lookup"><span data-stu-id="31630-111">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31630-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="31630-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31630-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="31630-113">Requirements</span></span>  
 <span data-ttu-id="31630-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31630-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31630-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="31630-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31630-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31630-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31630-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31630-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31630-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="31630-118">See Also</span></span>  
 [<span data-ttu-id="31630-119">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="31630-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="31630-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="31630-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
