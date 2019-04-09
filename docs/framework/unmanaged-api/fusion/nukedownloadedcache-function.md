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
ms.openlocfilehash: 4e549e13c0d51e4aa708a674a2224168ab66f8ad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178168"
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="80c6c-102">NukeDownloadedCache — Funkcja</span><span class="sxs-lookup"><span data-stu-id="80c6c-102">NukeDownloadedCache Function</span></span>
<span data-ttu-id="80c6c-103">Usuwa wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) pamięci podręcznej pobierania.</span><span class="sxs-lookup"><span data-stu-id="80c6c-103">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80c6c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="80c6c-104">Syntax</span></span>  
  
```  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="80c6c-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="80c6c-105">Return Value</span></span>  
 <span data-ttu-id="80c6c-106">Ta metoda zwraca standardowe kody błędu modelu COM, zgodnie z definicją w pliku WinError.h.</span><span class="sxs-lookup"><span data-stu-id="80c6c-106">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80c6c-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80c6c-107">Remarks</span></span>  
 <span data-ttu-id="80c6c-108">Pamięć podręczna pobierania CLR jest obszar przechowywania o silnych nazwach, które zostały pobrane z adresu URL do możliwości ponownego użycia.</span><span class="sxs-lookup"><span data-stu-id="80c6c-108">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80c6c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="80c6c-109">Requirements</span></span>  
 <span data-ttu-id="80c6c-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80c6c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80c6c-111">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="80c6c-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="80c6c-112">**Biblioteka:** Fusion.dll i Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="80c6c-112">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="80c6c-113">Użyj Fusion.dll zamiast Mscorwks.dll zapewnienie docelowych poprawną wersję programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="80c6c-113">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 **<span data-ttu-id="80c6c-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="80c6c-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="80c6c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80c6c-115">See also</span></span>

- [<span data-ttu-id="80c6c-116">CreateHistoryReader — Funkcja</span><span class="sxs-lookup"><span data-stu-id="80c6c-116">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [<span data-ttu-id="80c6c-117">GetHistoryFileDirectory — Funkcja</span><span class="sxs-lookup"><span data-stu-id="80c6c-117">GetHistoryFileDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)
- [<span data-ttu-id="80c6c-118">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="80c6c-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
