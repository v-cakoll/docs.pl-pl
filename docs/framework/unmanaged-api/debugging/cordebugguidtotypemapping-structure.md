---
title: CorDebugGuidToTypeMapping — Struktura
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugGuidToTypeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGuidToTypeMapping
helpviewer_keywords:
- CorDebugGuidToTypeMapping structure [.NET Framework debugging]
ms.assetid: 57dbccd9-b16d-4da3-ae25-7a2cf9adf679
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c803a805da605bd52fd50eb1e292c0e277143d7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="91f24-102">CorDebugGuidToTypeMapping — Struktura</span><span class="sxs-lookup"><span data-stu-id="91f24-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="91f24-103">Mapy [!INCLUDE[wrt](../../../../includes/wrt-md.md)] identyfikator GUID na jego odpowiedni obiekt ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="91f24-103">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91f24-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="91f24-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="91f24-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="91f24-105">Members</span></span>  
  
|<span data-ttu-id="91f24-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="91f24-106">Member</span></span>|<span data-ttu-id="91f24-107">Opis</span><span class="sxs-lookup"><span data-stu-id="91f24-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="91f24-108">Identyfikator GUID zapisane w pamięci podręcznej [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typu.</span><span class="sxs-lookup"><span data-stu-id="91f24-108">The GUID of the cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`pType`|<span data-ttu-id="91f24-109">Wskaźnik do obiektu ICorDebugType, który zawiera informacje o pamięci podręcznej typu.</span><span class="sxs-lookup"><span data-stu-id="91f24-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="91f24-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="91f24-110">Requirements</span></span>  
 <span data-ttu-id="91f24-111">**Platformy:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span><span class="sxs-lookup"><span data-stu-id="91f24-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span></span>  
  
 <span data-ttu-id="91f24-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91f24-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91f24-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91f24-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91f24-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91f24-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91f24-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="91f24-115">See Also</span></span>  
 [<span data-ttu-id="91f24-116">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="91f24-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="91f24-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="91f24-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
