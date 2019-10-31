---
title: NukeDownloadedCache — Funkcja
ms.date: 03/30/2017
api_name:
- NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- NukeDownloadedCache
helpviewer_keywords:
- NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type:
- apiref
ms.openlocfilehash: 8f97614412eb2d49b202e86bdabc727159deb5d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131695"
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="ccf9d-102">NukeDownloadedCache — Funkcja</span><span class="sxs-lookup"><span data-stu-id="ccf9d-102">NukeDownloadedCache Function</span></span>
<span data-ttu-id="ccf9d-103">Usuwa pamięć podręczną pobierania środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="ccf9d-103">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccf9d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ccf9d-104">Syntax</span></span>  
  
```cpp  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ccf9d-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ccf9d-105">Return Value</span></span>  
 <span data-ttu-id="ccf9d-106">Ta metoda zwraca standardowe kody błędów COM, zgodnie z definicją w WinError. h.</span><span class="sxs-lookup"><span data-stu-id="ccf9d-106">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ccf9d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ccf9d-107">Remarks</span></span>  
 <span data-ttu-id="ccf9d-108">Pamięć podręczna pobierania środowiska CLR to obszar, w którym zestawy o silnych nazwach pobrane z adresu URL są przechowywane do ponownego użycia.</span><span class="sxs-lookup"><span data-stu-id="ccf9d-108">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccf9d-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ccf9d-109">Requirements</span></span>  
 <span data-ttu-id="ccf9d-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccf9d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccf9d-111">**Nagłówek:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="ccf9d-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ccf9d-112">**Biblioteka:** Fusion. dll i mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="ccf9d-112">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="ccf9d-113">Aby upewnić się, że docelowa wersja .NET Framework, należy użyć pliku Fusion. dll zamiast Mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="ccf9d-113">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="ccf9d-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccf9d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccf9d-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ccf9d-115">See also</span></span>

- [<span data-ttu-id="ccf9d-116">CreateHistoryReader, funkcja</span><span class="sxs-lookup"><span data-stu-id="ccf9d-116">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)
- [<span data-ttu-id="ccf9d-117">GetHistoryFileDirectory, funkcja</span><span class="sxs-lookup"><span data-stu-id="ccf9d-117">GetHistoryFileDirectory Function</span></span>](gethistoryfiledirectory-function.md)
- [<span data-ttu-id="ccf9d-118">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="ccf9d-118">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
