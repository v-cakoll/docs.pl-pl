---
title: "ISymUnmanagedAsyncMethod — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3ee944940cef0d3162a020c81353fd6b8cfb82f8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="e895b-102">ISymUnmanagedAsyncMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e895b-102">ISymUnmanagedAsyncMethod Interface</span></span>
<span data-ttu-id="e895b-103">Ten interfejs jest uzupełnienie odczytu [isymunmanagedasyncmethodpropertieswriter — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e895b-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e895b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e895b-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="e895b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e895b-105">Methods</span></span>  
 <span data-ttu-id="e895b-106">Ten interfejs zawiera następujące metody:</span><span class="sxs-lookup"><span data-stu-id="e895b-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="e895b-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="e895b-107">Method</span></span>|<span data-ttu-id="e895b-108">Opis</span><span class="sxs-lookup"><span data-stu-id="e895b-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e895b-109">GetAsyncStepInfo — metoda</span><span class="sxs-lookup"><span data-stu-id="e895b-109">GetAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="e895b-110">Zobacz [DefineAsyncStepInfo — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="e895b-110">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="e895b-111">GetAsyncStepInfoCount — metoda</span><span class="sxs-lookup"><span data-stu-id="e895b-111">GetAsyncStepInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="e895b-112">Zobacz [DefineAsyncStepInfo — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="e895b-112">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="e895b-113">GetCatchHandlerILOffset — metoda</span><span class="sxs-lookup"><span data-stu-id="e895b-113">GetCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="e895b-114">Zobacz [DefineCatchHandlerILOffset — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="e895b-114">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="e895b-115">GetKickoffMethod — metoda</span><span class="sxs-lookup"><span data-stu-id="e895b-115">GetKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="e895b-116">Zobacz [DefineKickoffMethod — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="e895b-116">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="e895b-117">HasCatchHandlerILOffset — metoda</span><span class="sxs-lookup"><span data-stu-id="e895b-117">HasCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="e895b-118">Zobacz [DefineCatchHandlerILOffset — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="e895b-118">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="e895b-119">IsAsyncMethod — metoda</span><span class="sxs-lookup"><span data-stu-id="e895b-119">IsAsyncMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="e895b-120">Sprawdza, czy metoda ma informacje o asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="e895b-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="e895b-121">Jeśli ta metoda zwraca `FALSE` , a następnie jest wywoływać inne metody w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="e895b-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="e895b-122">One będą zwracane wszystkie `E_UNEXPECTED` w takim przypadku.</span><span class="sxs-lookup"><span data-stu-id="e895b-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e895b-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e895b-123">Requirements</span></span>  
 <span data-ttu-id="e895b-124">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e895b-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e895b-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e895b-125">See Also</span></span>  
 [<span data-ttu-id="e895b-126">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="e895b-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
