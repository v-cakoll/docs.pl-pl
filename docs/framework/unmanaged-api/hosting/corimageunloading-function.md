---
title: _CorImageUnloading — Funkcja
ms.date: 03/30/2017
api_name:
- _CorImageUnloading
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorImageUnloading
helpviewer_keywords:
- _CorImageUnloading function [.NET Framework hosting]
ms.assetid: b4367214-6dac-4280-aa11-fd487ff30bc4
topic_type:
- apiref
ms.openlocfilehash: 4932e1fd6294f4a01264e982835dd0707324082a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178230"
---
# <a name="_corimageunloading-function"></a><span data-ttu-id="afb98-102">_CorImageUnloading — Funkcja</span><span class="sxs-lookup"><span data-stu-id="afb98-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="afb98-103">Powiadamia moduł ładujący, gdy obrazy modułu zarządzanego są zwalniane.</span><span class="sxs-lookup"><span data-stu-id="afb98-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="afb98-104">Ta funkcja nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="afb98-104">This function is not implemented.</span></span> <span data-ttu-id="afb98-105">Jeśli wywoływane, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="afb98-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afb98-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="afb98-106">Syntax</span></span>  
  
```cpp  
STDAPI (VOID) _CorImageUnloading(
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afb98-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="afb98-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="afb98-108">[w] Wskaźnik do lokalizacji początkowej obrazu do wyładowania.</span><span class="sxs-lookup"><span data-stu-id="afb98-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afb98-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="afb98-109">Requirements</span></span>  
 <span data-ttu-id="afb98-110">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afb98-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afb98-111">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="afb98-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="afb98-112">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="afb98-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="afb98-113">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afb98-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afb98-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="afb98-114">See also</span></span>

- [<span data-ttu-id="afb98-115">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="afb98-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
