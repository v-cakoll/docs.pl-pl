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
ms.openlocfilehash: c37f039d9636854c464e7981693c573bd60deab9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132345"
---
# <a name="cor_il_map-structure"></a><span data-ttu-id="8b0ae-102">COR_IL_MAP — Struktura</span><span class="sxs-lookup"><span data-stu-id="8b0ae-102">COR_IL_MAP Structure</span></span>
<span data-ttu-id="8b0ae-103">Określa zmiany w względnym przesunięciu funkcji.</span><span class="sxs-lookup"><span data-stu-id="8b0ae-103">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b0ae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b0ae-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="8b0ae-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8b0ae-105">Members</span></span>  
  
|<span data-ttu-id="8b0ae-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="8b0ae-106">Member</span></span>|<span data-ttu-id="8b0ae-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8b0ae-107">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="8b0ae-108">Poprzednie przesunięcie języka pośredniego firmy Microsoft (MSIL) względem początku funkcji.</span><span class="sxs-lookup"><span data-stu-id="8b0ae-108">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="8b0ae-109">Nowe przesunięcie MSIL względem początku funkcji.</span><span class="sxs-lookup"><span data-stu-id="8b0ae-109">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="8b0ae-110">`true`, jeśli mapowanie jest znane z dokładnością; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="8b0ae-110">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b0ae-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b0ae-111">Remarks</span></span>  
 <span data-ttu-id="8b0ae-112">Format mapy jest następujący: debuger przyjmie, że `oldOffset` odnosi się do przesunięcia MSIL w oryginalnym, niezmodyfikowanym kodzie MSIL.</span><span class="sxs-lookup"><span data-stu-id="8b0ae-112">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="8b0ae-113">`newOffset` parametr odnosi się do odpowiedniego przesunięcia MSIL w nowym, Instrumentacji kodu.</span><span class="sxs-lookup"><span data-stu-id="8b0ae-113">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="8b0ae-114">Aby wykonać prawidłowe działanie, należy spełnić następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="8b0ae-114">For stepping to work properly, the following requirements should be met:</span></span>  
  
- <span data-ttu-id="8b0ae-115">Mapa powinna być posortowana w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="8b0ae-115">The map should be sorted in ascending order.</span></span>  
  
- <span data-ttu-id="8b0ae-116">Nie należy zmienić kolejności kodu MSIL z instrumentacją.</span><span class="sxs-lookup"><span data-stu-id="8b0ae-116">Instrumented MSIL code should not be reordered.</span></span>  
  
- <span data-ttu-id="8b0ae-117">Nie należy usuwać oryginalnego kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="8b0ae-117">Original MSIL code should not be removed.</span></span>  
  
- <span data-ttu-id="8b0ae-118">Mapa powinna zawierać wpisy umożliwiające zamapowanie wszystkich punktów sekwencji z pliku bazy danych programu (PDB).</span><span class="sxs-lookup"><span data-stu-id="8b0ae-118">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="8b0ae-119">Mapa nie wykonuje interpolacji brakujących wpisów.</span><span class="sxs-lookup"><span data-stu-id="8b0ae-119">The map does not interpolate missing entries.</span></span> <span data-ttu-id="8b0ae-120">Poniższy przykład pokazuje mapę i jej wyniki.</span><span class="sxs-lookup"><span data-stu-id="8b0ae-120">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="8b0ae-121">Zmapować</span><span class="sxs-lookup"><span data-stu-id="8b0ae-121">Map:</span></span>  
  
- <span data-ttu-id="8b0ae-122">0 Stare przesunięcie, 0 nowe przesunięcie</span><span class="sxs-lookup"><span data-stu-id="8b0ae-122">0 old offset, 0 new offset</span></span>  
  
- <span data-ttu-id="8b0ae-123">5 starych przesunięcia, 10 nowego przesunięcia</span><span class="sxs-lookup"><span data-stu-id="8b0ae-123">5 old offset, 10 new offset</span></span>  
  
- <span data-ttu-id="8b0ae-124">9 Stare przesunięcie, 20 nowego przesunięcia</span><span class="sxs-lookup"><span data-stu-id="8b0ae-124">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="8b0ae-125">Uzyskane</span><span class="sxs-lookup"><span data-stu-id="8b0ae-125">Results:</span></span>  
  
- <span data-ttu-id="8b0ae-126">Stare przesunięcie 0, 1, 2, 3 lub 4 zostanie zmapowane na nowe przesunięcie o wartości 0.</span><span class="sxs-lookup"><span data-stu-id="8b0ae-126">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
- <span data-ttu-id="8b0ae-127">Stare przesunięcie o wartości 5, 6, 7 lub 8 zostanie zmapowane na nowe przesunięcie 10.</span><span class="sxs-lookup"><span data-stu-id="8b0ae-127">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
- <span data-ttu-id="8b0ae-128">Stare przesunięcie w wysokości 9 lub wyższej zostanie zmapowane do nowego przesunięcia 20.</span><span class="sxs-lookup"><span data-stu-id="8b0ae-128">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
- <span data-ttu-id="8b0ae-129">Nowe przesunięcie 0, 1, 2, 3, 4, 5, 6, 7, 8 lub 9 zostanie zmapowane do starego przesunięcia 0.</span><span class="sxs-lookup"><span data-stu-id="8b0ae-129">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
- <span data-ttu-id="8b0ae-130">Nowe przesunięcie 10, 11, 12, 13, 14, 15, 16, 17, 18 lub 19 zostanie zmapowane do starego przesunięcia 5.</span><span class="sxs-lookup"><span data-stu-id="8b0ae-130">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
- <span data-ttu-id="8b0ae-131">Nowe przesunięcie o wartości 20 lub wyższej zostanie zmapowane do starego przesunięcia 9.</span><span class="sxs-lookup"><span data-stu-id="8b0ae-131">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b0ae-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b0ae-132">Requirements</span></span>  
 <span data-ttu-id="8b0ae-133">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b0ae-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b0ae-134">**Nagłówek:** CorDebug. idl, CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="8b0ae-134">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="8b0ae-135">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8b0ae-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b0ae-136">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b0ae-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b0ae-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b0ae-137">See also</span></span>

- [<span data-ttu-id="8b0ae-138">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="8b0ae-138">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="8b0ae-139">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="8b0ae-139">Debugging</span></span>](index.md)
