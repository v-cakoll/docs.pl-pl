---
title: ICorDebugNativeFrame::CanSetIP — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type:
- apiref
ms.openlocfilehash: b3758ac1a84092b8bf2678f9cc2c19c9d9961690
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137325"
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="2a564-102">ICorDebugNativeFrame::CanSetIP — Metoda</span><span class="sxs-lookup"><span data-stu-id="2a564-102">ICorDebugNativeFrame::CanSetIP Method</span></span>
<span data-ttu-id="2a564-103">Pobiera wartość HRESULT, która wskazuje, czy można bezpiecznie ustawić wskaźnik instrukcji (IP) na określoną lokalizację przesunięcia w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="2a564-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a564-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a564-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a564-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2a564-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="2a564-106">podczas Odpowiednie ustawienie wskaźnika instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2a564-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a564-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2a564-107">Remarks</span></span>  
 <span data-ttu-id="2a564-108">Przed wywołaniem metody [ICorDebugNativeFrame:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) użyj metody `CanSetIP`.</span><span class="sxs-lookup"><span data-stu-id="2a564-108">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="2a564-109">Jeśli `CanSetIP` zwraca wszystkie HRESULT inne niż S_OK, nadal można wywołać `ICorDebugNativeFrame::SetIP`, ale nie ma gwarancji, że debuger będzie kontynuował bezpieczne i prawidłowe wykonywanie debugowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="2a564-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a564-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2a564-110">Requirements</span></span>  
 <span data-ttu-id="2a564-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a564-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a564-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2a564-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a564-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2a564-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a564-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a564-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a564-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a564-115">See also</span></span>
