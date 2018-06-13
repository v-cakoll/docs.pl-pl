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
ms.openlocfilehash: e06dc35998a2874ed1d2f76725078874817e94d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420098"
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="f63c9-102">ICorDebugProcess::IsTransitionStub — Metoda</span><span class="sxs-lookup"><span data-stu-id="f63c9-102">ICorDebugProcess::IsTransitionStub Method</span></span>
<span data-ttu-id="f63c9-103">Pobiera wartość wskazującą, czy adres znajduje się wewnątrz skrótowa, która spowoduje przejście do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="f63c9-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f63c9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f63c9-104">Syntax</span></span>  
  
```  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f63c9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f63c9-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="f63c9-106">[in] A `CORDB_ADDRESS` wartość, która określa adres jest zagrożona.</span><span class="sxs-lookup"><span data-stu-id="f63c9-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="f63c9-107">[out] Wskaźnik do wartość logiczna, która jest `true` , jeśli określony adres znajduje się wewnątrz skrótowa, która spowoduje przejście do zarządzanego kodu; w przeciwnym razie \*`pbTransitionStub` jest `false`.</span><span class="sxs-lookup"><span data-stu-id="f63c9-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise \*`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f63c9-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f63c9-108">Remarks</span></span>  
 <span data-ttu-id="f63c9-109">`IsTransitionStub` Metoda pozwala przez kod niezarządzany wykonywania krokowego podjęcie decyzji dotyczącej powrócić wykonywania krokowego kontroli do zarządzanych stepper.</span><span class="sxs-lookup"><span data-stu-id="f63c9-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="f63c9-110">Można również klas zastępczych przejścia tożsamości, analizując informacje w przenośny plik wykonywalny (PE).</span><span class="sxs-lookup"><span data-stu-id="f63c9-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f63c9-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f63c9-111">Requirements</span></span>  
 <span data-ttu-id="f63c9-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f63c9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f63c9-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f63c9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f63c9-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f63c9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f63c9-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f63c9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
