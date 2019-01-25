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
ms.openlocfilehash: 349f6922c18a7745c8eff05b1786dc649f8bb70a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520987"
---
# <a name="couninitializecor-function"></a><span data-ttu-id="46a98-102">CoUninitializeCor — Funkcja</span><span class="sxs-lookup"><span data-stu-id="46a98-102">CoUninitializeCor Function</span></span>
<span data-ttu-id="46a98-103">`CoUninitializeCor` jest przestarzały.</span><span class="sxs-lookup"><span data-stu-id="46a98-103">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46a98-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="46a98-104">Syntax</span></span>  
  
```  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="46a98-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="46a98-105">Remarks</span></span>  
 <span data-ttu-id="46a98-106">Środowisko uruchomieniowe języka wspólnego nie może być zwolnione z procesu.</span><span class="sxs-lookup"><span data-stu-id="46a98-106">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="46a98-107">Aby całkowicie usunąć środowisko uruchomieniowe z uruchomionego procesu, należy zamknąć ten proces.</span><span class="sxs-lookup"><span data-stu-id="46a98-107">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46a98-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="46a98-108">See also</span></span>
- [<span data-ttu-id="46a98-109">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="46a98-109">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
