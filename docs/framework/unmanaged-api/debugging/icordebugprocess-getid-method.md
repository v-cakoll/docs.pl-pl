---
title: "ICorDebugProcess::GetID — Metoda"
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
- ICorDebugProcess.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetID
helpviewer_keywords:
- GetID method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetID method [.NET Framework debugging]
ms.assetid: b0ba8453-fa7e-4c14-93e5-335409cd4a47
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d09888434048c312bd78dddf29d39a45f023695e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessgetid-method"></a><span data-ttu-id="78026-102">ICorDebugProcess::GetID — Metoda</span><span class="sxs-lookup"><span data-stu-id="78026-102">ICorDebugProcess::GetID Method</span></span>
<span data-ttu-id="78026-103">Pobiera identyfikator systemu operacyjnego (OS) procesu.</span><span class="sxs-lookup"><span data-stu-id="78026-103">Gets the operating system (OS) ID of the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78026-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="78026-104">Syntax</span></span>  
  
```  
HRESULT GetID([out] DWORD *pdwProcessId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78026-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78026-105">Parameters</span></span>  
 `pdwProcessId`  
 <span data-ttu-id="78026-106">[out] Unikatowy identyfikator procesu.</span><span class="sxs-lookup"><span data-stu-id="78026-106">[out] The unique ID of the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78026-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="78026-107">Requirements</span></span>  
 <span data-ttu-id="78026-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78026-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78026-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78026-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78026-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78026-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78026-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78026-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
