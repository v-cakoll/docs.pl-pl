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
ms.openlocfilehash: 2b228383c3b393fe43f60d39e59cca37af36233f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212494"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="0205c-102">ICorDebugProcess2::ClearUnmanagedBreakpoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="0205c-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="0205c-103">Usuwa poprzednio ustawiony punkt przerwania pod podanym adresem.</span><span class="sxs-lookup"><span data-stu-id="0205c-103">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0205c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0205c-104">Syntax</span></span>  
  
```cpp  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0205c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0205c-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="0205c-106">podczas `CORDB_ADDRESS`Wartość określająca adres, pod którym został ustawiony punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="0205c-106">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0205c-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0205c-107">Remarks</span></span>  
 <span data-ttu-id="0205c-108">Określony punkt przerwania zostałby wcześniej ustawiony przez wcześniejsze wywołanie [ICorDebugProcess2:: SetUnmanagedBreakpoint —](icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="0205c-108">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="0205c-109">`ClearUnmanagedBreakpoint`Metodę można wywołać, gdy debugowany proces jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="0205c-109">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="0205c-110">`ClearUnmanagedBreakpoint`Metoda zwraca kod błędu, Jeśli debuger jest dołączony w trybie tylko zarządzanym lub jeśli punkt przerwania nie istnieje pod podanym adresem.</span><span class="sxs-lookup"><span data-stu-id="0205c-110">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0205c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0205c-111">Requirements</span></span>  
 <span data-ttu-id="0205c-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0205c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0205c-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0205c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0205c-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0205c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0205c-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0205c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
