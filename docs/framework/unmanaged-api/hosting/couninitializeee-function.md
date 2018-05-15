---
title: CoUninitializeEE — Funkcja
ms.date: 03/30/2017
api_name:
- CoUninitializeEE
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeEE
helpviewer_keywords:
- CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73fa281d28e9b5362ff386b55b07dd431f1915f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="couninitializeee-function"></a><span data-ttu-id="9c9e1-102">CoUninitializeEE — Funkcja</span><span class="sxs-lookup"><span data-stu-id="9c9e1-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="9c9e1-103">`CoUninitializeEE` jest przestarzały i nie zawiera żadnych funkcji.</span><span class="sxs-lookup"><span data-stu-id="9c9e1-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c9e1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9c9e1-104">Syntax</span></span>  
  
```  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="9c9e1-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9c9e1-105">Remarks</span></span>  
 <span data-ttu-id="9c9e1-106">Aparat wykonywania środowiska uruchomieniowego języka wspólnego nie może być zwolniony z procesem.</span><span class="sxs-lookup"><span data-stu-id="9c9e1-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="9c9e1-107">Można zamknąć wywołanie aparatu wykonywania [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="9c9e1-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c9e1-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c9e1-108">See Also</span></span>  
 [<span data-ttu-id="9c9e1-109">CoInitializeEE, funkcja</span><span class="sxs-lookup"><span data-stu-id="9c9e1-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 [<span data-ttu-id="9c9e1-110">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="9c9e1-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
