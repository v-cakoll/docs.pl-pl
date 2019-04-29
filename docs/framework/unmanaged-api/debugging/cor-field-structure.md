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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609493"
---
# <a name="corfield-structure"></a><span data-ttu-id="4700b-102">COR_FIELD — Struktura</span><span class="sxs-lookup"><span data-stu-id="4700b-102">COR_FIELD Structure</span></span>
<span data-ttu-id="4700b-103">Zawiera informacje dotyczące pól w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="4700b-103">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4700b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4700b-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="4700b-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4700b-105">Members</span></span>  
  
|<span data-ttu-id="4700b-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="4700b-106">Member</span></span>|<span data-ttu-id="4700b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4700b-107">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="4700b-108">`mdFieldDef` Token, którego można uzyskać informacji o polu.</span><span class="sxs-lookup"><span data-stu-id="4700b-108">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="4700b-109">Przesunięcie w bajtach, do pola danych w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="4700b-109">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="4700b-110">A [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) wartość, która identyfikuje typ tego pola.</span><span class="sxs-lookup"><span data-stu-id="4700b-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="4700b-111">Corelementtype — wartość wyliczenia, który wskazuje typ pola.</span><span class="sxs-lookup"><span data-stu-id="4700b-111">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4700b-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4700b-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4700b-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4700b-113">Requirements</span></span>  
 <span data-ttu-id="4700b-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4700b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4700b-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4700b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4700b-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4700b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4700b-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4700b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4700b-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4700b-118">See also</span></span>

- [<span data-ttu-id="4700b-119">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="4700b-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="4700b-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="4700b-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
