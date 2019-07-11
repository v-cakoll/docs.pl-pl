---
title: ICorDebugNativeFrame::GetIP — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71e9149bafc866f89253c4318ac69f2705431e48
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765301"
---
# <a name="icordebugnativeframegetip-method"></a><span data-ttu-id="91e64-102">ICorDebugNativeFrame::GetIP — Metoda</span><span class="sxs-lookup"><span data-stu-id="91e64-102">ICorDebugNativeFrame::GetIP Method</span></span>
<span data-ttu-id="91e64-103">Pobiera kodu macierzystego przesunięcia lokalizacji, do której jest aktualnie ustawiona wskaźnik instrukcji.</span><span class="sxs-lookup"><span data-stu-id="91e64-103">Gets the native code offset location to which the instruction pointer is currently set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91e64-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="91e64-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91e64-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91e64-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="91e64-106">[out] Wskaźnik do przesunięcia lokalizacji w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="91e64-106">[out] A pointer to the offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91e64-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="91e64-107">Remarks</span></span>  
 <span data-ttu-id="91e64-108">Jeśli ramka stosu, który jest reprezentowany przez ten icordebugnativeframe "—" jest aktywna, przesunięcie jest adres następnej instrukcji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="91e64-108">If the stack frame that is represented by this "ICorDebugNativeFrame" is active, the offset is the address of the next instruction to be executed.</span></span> <span data-ttu-id="91e64-109">Jeśli tej ramki stosu nie jest aktywny, przesunięcie jest adres następnej instrukcji do wykonania podczas ponownego uaktywniania ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="91e64-109">If this stack frame is not active, the offset is the address of the next instruction to be executed when the stack frame is reactivated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91e64-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="91e64-110">Requirements</span></span>  
 <span data-ttu-id="91e64-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91e64-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91e64-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91e64-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91e64-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91e64-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91e64-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91e64-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91e64-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91e64-115">See also</span></span>
