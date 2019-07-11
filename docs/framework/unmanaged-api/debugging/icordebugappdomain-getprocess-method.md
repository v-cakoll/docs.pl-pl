---
title: ICorDebugAppDomain::GetProcess — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetProcess method [.NET Framework debugging]
ms.assetid: 9d0b9628-a91c-40d0-b9bc-00b34a396b8f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eebb0c39cb8ae69dfce1e865f2784bbe9a408786
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737833"
---
# <a name="icordebugappdomaingetprocess-method"></a><span data-ttu-id="0d06e-102">ICorDebugAppDomain::GetProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="0d06e-102">ICorDebugAppDomain::GetProcess Method</span></span>
<span data-ttu-id="0d06e-103">Pobiera proces zawierający domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0d06e-103">Gets the process containing the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d06e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0d06e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d06e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0d06e-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="0d06e-106">[out] Wskaźnik na adres obiektu ICorDebugProcess, który reprezentuje proces.</span><span class="sxs-lookup"><span data-stu-id="0d06e-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d06e-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0d06e-107">Requirements</span></span>  
 <span data-ttu-id="0d06e-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d06e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d06e-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0d06e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d06e-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d06e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d06e-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d06e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
