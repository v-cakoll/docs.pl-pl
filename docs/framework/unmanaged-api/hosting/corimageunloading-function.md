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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ebd7ef3b329eae8e35b680f3d8c74864e2a0f4d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428690"
---
# <a name="corimageunloading-function"></a><span data-ttu-id="d6bf9-102">_CorImageUnloading — Funkcja</span><span class="sxs-lookup"><span data-stu-id="d6bf9-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="d6bf9-103">Powiadamia program ładujący, gdy moduł zarządzany obrazy są usuwane z pamięci.</span><span class="sxs-lookup"><span data-stu-id="d6bf9-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="d6bf9-104">Ta funkcja nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="d6bf9-104">This function is not implemented.</span></span> <span data-ttu-id="d6bf9-105">Wywołuje się, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="d6bf9-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6bf9-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6bf9-106">Syntax</span></span>  
  
```  
STDAPI (VOID) _CorImageUnloading(   
   [in] PVOID* ImageBase  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6bf9-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6bf9-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="d6bf9-108">[in] Wskaźnik do rozpoczęcia lokalizacji obrazu do zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="d6bf9-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6bf9-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d6bf9-109">Requirements</span></span>  
 <span data-ttu-id="d6bf9-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6bf9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6bf9-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d6bf9-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6bf9-112">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d6bf9-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d6bf9-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6bf9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6bf9-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d6bf9-114">See Also</span></span>  
 [<span data-ttu-id="d6bf9-115">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="d6bf9-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
