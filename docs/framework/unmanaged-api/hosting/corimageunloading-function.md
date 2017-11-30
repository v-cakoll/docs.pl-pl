---
title: "_CorImageUnloading — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _CorImageUnloading
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: _CorImageUnloading
helpviewer_keywords: _CorImageUnloading function [.NET Framework hosting]
ms.assetid: b4367214-6dac-4280-aa11-fd487ff30bc4
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 90df58e2765cdecf4a1ec22cf5540e5cfa9530a9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="corimageunloading-function"></a><span data-ttu-id="a8c9c-102">_CorImageUnloading — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a8c9c-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="a8c9c-103">Powiadamia program ładujący, gdy moduł zarządzany obrazy są usuwane z pamięci.</span><span class="sxs-lookup"><span data-stu-id="a8c9c-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="a8c9c-104">Ta funkcja nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="a8c9c-104">This function is not implemented.</span></span> <span data-ttu-id="a8c9c-105">Wywołuje się, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="a8c9c-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8c9c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a8c9c-106">Syntax</span></span>  
  
```  
STDAPI (VOID) _CorImageUnloading(   
   [in] PVOID* ImageBase  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a8c9c-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8c9c-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="a8c9c-108">[in] Wskaźnik do rozpoczęcia lokalizacji obrazu do zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="a8c9c-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8c9c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a8c9c-109">Requirements</span></span>  
 <span data-ttu-id="a8c9c-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8c9c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8c9c-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a8c9c-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a8c9c-112">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a8c9c-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a8c9c-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8c9c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8c9c-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8c9c-114">See Also</span></span>  
 [<span data-ttu-id="a8c9c-115">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="a8c9c-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
