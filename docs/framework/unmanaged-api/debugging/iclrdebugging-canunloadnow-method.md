---
title: ICLRDebugging::CanUnloadNow — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 557b53df3669bb0567e4d1261124ac725c796c70
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407477"
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="23a46-102">ICLRDebugging::CanUnloadNow — Metoda</span><span class="sxs-lookup"><span data-stu-id="23a46-102">ICLRDebugging::CanUnloadNow Method</span></span>
<span data-ttu-id="23a46-103">Określa, czy biblioteki, który został dostarczony przez [iclrdebugginglibraryprovider —](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interfejsu jest nadal używane lub może zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="23a46-103">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23a46-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="23a46-104">Syntax</span></span>  
  
```  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23a46-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="23a46-105">Parameters</span></span>  
 `hmodule`  
 <span data-ttu-id="23a46-106">[in] Adres podstawowy modułu w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="23a46-106">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23a46-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="23a46-107">Return Value</span></span>  
 <span data-ttu-id="23a46-108">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="23a46-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="23a46-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="23a46-109">HRESULT</span></span>|<span data-ttu-id="23a46-110">Opis</span><span class="sxs-lookup"><span data-stu-id="23a46-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="23a46-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="23a46-111">S_OK</span></span>|<span data-ttu-id="23a46-112">Moduł, który odwołuje się do niego `hmodule` może zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="23a46-112">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="23a46-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="23a46-113">S_FALSE</span></span>|<span data-ttu-id="23a46-114">Moduł, który odwołuje się do niego `hmodule` jest nadal używane.</span><span class="sxs-lookup"><span data-stu-id="23a46-114">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="23a46-115">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="23a46-115">COR_E_NOT_CLR</span></span>|<span data-ttu-id="23a46-116">Wskazany modułu nie jest modułem CLR.</span><span class="sxs-lookup"><span data-stu-id="23a46-116">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="23a46-117">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="23a46-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23a46-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="23a46-118">Remarks</span></span>  
 <span data-ttu-id="23a46-119">Ta metoda sprawdza, czy wszystkie wystąpienia `ICorDebug*` interfejsy zostały zwolnione i wątku nie znajduje się obecnie w wywołaniu [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="23a46-119">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23a46-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="23a46-120">Requirements</span></span>  
 <span data-ttu-id="23a46-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23a46-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23a46-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23a46-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23a46-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23a46-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23a46-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23a46-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23a46-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23a46-125">See Also</span></span>  
 [<span data-ttu-id="23a46-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="23a46-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="23a46-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="23a46-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
