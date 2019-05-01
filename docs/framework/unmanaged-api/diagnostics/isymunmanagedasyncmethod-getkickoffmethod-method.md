---
title: ISymUnmanagedAsyncMethod::GetKickoffMethod — Metoda
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4599d41336778db8ce8dcf3ac567e4e2cc8833e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940208"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="7f5ec-102">ISymUnmanagedAsyncMethod::GetKickoffMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="7f5ec-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="7f5ec-103">Zobacz [DefineKickoffMethod, Metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="7f5ec-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f5ec-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f5ec-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f5ec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f5ec-105">Parameters</span></span>  
  
|<span data-ttu-id="7f5ec-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="7f5ec-106">Parameter</span></span>|<span data-ttu-id="7f5ec-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7f5ec-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="7f5ec-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7f5ec-108">Return Value</span></span>  
 <span data-ttu-id="7f5ec-109">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="7f5ec-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f5ec-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7f5ec-110">Requirements</span></span>  
 <span data-ttu-id="7f5ec-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7f5ec-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f5ec-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f5ec-112">See also</span></span>

- [<span data-ttu-id="7f5ec-113">ISymUnmanagedAsyncMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="7f5ec-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
