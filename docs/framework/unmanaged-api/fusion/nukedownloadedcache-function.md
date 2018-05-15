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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0436991512713c05e60a3c10d6fbdaa17bb378c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="6fa33-102">NukeDownloadedCache — Funkcja</span><span class="sxs-lookup"><span data-stu-id="6fa33-102">NukeDownloadedCache Function</span></span>
<span data-ttu-id="6fa33-103">Usuwa wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) pamięć podręczną pobierania.</span><span class="sxs-lookup"><span data-stu-id="6fa33-103">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fa33-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6fa33-104">Syntax</span></span>  
  
```  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6fa33-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6fa33-105">Return Value</span></span>  
 <span data-ttu-id="6fa33-106">Ta metoda zwraca standardowe kody błędów COM, zgodnie z definicją w pliku WinError.h.</span><span class="sxs-lookup"><span data-stu-id="6fa33-106">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fa33-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6fa33-107">Remarks</span></span>  
 <span data-ttu-id="6fa33-108">Pamięć podręczną pobierania CLR jest obszar przechowywania zestawy o silnych nazwach, które są pobierane z adresu URL do możliwości ponownego użycia.</span><span class="sxs-lookup"><span data-stu-id="6fa33-108">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fa33-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6fa33-109">Requirements</span></span>  
 <span data-ttu-id="6fa33-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fa33-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fa33-111">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="6fa33-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="6fa33-112">**Biblioteka:** Fusion.dll i Mscorwks.dll.a;a;pierwsza.</span><span class="sxs-lookup"><span data-stu-id="6fa33-112">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="6fa33-113">Użyj Fusion.dll zamiast Mscorwks.dll.a;a;pierwsza, aby upewnić się, że docelowy poprawna wersja programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6fa33-113">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="6fa33-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fa33-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fa33-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6fa33-115">See Also</span></span>  
 [<span data-ttu-id="6fa33-116">CreateHistoryReader, funkcja</span><span class="sxs-lookup"><span data-stu-id="6fa33-116">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [<span data-ttu-id="6fa33-117">GetHistoryFileDirectory, funkcja</span><span class="sxs-lookup"><span data-stu-id="6fa33-117">GetHistoryFileDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 [<span data-ttu-id="6fa33-118">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="6fa33-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
