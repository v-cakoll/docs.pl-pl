---
title: ISymUnmanagedAsyncMethod::GetKickoffMethod — Metoda
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84aef2b26e008d1a3c6d95d7ec1e130ab0594a11
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484553"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="50a09-102">ISymUnmanagedAsyncMethod::GetKickoffMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="50a09-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="50a09-103">Zobacz [DefineKickoffMethod, Metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="50a09-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50a09-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="50a09-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50a09-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="50a09-105">Parameters</span></span>  
  
|<span data-ttu-id="50a09-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="50a09-106">Parameter</span></span>|<span data-ttu-id="50a09-107">Opis</span><span class="sxs-lookup"><span data-stu-id="50a09-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="50a09-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="50a09-108">Return Value</span></span>  
 <span data-ttu-id="50a09-109">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="50a09-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50a09-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="50a09-110">Requirements</span></span>  
 <span data-ttu-id="50a09-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="50a09-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50a09-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50a09-112">See also</span></span>
- [<span data-ttu-id="50a09-113">ISymUnmanagedAsyncMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="50a09-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
