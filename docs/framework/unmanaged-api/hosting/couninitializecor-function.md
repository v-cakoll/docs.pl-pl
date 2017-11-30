---
title: "CoUninitializeCor — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoUninitializeCor
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CoUninitializeCor
helpviewer_keywords: CoUninitializeCor function [.NET Framework hosting]
ms.assetid: 50a95b8b-9766-470e-bb29-2c7ecddfd4a1
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 57740ed8f20891b240bca5e9e19591484022b8ec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="couninitializecor-function"></a><span data-ttu-id="17e01-102">CoUninitializeCor — Funkcja</span><span class="sxs-lookup"><span data-stu-id="17e01-102">CoUninitializeCor Function</span></span>
<span data-ttu-id="17e01-103">`CoUninitializeCor`jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="17e01-103">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17e01-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="17e01-104">Syntax</span></span>  
  
```  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="17e01-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="17e01-105">Remarks</span></span>  
 <span data-ttu-id="17e01-106">Środowisko uruchomieniowe języka wspólnego nie może być zwolniony z procesem.</span><span class="sxs-lookup"><span data-stu-id="17e01-106">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="17e01-107">Aby całkowicie usunąć środowiska uruchomieniowego z uruchomionego procesu, należy zamknąć ten proces.</span><span class="sxs-lookup"><span data-stu-id="17e01-107">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17e01-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17e01-108">See Also</span></span>  
 [<span data-ttu-id="17e01-109">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="17e01-109">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
