---
title: "CorDebugGuidToTypeMapping — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: CorDebugGuidToTypeMapping
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugGuidToTypeMapping
helpviewer_keywords: CorDebugGuidToTypeMapping structure [.NET Framework debugging]
ms.assetid: 57dbccd9-b16d-4da3-ae25-7a2cf9adf679
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e4c829f4a74c3d2e84a070dfbe5d35d89b1b7ae6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="6088e-102">CorDebugGuidToTypeMapping — Struktura</span><span class="sxs-lookup"><span data-stu-id="6088e-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="6088e-103">Mapy [!INCLUDE[wrt](../../../../includes/wrt-md.md)] identyfikator GUID na jego odpowiedni obiekt ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="6088e-103">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6088e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6088e-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="6088e-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="6088e-105">Members</span></span>  
  
|<span data-ttu-id="6088e-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="6088e-106">Member</span></span>|<span data-ttu-id="6088e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6088e-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="6088e-108">Identyfikator GUID zapisane w pamięci podręcznej [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typu.</span><span class="sxs-lookup"><span data-stu-id="6088e-108">The GUID of the cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`pType`|<span data-ttu-id="6088e-109">Wskaźnik do obiektu ICorDebugType, który zawiera informacje o pamięci podręcznej typu.</span><span class="sxs-lookup"><span data-stu-id="6088e-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6088e-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6088e-110">Requirements</span></span>  
 <span data-ttu-id="6088e-111">**Platformy:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6088e-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span></span>  
  
 <span data-ttu-id="6088e-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6088e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6088e-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6088e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6088e-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6088e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6088e-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6088e-115">See Also</span></span>  
 [<span data-ttu-id="6088e-116">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="6088e-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="6088e-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="6088e-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
