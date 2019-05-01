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
ms.openlocfilehash: 38f913b742f7ece2f136454f801ae780124aed87
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987977"
---
# <a name="icordebugnativeframegetip-method"></a><span data-ttu-id="c0126-102">ICorDebugNativeFrame::GetIP — Metoda</span><span class="sxs-lookup"><span data-stu-id="c0126-102">ICorDebugNativeFrame::GetIP Method</span></span>
<span data-ttu-id="c0126-103">Pobiera kodu macierzystego przesunięcia lokalizacji, do której jest aktualnie ustawiona wskaźnik instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c0126-103">Gets the native code offset location to which the instruction pointer is currently set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0126-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c0126-104">Syntax</span></span>  
  
```  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0126-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c0126-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="c0126-106">[out] Wskaźnik do przesunięcia lokalizacji w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="c0126-106">[out] A pointer to the offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0126-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c0126-107">Remarks</span></span>  
 <span data-ttu-id="c0126-108">Jeśli ramka stosu, który jest reprezentowany przez ten icordebugnativeframe "—" jest aktywna, przesunięcie jest adres następnej instrukcji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="c0126-108">If the stack frame that is represented by this "ICorDebugNativeFrame" is active, the offset is the address of the next instruction to be executed.</span></span> <span data-ttu-id="c0126-109">Jeśli tej ramki stosu nie jest aktywny, przesunięcie jest adres następnej instrukcji do wykonania podczas ponownego uaktywniania ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="c0126-109">If this stack frame is not active, the offset is the address of the next instruction to be executed when the stack frame is reactivated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0126-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c0126-110">Requirements</span></span>  
 <span data-ttu-id="c0126-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0126-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0126-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0126-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0126-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0126-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0126-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0126-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0126-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0126-115">See also</span></span>
