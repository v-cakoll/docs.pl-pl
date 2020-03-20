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
ms.openlocfilehash: 4c79d0e4e37f3f884651e49c8fff6db72fac4f50
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179289"
---
# <a name="cor_il_map-structure"></a><span data-ttu-id="ccbe0-102">COR_IL_MAP — Struktura</span><span class="sxs-lookup"><span data-stu-id="ccbe0-102">COR_IL_MAP Structure</span></span>
<span data-ttu-id="ccbe0-103">Określa zmiany względnego odsunięcia funkcji.</span><span class="sxs-lookup"><span data-stu-id="ccbe0-103">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccbe0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ccbe0-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;
    ULONG32 newOffset;
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="ccbe0-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ccbe0-105">Members</span></span>  
  
|<span data-ttu-id="ccbe0-106">Członek</span><span class="sxs-lookup"><span data-stu-id="ccbe0-106">Member</span></span>|<span data-ttu-id="ccbe0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ccbe0-107">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="ccbe0-108">Stare przesunięcie języka pośredniego firmy Microsoft (MSIL) względem początku funkcji.</span><span class="sxs-lookup"><span data-stu-id="ccbe0-108">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="ccbe0-109">Nowe przesunięcie MSIL względem początku funkcji.</span><span class="sxs-lookup"><span data-stu-id="ccbe0-109">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="ccbe0-110">`true`jeśli wiadomo, że mapowanie jest dokładne; w `false`przeciwnym razie , .</span><span class="sxs-lookup"><span data-stu-id="ccbe0-110">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ccbe0-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ccbe0-111">Remarks</span></span>  
 <span data-ttu-id="ccbe0-112">Format mapy jest następujący: Debuger przyjmie, `oldOffset` że odnosi się do przesunięcia MSIL w oryginalnym, niezmodyfikowanym kodzie MSIL.</span><span class="sxs-lookup"><span data-stu-id="ccbe0-112">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="ccbe0-113">Parametr `newOffset` odnosi się do odpowiedniego przesunięcia MSIL w nowym, oprzyrządowanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ccbe0-113">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="ccbe0-114">W celu prawidłowego przechodzenia do pracy należy spełnić następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="ccbe0-114">For stepping to work properly, the following requirements should be met:</span></span>  
  
- <span data-ttu-id="ccbe0-115">Mapa powinna być sortowana w porządku rosnącym.</span><span class="sxs-lookup"><span data-stu-id="ccbe0-115">The map should be sorted in ascending order.</span></span>  
  
- <span data-ttu-id="ccbe0-116">Instrumentowany kod MSIL nie powinien być ponownie zamówiony.</span><span class="sxs-lookup"><span data-stu-id="ccbe0-116">Instrumented MSIL code should not be reordered.</span></span>  
  
- <span data-ttu-id="ccbe0-117">Oryginalny kod MSIL nie powinien zostać usunięty.</span><span class="sxs-lookup"><span data-stu-id="ccbe0-117">Original MSIL code should not be removed.</span></span>  
  
- <span data-ttu-id="ccbe0-118">Mapa powinna zawierać wpisy do mapowania wszystkich punktów sekwencji z pliku bazy danych programu (PDB).</span><span class="sxs-lookup"><span data-stu-id="ccbe0-118">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="ccbe0-119">Mapa nie interpoluje brakujących wpisów.</span><span class="sxs-lookup"><span data-stu-id="ccbe0-119">The map does not interpolate missing entries.</span></span> <span data-ttu-id="ccbe0-120">Poniższy przykład pokazuje mapę i jej wyniki.</span><span class="sxs-lookup"><span data-stu-id="ccbe0-120">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="ccbe0-121">Mapę:</span><span class="sxs-lookup"><span data-stu-id="ccbe0-121">Map:</span></span>  
  
- <span data-ttu-id="ccbe0-122">0 stare przesunięcie, 0 nowe przesunięcie</span><span class="sxs-lookup"><span data-stu-id="ccbe0-122">0 old offset, 0 new offset</span></span>  
  
- <span data-ttu-id="ccbe0-123">5 stare przesunięcie, 10 nowych offset</span><span class="sxs-lookup"><span data-stu-id="ccbe0-123">5 old offset, 10 new offset</span></span>  
  
- <span data-ttu-id="ccbe0-124">9 stare przesunięcie, 20 nowych offset</span><span class="sxs-lookup"><span data-stu-id="ccbe0-124">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="ccbe0-125">Wyniki:</span><span class="sxs-lookup"><span data-stu-id="ccbe0-125">Results:</span></span>  
  
- <span data-ttu-id="ccbe0-126">Stare przesunięcie 0, 1, 2, 3 lub 4 zostanie odwzorowane na nowe przesunięcie 0.</span><span class="sxs-lookup"><span data-stu-id="ccbe0-126">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
- <span data-ttu-id="ccbe0-127">Stare przesunięcie 5, 6, 7 lub 8 zostanie odwzorowane na nowe przesunięcie 10.</span><span class="sxs-lookup"><span data-stu-id="ccbe0-127">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
- <span data-ttu-id="ccbe0-128">Stare przesunięcie 9 lub wyższe zostanie zmapowane na nowe przesunięcie 20.</span><span class="sxs-lookup"><span data-stu-id="ccbe0-128">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
- <span data-ttu-id="ccbe0-129">Nowe przesunięcie 0, 1, 2, 3, 4, 5, 6, 7, 8 lub 9 zostanie odwzorowane na stare przesunięcie 0.</span><span class="sxs-lookup"><span data-stu-id="ccbe0-129">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
- <span data-ttu-id="ccbe0-130">Nowe przesunięcie 10, 11, 12, 13, 14, 15, 16, 17, 18 lub 19 zostanie odwzorowane na stare przesunięcie 5.</span><span class="sxs-lookup"><span data-stu-id="ccbe0-130">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
- <span data-ttu-id="ccbe0-131">Nowe przesunięcie 20 lub wyższe zostanie odwzorowane na stare przesunięcie 9.</span><span class="sxs-lookup"><span data-stu-id="ccbe0-131">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccbe0-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ccbe0-132">Requirements</span></span>  
 <span data-ttu-id="ccbe0-133">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccbe0-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccbe0-134">**Nagłówek:** CorDebug.idl, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="ccbe0-134">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="ccbe0-135">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ccbe0-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ccbe0-136">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccbe0-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccbe0-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ccbe0-137">See also</span></span>

- [<span data-ttu-id="ccbe0-138">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="ccbe0-138">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="ccbe0-139">Debugging</span><span class="sxs-lookup"><span data-stu-id="ccbe0-139">Debugging</span></span>](index.md)
