---
title: CoUninitializeEE — Funkcja
ms.date: 03/30/2017
api_name:
- CoUninitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
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
ms.openlocfilehash: 7b3712b4cb66facc105a03d7bfad235f09339056
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985741"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="c9816-102">CoUninitializeEE — Funkcja</span><span class="sxs-lookup"><span data-stu-id="c9816-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="c9816-103">`CoUninitializeEE` jest przestarzały i nie zawiera żadnych funkcji.</span><span class="sxs-lookup"><span data-stu-id="c9816-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9816-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c9816-104">Syntax</span></span>  
  
```  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="c9816-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c9816-105">Remarks</span></span>  
 <span data-ttu-id="c9816-106">Aparat wykonywania środowiska uruchomieniowego języka wspólnego nie może być zwolnione z procesu.</span><span class="sxs-lookup"><span data-stu-id="c9816-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="c9816-107">Zamknąć wywołanie aparatu wykonywania [corexitprocess —](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="c9816-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9816-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9816-108">See also</span></span>

- [<span data-ttu-id="c9816-109">CoInitializeEE, funkcja</span><span class="sxs-lookup"><span data-stu-id="c9816-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)
- [<span data-ttu-id="c9816-110">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="c9816-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
