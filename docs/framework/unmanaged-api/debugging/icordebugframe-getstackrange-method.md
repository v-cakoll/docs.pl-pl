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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5da87071bc23ac17a3077049cd77f0fb8611439f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413023"
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="e2342-102">ICorDebugFrame::GetStackRange — Metoda</span><span class="sxs-lookup"><span data-stu-id="e2342-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="e2342-103">Pobiera adres bezwzględny zakres tej ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="e2342-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2342-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e2342-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2342-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2342-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="e2342-106">[out] Wskaźnik do `CORDB_ADDRESS` , który określa adres początkowy ramki stosu reprezentowany przez to `ICorDebugFrame` obiektu.</span><span class="sxs-lookup"><span data-stu-id="e2342-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="e2342-107">[out] Wskaźnik do `CORDB_ADDRESS` , który określa adres końcowy ramki stosu reprezentowany przez to `ICorDebugFrame` obiektu.</span><span class="sxs-lookup"><span data-stu-id="e2342-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2342-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e2342-108">Remarks</span></span>  
 <span data-ttu-id="e2342-109">Zakres adresów stosu jest przydatne w przypadku piecing razem śladów stosu przeplotem zebrane z wielu aparaty debugowania.</span><span class="sxs-lookup"><span data-stu-id="e2342-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="e2342-110">Zakres liczb nie zawiera żadnych informacji o zawartości ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="e2342-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="e2342-111">Jest łatwy do rozpoznania tylko do porównania z lokalizacji ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="e2342-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2342-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e2342-112">Requirements</span></span>  
 <span data-ttu-id="e2342-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2342-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2342-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e2342-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2342-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2342-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2342-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2342-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
