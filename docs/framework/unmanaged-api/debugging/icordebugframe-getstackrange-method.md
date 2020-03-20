---
title: ICorDebugFrame::GetStackRange — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type:
- apiref
ms.openlocfilehash: 7a35ce025360e0ec8b7085d68e54548026b7c7fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178910"
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="7c0a7-102">ICorDebugFrame::GetStackRange — Metoda</span><span class="sxs-lookup"><span data-stu-id="7c0a7-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="7c0a7-103">Pobiera bezwzględny zakres adresów tej ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="7c0a7-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c0a7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c0a7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c0a7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c0a7-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="7c0a7-106">[na zewnątrz] Wskaźnik do, `CORDB_ADDRESS` który określa adres początkowy ramki stosu `ICorDebugFrame` reprezentowanej przez ten obiekt.</span><span class="sxs-lookup"><span data-stu-id="7c0a7-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="7c0a7-107">[na zewnątrz] Wskaźnik do, `CORDB_ADDRESS` który określa adres końcowy ramki stosu `ICorDebugFrame` reprezentowanej przez ten obiekt.</span><span class="sxs-lookup"><span data-stu-id="7c0a7-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c0a7-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c0a7-108">Remarks</span></span>  
 <span data-ttu-id="7c0a7-109">Zakres adresów stosu jest przydatne do piecing razem przeplotem ślady stosu zebrane z wielu aparatów debugowania.</span><span class="sxs-lookup"><span data-stu-id="7c0a7-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="7c0a7-110">Zakres liczbowy nie zawiera żadnych informacji o zawartości ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="7c0a7-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="7c0a7-111">Ma znaczenie tylko dla porównania lokalizacji ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="7c0a7-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c0a7-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7c0a7-112">Requirements</span></span>  
 <span data-ttu-id="7c0a7-113">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c0a7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c0a7-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c0a7-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c0a7-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c0a7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c0a7-116">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c0a7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
