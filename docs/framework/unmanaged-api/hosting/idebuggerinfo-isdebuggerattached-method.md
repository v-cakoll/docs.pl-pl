---
title: "IDebuggerInfo::IsDebuggerAttached — Metoda"
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
- IDebuggerInfo.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IsDebuggerAttached
helpviewer_keywords:
- IDebuggerInfo::IsDebuggerAttached method [.NET Framework hosting]
- IsDebuggerAttached method, IDebuggerInfo interface [.NET Framework hosting]
ms.assetid: 6e21872f-602f-411a-a423-bff5cdf27000
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7c241af6b71591374d8ce8cc8d1610a8dce91b2e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="4cb96-102">IDebuggerInfo::IsDebuggerAttached — Metoda</span><span class="sxs-lookup"><span data-stu-id="4cb96-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="4cb96-103">Pobiera wartość wskazującą, czy zarządzany debuger jest dołączony do tego procesu.</span><span class="sxs-lookup"><span data-stu-id="4cb96-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cb96-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4cb96-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4cb96-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4cb96-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="4cb96-106">[out] Wskaźnik do wartości, która jest `true` Jeśli zarządzanych debuger jest dołączony do procesu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="4cb96-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cb96-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4cb96-107">Requirements</span></span>  
 <span data-ttu-id="4cb96-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cb96-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cb96-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4cb96-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4cb96-110">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4cb96-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4cb96-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cb96-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cb96-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4cb96-112">See Also</span></span>  
 [<span data-ttu-id="4cb96-113">IDebuggerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="4cb96-113">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)
