---
title: "ISymUnmanagedAsyncMethod::IsAsyncMethod — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 560690e95e7aa0aef37e3a708183641bd70ee97d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="b1081-102">ISymUnmanagedAsyncMethod::IsAsyncMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="b1081-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="b1081-103">Sprawdza, czy metoda ma informacje o asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="b1081-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="b1081-104">Jeśli ta metoda zwraca `FALSE` , a następnie jest wywoływać inne metody w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="b1081-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="b1081-105">One będą zwracane wszystkie `E_UNEXPECTED` w takim przypadku.</span><span class="sxs-lookup"><span data-stu-id="b1081-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1081-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1081-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1081-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1081-107">Parameters</span></span>  
  
|<span data-ttu-id="b1081-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="b1081-108">Parameter</span></span>|<span data-ttu-id="b1081-109">Opis</span><span class="sxs-lookup"><span data-stu-id="b1081-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="b1081-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b1081-110">Return Value</span></span>  
 <span data-ttu-id="b1081-111">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="b1081-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1081-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1081-112">Requirements</span></span>  
 <span data-ttu-id="b1081-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b1081-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1081-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b1081-114">See Also</span></span>  
 [<span data-ttu-id="b1081-115">ISymUnmanagedAsyncMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="b1081-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
