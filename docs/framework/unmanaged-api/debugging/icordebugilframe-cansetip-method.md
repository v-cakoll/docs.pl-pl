---
title: ICorDebugILFrame::CanSetIP — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75b28dafae2861a2d33363f95a46bf1abf4cda35
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756574"
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="99a44-102">ICorDebugILFrame::CanSetIP — Metoda</span><span class="sxs-lookup"><span data-stu-id="99a44-102">ICorDebugILFrame::CanSetIP Method</span></span>
<span data-ttu-id="99a44-103">Pobiera wartość HRESULT, która wskazuje, czy można bezpiecznie Ustaw wskaźnik instrukcji do określonej lokalizacji przesunięcia w kodzie Microsoft Intermediate Language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="99a44-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99a44-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="99a44-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99a44-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99a44-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="99a44-106">[in] Odpowiednie ustawienie wskaźnik instrukcji.</span><span class="sxs-lookup"><span data-stu-id="99a44-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99a44-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99a44-107">Remarks</span></span>  
 <span data-ttu-id="99a44-108">Użyj `CanSetIP` metoda przed wywołaniem [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="99a44-108">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="99a44-109">Jeśli `CanSetIP` zwraca wartość HRESULT żadnych innych niż S_OK, nadal mogą wywoływać `ICorDebugILFrame::SetIP`, ale nie ma żadnej gwarancji, że debuger będą nadal bezpiecznego i prawidłowe wykonywanie debugowany kod.</span><span class="sxs-lookup"><span data-stu-id="99a44-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99a44-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="99a44-110">Requirements</span></span>  
 <span data-ttu-id="99a44-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99a44-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99a44-112">**Nagłówek:** CorDebug.idl, CorDebug,h</span><span class="sxs-lookup"><span data-stu-id="99a44-112">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="99a44-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99a44-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99a44-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99a44-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
