---
title: ICorDebugProcess::EnumerateAppDomains — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnumerateAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnumerateAppDomains
helpviewer_keywords:
- ICorDebugProcess::EnumerateAppDomains method [.NET Framework debugging]
- EnumerateAppDomains method [.NET Framework debugging]
ms.assetid: d508981f-e2b2-445b-a649-69951c22702d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3c0f20cc93b02e048c9d1952188af3d21d37221
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766124"
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="8916e-102">ICorDebugProcess::EnumerateAppDomains — Metoda</span><span class="sxs-lookup"><span data-stu-id="8916e-102">ICorDebugProcess::EnumerateAppDomains Method</span></span>
<span data-ttu-id="8916e-103">Wylicza wszystkie domeny aplikacji w ramach tego procesu.</span><span class="sxs-lookup"><span data-stu-id="8916e-103">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8916e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8916e-104">Syntax</span></span>  
  
``` cpp 
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8916e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8916e-105">Parameters</span></span>  
 `ppAppDomains`  
 <span data-ttu-id="8916e-106">[out] Wskaźnik na adres [icordebugappdomainenum —](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md) oznacza to moduł wyliczający dla domen aplikacji w ramach tego procesu.</span><span class="sxs-lookup"><span data-stu-id="8916e-106">[out] A pointer to the address of an [ICorDebugAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8916e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8916e-107">Remarks</span></span>  
 <span data-ttu-id="8916e-108">Ta metoda może być używana przed [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="8916e-108">This method can be used before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8916e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8916e-109">Requirements</span></span>  
 <span data-ttu-id="8916e-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8916e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8916e-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8916e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8916e-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8916e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8916e-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8916e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
