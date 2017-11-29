---
title: "ICorDebugProcess2::ClearUnmanagedBreakpoint — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.ClearUnmanagedBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::ClearUnmanagedBreakpoint
helpviewer_keywords:
- ClearUnmanagedBreakpoint method [.NET Framework debugging]
- ICorDebugProcess2::ClearUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 12ed0fff-7f0e-4d7a-bb70-b3376371f36c
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ca1514eaa916f5e607e49b5a5713763f855d937
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="2136f-102">ICorDebugProcess2::ClearUnmanagedBreakpoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="2136f-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="2136f-103">Usuwa wcześniej ustawiony punkt przerwania pod podanym adresem.</span><span class="sxs-lookup"><span data-stu-id="2136f-103">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2136f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2136f-104">Syntax</span></span>  
  
```  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2136f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2136f-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="2136f-106">[in] A `CORDB_ADDRESS` wartości, który określa adres, pod którym został ustawiony punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="2136f-106">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2136f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2136f-107">Remarks</span></span>  
 <span data-ttu-id="2136f-108">Określony punkt przerwania czy zostały ustawione wcześniej przez wywołanie wcześniejszych [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="2136f-108">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="2136f-109">`ClearUnmanagedBreakpoint` Można wywołać metody uruchomionej debugowanego procesu.</span><span class="sxs-lookup"><span data-stu-id="2136f-109">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="2136f-110">`ClearUnmanagedBreakpoint` Metoda zwraca kod błędu, jeśli debuger jest dołączony w trybie tylko do zarządzanych lub przerwania nie istnieje pod określonym adresem.</span><span class="sxs-lookup"><span data-stu-id="2136f-110">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2136f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2136f-111">Requirements</span></span>  
 <span data-ttu-id="2136f-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2136f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2136f-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2136f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2136f-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2136f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2136f-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2136f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
