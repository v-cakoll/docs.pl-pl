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
ms.openlocfilehash: 7d17ac4230296674381c87851377fcb535837ad3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugnativeframegetip-method"></a><span data-ttu-id="2a913-102">ICorDebugNativeFrame::GetIP — Metoda</span><span class="sxs-lookup"><span data-stu-id="2a913-102">ICorDebugNativeFrame::GetIP Method</span></span>
<span data-ttu-id="2a913-103">Pobiera kod macierzysty przesunięcia lokalizacji, do której jest aktualnie ustawione wskaźnik instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2a913-103">Gets the native code offset location to which the instruction pointer is currently set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a913-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a913-104">Syntax</span></span>  
  
```  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a913-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2a913-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="2a913-106">[out] Wskaźnik do przesunięcia lokalizacji w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="2a913-106">[out] A pointer to the offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a913-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2a913-107">Remarks</span></span>  
 <span data-ttu-id="2a913-108">Jeśli ramka stosu reprezentowanego przez ten "ICorDebugNativeFrame" jest aktywna, przesunięcie jest adresem następną instrukcję do wykonania.</span><span class="sxs-lookup"><span data-stu-id="2a913-108">If the stack frame that is represented by this "ICorDebugNativeFrame" is active, the offset is the address of the next instruction to be executed.</span></span> <span data-ttu-id="2a913-109">Jeśli ta ramka stosu nie jest aktywne, przesunięcie jest adresem następną instrukcję do wykonania po ponownym uaktywnieniu ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="2a913-109">If this stack frame is not active, the offset is the address of the next instruction to be executed when the stack frame is reactivated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a913-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2a913-110">Requirements</span></span>  
 <span data-ttu-id="2a913-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a913-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a913-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a913-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a913-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a913-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a913-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a913-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a913-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a913-115">See Also</span></span>  
 
