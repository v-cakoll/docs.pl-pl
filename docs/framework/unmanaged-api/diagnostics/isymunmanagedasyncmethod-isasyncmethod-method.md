---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod — Metoda
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
ms.openlocfilehash: 91b4c2688dadf12fa4a835a662622267d7831cf8
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441802"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="730ca-102">ISymUnmanagedAsyncMethod::IsAsyncMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="730ca-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="730ca-103">Sprawdza, czy metoda ma informacje asynchroniczne, czy nie.</span><span class="sxs-lookup"><span data-stu-id="730ca-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="730ca-104">Jeśli ta metoda zwróci wartość `FALSE` , jest ona nieprawidłowa do wywołania innych metod w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="730ca-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="730ca-105">Wszystkie zwracają `E_UNEXPECTED` w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="730ca-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="730ca-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="730ca-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="730ca-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="730ca-107">Parameters</span></span>  
  
|<span data-ttu-id="730ca-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="730ca-108">Parameter</span></span>|<span data-ttu-id="730ca-109">Opis</span><span class="sxs-lookup"><span data-stu-id="730ca-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="730ca-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="730ca-110">Return Value</span></span>  
 <span data-ttu-id="730ca-111">Zwraca wartość `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="730ca-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="730ca-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="730ca-112">Requirements</span></span>  
 <span data-ttu-id="730ca-113">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="730ca-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="730ca-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="730ca-114">See also</span></span>

- [<span data-ttu-id="730ca-115">ISymUnmanagedAsyncMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="730ca-115">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
