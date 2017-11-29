---
title: "CloseAssembly — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.CloseAssembly
- CloseAssembly
api_location: alink.dll
api_type: COM
f1_keywords: CloseAssembly
helpviewer_keywords: CloseAssembly method
ms.assetid: f66a43bc-a5c5-4190-acbe-63fd27640634
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: be68348b619f342eca4841a6052088bf7152f453
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="closeassembly-method"></a><span data-ttu-id="5817b-102">CloseAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="5817b-102">CloseAssembly Method</span></span>
<span data-ttu-id="5817b-103">Kończenie znajdujących się w zestawie operacji.</span><span class="sxs-lookup"><span data-stu-id="5817b-103">Finalizes assembly operations.</span></span> <span data-ttu-id="5817b-104">Tę metodę należy wywołać przed rozpoczęciem nowego zestawu lub modułu niepowiązanych.</span><span class="sxs-lookup"><span data-stu-id="5817b-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5817b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5817b-105">Syntax</span></span>  
  
```  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5817b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5817b-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="5817b-107">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="5817b-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5817b-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5817b-108">Return Value</span></span>  
 <span data-ttu-id="5817b-109">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="5817b-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5817b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5817b-110">Requirements</span></span>  
 <span data-ttu-id="5817b-111">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="5817b-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5817b-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5817b-112">See Also</span></span>  
 [<span data-ttu-id="5817b-113">Ialink — interfejs</span><span class="sxs-lookup"><span data-stu-id="5817b-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="5817b-114">Ialink2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="5817b-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="5817b-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="5817b-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
