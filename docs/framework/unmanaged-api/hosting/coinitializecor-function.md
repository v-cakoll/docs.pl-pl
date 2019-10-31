---
title: CoInitializeCor — Funkcja
ms.date: 03/30/2017
api_name:
- CoInitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeCor
helpviewer_keywords:
- CoInitializeCor function [.NET Framework hosting]
ms.assetid: 9b9079fb-579e-4141-b3f0-791072dd40dc
topic_type:
- apiref
ms.openlocfilehash: e8d65e739504e01a7d11b37d1b34d7313b13a5e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138335"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="b42f0-102">CoInitializeCor — Funkcja</span><span class="sxs-lookup"><span data-stu-id="b42f0-102">CoInitializeCor Function</span></span>
<span data-ttu-id="b42f0-103">`CoInitializeCor` jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="b42f0-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b42f0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b42f0-104">Syntax</span></span>  
  
```cpp  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="b42f0-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b42f0-105">Remarks</span></span>  
 <span data-ttu-id="b42f0-106">Aby zainicjować środowisko uruchomieniowe języka wspólnego, użyj opcji [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) lub [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="b42f0-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b42f0-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b42f0-107">Requirements</span></span>  
 <span data-ttu-id="b42f0-108">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b42f0-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b42f0-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b42f0-109">See also</span></span>

- [<span data-ttu-id="b42f0-110">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="b42f0-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
