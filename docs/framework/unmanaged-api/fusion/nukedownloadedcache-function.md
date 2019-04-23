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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178168"
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="91d40-102">NukeDownloadedCache — Funkcja</span><span class="sxs-lookup"><span data-stu-id="91d40-102">NukeDownloadedCache Function</span></span>
<span data-ttu-id="91d40-103">Usuwa wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) pamięci podręcznej pobierania.</span><span class="sxs-lookup"><span data-stu-id="91d40-103">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91d40-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="91d40-104">Syntax</span></span>  
  
```  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="91d40-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="91d40-105">Return Value</span></span>  
 <span data-ttu-id="91d40-106">Ta metoda zwraca standardowe kody błędu modelu COM, zgodnie z definicją w pliku WinError.h.</span><span class="sxs-lookup"><span data-stu-id="91d40-106">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91d40-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="91d40-107">Remarks</span></span>  
 <span data-ttu-id="91d40-108">Pamięć podręczna pobierania CLR jest obszar przechowywania o silnych nazwach, które zostały pobrane z adresu URL do możliwości ponownego użycia.</span><span class="sxs-lookup"><span data-stu-id="91d40-108">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91d40-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="91d40-109">Requirements</span></span>  
 <span data-ttu-id="91d40-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91d40-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91d40-111">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="91d40-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="91d40-112">**Biblioteka:** Fusion.dll i Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="91d40-112">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="91d40-113">Użyj Fusion.dll zamiast Mscorwks.dll zapewnienie docelowych poprawną wersję programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="91d40-113">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="91d40-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91d40-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91d40-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91d40-115">See also</span></span>

- [<span data-ttu-id="91d40-116">CreateHistoryReader, funkcja</span><span class="sxs-lookup"><span data-stu-id="91d40-116">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [<span data-ttu-id="91d40-117">GetHistoryFileDirectory, funkcja</span><span class="sxs-lookup"><span data-stu-id="91d40-117">GetHistoryFileDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)
- [<span data-ttu-id="91d40-118">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="91d40-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
