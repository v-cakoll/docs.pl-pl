---
title: "GetResolutionScope — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.GetResolutionScope
api_location: alink.dll
api_type: COM
f1_keywords: GetResolutionScope
helpviewer_keywords: GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 11ccbce4d8e9783514050f6b41c6e32cde6c274f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="49f6b-102">GetResolutionScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="49f6b-102">GetResolutionScope Method</span></span>
<span data-ttu-id="49f6b-103">Pobiera zakres danego typu.</span><span class="sxs-lookup"><span data-stu-id="49f6b-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49f6b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="49f6b-104">Syntax</span></span>  
  
```  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="49f6b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="49f6b-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="49f6b-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="49f6b-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="49f6b-107">Plik, który wymaga odwołania.</span><span class="sxs-lookup"><span data-stu-id="49f6b-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="49f6b-108">Token pliku tego typu jest zdefiniowany w, zwykle pobrany za pomocą [ImportFile — metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="49f6b-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="49f6b-109">Odbiera zestawu lub odwołania do modułu.</span><span class="sxs-lookup"><span data-stu-id="49f6b-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49f6b-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="49f6b-110">Return Value</span></span>  
 <span data-ttu-id="49f6b-111">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="49f6b-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49f6b-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="49f6b-112">Requirements</span></span>  
 <span data-ttu-id="49f6b-113">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="49f6b-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49f6b-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="49f6b-114">See Also</span></span>  
 [<span data-ttu-id="49f6b-115">Ialink — interfejs</span><span class="sxs-lookup"><span data-stu-id="49f6b-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="49f6b-116">Ialink2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="49f6b-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="49f6b-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="49f6b-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
