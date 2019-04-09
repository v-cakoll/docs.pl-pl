---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod — Metoda
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5cddf34f1a6277e966901c9692bff63e26a3b8e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136737"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="c6cea-102">ISymUnmanagedAsyncMethod::IsAsyncMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="c6cea-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="c6cea-103">Sprawdza, czy metoda ma informacje o asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="c6cea-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="c6cea-104">Jeśli ta metoda zwraca `FALSE` to wywoływać wszelkich innych metod, w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="c6cea-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="c6cea-105">Będą oni mogli zwrócenia wszystkich `E_UNEXPECTED` w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="c6cea-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6cea-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c6cea-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6cea-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6cea-107">Parameters</span></span>  
  
|<span data-ttu-id="c6cea-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="c6cea-108">Parameter</span></span>|<span data-ttu-id="c6cea-109">Opis</span><span class="sxs-lookup"><span data-stu-id="c6cea-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="c6cea-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c6cea-110">Return Value</span></span>  
 <span data-ttu-id="c6cea-111">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="c6cea-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6cea-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c6cea-112">Requirements</span></span>  
 <span data-ttu-id="c6cea-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c6cea-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6cea-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c6cea-114">See also</span></span>

- [<span data-ttu-id="c6cea-115">ISymUnmanagedAsyncMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c6cea-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
