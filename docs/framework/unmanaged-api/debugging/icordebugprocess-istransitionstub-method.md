---
title: ICorDebugProcess::IsTransitionStub — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsTransitionStub
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ec29aa748c437199434fa1394e1a00c82154447
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766872"
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="2a01e-102">ICorDebugProcess::IsTransitionStub — Metoda</span><span class="sxs-lookup"><span data-stu-id="2a01e-102">ICorDebugProcess::IsTransitionStub Method</span></span>
<span data-ttu-id="2a01e-103">Pobiera wartość wskazującą, czy adres znajduje się wewnątrz odcinek, który spowoduje przejście do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="2a01e-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a01e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a01e-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a01e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2a01e-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="2a01e-106">[in] A `CORDB_ADDRESS` wartość, która określa danego adresu.</span><span class="sxs-lookup"><span data-stu-id="2a01e-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="2a01e-107">[out] Wskaźnik na wartość logiczną, która jest `true` Jeśli określony adres znajduje się wewnątrz odcinek, który spowoduje przejście do zarządzanego kodu; w przeciwnym razie \*`pbTransitionStub` jest `false`.</span><span class="sxs-lookup"><span data-stu-id="2a01e-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise \*`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a01e-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2a01e-108">Remarks</span></span>  
 <span data-ttu-id="2a01e-109">`IsTransitionStub` Metoda może służyć przez kod niezarządzany przechodzenia krok po kroku w podjęciu decyzji, przywrócenie kontroli przechodzenia krok po kroku do stepper zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="2a01e-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="2a01e-110">Można również wycinków przejścia tożsamości, analizując informacje zawarte w przenośny plik wykonywalny (PE).</span><span class="sxs-lookup"><span data-stu-id="2a01e-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a01e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2a01e-111">Requirements</span></span>  
 <span data-ttu-id="2a01e-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a01e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a01e-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a01e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a01e-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a01e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a01e-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a01e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
