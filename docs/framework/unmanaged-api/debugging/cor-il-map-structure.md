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
ms.openlocfilehash: 5ae4c5743b01c4a9087323678d315473631cb32f
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274050"
---
# <a name="cor_il_map-structure"></a><span data-ttu-id="1b4a4-102">COR_IL_MAP — Struktura</span><span class="sxs-lookup"><span data-stu-id="1b4a4-102">COR_IL_MAP Structure</span></span>
<span data-ttu-id="1b4a4-103">Określa zmiany w względnym przesunięciu funkcji.</span><span class="sxs-lookup"><span data-stu-id="1b4a4-103">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b4a4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b4a4-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="1b4a4-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="1b4a4-105">Members</span></span>  
  
|<span data-ttu-id="1b4a4-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="1b4a4-106">Member</span></span>|<span data-ttu-id="1b4a4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1b4a4-107">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="1b4a4-108">Poprzednie przesunięcie języka pośredniego firmy Microsoft (MSIL) względem początku funkcji.</span><span class="sxs-lookup"><span data-stu-id="1b4a4-108">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="1b4a4-109">Nowe przesunięcie MSIL względem początku funkcji.</span><span class="sxs-lookup"><span data-stu-id="1b4a4-109">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="1b4a4-110">`true`Jeśli mapowanie jest znane, aby było dokładne; w przeciwnym razie. `false`</span><span class="sxs-lookup"><span data-stu-id="1b4a4-110">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b4a4-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1b4a4-111">Remarks</span></span>  
 <span data-ttu-id="1b4a4-112">Format mapy jest następujący: Zostanie przyjęty debuger, `oldOffset` który odwołuje się do przesunięcia MSIL w oryginalnym, niezmodyfikowanym kodzie MSIL.</span><span class="sxs-lookup"><span data-stu-id="1b4a4-112">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="1b4a4-113">`newOffset` Parametr odnosi się do odpowiedniego przesunięcia MSIL w nowym, Instrumentacji kodu.</span><span class="sxs-lookup"><span data-stu-id="1b4a4-113">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="1b4a4-114">Aby wykonać prawidłowe działanie, należy spełnić następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="1b4a4-114">For stepping to work properly, the following requirements should be met:</span></span>  
  
- <span data-ttu-id="1b4a4-115">Mapa powinna być posortowana w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="1b4a4-115">The map should be sorted in ascending order.</span></span>  
  
- <span data-ttu-id="1b4a4-116">Nie należy zmienić kolejności kodu MSIL z instrumentacją.</span><span class="sxs-lookup"><span data-stu-id="1b4a4-116">Instrumented MSIL code should not be reordered.</span></span>  
  
- <span data-ttu-id="1b4a4-117">Nie należy usuwać oryginalnego kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="1b4a4-117">Original MSIL code should not be removed.</span></span>  
  
- <span data-ttu-id="1b4a4-118">Mapa powinna zawierać wpisy umożliwiające zamapowanie wszystkich punktów sekwencji z pliku bazy danych programu (PDB).</span><span class="sxs-lookup"><span data-stu-id="1b4a4-118">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="1b4a4-119">Mapa nie wykonuje interpolacji brakujących wpisów.</span><span class="sxs-lookup"><span data-stu-id="1b4a4-119">The map does not interpolate missing entries.</span></span> <span data-ttu-id="1b4a4-120">Poniższy przykład pokazuje mapę i jej wyniki.</span><span class="sxs-lookup"><span data-stu-id="1b4a4-120">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="1b4a4-121">Zmapować</span><span class="sxs-lookup"><span data-stu-id="1b4a4-121">Map:</span></span>  
  
- <span data-ttu-id="1b4a4-122">0 Stare przesunięcie, 0 nowe przesunięcie</span><span class="sxs-lookup"><span data-stu-id="1b4a4-122">0 old offset, 0 new offset</span></span>  
  
- <span data-ttu-id="1b4a4-123">5 starych przesunięcia, 10 nowego przesunięcia</span><span class="sxs-lookup"><span data-stu-id="1b4a4-123">5 old offset, 10 new offset</span></span>  
  
- <span data-ttu-id="1b4a4-124">9 Stare przesunięcie, 20 nowego przesunięcia</span><span class="sxs-lookup"><span data-stu-id="1b4a4-124">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="1b4a4-125">Uzyskane</span><span class="sxs-lookup"><span data-stu-id="1b4a4-125">Results:</span></span>  
  
- <span data-ttu-id="1b4a4-126">Stare przesunięcie 0, 1, 2, 3 lub 4 zostanie zmapowane na nowe przesunięcie o wartości 0.</span><span class="sxs-lookup"><span data-stu-id="1b4a4-126">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
- <span data-ttu-id="1b4a4-127">Stare przesunięcie o wartości 5, 6, 7 lub 8 zostanie zmapowane na nowe przesunięcie 10.</span><span class="sxs-lookup"><span data-stu-id="1b4a4-127">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
- <span data-ttu-id="1b4a4-128">Stare przesunięcie w wysokości 9 lub wyższej zostanie zmapowane do nowego przesunięcia 20.</span><span class="sxs-lookup"><span data-stu-id="1b4a4-128">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
- <span data-ttu-id="1b4a4-129">Nowe przesunięcie 0, 1, 2, 3, 4, 5, 6, 7, 8 lub 9 zostanie zmapowane do starego przesunięcia 0.</span><span class="sxs-lookup"><span data-stu-id="1b4a4-129">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
- <span data-ttu-id="1b4a4-130">Nowe przesunięcie 10, 11, 12, 13, 14, 15, 16, 17, 18 lub 19 zostanie zmapowane do starego przesunięcia 5.</span><span class="sxs-lookup"><span data-stu-id="1b4a4-130">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
- <span data-ttu-id="1b4a4-131">Nowe przesunięcie o wartości 20 lub wyższej zostanie zmapowane do starego przesunięcia 9.</span><span class="sxs-lookup"><span data-stu-id="1b4a4-131">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b4a4-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1b4a4-132">Requirements</span></span>  
 <span data-ttu-id="1b4a4-133">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b4a4-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b4a4-134">**Nagłówki** CorDebug.idl, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="1b4a4-134">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="1b4a4-135">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b4a4-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b4a4-136">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b4a4-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b4a4-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b4a4-137">See also</span></span>

- [<span data-ttu-id="1b4a4-138">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="1b4a4-138">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="1b4a4-139">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="1b4a4-139">Debugging</span></span>](index.md)
