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
ms.openlocfilehash: 4489238df05edef384b4073ee738a184ff8809ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178670"
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="d843f-102">ICorDebugProcess::EnumerateAppDomains — Metoda</span><span class="sxs-lookup"><span data-stu-id="d843f-102">ICorDebugProcess::EnumerateAppDomains Method</span></span>
<span data-ttu-id="d843f-103">Wylicza wszystkie domeny aplikacji w tym procesie.</span><span class="sxs-lookup"><span data-stu-id="d843f-103">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d843f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d843f-104">Syntax</span></span>  
  
``` cpp
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d843f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d843f-105">Parameters</span></span>  
 `ppAppDomains`  
 <span data-ttu-id="d843f-106">[na zewnątrz] Wskaźnik do adresu [ICorDebugAppDomainEnum,](icordebugappdomainenum-interface.md) który jest wyliczaczem domen aplikacji w tym procesie.</span><span class="sxs-lookup"><span data-stu-id="d843f-106">[out] A pointer to the address of an [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d843f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d843f-107">Remarks</span></span>  
 <span data-ttu-id="d843f-108">Ta metoda może służyć przed [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="d843f-108">This method can be used before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d843f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d843f-109">Requirements</span></span>  
 <span data-ttu-id="d843f-110">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d843f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d843f-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d843f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d843f-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d843f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d843f-113">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d843f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
