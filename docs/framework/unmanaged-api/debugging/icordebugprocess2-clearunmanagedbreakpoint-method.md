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
ms.openlocfilehash: e2aaf902afd71a4a81f7d64ef3fec046aacc91fc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792530"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="a9ffb-102">ICorDebugProcess2::ClearUnmanagedBreakpoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="a9ffb-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="a9ffb-103">Usuwa poprzednio ustawiony punkt przerwania pod podanym adresem.</span><span class="sxs-lookup"><span data-stu-id="a9ffb-103">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9ffb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9ffb-104">Syntax</span></span>  
  
```cpp  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9ffb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a9ffb-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="a9ffb-106">podczas Wartość `CORDB_ADDRESS`, która określa adres, pod którym został ustawiony punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="a9ffb-106">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9ffb-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a9ffb-107">Remarks</span></span>  
 <span data-ttu-id="a9ffb-108">Określony punkt przerwania zostałby wcześniej ustawiony przez wcześniejsze wywołanie [ICorDebugProcess2:: SetUnmanagedBreakpoint —](icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="a9ffb-108">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="a9ffb-109">Metodę `ClearUnmanagedBreakpoint` można wywołać, gdy debugowany proces jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="a9ffb-109">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="a9ffb-110">Metoda `ClearUnmanagedBreakpoint` zwraca kod błędu, Jeśli debuger jest dołączony w trybie tylko zarządzanym lub jeśli punkt przerwania nie istnieje pod podanym adresem.</span><span class="sxs-lookup"><span data-stu-id="a9ffb-110">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9ffb-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a9ffb-111">Requirements</span></span>  
 <span data-ttu-id="a9ffb-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9ffb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9ffb-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a9ffb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9ffb-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a9ffb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9ffb-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9ffb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
