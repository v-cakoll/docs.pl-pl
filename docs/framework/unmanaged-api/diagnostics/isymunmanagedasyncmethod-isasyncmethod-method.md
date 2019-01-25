---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod — Metoda
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 049f8e4d04498b70533134c01765af2d996d86dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499109"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="729de-102">ISymUnmanagedAsyncMethod::IsAsyncMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="729de-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="729de-103">Sprawdza, czy metoda ma informacje o asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="729de-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="729de-104">Jeśli ta metoda zwraca `FALSE` to wywoływać wszelkich innych metod, w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="729de-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="729de-105">Będą oni mogli zwrócenia wszystkich `E_UNEXPECTED` w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="729de-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="729de-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="729de-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="729de-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="729de-107">Parameters</span></span>  
  
|<span data-ttu-id="729de-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="729de-108">Parameter</span></span>|<span data-ttu-id="729de-109">Opis</span><span class="sxs-lookup"><span data-stu-id="729de-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="729de-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="729de-110">Return Value</span></span>  
 <span data-ttu-id="729de-111">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="729de-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="729de-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="729de-112">Requirements</span></span>  
 <span data-ttu-id="729de-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="729de-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="729de-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="729de-114">See also</span></span>
- [<span data-ttu-id="729de-115">ISymUnmanagedAsyncMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="729de-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
