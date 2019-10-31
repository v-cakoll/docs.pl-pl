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
ms.openlocfilehash: 30e3a88140c8a438001e8428df4c5ee879c83376
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136921"
---
# <a name="_corimageunloading-function"></a><span data-ttu-id="7b023-102">_CorImageUnloading — Funkcja</span><span class="sxs-lookup"><span data-stu-id="7b023-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="7b023-103">Powiadamia moduł ładujący, gdy obrazy modułu zarządzanego są zwolnione.</span><span class="sxs-lookup"><span data-stu-id="7b023-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="7b023-104">Ta funkcja nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="7b023-104">This function is not implemented.</span></span> <span data-ttu-id="7b023-105">Jeśli zostanie wywołana, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="7b023-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b023-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="7b023-106">Syntax</span></span>  
  
```cpp  
STDAPI (VOID) _CorImageUnloading(   
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b023-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b023-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="7b023-108">podczas Wskaźnik do lokalizacji początkowej obrazu do zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="7b023-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b023-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7b023-109">Requirements</span></span>  
 <span data-ttu-id="7b023-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b023-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b023-111">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7b023-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7b023-112">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7b023-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7b023-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b023-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b023-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7b023-114">See also</span></span>

- [<span data-ttu-id="7b023-115">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="7b023-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
