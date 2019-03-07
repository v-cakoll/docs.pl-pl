---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod — Metoda
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 460d6781405b6042262d50e1aa79ee8c77f781a7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489728"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="7f2ed-102">ISymUnmanagedAsyncMethod::IsAsyncMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="7f2ed-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="7f2ed-103">Sprawdza, czy metoda ma informacje o asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="7f2ed-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="7f2ed-104">Jeśli ta metoda zwraca `FALSE` to wywoływać wszelkich innych metod, w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="7f2ed-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="7f2ed-105">Będą oni mogli zwrócenia wszystkich `E_UNEXPECTED` w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="7f2ed-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f2ed-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f2ed-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f2ed-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f2ed-107">Parameters</span></span>  
  
|<span data-ttu-id="7f2ed-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="7f2ed-108">Parameter</span></span>|<span data-ttu-id="7f2ed-109">Opis</span><span class="sxs-lookup"><span data-stu-id="7f2ed-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="7f2ed-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7f2ed-110">Return Value</span></span>  
 <span data-ttu-id="7f2ed-111">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="7f2ed-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f2ed-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7f2ed-112">Requirements</span></span>  
 <span data-ttu-id="7f2ed-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7f2ed-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f2ed-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f2ed-114">See also</span></span>
- [<span data-ttu-id="7f2ed-115">ISymUnmanagedAsyncMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="7f2ed-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
