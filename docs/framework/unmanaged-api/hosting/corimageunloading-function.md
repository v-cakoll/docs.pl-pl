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
ms.openlocfilehash: be2edd5b217466a58aa9c478dadc10004ebda721
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556145"
---
# <a name="corimageunloading-function"></a><span data-ttu-id="4fb56-102">_CorImageUnloading — Funkcja</span><span class="sxs-lookup"><span data-stu-id="4fb56-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="4fb56-103">Powiadamia moduł ładujący, gdy obrazy modułu zarządzanego są usuwane z pamięci.</span><span class="sxs-lookup"><span data-stu-id="4fb56-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="4fb56-104">Ta funkcja nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="4fb56-104">This function is not implemented.</span></span> <span data-ttu-id="4fb56-105">Jeżeli jest wywoływana, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="4fb56-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fb56-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4fb56-106">Syntax</span></span>  
  
```  
STDAPI (VOID) _CorImageUnloading(   
   [in] PVOID* ImageBase  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4fb56-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="4fb56-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="4fb56-108">[in] Wskaźnik do wyjścia lokalizację obrazu, aby zwolnić.</span><span class="sxs-lookup"><span data-stu-id="4fb56-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fb56-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4fb56-109">Requirements</span></span>  
 <span data-ttu-id="4fb56-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fb56-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fb56-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="4fb56-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4fb56-112">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4fb56-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4fb56-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fb56-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fb56-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4fb56-114">See also</span></span>
- [<span data-ttu-id="4fb56-115">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="4fb56-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
