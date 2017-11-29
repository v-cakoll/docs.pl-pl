---
title: "NukeDownloadedCache — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: NukeDownloadedCache
helpviewer_keywords: NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5ff24cf46ab24fe94ab19cee04d9e32ed1a34b53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="71737-102">NukeDownloadedCache — Funkcja</span><span class="sxs-lookup"><span data-stu-id="71737-102">NukeDownloadedCache Function</span></span>
<span data-ttu-id="71737-103">Usuwa wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) pamięć podręczną pobierania.</span><span class="sxs-lookup"><span data-stu-id="71737-103">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71737-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="71737-104">Syntax</span></span>  
  
```  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="71737-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="71737-105">Return Value</span></span>  
 <span data-ttu-id="71737-106">Ta metoda zwraca standardowe kody błędów COM, zgodnie z definicją w pliku WinError.h.</span><span class="sxs-lookup"><span data-stu-id="71737-106">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71737-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="71737-107">Remarks</span></span>  
 <span data-ttu-id="71737-108">Pamięć podręczną pobierania CLR jest obszar przechowywania zestawy o silnych nazwach, które są pobierane z adresu URL do możliwości ponownego użycia.</span><span class="sxs-lookup"><span data-stu-id="71737-108">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71737-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="71737-109">Requirements</span></span>  
 <span data-ttu-id="71737-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71737-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71737-111">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="71737-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="71737-112">**Biblioteka:** Fusion.dll i Mscorwks.dll.a;a;pierwsza.</span><span class="sxs-lookup"><span data-stu-id="71737-112">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="71737-113">Użyj Fusion.dll zamiast Mscorwks.dll.a;a;pierwsza, aby upewnić się, że docelowy poprawna wersja programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="71737-113">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="71737-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71737-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71737-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71737-115">See Also</span></span>  
 [<span data-ttu-id="71737-116">Createhistoryreader — funkcja</span><span class="sxs-lookup"><span data-stu-id="71737-116">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [<span data-ttu-id="71737-117">Gethistoryfiledirectory — funkcja</span><span class="sxs-lookup"><span data-stu-id="71737-117">GetHistoryFileDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 [<span data-ttu-id="71737-118">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="71737-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
