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
ms.openlocfilehash: 1263467fc5db92d4dd21c4f09a98af309e2c4d55
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504423"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="c75a4-102">CoInitializeCor — Funkcja</span><span class="sxs-lookup"><span data-stu-id="c75a4-102">CoInitializeCor Function</span></span>
<span data-ttu-id="c75a4-103">`CoInitializeCor`jest przestarzały.</span><span class="sxs-lookup"><span data-stu-id="c75a4-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c75a4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c75a4-104">Syntax</span></span>  
  
```cpp  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="c75a4-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c75a4-105">Remarks</span></span>  
 <span data-ttu-id="c75a4-106">Aby zainicjować środowisko uruchomieniowe języka wspólnego, użyj opcji [CorBindToRuntimeEx](corbindtoruntimeex-function.md) lub [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="c75a4-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c75a4-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c75a4-107">Requirements</span></span>  
 <span data-ttu-id="c75a4-108">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c75a4-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c75a4-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c75a4-109">See also</span></span>

- [<span data-ttu-id="c75a4-110">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="c75a4-110">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
