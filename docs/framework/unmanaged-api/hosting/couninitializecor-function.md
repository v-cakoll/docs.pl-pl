---
title: CoUninitializeCor — Funkcja
ms.date: 03/30/2017
api_name:
- CoUninitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
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
ms.openlocfilehash: e3ce0b9a40d5375f563662d73964d28724209dcd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758293"
---
# <a name="couninitializecor-function"></a><span data-ttu-id="07a42-102">CoUninitializeCor — Funkcja</span><span class="sxs-lookup"><span data-stu-id="07a42-102">CoUninitializeCor Function</span></span>
<span data-ttu-id="07a42-103">`CoUninitializeCor` jest przestarzały.</span><span class="sxs-lookup"><span data-stu-id="07a42-103">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07a42-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="07a42-104">Syntax</span></span>  
  
```cpp  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="07a42-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="07a42-105">Remarks</span></span>  
 <span data-ttu-id="07a42-106">Środowisko uruchomieniowe języka wspólnego nie może być zwolnione z procesu.</span><span class="sxs-lookup"><span data-stu-id="07a42-106">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="07a42-107">Aby całkowicie usunąć środowisko uruchomieniowe z uruchomionego procesu, należy zamknąć ten proces.</span><span class="sxs-lookup"><span data-stu-id="07a42-107">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07a42-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07a42-108">See also</span></span>

- [<span data-ttu-id="07a42-109">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="07a42-109">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
