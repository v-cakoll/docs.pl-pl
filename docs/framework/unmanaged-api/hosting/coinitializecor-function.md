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
ms.openlocfilehash: 188f98504fa73c4a85615a4e688bae02d966b9b6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616752"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="8307e-102">CoInitializeCor — Funkcja</span><span class="sxs-lookup"><span data-stu-id="8307e-102">CoInitializeCor Function</span></span>
<span data-ttu-id="8307e-103">`CoInitializeCor`jest przestarzały.</span><span class="sxs-lookup"><span data-stu-id="8307e-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8307e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8307e-104">Syntax</span></span>  
  
```cpp  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="8307e-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8307e-105">Remarks</span></span>  
 <span data-ttu-id="8307e-106">Aby zainicjować środowisko uruchomieniowe języka wspólnego, użyj opcji [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) lub [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="8307e-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8307e-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8307e-107">Requirements</span></span>  
 <span data-ttu-id="8307e-108">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8307e-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8307e-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8307e-109">See also</span></span>

- [<span data-ttu-id="8307e-110">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="8307e-110">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
