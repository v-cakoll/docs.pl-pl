---
title: "COR_PRF_FUNCTION — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_FUNCTION
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_FUNCTION
helpviewer_keywords: COR_PRF_FUNCTION structure [.NET Framework profiling]
ms.assetid: 8bb5acf5-cf4b-4ccb-93f1-46db1f3f8bf3
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4b8ca316814b6f4df8792d068bea36d499b77374
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="corprffunction-structure"></a><span data-ttu-id="88d28-102">COR_PRF_FUNCTION — Struktura</span><span class="sxs-lookup"><span data-stu-id="88d28-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="88d28-103">Udostępnia reprezentację unikatowy funkcji przez połączenie jej z Identyfikatorem odpowiadającym jej wersji ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="88d28-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88d28-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="88d28-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="88d28-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="88d28-105">Members</span></span>  
  
|<span data-ttu-id="88d28-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="88d28-106">Member</span></span>|<span data-ttu-id="88d28-107">Opis</span><span class="sxs-lookup"><span data-stu-id="88d28-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="88d28-108">Identyfikator funkcji.</span><span class="sxs-lookup"><span data-stu-id="88d28-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="88d28-109">Identyfikator funkcji ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="88d28-109">The ID of the recompiled function.</span></span> <span data-ttu-id="88d28-110">Wartość 0 (zero) reprezentuje z oryginalną wersją funkcji.</span><span class="sxs-lookup"><span data-stu-id="88d28-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88d28-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88d28-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88d28-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="88d28-112">Requirements</span></span>  
 <span data-ttu-id="88d28-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88d28-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88d28-114">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="88d28-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="88d28-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88d28-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88d28-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88d28-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88d28-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="88d28-117">See Also</span></span>  
 [<span data-ttu-id="88d28-118">Struktury profilowania</span><span class="sxs-lookup"><span data-stu-id="88d28-118">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
