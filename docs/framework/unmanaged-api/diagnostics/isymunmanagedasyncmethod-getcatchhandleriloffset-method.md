---
title: "ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d5f88656-433d-447c-b21c-2a12bed2e72a
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4d04c34bdc1b61f81fa542dfb22de9a6998f9cc9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodgetcatchhandleriloffset-method"></a><span data-ttu-id="4c46f-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="4c46f-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset Method</span></span>
<span data-ttu-id="4c46f-103">Zobacz [DefineCatchHandlerILOffset — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="4c46f-103">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c46f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c46f-104">Syntax</span></span>  
  
```idl  
HRESULT GetCatchHandlerILOffset(    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4c46f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c46f-105">Parameters</span></span>  
  
|<span data-ttu-id="4c46f-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="4c46f-106">Parameter</span></span>|<span data-ttu-id="4c46f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4c46f-107">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="4c46f-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4c46f-108">Return Value</span></span>  
 <span data-ttu-id="4c46f-109">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="4c46f-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c46f-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4c46f-110">Requirements</span></span>  
 <span data-ttu-id="4c46f-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4c46f-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c46f-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4c46f-112">See Also</span></span>  
 [<span data-ttu-id="4c46f-113">Isymunmanagedasyncmethod — interfejs</span><span class="sxs-lookup"><span data-stu-id="4c46f-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
