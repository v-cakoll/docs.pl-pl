---
title: "ICorDebugAppDomain::GetProcess — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.GetProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetProcess method [.NET Framework debugging]
ms.assetid: 9d0b9628-a91c-40d0-b9bc-00b34a396b8f
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 27c092c029f259ed64eda26401bb9085f23d2bfa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomaingetprocess-method"></a><span data-ttu-id="a0a5e-102">ICorDebugAppDomain::GetProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="a0a5e-102">ICorDebugAppDomain::GetProcess Method</span></span>
<span data-ttu-id="a0a5e-103">Pobiera proces zawierający domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a0a5e-103">Gets the process containing the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0a5e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a0a5e-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0a5e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0a5e-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="a0a5e-106">[out] Wskaźnik do adresu ICorDebugProcess obiekt, który reprezentuje procesu.</span><span class="sxs-lookup"><span data-stu-id="a0a5e-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0a5e-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a0a5e-107">Requirements</span></span>  
 <span data-ttu-id="a0a5e-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0a5e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0a5e-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0a5e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0a5e-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0a5e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0a5e-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0a5e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
