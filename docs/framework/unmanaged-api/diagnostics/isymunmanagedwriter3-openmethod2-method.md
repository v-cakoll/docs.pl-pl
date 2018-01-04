---
title: "ISymUnmanagedWriter3::OpenMethod2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter3.OpenMethod2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8da6de0271ddce5b956e667420a206c09cc291d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="fc65b-102">ISymUnmanagedWriter3::OpenMethod2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="fc65b-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="fc65b-103">Otwiera metody i zapewnia jego przesunięcie rzeczywistych sekcji w obrazie.</span><span class="sxs-lookup"><span data-stu-id="fc65b-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc65b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc65b-104">Syntax</span></span>  
  
```  
HRESULT OpenMethod2(   
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc65b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc65b-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="fc65b-106">[in] Token metadanych metody, która ma zostać otwarty.</span><span class="sxs-lookup"><span data-stu-id="fc65b-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="fc65b-107">[in] Przesunięcie sekcji w obrazie.</span><span class="sxs-lookup"><span data-stu-id="fc65b-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="fc65b-108">[in] Przesunięcie w obrazie.</span><span class="sxs-lookup"><span data-stu-id="fc65b-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc65b-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fc65b-109">Return Value</span></span>  
 <span data-ttu-id="fc65b-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="fc65b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc65b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc65b-111">Requirements</span></span>  
 <span data-ttu-id="fc65b-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fc65b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc65b-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc65b-113">See Also</span></span>  
 [<span data-ttu-id="fc65b-114">ISymUnmanagedWriter3, interfejs</span><span class="sxs-lookup"><span data-stu-id="fc65b-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 [<span data-ttu-id="fc65b-115">OpenMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="fc65b-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
