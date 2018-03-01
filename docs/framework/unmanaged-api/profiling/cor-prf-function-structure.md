---
title: "COR_PRF_FUNCTION — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- COR_PRF_FUNCTION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION
helpviewer_keywords:
- COR_PRF_FUNCTION structure [.NET Framework profiling]
ms.assetid: 8bb5acf5-cf4b-4ccb-93f1-46db1f3f8bf3
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 15ef81f07438a7cc18f7a131ee8cf9c50c47eb6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corprffunction-structure"></a><span data-ttu-id="5cca8-102">COR_PRF_FUNCTION — Struktura</span><span class="sxs-lookup"><span data-stu-id="5cca8-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="5cca8-103">Udostępnia reprezentację unikatowy funkcji przez połączenie jej z Identyfikatorem odpowiadającym jej wersji ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5cca8-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cca8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5cca8-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="5cca8-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5cca8-105">Members</span></span>  
  
|<span data-ttu-id="5cca8-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="5cca8-106">Member</span></span>|<span data-ttu-id="5cca8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5cca8-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="5cca8-108">Identyfikator funkcji.</span><span class="sxs-lookup"><span data-stu-id="5cca8-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="5cca8-109">Identyfikator funkcji ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5cca8-109">The ID of the recompiled function.</span></span> <span data-ttu-id="5cca8-110">Wartość 0 (zero) reprezentuje z oryginalną wersją funkcji.</span><span class="sxs-lookup"><span data-stu-id="5cca8-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5cca8-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5cca8-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cca8-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5cca8-112">Requirements</span></span>  
 <span data-ttu-id="5cca8-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cca8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cca8-114">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="5cca8-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="5cca8-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5cca8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5cca8-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cca8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cca8-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5cca8-117">See Also</span></span>  
 [<span data-ttu-id="5cca8-118">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="5cca8-118">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
