---
title: "ICorDebugNativeFrame::CanSetIP — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b87ff9ae71b916a9a1141c2e5fedce7f79fbcd23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="f9594-102">ICorDebugNativeFrame::CanSetIP — Metoda</span><span class="sxs-lookup"><span data-stu-id="f9594-102">ICorDebugNativeFrame::CanSetIP Method</span></span>
<span data-ttu-id="f9594-103">Pobiera wartość HRESULT, która wskazuje, czy jest bezpieczne, można ustawić wskaźnika instrukcji (IP) w określonej lokalizacji przesunięcia w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="f9594-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9594-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9594-104">Syntax</span></span>  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9594-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9594-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="f9594-106">[in] Odpowiednie ustawienie wskaźnik instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f9594-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9594-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9594-107">Remarks</span></span>  
 <span data-ttu-id="f9594-108">Użyj `CanSetIP` metoda przed wywołaniem [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="f9594-108">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="f9594-109">Jeśli `CanSetIP` zwraca HRESULT żadnych innych niż S_OK, nadal mogą wywoływać `ICorDebugNativeFrame::SetIP`, ale nie ma żadnej gwarancji, że debuger będzie bezpieczne i prawidłowe wykonywanie kodu debugowany.</span><span class="sxs-lookup"><span data-stu-id="f9594-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9594-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f9594-110">Requirements</span></span>  
 <span data-ttu-id="f9594-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9594-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9594-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9594-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9594-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9594-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9594-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9594-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9594-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9594-115">See Also</span></span>  
 
