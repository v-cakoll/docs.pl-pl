---
title: CoInitializeCor — Funkcja
ms.date: 03/30/2017
api_name:
- CoInitializeCor
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeCor
helpviewer_keywords:
- CoInitializeCor function [.NET Framework hosting]
ms.assetid: 9b9079fb-579e-4141-b3f0-791072dd40dc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91315e8af0cc46a3450a7515b885988cffe34927
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429991"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="d28c3-102">CoInitializeCor — Funkcja</span><span class="sxs-lookup"><span data-stu-id="d28c3-102">CoInitializeCor Function</span></span>
<span data-ttu-id="d28c3-103">`CoInitializeCor` jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="d28c3-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d28c3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d28c3-104">Syntax</span></span>  
  
```  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="d28c3-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d28c3-105">Remarks</span></span>  
 <span data-ttu-id="d28c3-106">Aby zainicjować środowiska CLR, użyj [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) lub [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="d28c3-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d28c3-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d28c3-107">Requirements</span></span>  
 <span data-ttu-id="d28c3-108">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d28c3-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d28c3-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d28c3-109">See Also</span></span>  
 [<span data-ttu-id="d28c3-110">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="d28c3-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
