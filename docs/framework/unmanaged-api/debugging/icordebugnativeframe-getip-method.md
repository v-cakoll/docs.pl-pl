---
title: "ICorDebugNativeFrame::GetIP — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame.GetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2f9ea20577b3132a2378013e7c5fa8356c14c8b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframegetip-method"></a><span data-ttu-id="f509a-102">ICorDebugNativeFrame::GetIP — Metoda</span><span class="sxs-lookup"><span data-stu-id="f509a-102">ICorDebugNativeFrame::GetIP Method</span></span>
<span data-ttu-id="f509a-103">Pobiera kod macierzysty przesunięcia lokalizacji, do której jest aktualnie ustawione wskaźnik instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f509a-103">Gets the native code offset location to which the instruction pointer is currently set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f509a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f509a-104">Syntax</span></span>  
  
```  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f509a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f509a-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="f509a-106">[out] Wskaźnik do przesunięcia lokalizacji w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="f509a-106">[out] A pointer to the offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f509a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f509a-107">Remarks</span></span>  
 <span data-ttu-id="f509a-108">Jeśli ramka stosu reprezentowanego przez ten "ICorDebugNativeFrame" jest aktywna, przesunięcie jest adresem następną instrukcję do wykonania.</span><span class="sxs-lookup"><span data-stu-id="f509a-108">If the stack frame that is represented by this "ICorDebugNativeFrame" is active, the offset is the address of the next instruction to be executed.</span></span> <span data-ttu-id="f509a-109">Jeśli ta ramka stosu nie jest aktywne, przesunięcie jest adresem następną instrukcję do wykonania po ponownym uaktywnieniu ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="f509a-109">If this stack frame is not active, the offset is the address of the next instruction to be executed when the stack frame is reactivated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f509a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f509a-110">Requirements</span></span>  
 <span data-ttu-id="f509a-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f509a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f509a-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f509a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f509a-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f509a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f509a-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f509a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f509a-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f509a-115">See Also</span></span>  
 
