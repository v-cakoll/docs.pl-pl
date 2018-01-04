---
title: "COR_IL_MAP — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_IL_MAP
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_IL_MAP
helpviewer_keywords: COR_IL_MAP structure [.NET Framework debugging]
ms.assetid: 534ebc17-963d-4b26-8375-8cd940281db3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e2772833d75ced2209896ca37cf6cf37fb965f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corilmap-structure"></a><span data-ttu-id="22be7-102">COR_IL_MAP — Struktura</span><span class="sxs-lookup"><span data-stu-id="22be7-102">COR_IL_MAP Structure</span></span>
<span data-ttu-id="22be7-103">Określa przesunięcie względną funkcji zmiany.</span><span class="sxs-lookup"><span data-stu-id="22be7-103">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22be7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="22be7-104">Syntax</span></span>  
  
```  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="22be7-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="22be7-105">Members</span></span>  
  
|<span data-ttu-id="22be7-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="22be7-106">Member</span></span>|<span data-ttu-id="22be7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="22be7-107">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="22be7-108">Stary Microsoft język pośredni (MSIL) przesuwane względem początku funkcji.</span><span class="sxs-lookup"><span data-stu-id="22be7-108">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="22be7-109">Nowe MSIL przesunięcie względem początku funkcji.</span><span class="sxs-lookup"><span data-stu-id="22be7-109">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="22be7-110">`true`Jeśli mapowanie jest znany jako dokładne; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="22be7-110">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22be7-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="22be7-111">Remarks</span></span>  
 <span data-ttu-id="22be7-112">Format mapy jest następujący: debuger zakłada, że `oldOffset` odwołuje się do MSIL przesunięcie w oryginalnym niezmodyfikowanego kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="22be7-112">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="22be7-113">`newOffset` Parametr odwołuje się do odpowiedniego przesunięcie MSIL kodem nowy, instrumentacją.</span><span class="sxs-lookup"><span data-stu-id="22be7-113">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="22be7-114">Dla wykonywanie krok po kroku, aby działała poprawnie, powinny być spełnione następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="22be7-114">For stepping to work properly, the following requirements should be met:</span></span>  
  
-   <span data-ttu-id="22be7-115">Mapy mają być sortowane w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="22be7-115">The map should be sorted in ascending order.</span></span>  
  
-   <span data-ttu-id="22be7-116">Nie wymagają zmiany kolejności instrumentowanych kod MSIL.</span><span class="sxs-lookup"><span data-stu-id="22be7-116">Instrumented MSIL code should not be reordered.</span></span>  
  
-   <span data-ttu-id="22be7-117">Oryginalny kod MSIL nie powinien zostać usunięty.</span><span class="sxs-lookup"><span data-stu-id="22be7-117">Original MSIL code should not be removed.</span></span>  
  
-   <span data-ttu-id="22be7-118">Mapy powinny zawierać wpisy do wszystkich punktów sekwencji z programu (PDB) pliku mapowania.</span><span class="sxs-lookup"><span data-stu-id="22be7-118">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="22be7-119">Mapa nie interpolować Brak wpisów.</span><span class="sxs-lookup"><span data-stu-id="22be7-119">The map does not interpolate missing entries.</span></span> <span data-ttu-id="22be7-120">W poniższym przykładzie przedstawiono mapy, a jego wyniki.</span><span class="sxs-lookup"><span data-stu-id="22be7-120">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="22be7-121">Mapa:</span><span class="sxs-lookup"><span data-stu-id="22be7-121">Map:</span></span>  
  
-   <span data-ttu-id="22be7-122">Przesunięcie starego 0, 0 przesunięcie nowy</span><span class="sxs-lookup"><span data-stu-id="22be7-122">0 old offset, 0 new offset</span></span>  
  
-   <span data-ttu-id="22be7-123">Przesunięcie starego 5, 10 nowych przesunięcie</span><span class="sxs-lookup"><span data-stu-id="22be7-123">5 old offset, 10 new offset</span></span>  
  
-   <span data-ttu-id="22be7-124">Przesunięcie starego 9, 20 przesunięcie nowy</span><span class="sxs-lookup"><span data-stu-id="22be7-124">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="22be7-125">Wyniki:</span><span class="sxs-lookup"><span data-stu-id="22be7-125">Results:</span></span>  
  
-   <span data-ttu-id="22be7-126">Stary przesunięciem równym 0, 1, 2, 3 lub 4 zostaną zmapowane do nowego przesunięciem równym 0.</span><span class="sxs-lookup"><span data-stu-id="22be7-126">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
-   <span data-ttu-id="22be7-127">Stary przesunięcie 5, 6, 7 lub 8 zostaną zmapowane do nowego przesunięcie 10.</span><span class="sxs-lookup"><span data-stu-id="22be7-127">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
-   <span data-ttu-id="22be7-128">Przesunięcie starego 9 lub nowszą zostaną zmapowane do nowego przesunięcie 20.</span><span class="sxs-lookup"><span data-stu-id="22be7-128">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
-   <span data-ttu-id="22be7-129">Nowe przesunięcie 0, 1, 2, 3, 4, 5, 6, 7, 8 lub 9 zostaną zmapowane do starego przesunięciu 0.</span><span class="sxs-lookup"><span data-stu-id="22be7-129">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
-   <span data-ttu-id="22be7-130">Nowe przesunięcie 10, 11, 12, 13, 14, 15, 16, 17, 18 lub 19 zostaną zmapowane do starego przesunięcie 5.</span><span class="sxs-lookup"><span data-stu-id="22be7-130">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
-   <span data-ttu-id="22be7-131">Nowe przesunięcie 20 lub wyższe zostaną zmapowane do starego przesunięcie 9.</span><span class="sxs-lookup"><span data-stu-id="22be7-131">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22be7-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="22be7-132">Requirements</span></span>  
 <span data-ttu-id="22be7-133">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22be7-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22be7-134">**Nagłówek:** CorDebug.idl, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="22be7-134">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="22be7-135">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22be7-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22be7-136">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22be7-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22be7-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22be7-137">See Also</span></span>  
 [<span data-ttu-id="22be7-138">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="22be7-138">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="22be7-139">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="22be7-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
