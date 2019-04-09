---
title: ICorDebugCode::CreateBreakpoint — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d193f9aa4d051baa73944545d28a455495aeda40
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59185773"
---
# <a name="icordebugcodecreatebreakpoint-method"></a><span data-ttu-id="91159-102">ICorDebugCode::CreateBreakpoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="91159-102">ICorDebugCode::CreateBreakpoint Method</span></span>
<span data-ttu-id="91159-103">Tworzy punkt przerwania w tym segmencie kodu od określonego przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="91159-103">Creates a breakpoint in this code segment at the specified offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91159-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="91159-104">Syntax</span></span>  
  
```  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91159-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91159-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="91159-106">[in] Przesunięcie, przy którym chcesz utworzyć punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="91159-106">[in] The offset at which to create the breakpoint.</span></span>  
  
 `ppBreakpoint`  
 <span data-ttu-id="91159-107">[out] Wskaźnik na adres obiektu "icordebugfunctionbreakpoint —", który reprezentuje punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="91159-107">[out] A pointer to the address of an "ICorDebugFunctionBreakpoint" object that represents the breakpoint.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91159-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="91159-108">Remarks</span></span>  
 <span data-ttu-id="91159-109">Zanim punkt przerwania jest aktywna, należy dodać do obiektu procesu.</span><span class="sxs-lookup"><span data-stu-id="91159-109">Before the breakpoint is active, it must be added to the process object.</span></span>  
  
 <span data-ttu-id="91159-110">Jeśli ten kod jest kod intermediate language (MSIL) firmy Microsoft, a istnieje just-in-time (JIT)-skompilowanego, natywne wersję kodu, punkt przerwania zostaną zastosowane również kod kompilowany dokładnie na czas.</span><span class="sxs-lookup"><span data-stu-id="91159-110">If this code is Microsoft intermediate language (MSIL) code, and there is a just-in-time (JIT)-compiled, native version of the code, the breakpoint will be applied in the JIT-compiled code as well.</span></span> <span data-ttu-id="91159-111">(Taka sama jest wartość true, jeśli kod jest kompilowany dokładnie na czas później).</span><span class="sxs-lookup"><span data-stu-id="91159-111">(The same is true if the code is JIT-compiled later.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91159-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="91159-112">Requirements</span></span>  
 <span data-ttu-id="91159-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91159-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91159-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91159-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91159-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91159-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="91159-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="91159-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="91159-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91159-117">See also</span></span>
