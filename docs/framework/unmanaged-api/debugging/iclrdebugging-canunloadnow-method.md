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
ms.openlocfilehash: e69957bdc5f70aba361b2574a7f6ebe26d4dd43f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738395"
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="73a72-102">ICLRDebugging::CanUnloadNow — Metoda</span><span class="sxs-lookup"><span data-stu-id="73a72-102">ICLRDebugging::CanUnloadNow Method</span></span>
<span data-ttu-id="73a72-103">Określa, czy biblioteka, który został dostarczony przez [iclrdebugginglibraryprovider —](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interfejsu jest nadal w użyciu lub może być zwolniony.</span><span class="sxs-lookup"><span data-stu-id="73a72-103">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73a72-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="73a72-104">Syntax</span></span>  
  
```cpp  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73a72-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73a72-105">Parameters</span></span>  
 `hmodule`  
 <span data-ttu-id="73a72-106">[in] Adres podstawowy moduł w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="73a72-106">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73a72-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="73a72-107">Return Value</span></span>  
 <span data-ttu-id="73a72-108">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="73a72-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="73a72-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="73a72-109">HRESULT</span></span>|<span data-ttu-id="73a72-110">Opis</span><span class="sxs-lookup"><span data-stu-id="73a72-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="73a72-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="73a72-111">S_OK</span></span>|<span data-ttu-id="73a72-112">Moduł, który odwołuje się do niej `hmodule` może zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="73a72-112">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="73a72-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="73a72-113">S_FALSE</span></span>|<span data-ttu-id="73a72-114">Moduł, który odwołuje się do niej `hmodule` jest nadal w użyciu.</span><span class="sxs-lookup"><span data-stu-id="73a72-114">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="73a72-115">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="73a72-115">COR_E_NOT_CLR</span></span>|<span data-ttu-id="73a72-116">Wskazany modułu nie jest modułem środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="73a72-116">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="73a72-117">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="73a72-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73a72-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="73a72-118">Remarks</span></span>  
 <span data-ttu-id="73a72-119">Ta metoda sprawdza, czy wszystkie wystąpienia elementu `ICorDebug*` wydano interfejsów i żaden wątek nie znajduje się obecnie w wywołaniu [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="73a72-119">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73a72-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73a72-120">Requirements</span></span>  
 <span data-ttu-id="73a72-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73a72-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73a72-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73a72-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73a72-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73a72-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73a72-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73a72-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73a72-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73a72-125">See also</span></span>

- [<span data-ttu-id="73a72-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="73a72-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="73a72-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="73a72-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
