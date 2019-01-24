---
title: ICorDebugValueBreakpoint::GetValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValueBreakpoint.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint::GetValue
helpviewer_keywords:
- GetValue method, ICorDebugValueBreakpoint interface [.NET Framework debugging]
- ICorDebugValueBreakpoint::GetValue method [.NET Framework debugging]
ms.assetid: 52a73654-bc47-48b6-b2b1-a4456b10140c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7f0ca805b6f2085498977720cb4cb78dac9afae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54652582"
---
# <a name="icordebugvaluebreakpointgetvalue-method"></a><span data-ttu-id="7e380-102">ICorDebugValueBreakpoint::GetValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="7e380-102">ICorDebugValueBreakpoint::GetValue Method</span></span>
<span data-ttu-id="7e380-103">Pobiera wskaźnik interfejsu do obiektu "ICorDebugValue", który reprezentuje wartość obiektu, na którym ustawiono punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="7e380-103">Gets an interface pointer to an "ICorDebugValue" object that represents the value of the object on which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e380-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7e380-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e380-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e380-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="7e380-106">[out] Wskaźnik na adres `ICorDebugValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="7e380-106">[out] A pointer to the address of an `ICorDebugValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e380-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7e380-107">Requirements</span></span>  
 <span data-ttu-id="7e380-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e380-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e380-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e380-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e380-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e380-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e380-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e380-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e380-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e380-112">See also</span></span>

