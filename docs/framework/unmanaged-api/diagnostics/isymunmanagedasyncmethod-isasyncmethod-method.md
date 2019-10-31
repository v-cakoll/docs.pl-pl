---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod — Metoda
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
ms.openlocfilehash: 0ea4c21e9e6a49d7bbbad5e1853598c440cd6410
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129208"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="865d3-102">ISymUnmanagedAsyncMethod::IsAsyncMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="865d3-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="865d3-103">Sprawdza, czy metoda ma informacje asynchroniczne, czy nie.</span><span class="sxs-lookup"><span data-stu-id="865d3-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="865d3-104">Jeśli ta metoda zwraca `FALSE`, to jest nieprawidłowa, aby wywołać inne metody w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="865d3-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="865d3-105">Wszystkie zwracają `E_UNEXPECTED` w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="865d3-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="865d3-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="865d3-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="865d3-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="865d3-107">Parameters</span></span>  
  
|<span data-ttu-id="865d3-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="865d3-108">Parameter</span></span>|<span data-ttu-id="865d3-109">Opis</span><span class="sxs-lookup"><span data-stu-id="865d3-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="865d3-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="865d3-110">Return Value</span></span>  
 <span data-ttu-id="865d3-111">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="865d3-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="865d3-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="865d3-112">Requirements</span></span>  
 <span data-ttu-id="865d3-113">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="865d3-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="865d3-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="865d3-114">See also</span></span>

- [<span data-ttu-id="865d3-115">ISymUnmanagedAsyncMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="865d3-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
