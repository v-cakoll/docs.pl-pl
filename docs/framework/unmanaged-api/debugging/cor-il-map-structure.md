---
title: COR_IL_MAP — Struktura
ms.date: 03/30/2017
api_name:
- COR_IL_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_IL_MAP
helpviewer_keywords:
- COR_IL_MAP structure [.NET Framework debugging]
ms.assetid: 534ebc17-963d-4b26-8375-8cd940281db3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e6d8023c7ac6d917c9df40fb18316ddc12df5ec1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190434"
---
# <a name="corilmap-structure"></a><span data-ttu-id="5866f-102">COR_IL_MAP — Struktura</span><span class="sxs-lookup"><span data-stu-id="5866f-102">COR_IL_MAP Structure</span></span>
<span data-ttu-id="5866f-103">Określa przesunięcie względne funkcji zmiany.</span><span class="sxs-lookup"><span data-stu-id="5866f-103">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5866f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5866f-104">Syntax</span></span>  
  
```  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="5866f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5866f-105">Members</span></span>  
  
|<span data-ttu-id="5866f-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="5866f-106">Member</span></span>|<span data-ttu-id="5866f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5866f-107">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="5866f-108">Stary języka Microsoft intermediate language (MSIL) przesunięcie względem początku funkcji.</span><span class="sxs-lookup"><span data-stu-id="5866f-108">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="5866f-109">Nowe MSIL przesunięcie względem początku funkcji.</span><span class="sxs-lookup"><span data-stu-id="5866f-109">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|`true` <span data-ttu-id="5866f-110">Jeśli wiadomo, że mapowanie jest dokładne; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="5866f-110">if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5866f-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5866f-111">Remarks</span></span>  
 <span data-ttu-id="5866f-112">Format mapy jest w następujący sposób: Debuger będzie przyjęto założenie, że `oldOffset` odwołuje się do przesunięcia MSIL w kodzie MSIL oryginalne, niezmodyfikowanego.</span><span class="sxs-lookup"><span data-stu-id="5866f-112">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="5866f-113">`newOffset` Parametr odnosi się do odpowiedniego przesunięcia MSIL kodem nowe, instrumentowaną.</span><span class="sxs-lookup"><span data-stu-id="5866f-113">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="5866f-114">Przechodzenie krok po kroku, aby zapewnić prawidłowe działanie, aby uzyskać być spełnione następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="5866f-114">For stepping to work properly, the following requirements should be met:</span></span>  
  
-   <span data-ttu-id="5866f-115">Mapa powinny być sortowane w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="5866f-115">The map should be sorted in ascending order.</span></span>  
  
-   <span data-ttu-id="5866f-116">Instrumentowane kod MSIL nie wymagają zmiany kolejności.</span><span class="sxs-lookup"><span data-stu-id="5866f-116">Instrumented MSIL code should not be reordered.</span></span>  
  
-   <span data-ttu-id="5866f-117">Oryginalny kod MSIL nie powinny być usuwane.</span><span class="sxs-lookup"><span data-stu-id="5866f-117">Original MSIL code should not be removed.</span></span>  
  
-   <span data-ttu-id="5866f-118">Mapa powinny zawierać wpisy, aby zamapować wszystkie punkty sekwencji z plik bazy danych (PDB) programu.</span><span class="sxs-lookup"><span data-stu-id="5866f-118">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="5866f-119">Mapa nie interpolacji Brak wpisów.</span><span class="sxs-lookup"><span data-stu-id="5866f-119">The map does not interpolate missing entries.</span></span> <span data-ttu-id="5866f-120">Poniższy przykład pokazuje, mapy i jego wyniki.</span><span class="sxs-lookup"><span data-stu-id="5866f-120">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="5866f-121">Mapy:</span><span class="sxs-lookup"><span data-stu-id="5866f-121">Map:</span></span>  
  
-   <span data-ttu-id="5866f-122">Przesunięcie stare 0, 0 nowe przesunięcie</span><span class="sxs-lookup"><span data-stu-id="5866f-122">0 old offset, 0 new offset</span></span>  
  
-   <span data-ttu-id="5866f-123">Przesunięcie stare 5, 10 nowych przesunięcie</span><span class="sxs-lookup"><span data-stu-id="5866f-123">5 old offset, 10 new offset</span></span>  
  
-   <span data-ttu-id="5866f-124">Przesunięcie stare 9, 20 nowych przesunięcie</span><span class="sxs-lookup"><span data-stu-id="5866f-124">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="5866f-125">Liczba wyników:</span><span class="sxs-lookup"><span data-stu-id="5866f-125">Results:</span></span>  
  
-   <span data-ttu-id="5866f-126">Stary przesunięcia 0, 1, 2, 3 lub 4 zostanie zamapowane do nowego przesunięcia 0.</span><span class="sxs-lookup"><span data-stu-id="5866f-126">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
-   <span data-ttu-id="5866f-127">Przesunięcie stare 5, 6, 7 lub 8 zostaną odwzorowane na nowe przesunięcie 10.</span><span class="sxs-lookup"><span data-stu-id="5866f-127">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
-   <span data-ttu-id="5866f-128">Stary przesunięcie 9 lub nowszą zostaną odwzorowane na nowe przesunięcie 20.</span><span class="sxs-lookup"><span data-stu-id="5866f-128">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
-   <span data-ttu-id="5866f-129">Nowe przesunięcie 0, 1, 2, 3, 4, 5, 6, 7, 8 lub 9 zostaną zmapowane do starego przesunięciu 0.</span><span class="sxs-lookup"><span data-stu-id="5866f-129">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
-   <span data-ttu-id="5866f-130">Nowe przesunięcie 10, 11, 12, 13, 14, 15, 16, 17, 18 lub 19 zostanie zamapowane do starego przesunięcia 5.</span><span class="sxs-lookup"><span data-stu-id="5866f-130">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
-   <span data-ttu-id="5866f-131">Nowe przesunięcie 20 lub nowszej zostanie zamapowane do starego przesunięcia 9.</span><span class="sxs-lookup"><span data-stu-id="5866f-131">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5866f-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5866f-132">Requirements</span></span>  
 <span data-ttu-id="5866f-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5866f-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5866f-134">**Nagłówek:** CorDebug.idl, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="5866f-134">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="5866f-135">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5866f-135">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5866f-136">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5866f-136">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5866f-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5866f-137">See also</span></span>

- [<span data-ttu-id="5866f-138">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="5866f-138">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="5866f-139">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="5866f-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
