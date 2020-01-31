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
ms.openlocfilehash: c6a02b080739d00667893008be4a19b4fa9a6ef2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788594"
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="1be71-102">ICorDebugILFrame::CanSetIP — Metoda</span><span class="sxs-lookup"><span data-stu-id="1be71-102">ICorDebugILFrame::CanSetIP Method</span></span>
<span data-ttu-id="1be71-103">Pobiera wartość HRESULT, która wskazuje, czy można bezpiecznie ustawić wskaźnik instrukcji na określoną lokalizację przesunięcia w kodzie języka pośredniego (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1be71-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1be71-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1be71-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1be71-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1be71-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="1be71-106">podczas Odpowiednie ustawienie wskaźnika instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1be71-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1be71-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1be71-107">Remarks</span></span>  
 <span data-ttu-id="1be71-108">Przed wywołaniem metody [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) użyj metody `CanSetIP`.</span><span class="sxs-lookup"><span data-stu-id="1be71-108">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="1be71-109">Jeśli `CanSetIP` zwraca wszystkie HRESULT inne niż S_OK, można nadal wywoływać `ICorDebugILFrame::SetIP`, ale nie ma żadnej gwarancji, że debuger będzie kontynuował bezpieczne i prawidłowe wykonywanie debugowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="1be71-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1be71-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1be71-110">Requirements</span></span>  
 <span data-ttu-id="1be71-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1be71-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1be71-112">**Nagłówek:** CorDebug. idl, CorDebug, h</span><span class="sxs-lookup"><span data-stu-id="1be71-112">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="1be71-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1be71-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1be71-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1be71-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
