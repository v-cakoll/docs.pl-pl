---
title: ISymUnmanagedAsyncMethod — Interfejs
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
ms.openlocfilehash: fef1af75587b889afad9cb5b93d0cd722294006b
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441815"
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="bcc62-102">ISymUnmanagedAsyncMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bcc62-102">ISymUnmanagedAsyncMethod Interface</span></span>
<span data-ttu-id="bcc62-103">Ten interfejs jest uzupełnieniem odczytu do [interfejsu ISymUnmanagedAsyncMethodPropertiesWriter](isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="bcc62-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcc62-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bcc62-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="bcc62-105">Metody</span><span class="sxs-lookup"><span data-stu-id="bcc62-105">Methods</span></span>  
 <span data-ttu-id="bcc62-106">Ten interfejs zawiera następujące metody:</span><span class="sxs-lookup"><span data-stu-id="bcc62-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="bcc62-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="bcc62-107">Method</span></span>|<span data-ttu-id="bcc62-108">Opis</span><span class="sxs-lookup"><span data-stu-id="bcc62-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bcc62-109">GetAsyncStepInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="bcc62-109">GetAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="bcc62-110">Zobacz [DefineAsyncStepInfo —](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="bcc62-110">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="bcc62-111">GetAsyncStepInfoCount, metoda</span><span class="sxs-lookup"><span data-stu-id="bcc62-111">GetAsyncStepInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="bcc62-112">Zobacz [DefineAsyncStepInfo —](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="bcc62-112">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="bcc62-113">GetCatchHandlerILOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="bcc62-113">GetCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="bcc62-114">Zobacz [DefineCatchHandlerILOffset —](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="bcc62-114">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="bcc62-115">GetKickoffMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="bcc62-115">GetKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="bcc62-116">Zobacz [DefineKickoffMethod —](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="bcc62-116">See [DefineKickoffMethod Method](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="bcc62-117">HasCatchHandlerILOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="bcc62-117">HasCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="bcc62-118">Zobacz [DefineCatchHandlerILOffset —](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="bcc62-118">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="bcc62-119">IsAsyncMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="bcc62-119">IsAsyncMethod Method</span></span>](isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="bcc62-120">Sprawdza, czy metoda ma informacje asynchroniczne, czy nie.</span><span class="sxs-lookup"><span data-stu-id="bcc62-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="bcc62-121">Jeśli ta metoda zwróci wartość `FALSE` , jest ona nieprawidłowa do wywołania innych metod w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="bcc62-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="bcc62-122">Wszystkie zwracają `E_UNEXPECTED` w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="bcc62-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bcc62-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bcc62-123">Requirements</span></span>  
 <span data-ttu-id="bcc62-124">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="bcc62-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcc62-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bcc62-125">See also</span></span>

- [<span data-ttu-id="bcc62-126">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="bcc62-126">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
