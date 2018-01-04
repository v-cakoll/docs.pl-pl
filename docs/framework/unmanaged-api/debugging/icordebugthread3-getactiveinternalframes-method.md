---
title: "ICorDebugThread3::GetActiveInternalFrames — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread3.GetActiveInternalFrames Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ecfbaeff9416ee8e6541a23bac6ec76f99abd2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread3getactiveinternalframes-method"></a><span data-ttu-id="8724f-102">ICorDebugThread3::GetActiveInternalFrames — Metoda</span><span class="sxs-lookup"><span data-stu-id="8724f-102">ICorDebugThread3::GetActiveInternalFrames Method</span></span>
<span data-ttu-id="8724f-103">Zwraca tablicę wewnętrzny ramki ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) obiektów) na stosie.</span><span class="sxs-lookup"><span data-stu-id="8724f-103">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8724f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8724f-104">Syntax</span></span>  
  
```  
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8724f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8724f-105">Parameters</span></span>  
 `cInternalFrames`  
 <span data-ttu-id="8724f-106">[in] Liczba ramek wewnętrznego w `ppInternalFrames`.</span><span class="sxs-lookup"><span data-stu-id="8724f-106">[in] The number of internal frames expected in `ppInternalFrames`.</span></span>  
  
 `pcInternalFrames`  
 <span data-ttu-id="8724f-107">[out] Wskaźnik do `ULONG32` zawierającą numer wewnętrzny ramek na stosie.</span><span class="sxs-lookup"><span data-stu-id="8724f-107">[out] A pointer to a `ULONG32` that contains the number of internal frames on the stack.</span></span>  
  
 `ppInternalFrames`  
 <span data-ttu-id="8724f-108">[w, out] Wskaźnik do adresu tablicy wewnętrznej ramek na stosie.</span><span class="sxs-lookup"><span data-stu-id="8724f-108">[in, out] A pointer to the address of an array of internal frames on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8724f-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8724f-109">Return Value</span></span>  
 <span data-ttu-id="8724f-110">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="8724f-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8724f-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8724f-111">HRESULT</span></span>|<span data-ttu-id="8724f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8724f-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8724f-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="8724f-113">S_OK</span></span>|<span data-ttu-id="8724f-114">[ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) obiekt został utworzony pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8724f-114">The [ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) object was successfully created.</span></span>|  
|<span data-ttu-id="8724f-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8724f-115">E_INVALIDARG</span></span>|<span data-ttu-id="8724f-116">`cInternalFrames`nie jest równa zero i `ppInternalFrames` jest `null`, lub `pcInternalFrames` jest `null`.</span><span class="sxs-lookup"><span data-stu-id="8724f-116">`cInternalFrames` is not zero and `ppInternalFrames` is `null`, or `pcInternalFrames` is `null`.</span></span>|  
|<span data-ttu-id="8724f-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="8724f-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="8724f-118">`ppInternalFrames`jest mniejszy niż liczba ramek wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="8724f-118">`ppInternalFrames` is smaller than the count of internal frames.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="8724f-119">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="8724f-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8724f-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8724f-120">Remarks</span></span>  
 <span data-ttu-id="8724f-121">Wewnętrzny ramki są struktur danych wypychana na stosie przez środowisko uruchomieniowe do przechowywania danych tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="8724f-121">Internal frames are data structures pushed onto the stack by the runtime to store temporary data.</span></span>  
  
 <span data-ttu-id="8724f-122">Po pierwsze wywołanie `GetActiveInternalFrames`, należy ustawić `cInternalFrames` parametru na wartość 0 (zero) i `ppInternalFrames` parametru na wartość null.</span><span class="sxs-lookup"><span data-stu-id="8724f-122">When you first call `GetActiveInternalFrames`, you should set the `cInternalFrames` parameter to 0 (zero), and the `ppInternalFrames` parameter to null.</span></span> <span data-ttu-id="8724f-123">Gdy `GetActiveInternalFrames` zwraca najpierw `pcInternalFrames` zawiera liczbę wewnętrzny ramek na stosie.</span><span class="sxs-lookup"><span data-stu-id="8724f-123">When `GetActiveInternalFrames` first returns, `pcInternalFrames` contains the count of the internal frames on the stack.</span></span>  
  
 <span data-ttu-id="8724f-124">`GetActiveInternalFrames`należy następnie wywołać po raz drugi.</span><span class="sxs-lookup"><span data-stu-id="8724f-124">`GetActiveInternalFrames` should then be called a second time.</span></span> <span data-ttu-id="8724f-125">Należy przekazać odpowiednie liczby (`pcInternalFrames`) w `cInternalFrames` parametru, i określić wskaźnik do tablicy odpowiednio rozmiarze w `ppInternalFrames`.</span><span class="sxs-lookup"><span data-stu-id="8724f-125">You should pass the proper count (`pcInternalFrames`) in the `cInternalFrames` parameter, and specify a pointer to an appropriately sized array in `ppInternalFrames`.</span></span>  
  
 <span data-ttu-id="8724f-126">Użyj [ICorDebugStackWalk::GetFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) metody do zwrócenia rzeczywistego ramek na stosie.</span><span class="sxs-lookup"><span data-stu-id="8724f-126">Use the [ICorDebugStackWalk::GetFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return actual stack frames.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8724f-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8724f-127">Requirements</span></span>  
 <span data-ttu-id="8724f-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8724f-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8724f-129">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8724f-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8724f-130">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8724f-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8724f-131">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8724f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8724f-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8724f-132">See Also</span></span>  
 [<span data-ttu-id="8724f-133">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8724f-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8724f-134">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="8724f-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
