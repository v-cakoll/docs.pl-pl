---
title: "CoInitializeCor — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoInitializeCor
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CoInitializeCor
helpviewer_keywords: CoInitializeCor function [.NET Framework hosting]
ms.assetid: 9b9079fb-579e-4141-b3f0-791072dd40dc
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 119a01a33faeedc49931f3e7cbb1685b26366d0a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="coinitializecor-function"></a><span data-ttu-id="e83ae-102">CoInitializeCor — Funkcja</span><span class="sxs-lookup"><span data-stu-id="e83ae-102">CoInitializeCor Function</span></span>
<span data-ttu-id="e83ae-103">`CoInitializeCor`jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="e83ae-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e83ae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e83ae-104">Syntax</span></span>  
  
```  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="e83ae-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e83ae-105">Remarks</span></span>  
 <span data-ttu-id="e83ae-106">Aby zainicjować środowiska CLR, użyj [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) lub [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="e83ae-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e83ae-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e83ae-107">Requirements</span></span>  
 <span data-ttu-id="e83ae-108">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e83ae-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e83ae-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e83ae-109">See Also</span></span>  
 [<span data-ttu-id="e83ae-110">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="e83ae-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
