---
title: ISymUnmanagedAsyncMethod — Interfejs
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
ms.openlocfilehash: 0b8adba9dbffbdc47bb526cef9aad3ffa4b48065
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129227"
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="581c2-102">ISymUnmanagedAsyncMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="581c2-102">ISymUnmanagedAsyncMethod Interface</span></span>
<span data-ttu-id="581c2-103">Ten interfejs jest uzupełnieniem odczytu do [interfejsu ISymUnmanagedAsyncMethodPropertiesWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="581c2-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="581c2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="581c2-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="581c2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="581c2-105">Methods</span></span>  
 <span data-ttu-id="581c2-106">Ten interfejs zawiera następujące metody:</span><span class="sxs-lookup"><span data-stu-id="581c2-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="581c2-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="581c2-107">Method</span></span>|<span data-ttu-id="581c2-108">Opis</span><span class="sxs-lookup"><span data-stu-id="581c2-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="581c2-109">GetAsyncStepInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="581c2-109">GetAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="581c2-110">Zobacz [DefineAsyncStepInfo —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="581c2-110">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="581c2-111">GetAsyncStepInfoCount, metoda</span><span class="sxs-lookup"><span data-stu-id="581c2-111">GetAsyncStepInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="581c2-112">Zobacz [DefineAsyncStepInfo —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="581c2-112">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="581c2-113">GetCatchHandlerILOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="581c2-113">GetCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="581c2-114">Zobacz [DefineCatchHandlerILOffset —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="581c2-114">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="581c2-115">GetKickoffMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="581c2-115">GetKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="581c2-116">Zobacz [DefineKickoffMethod —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="581c2-116">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="581c2-117">HasCatchHandlerILOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="581c2-117">HasCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="581c2-118">Zobacz [DefineCatchHandlerILOffset —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="581c2-118">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="581c2-119">IsAsyncMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="581c2-119">IsAsyncMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="581c2-120">Sprawdza, czy metoda ma informacje asynchroniczne, czy nie.</span><span class="sxs-lookup"><span data-stu-id="581c2-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="581c2-121">Jeśli ta metoda zwraca `FALSE`, to jest nieprawidłowa, aby wywołać inne metody w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="581c2-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="581c2-122">Wszystkie zwracają `E_UNEXPECTED` w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="581c2-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="581c2-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="581c2-123">Requirements</span></span>  
 <span data-ttu-id="581c2-124">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="581c2-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="581c2-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="581c2-125">See also</span></span>

- [<span data-ttu-id="581c2-126">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="581c2-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
