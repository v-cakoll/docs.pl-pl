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
ms.openlocfilehash: 9dc7093edaf12e801a1e1adc52b0be823ff92b91
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079919"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="883c7-102">CorDebugGuidToTypeMapping — Struktura</span><span class="sxs-lookup"><span data-stu-id="883c7-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="883c7-103">Mapy [!INCLUDE[wrt](../../../../includes/wrt-md.md)] identyfikator GUID służący do jego odpowiedniego obiektu ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="883c7-103">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="883c7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="883c7-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="883c7-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="883c7-105">Members</span></span>  
  
|<span data-ttu-id="883c7-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="883c7-106">Member</span></span>|<span data-ttu-id="883c7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="883c7-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="883c7-108">Identyfikator GUID buforowane [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typu.</span><span class="sxs-lookup"><span data-stu-id="883c7-108">The GUID of the cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`pType`|<span data-ttu-id="883c7-109">Wskaźnik do obiektu ICorDebugType, który zawiera informacje o typie pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="883c7-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="883c7-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="883c7-110">Requirements</span></span>  
 <span data-ttu-id="883c7-111">**Platformy:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span><span class="sxs-lookup"><span data-stu-id="883c7-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span></span>  
  
 <span data-ttu-id="883c7-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="883c7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="883c7-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="883c7-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="883c7-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="883c7-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="883c7-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="883c7-115">See also</span></span>

- [<span data-ttu-id="883c7-116">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="883c7-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="883c7-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="883c7-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
