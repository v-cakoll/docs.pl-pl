---
title: "EndMerge — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.EndMerge
- EndMerge
api_location: alink.dll
api_type: COM
f1_keywords: EndMerge
helpviewer_keywords: EndMerge method
ms.assetid: 1d03bb15-a2c8-4a04-8fc6-b126c89c3778
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7f29abf03c636fc552fe550534ca1b1395b43aae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="endmerge-method"></a><span data-ttu-id="90373-102">EndMerge — Metoda</span><span class="sxs-lookup"><span data-stu-id="90373-102">EndMerge Method</span></span>
<span data-ttu-id="90373-103">Wskazuje, że wszystkie atrybuty niestandardowe zostały scalone w zakresie emitowanie.</span><span class="sxs-lookup"><span data-stu-id="90373-103">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90373-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="90373-104">Syntax</span></span>  
  
```  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90373-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="90373-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="90373-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="90373-106">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90373-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="90373-107">Return Value</span></span>  
 <span data-ttu-id="90373-108">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="90373-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90373-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="90373-109">Requirements</span></span>  
 <span data-ttu-id="90373-110">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="90373-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90373-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="90373-111">See Also</span></span>  
 [<span data-ttu-id="90373-112">Ialink — interfejs</span><span class="sxs-lookup"><span data-stu-id="90373-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="90373-113">Ialink2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="90373-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="90373-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="90373-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
