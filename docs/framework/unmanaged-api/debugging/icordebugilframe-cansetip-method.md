---
title: "ICorDebugILFrame::CanSetIP — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.CanSetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 22d0df9add0a4ce35b1a590d65e30a6756fec49c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="66748-102">ICorDebugILFrame::CanSetIP — Metoda</span><span class="sxs-lookup"><span data-stu-id="66748-102">ICorDebugILFrame::CanSetIP Method</span></span>
<span data-ttu-id="66748-103">Pobiera wartość HRESULT, która wskazuje, czy jest bezpieczne, można ustawić wskaźnika instrukcji w określonej lokalizacji przesunięcia w kodzie Microsoft języka pośredniego (MSIL).</span><span class="sxs-lookup"><span data-stu-id="66748-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66748-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="66748-104">Syntax</span></span>  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66748-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66748-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="66748-106">[in] Odpowiednie ustawienie wskaźnik instrukcji.</span><span class="sxs-lookup"><span data-stu-id="66748-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66748-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="66748-107">Remarks</span></span>  
 <span data-ttu-id="66748-108">Użyj `CanSetIP` metoda przed wywołaniem [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="66748-108">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="66748-109">Jeśli `CanSetIP` zwraca HRESULT żadnych innych niż S_OK, nadal mogą wywoływać `ICorDebugILFrame::SetIP`, ale nie ma żadnej gwarancji, że debuger będzie bezpieczne i prawidłowe wykonywanie kodu debugowany.</span><span class="sxs-lookup"><span data-stu-id="66748-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66748-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="66748-110">Requirements</span></span>  
 <span data-ttu-id="66748-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66748-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66748-112">**Nagłówek:** CorDebug.idl, CorDebug, h</span><span class="sxs-lookup"><span data-stu-id="66748-112">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="66748-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66748-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66748-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66748-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
