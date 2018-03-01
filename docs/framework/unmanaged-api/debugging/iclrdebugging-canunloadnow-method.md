---
title: "ICLRDebugging::CanUnloadNow — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRDebugging.CanUnloadNow Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::CanUnloadNow
helpviewer_keywords:
- CanUnloadNow method [.NET Framework debugging]
- ICLRDebugging::CanUnloadNow method [.NET Framework debugging]
ms.assetid: 62e0630c-8cb7-45d2-b622-5a472abfd8cf
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b781db409991b07463002008a834dfb7ac32c9e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="2ccc2-102">ICLRDebugging::CanUnloadNow — Metoda</span><span class="sxs-lookup"><span data-stu-id="2ccc2-102">ICLRDebugging::CanUnloadNow Method</span></span>
<span data-ttu-id="2ccc2-103">Określa, czy biblioteki, który został dostarczony przez [iclrdebugginglibraryprovider —](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interfejsu jest nadal używane lub może zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="2ccc2-103">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ccc2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ccc2-104">Syntax</span></span>  
  
```  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ccc2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ccc2-105">Parameters</span></span>  
 `hmodule`  
 <span data-ttu-id="2ccc2-106">[in] Adres podstawowy modułu w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="2ccc2-106">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ccc2-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2ccc2-107">Return Value</span></span>  
 <span data-ttu-id="2ccc2-108">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="2ccc2-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2ccc2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2ccc2-109">HRESULT</span></span>|<span data-ttu-id="2ccc2-110">Opis</span><span class="sxs-lookup"><span data-stu-id="2ccc2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2ccc2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2ccc2-111">S_OK</span></span>|<span data-ttu-id="2ccc2-112">Moduł, który odwołuje się do niego `hmodule` może zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="2ccc2-112">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="2ccc2-113">WARTOŚCI S_FALSE</span><span class="sxs-lookup"><span data-stu-id="2ccc2-113">S_FALSE</span></span>|<span data-ttu-id="2ccc2-114">Moduł, który odwołuje się do niego `hmodule` jest nadal używane.</span><span class="sxs-lookup"><span data-stu-id="2ccc2-114">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="2ccc2-115">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="2ccc2-115">COR_E_NOT_CLR</span></span>|<span data-ttu-id="2ccc2-116">Wskazany modułu nie jest modułem CLR.</span><span class="sxs-lookup"><span data-stu-id="2ccc2-116">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="2ccc2-117">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="2ccc2-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ccc2-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ccc2-118">Remarks</span></span>  
 <span data-ttu-id="2ccc2-119">Ta metoda sprawdza, czy wszystkie wystąpienia `ICorDebug*` interfejsy zostały zwolnione i wątku nie znajduje się obecnie w wywołaniu [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2ccc2-119">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ccc2-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ccc2-120">Requirements</span></span>  
 <span data-ttu-id="2ccc2-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ccc2-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ccc2-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ccc2-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ccc2-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ccc2-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ccc2-124">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ccc2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ccc2-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ccc2-125">See Also</span></span>  
 [<span data-ttu-id="2ccc2-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2ccc2-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="2ccc2-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="2ccc2-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
