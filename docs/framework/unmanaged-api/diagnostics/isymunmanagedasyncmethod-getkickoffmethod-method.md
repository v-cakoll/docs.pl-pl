---
title: ISymUnmanagedAsyncMethod::GetKickoffMethod — Metoda
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4599d41336778db8ce8dcf3ac567e4e2cc8833e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174944"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="b7689-102">ISymUnmanagedAsyncMethod::GetKickoffMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="b7689-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="b7689-103">Zobacz [DefineKickoffMethod, Metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="b7689-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7689-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b7689-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7689-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7689-105">Parameters</span></span>  
  
|<span data-ttu-id="b7689-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="b7689-106">Parameter</span></span>|<span data-ttu-id="b7689-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b7689-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="b7689-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b7689-108">Return Value</span></span>  
 <span data-ttu-id="b7689-109">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="b7689-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7689-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b7689-110">Requirements</span></span>  
 <span data-ttu-id="b7689-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b7689-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7689-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b7689-112">See also</span></span>

- [<span data-ttu-id="b7689-113">ISymUnmanagedAsyncMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7689-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
