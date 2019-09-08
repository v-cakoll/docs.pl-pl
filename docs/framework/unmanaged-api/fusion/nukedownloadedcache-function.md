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
ms.openlocfilehash: 29f492173a7fd22ab497d6e0096798e164fccf26
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796307"
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="7a88f-102">NukeDownloadedCache — Funkcja</span><span class="sxs-lookup"><span data-stu-id="7a88f-102">NukeDownloadedCache Function</span></span>
<span data-ttu-id="7a88f-103">Usuwa pamięć podręczną pobierania środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="7a88f-103">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a88f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a88f-104">Syntax</span></span>  
  
```cpp  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7a88f-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7a88f-105">Return Value</span></span>  
 <span data-ttu-id="7a88f-106">Ta metoda zwraca standardowe kody błędów COM, zgodnie z definicją w WinError. h.</span><span class="sxs-lookup"><span data-stu-id="7a88f-106">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a88f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7a88f-107">Remarks</span></span>  
 <span data-ttu-id="7a88f-108">Pamięć podręczna pobierania środowiska CLR to obszar, w którym zestawy o silnych nazwach pobrane z adresu URL są przechowywane do ponownego użycia.</span><span class="sxs-lookup"><span data-stu-id="7a88f-108">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a88f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7a88f-109">Requirements</span></span>  
 <span data-ttu-id="7a88f-110">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a88f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a88f-111">**Nagłówki** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="7a88f-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7a88f-112">**Biblioteki** Fusion. dll i mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="7a88f-112">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="7a88f-113">Aby upewnić się, że docelowa wersja .NET Framework, należy użyć pliku Fusion. dll zamiast Mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="7a88f-113">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="7a88f-114">**.NET Framework wersje:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a88f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a88f-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a88f-115">See also</span></span>

- [<span data-ttu-id="7a88f-116">CreateHistoryReader, funkcja</span><span class="sxs-lookup"><span data-stu-id="7a88f-116">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)
- [<span data-ttu-id="7a88f-117">GetHistoryFileDirectory, funkcja</span><span class="sxs-lookup"><span data-stu-id="7a88f-117">GetHistoryFileDirectory Function</span></span>](gethistoryfiledirectory-function.md)
- [<span data-ttu-id="7a88f-118">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="7a88f-118">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
