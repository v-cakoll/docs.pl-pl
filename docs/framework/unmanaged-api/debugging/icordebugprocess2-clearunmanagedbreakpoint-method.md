---
title: ICorDebugProcess2::ClearUnmanagedBreakpoint — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.ClearUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::ClearUnmanagedBreakpoint
helpviewer_keywords:
- ClearUnmanagedBreakpoint method [.NET Framework debugging]
- ICorDebugProcess2::ClearUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 12ed0fff-7f0e-4d7a-bb70-b3376371f36c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4dcfb977f5ca87f2219fd3ed8ef87d16c2defd2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472654"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="a582e-102">ICorDebugProcess2::ClearUnmanagedBreakpoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="a582e-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="a582e-103">Usuwa wcześniej ustawiony punkt przerwania pod podanym adresem.</span><span class="sxs-lookup"><span data-stu-id="a582e-103">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a582e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a582e-104">Syntax</span></span>  
  
```  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a582e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a582e-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="a582e-106">[in] A `CORDB_ADDRESS` wartość, która określa adres, w którym ustawiono punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="a582e-106">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a582e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a582e-107">Remarks</span></span>  
 <span data-ttu-id="a582e-108">Określony punkt przerwania mogły zostać wcześniej ustawione przez wcześniejsze wywołanie [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="a582e-108">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="a582e-109">`ClearUnmanagedBreakpoint` Metoda może być wywoływana, gdy debugowany proces jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="a582e-109">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="a582e-110">`ClearUnmanagedBreakpoint` Metoda zwraca kod błędu, jeśli jest dołączony debuger w trybie tylko do zarządzanych lub przerwania nie istnieje pod podanym adresem.</span><span class="sxs-lookup"><span data-stu-id="a582e-110">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a582e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a582e-111">Requirements</span></span>  
 <span data-ttu-id="a582e-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a582e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a582e-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a582e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a582e-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a582e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a582e-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a582e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
