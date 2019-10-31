---
title: ICorDebugController::Detach — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.Detach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Detach
helpviewer_keywords:
- Detach method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Detach method [.NET Framework debugging]
ms.assetid: 06fae364-f2c6-4a50-aa7e-3da9f2684dc3
topic_type:
- apiref
ms.openlocfilehash: b98077914d680c908587649fdd517aca9c8dcd40
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125432"
---
# <a name="icordebugcontrollerdetach-method"></a><span data-ttu-id="ee2ff-102">ICorDebugController::Detach — Metoda</span><span class="sxs-lookup"><span data-stu-id="ee2ff-102">ICorDebugController::Detach Method</span></span>
<span data-ttu-id="ee2ff-103">Odłącza debuger od domeny procesu lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ee2ff-103">Detaches the debugger from the process or application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee2ff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee2ff-104">Syntax</span></span>  
  
```cpp  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="ee2ff-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee2ff-105">Remarks</span></span>  
 <span data-ttu-id="ee2ff-106">Proces lub domena aplikacji kontynuuje wykonywanie normalnie, ale obiekt "ICorDebugProcess" lub "ICorDebugAppDomain" nie jest już ważny i nie będą wykonywane żadne kolejne wywołania zwrotne.</span><span class="sxs-lookup"><span data-stu-id="ee2ff-106">The process or application domain continues execution normally, but the "ICorDebugProcess" or "ICorDebugAppDomain" object is no longer valid and no further callbacks will occur.</span></span>  
  
 <span data-ttu-id="ee2ff-107">W .NET Framework w wersji 2,0, jeśli jest włączone debugowanie niezarządzane, ta metoda zakończy się niepowodzeniem z powodu ograniczeń systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="ee2ff-107">In the .NET Framework version 2.0, if unmanaged debugging is enabled, this method will fail due to operating system limitations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee2ff-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ee2ff-108">Requirements</span></span>  
 <span data-ttu-id="ee2ff-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee2ff-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee2ff-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ee2ff-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee2ff-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ee2ff-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee2ff-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee2ff-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee2ff-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee2ff-113">See also</span></span>
