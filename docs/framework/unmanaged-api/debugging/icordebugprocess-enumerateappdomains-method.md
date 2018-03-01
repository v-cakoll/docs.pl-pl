---
title: "ICorDebugProcess::EnumerateAppDomains — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0ba0f554a4ddf52b7c4ced1658055c4370f112ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="86f02-102">ICorDebugProcess::EnumerateAppDomains — Metoda</span><span class="sxs-lookup"><span data-stu-id="86f02-102">ICorDebugProcess::EnumerateAppDomains Method</span></span>
<span data-ttu-id="86f02-103">Wylicza wszystkie domeny aplikacji w tym procesie.</span><span class="sxs-lookup"><span data-stu-id="86f02-103">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86f02-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="86f02-104">Syntax</span></span>  
  
```  
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="86f02-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="86f02-105">Parameters</span></span>  
 `ppAppDomains`  
 <span data-ttu-id="86f02-106">[out] Wskaźnik do adresu [ICorDebugAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md) czyli moduł wyliczający dla domeny aplikacji w tym procesie.</span><span class="sxs-lookup"><span data-stu-id="86f02-106">[out] A pointer to the address of an [ICorDebugAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86f02-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86f02-107">Remarks</span></span>  
 <span data-ttu-id="86f02-108">Ta metoda może być używana przed [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="86f02-108">This method can be used before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86f02-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="86f02-109">Requirements</span></span>  
 <span data-ttu-id="86f02-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86f02-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86f02-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86f02-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86f02-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86f02-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86f02-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86f02-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
