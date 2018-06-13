---
title: ISymUnmanagedAsyncMethod::GetKickoffMethod — Metoda
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2f055dc19bf7f40036283102d8cc4549555b992
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424771"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="5cf76-102">ISymUnmanagedAsyncMethod::GetKickoffMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="5cf76-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="5cf76-103">Zobacz [DefineKickoffMethod — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="5cf76-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cf76-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5cf76-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5cf76-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5cf76-105">Parameters</span></span>  
  
|<span data-ttu-id="5cf76-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="5cf76-106">Parameter</span></span>|<span data-ttu-id="5cf76-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5cf76-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="5cf76-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5cf76-108">Return Value</span></span>  
 <span data-ttu-id="5cf76-109">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="5cf76-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cf76-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5cf76-110">Requirements</span></span>  
 <span data-ttu-id="5cf76-111">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5cf76-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cf76-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5cf76-112">See Also</span></span>  
 [<span data-ttu-id="5cf76-113">ISymUnmanagedAsyncMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="5cf76-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
