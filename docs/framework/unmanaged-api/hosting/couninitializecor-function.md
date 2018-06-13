---
title: CoUninitializeCor — Funkcja
ms.date: 03/30/2017
api_name:
- CoUninitializeCor
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeCor
helpviewer_keywords:
- CoUninitializeCor function [.NET Framework hosting]
ms.assetid: 50a95b8b-9766-470e-bb29-2c7ecddfd4a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 305a8d7b5a800c46ed814b1e654947859dc9bd03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427814"
---
# <a name="couninitializecor-function"></a><span data-ttu-id="1900f-102">CoUninitializeCor — Funkcja</span><span class="sxs-lookup"><span data-stu-id="1900f-102">CoUninitializeCor Function</span></span>
<span data-ttu-id="1900f-103">`CoUninitializeCor` jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="1900f-103">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1900f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1900f-104">Syntax</span></span>  
  
```  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="1900f-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1900f-105">Remarks</span></span>  
 <span data-ttu-id="1900f-106">Środowisko uruchomieniowe języka wspólnego nie może być zwolniony z procesem.</span><span class="sxs-lookup"><span data-stu-id="1900f-106">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="1900f-107">Aby całkowicie usunąć środowiska uruchomieniowego z uruchomionego procesu, należy zamknąć ten proces.</span><span class="sxs-lookup"><span data-stu-id="1900f-107">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1900f-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1900f-108">See Also</span></span>  
 [<span data-ttu-id="1900f-109">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="1900f-109">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
