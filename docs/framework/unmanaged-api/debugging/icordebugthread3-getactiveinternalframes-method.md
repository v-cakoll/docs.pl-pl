---
title: ICorDebugThread3::GetActiveInternalFrames — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.GetActiveInternalFrames Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e264f2361c739536d15fbf31d366db74e107bac2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085106"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a><span data-ttu-id="b858d-102">ICorDebugThread3::GetActiveInternalFrames — Metoda</span><span class="sxs-lookup"><span data-stu-id="b858d-102">ICorDebugThread3::GetActiveInternalFrames Method</span></span>
<span data-ttu-id="b858d-103">Zwraca informacje o ramkach wewnętrznych ([icordebuginternalframe2 —](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) obiektów) na stosie.</span><span class="sxs-lookup"><span data-stu-id="b858d-103">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b858d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b858d-104">Syntax</span></span>  
  
```  
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a><span data-ttu-id="b858d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b858d-105">Parameters</span></span>  
 `cInternalFrames`  
 <span data-ttu-id="b858d-106">[in] Liczba oczekiwana w ramkach wewnętrznych `ppInternalFrames`.</span><span class="sxs-lookup"><span data-stu-id="b858d-106">[in] The number of internal frames expected in `ppInternalFrames`.</span></span>  
  
 `pcInternalFrames`  
 <span data-ttu-id="b858d-107">[out] Wskaźnik do `ULONG32` zawiera numer wewnętrzny ramek na stosie.</span><span class="sxs-lookup"><span data-stu-id="b858d-107">[out] A pointer to a `ULONG32` that contains the number of internal frames on the stack.</span></span>  
  
 `ppInternalFrames`  
 <span data-ttu-id="b858d-108">[out w] Wskaźnik na adres tablicę wewnętrznego ramek na stosie.</span><span class="sxs-lookup"><span data-stu-id="b858d-108">[in, out] A pointer to the address of an array of internal frames on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b858d-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b858d-109">Return Value</span></span>  
 <span data-ttu-id="b858d-110">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="b858d-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b858d-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b858d-111">HRESULT</span></span>|<span data-ttu-id="b858d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b858d-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b858d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b858d-113">S_OK</span></span>|<span data-ttu-id="b858d-114">[Icordebuginternalframe2 —](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) obiekt został pomyślnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="b858d-114">The [ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) object was successfully created.</span></span>|  
|<span data-ttu-id="b858d-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b858d-115">E_INVALIDARG</span></span>|`cInternalFrames` <span data-ttu-id="b858d-116">nie jest równa zero i `ppInternalFrames` jest `null`, lub `pcInternalFrames` jest `null`.</span><span class="sxs-lookup"><span data-stu-id="b858d-116">is not zero and `ppInternalFrames` is `null`, or `pcInternalFrames` is `null`.</span></span>|  
|<span data-ttu-id="b858d-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="b858d-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|`ppInternalFrames` <span data-ttu-id="b858d-118">jest mniejsza niż liczba o ramkach wewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="b858d-118">is smaller than the count of internal frames.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="b858d-119">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="b858d-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b858d-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b858d-120">Remarks</span></span>  
 <span data-ttu-id="b858d-121">Wewnętrzny ramki są strukturami danych wypychane na stosie przez środowisko uruchomieniowe będzie zapisywał dane tymczasowe.</span><span class="sxs-lookup"><span data-stu-id="b858d-121">Internal frames are data structures pushed onto the stack by the runtime to store temporary data.</span></span>  
  
 <span data-ttu-id="b858d-122">Po pierwsze wywołanie `GetActiveInternalFrames`, należy ustawić `cInternalFrames` parametru na wartość 0 (zero), a `ppInternalFrames` parametru na wartość null.</span><span class="sxs-lookup"><span data-stu-id="b858d-122">When you first call `GetActiveInternalFrames`, you should set the `cInternalFrames` parameter to 0 (zero), and the `ppInternalFrames` parameter to null.</span></span> <span data-ttu-id="b858d-123">Gdy `GetActiveInternalFrames` zwraca najpierw `pcInternalFrames` zawiera liczbę wewnętrznych ramek na stosie.</span><span class="sxs-lookup"><span data-stu-id="b858d-123">When `GetActiveInternalFrames` first returns, `pcInternalFrames` contains the count of the internal frames on the stack.</span></span>  
  
 `GetActiveInternalFrames` <span data-ttu-id="b858d-124">powinien być wywoływany po raz drugi.</span><span class="sxs-lookup"><span data-stu-id="b858d-124">should then be called a second time.</span></span> <span data-ttu-id="b858d-125">Należy przekazać odpowiednie liczba (`pcInternalFrames`) w `cInternalFrames` parametru, a następnie określ wskaźnik do tablicy właściwy rozmiar w `ppInternalFrames`.</span><span class="sxs-lookup"><span data-stu-id="b858d-125">You should pass the proper count (`pcInternalFrames`) in the `cInternalFrames` parameter, and specify a pointer to an appropriately sized array in `ppInternalFrames`.</span></span>  
  
 <span data-ttu-id="b858d-126">Użyj [ICorDebugStackWalk::GetFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) metodę, aby zwracać rzeczywista ramek stosu.</span><span class="sxs-lookup"><span data-stu-id="b858d-126">Use the [ICorDebugStackWalk::GetFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return actual stack frames.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b858d-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b858d-127">Requirements</span></span>  
 <span data-ttu-id="b858d-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b858d-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b858d-129">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b858d-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b858d-130">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b858d-130">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b858d-131">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b858d-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b858d-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b858d-132">See also</span></span>

- [<span data-ttu-id="b858d-133">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="b858d-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b858d-134">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b858d-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
