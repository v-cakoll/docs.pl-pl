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
ms.openlocfilehash: 74f515626f5001cbea1a25e8268338c588524bde
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740535"
---
# <a name="corilmap-structure"></a><span data-ttu-id="3be73-102">COR_IL_MAP — Struktura</span><span class="sxs-lookup"><span data-stu-id="3be73-102">COR_IL_MAP Structure</span></span>
<span data-ttu-id="3be73-103">Określa przesunięcie względne funkcji zmiany.</span><span class="sxs-lookup"><span data-stu-id="3be73-103">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3be73-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3be73-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="3be73-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3be73-105">Members</span></span>  
  
|<span data-ttu-id="3be73-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="3be73-106">Member</span></span>|<span data-ttu-id="3be73-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3be73-107">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="3be73-108">Stary języka Microsoft intermediate language (MSIL) przesunięcie względem początku funkcji.</span><span class="sxs-lookup"><span data-stu-id="3be73-108">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="3be73-109">Nowe MSIL przesunięcie względem początku funkcji.</span><span class="sxs-lookup"><span data-stu-id="3be73-109">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="3be73-110">`true` Jeśli wiadomo, że mapowanie jest dokładne; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="3be73-110">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3be73-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3be73-111">Remarks</span></span>  
 <span data-ttu-id="3be73-112">Format mapy jest w następujący sposób: Debuger będzie przyjęto założenie, że `oldOffset` odwołuje się do przesunięcia MSIL w kodzie MSIL oryginalne, niezmodyfikowanego.</span><span class="sxs-lookup"><span data-stu-id="3be73-112">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="3be73-113">`newOffset` Parametr odnosi się do odpowiedniego przesunięcia MSIL kodem nowe, instrumentowaną.</span><span class="sxs-lookup"><span data-stu-id="3be73-113">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="3be73-114">Przechodzenie krok po kroku, aby zapewnić prawidłowe działanie, aby uzyskać być spełnione następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="3be73-114">For stepping to work properly, the following requirements should be met:</span></span>  
  
- <span data-ttu-id="3be73-115">Mapa powinny być sortowane w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="3be73-115">The map should be sorted in ascending order.</span></span>  
  
- <span data-ttu-id="3be73-116">Instrumentowane kod MSIL nie wymagają zmiany kolejności.</span><span class="sxs-lookup"><span data-stu-id="3be73-116">Instrumented MSIL code should not be reordered.</span></span>  
  
- <span data-ttu-id="3be73-117">Oryginalny kod MSIL nie powinny być usuwane.</span><span class="sxs-lookup"><span data-stu-id="3be73-117">Original MSIL code should not be removed.</span></span>  
  
- <span data-ttu-id="3be73-118">Mapa powinny zawierać wpisy, aby zamapować wszystkie punkty sekwencji z plik bazy danych (PDB) programu.</span><span class="sxs-lookup"><span data-stu-id="3be73-118">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="3be73-119">Mapa nie interpolacji Brak wpisów.</span><span class="sxs-lookup"><span data-stu-id="3be73-119">The map does not interpolate missing entries.</span></span> <span data-ttu-id="3be73-120">Poniższy przykład pokazuje, mapy i jego wyniki.</span><span class="sxs-lookup"><span data-stu-id="3be73-120">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="3be73-121">Mapy:</span><span class="sxs-lookup"><span data-stu-id="3be73-121">Map:</span></span>  
  
- <span data-ttu-id="3be73-122">Przesunięcie stare 0, 0 nowe przesunięcie</span><span class="sxs-lookup"><span data-stu-id="3be73-122">0 old offset, 0 new offset</span></span>  
  
- <span data-ttu-id="3be73-123">Przesunięcie stare 5, 10 nowych przesunięcie</span><span class="sxs-lookup"><span data-stu-id="3be73-123">5 old offset, 10 new offset</span></span>  
  
- <span data-ttu-id="3be73-124">Przesunięcie stare 9, 20 nowych przesunięcie</span><span class="sxs-lookup"><span data-stu-id="3be73-124">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="3be73-125">Liczba wyników:</span><span class="sxs-lookup"><span data-stu-id="3be73-125">Results:</span></span>  
  
- <span data-ttu-id="3be73-126">Stary przesunięcia 0, 1, 2, 3 lub 4 zostanie zamapowane do nowego przesunięcia 0.</span><span class="sxs-lookup"><span data-stu-id="3be73-126">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
- <span data-ttu-id="3be73-127">Przesunięcie stare 5, 6, 7 lub 8 zostaną odwzorowane na nowe przesunięcie 10.</span><span class="sxs-lookup"><span data-stu-id="3be73-127">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
- <span data-ttu-id="3be73-128">Stary przesunięcie 9 lub nowszą zostaną odwzorowane na nowe przesunięcie 20.</span><span class="sxs-lookup"><span data-stu-id="3be73-128">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
- <span data-ttu-id="3be73-129">Nowe przesunięcie 0, 1, 2, 3, 4, 5, 6, 7, 8 lub 9 zostaną zmapowane do starego przesunięciu 0.</span><span class="sxs-lookup"><span data-stu-id="3be73-129">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
- <span data-ttu-id="3be73-130">Nowe przesunięcie 10, 11, 12, 13, 14, 15, 16, 17, 18 lub 19 zostanie zamapowane do starego przesunięcia 5.</span><span class="sxs-lookup"><span data-stu-id="3be73-130">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
- <span data-ttu-id="3be73-131">Nowe przesunięcie 20 lub nowszej zostanie zamapowane do starego przesunięcia 9.</span><span class="sxs-lookup"><span data-stu-id="3be73-131">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3be73-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3be73-132">Requirements</span></span>  
 <span data-ttu-id="3be73-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3be73-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3be73-134">**Nagłówek:** CorDebug.idl, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="3be73-134">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="3be73-135">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3be73-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3be73-136">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3be73-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3be73-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3be73-137">See also</span></span>

- [<span data-ttu-id="3be73-138">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="3be73-138">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="3be73-139">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="3be73-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
