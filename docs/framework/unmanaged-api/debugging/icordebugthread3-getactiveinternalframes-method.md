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
ms.openlocfilehash: 680af5afa3ebef5bcaf9e34580e421dcc8093aaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178464"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a><span data-ttu-id="e2cdc-102">ICorDebugThread3::GetActiveInternalFrames — Metoda</span><span class="sxs-lookup"><span data-stu-id="e2cdc-102">ICorDebugThread3::GetActiveInternalFrames Method</span></span>
<span data-ttu-id="e2cdc-103">Zwraca tablicę ramek wewnętrznych[(Obiekty ICorDebugInternalFrame2)](icordebuginternalframe2-interface.md) na stosie.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-103">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2cdc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e2cdc-104">Syntax</span></span>  
  
```cpp
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2cdc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2cdc-105">Parameters</span></span>  
 `cInternalFrames`  
 <span data-ttu-id="e2cdc-106">[w] Liczba ramek wewnętrznych oczekiwanych w pliku `ppInternalFrames`.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-106">[in] The number of internal frames expected in `ppInternalFrames`.</span></span>  
  
 `pcInternalFrames`  
 <span data-ttu-id="e2cdc-107">[na zewnątrz] Wskaźnik do, `ULONG32` który zawiera liczbę klatek wewnętrznych na stosie.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-107">[out] A pointer to a `ULONG32` that contains the number of internal frames on the stack.</span></span>  
  
 `ppInternalFrames`  
 <span data-ttu-id="e2cdc-108">[w, na zewnątrz] Wskaźnik do adresu tablicy ramek wewnętrznych na stosie.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-108">[in, out] A pointer to the address of an array of internal frames on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2cdc-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e2cdc-109">Return Value</span></span>  
 <span data-ttu-id="e2cdc-110">Ta metoda zwraca następujące specyficzne HRESULTs, a także błędy HRESULT, które wskazują na niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e2cdc-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e2cdc-111">HRESULT</span></span>|<span data-ttu-id="e2cdc-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e2cdc-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e2cdc-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="e2cdc-113">S_OK</span></span>|<span data-ttu-id="e2cdc-114">Obiekt [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) został pomyślnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-114">The [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) object was successfully created.</span></span>|  
|<span data-ttu-id="e2cdc-115">E_invalidarg</span><span class="sxs-lookup"><span data-stu-id="e2cdc-115">E_INVALIDARG</span></span>|<span data-ttu-id="e2cdc-116">`cInternalFrames`nie jest `ppInternalFrames` zerowa `pcInternalFrames` i `null`jest `null`, lub jest .</span><span class="sxs-lookup"><span data-stu-id="e2cdc-116">`cInternalFrames` is not zero and `ppInternalFrames` is `null`, or `pcInternalFrames` is `null`.</span></span>|  
|<span data-ttu-id="e2cdc-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="e2cdc-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="e2cdc-118">`ppInternalFrames`jest mniejsza niż liczba klatek wewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-118">`ppInternalFrames` is smaller than the count of internal frames.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="e2cdc-119">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="e2cdc-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2cdc-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e2cdc-120">Remarks</span></span>  
 <span data-ttu-id="e2cdc-121">Ramki wewnętrzne są struktury danych wypchnięte do stosu przez środowisko wykonawcze do przechowywania danych tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-121">Internal frames are data structures pushed onto the stack by the runtime to store temporary data.</span></span>  
  
 <span data-ttu-id="e2cdc-122">Podczas pierwszego `GetActiveInternalFrames`wywołania należy `cInternalFrames` ustawić parametr na 0 `ppInternalFrames` (zero), a parametr na wartość null.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-122">When you first call `GetActiveInternalFrames`, you should set the `cInternalFrames` parameter to 0 (zero), and the `ppInternalFrames` parameter to null.</span></span> <span data-ttu-id="e2cdc-123">Po `GetActiveInternalFrames` pierwszym `pcInternalFrames` zwraca, zawiera liczbę ramek wewnętrznych na stosie.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-123">When `GetActiveInternalFrames` first returns, `pcInternalFrames` contains the count of the internal frames on the stack.</span></span>  
  
 <span data-ttu-id="e2cdc-124">`GetActiveInternalFrames`następnie należy nazwać po raz drugi.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-124">`GetActiveInternalFrames` should then be called a second time.</span></span> <span data-ttu-id="e2cdc-125">Należy przekazać właściwą`pcInternalFrames`liczbę ( `cInternalFrames` ) w parametrze i określić `ppInternalFrames`wskaźnik do tablicy o odpowiednim rozmiarze w .</span><span class="sxs-lookup"><span data-stu-id="e2cdc-125">You should pass the proper count (`pcInternalFrames`) in the `cInternalFrames` parameter, and specify a pointer to an appropriately sized array in `ppInternalFrames`.</span></span>  
  
 <span data-ttu-id="e2cdc-126">Użyj [metody ICorDebugStackWalk::GetFrame,](icordebugthread3-getactiveinternalframes-method.md) aby zwrócić rzeczywiste ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-126">Use the [ICorDebugStackWalk::GetFrame](icordebugthread3-getactiveinternalframes-method.md) method to return actual stack frames.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2cdc-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e2cdc-127">Requirements</span></span>  
 <span data-ttu-id="e2cdc-128">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2cdc-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2cdc-129">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e2cdc-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2cdc-130">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2cdc-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2cdc-131">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2cdc-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2cdc-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e2cdc-132">See also</span></span>

- [<span data-ttu-id="e2cdc-133">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="e2cdc-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e2cdc-134">Debugging</span><span class="sxs-lookup"><span data-stu-id="e2cdc-134">Debugging</span></span>](index.md)
