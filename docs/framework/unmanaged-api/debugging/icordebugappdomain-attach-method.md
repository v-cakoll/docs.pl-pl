---
title: ICorDebugAppDomain::Attach — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.Attach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::Attach
helpviewer_keywords:
- ICorDebugAppDomain::Attach method [.NET Framework debugging]
- Attach method [.NET Framework debugging]
ms.assetid: 0358b84a-4236-4c34-945b-4babff7df570
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d30b6cb083cc2f92bcbe089bf8e990fedd8e8f7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738092"
---
# <a name="icordebugappdomainattach-method"></a><span data-ttu-id="6b17b-102">ICorDebugAppDomain::Attach — Metoda</span><span class="sxs-lookup"><span data-stu-id="6b17b-102">ICorDebugAppDomain::Attach Method</span></span>
<span data-ttu-id="6b17b-103">Dołącza debuger do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6b17b-103">Attaches the debugger to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b17b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b17b-104">Syntax</span></span>  
  
```cpp  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6b17b-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b17b-105">Remarks</span></span>  
 <span data-ttu-id="6b17b-106">Debuger musi być dołączony do domeny aplikacji, aby odbierać zdarzenia i włączyć debugowanie stron domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6b17b-106">The debugger must be attached to the application domain to receive events and to enable debugging of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b17b-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b17b-107">Requirements</span></span>  
 <span data-ttu-id="6b17b-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b17b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b17b-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b17b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b17b-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b17b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b17b-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b17b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
