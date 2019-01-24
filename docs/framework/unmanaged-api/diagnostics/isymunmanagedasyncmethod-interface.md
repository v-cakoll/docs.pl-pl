---
title: ISymUnmanagedAsyncMethod — Interfejs
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3dd7b351de8e82f9fdbe623505f86b54f6eba68d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694870"
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="c665b-102">ISymUnmanagedAsyncMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c665b-102">ISymUnmanagedAsyncMethod Interface</span></span>
<span data-ttu-id="c665b-103">Ten interfejs jest to uzupełnienie odczytu [ISymUnmanagedAsyncMethodPropertiesWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c665b-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c665b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c665b-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="c665b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c665b-105">Methods</span></span>  
 <span data-ttu-id="c665b-106">Ten interfejs zawiera następujące metody:</span><span class="sxs-lookup"><span data-stu-id="c665b-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="c665b-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="c665b-107">Method</span></span>|<span data-ttu-id="c665b-108">Opis</span><span class="sxs-lookup"><span data-stu-id="c665b-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c665b-109">GetAsyncStepInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="c665b-109">GetAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="c665b-110">Zobacz [DefineAsyncStepInfo, Metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="c665b-110">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="c665b-111">GetAsyncStepInfoCount, metoda</span><span class="sxs-lookup"><span data-stu-id="c665b-111">GetAsyncStepInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="c665b-112">Zobacz [DefineAsyncStepInfo, Metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="c665b-112">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="c665b-113">GetCatchHandlerILOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="c665b-113">GetCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="c665b-114">Zobacz [DefineCatchHandlerILOffset, Metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="c665b-114">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="c665b-115">GetKickoffMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="c665b-115">GetKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="c665b-116">Zobacz [DefineKickoffMethod, Metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="c665b-116">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="c665b-117">HasCatchHandlerILOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="c665b-117">HasCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="c665b-118">Zobacz [DefineCatchHandlerILOffset, Metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="c665b-118">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="c665b-119">IsAsyncMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="c665b-119">IsAsyncMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="c665b-120">Sprawdza, czy metoda ma informacje o asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="c665b-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="c665b-121">Jeśli ta metoda zwraca `FALSE` to wywoływać wszelkich innych metod, w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="c665b-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="c665b-122">Będą oni mogli zwrócenia wszystkich `E_UNEXPECTED` w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="c665b-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c665b-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c665b-123">Requirements</span></span>  
 <span data-ttu-id="c665b-124">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c665b-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c665b-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c665b-125">See also</span></span>
- [<span data-ttu-id="c665b-126">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="c665b-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
