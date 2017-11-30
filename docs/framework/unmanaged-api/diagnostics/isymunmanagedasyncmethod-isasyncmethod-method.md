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
ms.openlocfilehash: ce91552d7468579d9941c1da75c4d281999d66fd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="06ea0-102">ISymUnmanagedAsyncMethod::IsAsyncMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="06ea0-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="06ea0-103">Sprawdza, czy metoda ma informacje o asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="06ea0-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="06ea0-104">Jeśli ta metoda zwraca `FALSE` , a następnie jest wywoływać inne metody w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="06ea0-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="06ea0-105">One będą zwracane wszystkie `E_UNEXPECTED` w takim przypadku.</span><span class="sxs-lookup"><span data-stu-id="06ea0-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06ea0-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="06ea0-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="06ea0-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="06ea0-107">Parameters</span></span>  
  
|<span data-ttu-id="06ea0-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="06ea0-108">Parameter</span></span>|<span data-ttu-id="06ea0-109">Opis</span><span class="sxs-lookup"><span data-stu-id="06ea0-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="06ea0-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="06ea0-110">Return Value</span></span>  
 <span data-ttu-id="06ea0-111">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="06ea0-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06ea0-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="06ea0-112">Requirements</span></span>  
 <span data-ttu-id="06ea0-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="06ea0-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06ea0-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06ea0-114">See Also</span></span>  
 [<span data-ttu-id="06ea0-115">Isymunmanagedasyncmethod — interfejs</span><span class="sxs-lookup"><span data-stu-id="06ea0-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
