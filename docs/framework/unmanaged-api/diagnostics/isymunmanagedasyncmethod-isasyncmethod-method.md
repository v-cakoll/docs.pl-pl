---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod — Metoda
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f5bf8252986ffa90ea5380d5342595cb91e5419
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="5c789-102">ISymUnmanagedAsyncMethod::IsAsyncMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="5c789-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="5c789-103">Sprawdza, czy metoda ma informacje o asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="5c789-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="5c789-104">Jeśli ta metoda zwraca `FALSE` , a następnie jest wywoływać inne metody w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="5c789-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="5c789-105">One będą zwracane wszystkie `E_UNEXPECTED` w takim przypadku.</span><span class="sxs-lookup"><span data-stu-id="5c789-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c789-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c789-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c789-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c789-107">Parameters</span></span>  
  
|<span data-ttu-id="5c789-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="5c789-108">Parameter</span></span>|<span data-ttu-id="5c789-109">Opis</span><span class="sxs-lookup"><span data-stu-id="5c789-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="5c789-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5c789-110">Return Value</span></span>  
 <span data-ttu-id="5c789-111">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="5c789-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c789-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5c789-112">Requirements</span></span>  
 <span data-ttu-id="5c789-113">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5c789-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c789-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c789-114">See Also</span></span>  
 [<span data-ttu-id="5c789-115">ISymUnmanagedAsyncMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="5c789-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
