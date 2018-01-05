---
title: "CoUninitializeEE — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoUninitializeEE
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CoUninitializeEE
helpviewer_keywords: CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4125a76ae50a293e35e326f775500c06120420d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="couninitializeee-function"></a><span data-ttu-id="89d81-102">CoUninitializeEE — Funkcja</span><span class="sxs-lookup"><span data-stu-id="89d81-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="89d81-103">`CoUninitializeEE`jest przestarzały i nie zawiera żadnych funkcji.</span><span class="sxs-lookup"><span data-stu-id="89d81-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89d81-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="89d81-104">Syntax</span></span>  
  
```  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="89d81-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="89d81-105">Remarks</span></span>  
 <span data-ttu-id="89d81-106">Aparat wykonywania środowiska uruchomieniowego języka wspólnego nie może być zwolniony z procesem.</span><span class="sxs-lookup"><span data-stu-id="89d81-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="89d81-107">Można zamknąć wywołanie aparatu wykonywania [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="89d81-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89d81-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89d81-108">See Also</span></span>  
 [<span data-ttu-id="89d81-109">CoInitializeEE, funkcja</span><span class="sxs-lookup"><span data-stu-id="89d81-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 [<span data-ttu-id="89d81-110">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="89d81-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
