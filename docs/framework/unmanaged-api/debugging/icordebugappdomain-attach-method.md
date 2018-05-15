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
ms.openlocfilehash: a290ca162e5ab71b4184d166bcd00f1d0217cb94
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugappdomainattach-method"></a><span data-ttu-id="3c2c4-102">ICorDebugAppDomain::Attach — Metoda</span><span class="sxs-lookup"><span data-stu-id="3c2c4-102">ICorDebugAppDomain::Attach Method</span></span>
<span data-ttu-id="3c2c4-103">Dołącza debuger do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3c2c4-103">Attaches the debugger to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c2c4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c2c4-104">Syntax</span></span>  
  
```  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="3c2c4-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3c2c4-105">Remarks</span></span>  
 <span data-ttu-id="3c2c4-106">Debuger musi być dołączony do domeny aplikacji na odbieranie zdarzeń i włączyć debugowanie stron domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3c2c4-106">The debugger must be attached to the application domain to receive events and to enable debugging of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c2c4-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3c2c4-107">Requirements</span></span>  
 <span data-ttu-id="3c2c4-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c2c4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c2c4-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c2c4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c2c4-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c2c4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c2c4-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c2c4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
