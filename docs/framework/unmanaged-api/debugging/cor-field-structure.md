---
title: "COR_FIELD — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_FIELD
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_FIELD
helpviewer_keywords: COR_FIELD structure [.NET Framework debugging]
ms.assetid: c0822423-a9df-4961-950d-50dcc152f863
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09a96a22a653688540bcc2ea3a03d86e242c10f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corfield-structure"></a><span data-ttu-id="56a05-102">COR_FIELD — Struktura</span><span class="sxs-lookup"><span data-stu-id="56a05-102">COR_FIELD Structure</span></span>
<span data-ttu-id="56a05-103">Zawiera informacje dotyczące pola w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="56a05-103">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56a05-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="56a05-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="56a05-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="56a05-105">Members</span></span>  
  
|<span data-ttu-id="56a05-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="56a05-106">Member</span></span>|<span data-ttu-id="56a05-107">Opis</span><span class="sxs-lookup"><span data-stu-id="56a05-107">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="56a05-108">`mdFieldDef` Token, który może służyć do pobrania informacji z pola.</span><span class="sxs-lookup"><span data-stu-id="56a05-108">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="56a05-109">Przesunięcie w bajtach, aby dane pola w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="56a05-109">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="56a05-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) wartość, która identyfikuje typu tego pola.</span><span class="sxs-lookup"><span data-stu-id="56a05-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="56a05-111">Wartość wyliczenia CorElementType, który wskazuje typ pola.</span><span class="sxs-lookup"><span data-stu-id="56a05-111">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56a05-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="56a05-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56a05-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="56a05-113">Requirements</span></span>  
 <span data-ttu-id="56a05-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56a05-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56a05-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56a05-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56a05-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56a05-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56a05-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56a05-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56a05-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56a05-118">See Also</span></span>  
 [<span data-ttu-id="56a05-119">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="56a05-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="56a05-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="56a05-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
