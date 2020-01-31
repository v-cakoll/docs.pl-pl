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
ms.openlocfilehash: 41b2e009f8f017a72147232015ea2357ae922ca1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793655"
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="cfb8a-102">ICLRDebugging::CanUnloadNow — Metoda</span><span class="sxs-lookup"><span data-stu-id="cfb8a-102">ICLRDebugging::CanUnloadNow Method</span></span>
<span data-ttu-id="cfb8a-103">Określa, czy biblioteka, która została dostarczona przez interfejs [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) , jest nadal używana, czy może zostać zwolniona.</span><span class="sxs-lookup"><span data-stu-id="cfb8a-103">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfb8a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cfb8a-104">Syntax</span></span>  
  
```cpp  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfb8a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cfb8a-105">Parameters</span></span>  
 `hmodule`  
 <span data-ttu-id="cfb8a-106">podczas Adres podstawowy modułu w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="cfb8a-106">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cfb8a-107">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="cfb8a-107">Return Value</span></span>  
 <span data-ttu-id="cfb8a-108">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="cfb8a-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="cfb8a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cfb8a-109">HRESULT</span></span>|<span data-ttu-id="cfb8a-110">Opis</span><span class="sxs-lookup"><span data-stu-id="cfb8a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cfb8a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="cfb8a-111">S_OK</span></span>|<span data-ttu-id="cfb8a-112">Moduł, do którego odwołuje się `hmodule`, może zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="cfb8a-112">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="cfb8a-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="cfb8a-113">S_FALSE</span></span>|<span data-ttu-id="cfb8a-114">Moduł, do którego odwołuje się `hmodule`, jest nadal w użyciu.</span><span class="sxs-lookup"><span data-stu-id="cfb8a-114">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="cfb8a-115">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="cfb8a-115">COR_E_NOT_CLR</span></span>|<span data-ttu-id="cfb8a-116">Wskazany moduł nie jest modułem CLR.</span><span class="sxs-lookup"><span data-stu-id="cfb8a-116">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="cfb8a-117">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="cfb8a-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfb8a-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cfb8a-118">Remarks</span></span>  
 <span data-ttu-id="cfb8a-119">Ta metoda sprawdza, czy wydano wszystkie wystąpienia `ICorDebug*` interfejsów i czy żaden wątek nie jest obecnie w wywołaniu metody [ICLRDebugging:: OpenVirtualProcess —](iclrdebugging-openvirtualprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cfb8a-119">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfb8a-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cfb8a-120">Requirements</span></span>  
 <span data-ttu-id="cfb8a-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfb8a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfb8a-122">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cfb8a-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cfb8a-123">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cfb8a-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfb8a-124">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfb8a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfb8a-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cfb8a-125">See also</span></span>

- [<span data-ttu-id="cfb8a-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="cfb8a-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="cfb8a-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="cfb8a-127">Debugging</span></span>](index.md)
