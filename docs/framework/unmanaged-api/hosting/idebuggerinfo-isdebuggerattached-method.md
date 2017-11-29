---
title: "IDebuggerInfo::IsDebuggerAttached — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebuggerInfo.IsDebuggerAttached
api_location: mscoree.dll
api_type: COM
f1_keywords: IsDebuggerAttached
helpviewer_keywords:
- IDebuggerInfo::IsDebuggerAttached method [.NET Framework hosting]
- IsDebuggerAttached method, IDebuggerInfo interface [.NET Framework hosting]
ms.assetid: 6e21872f-602f-411a-a423-bff5cdf27000
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a6e1f11939bc4f11b1fb49dc44f129176143fbca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="cbc06-102">IDebuggerInfo::IsDebuggerAttached — Metoda</span><span class="sxs-lookup"><span data-stu-id="cbc06-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="cbc06-103">Pobiera wartość wskazującą, czy zarządzany debuger jest dołączony do tego procesu.</span><span class="sxs-lookup"><span data-stu-id="cbc06-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbc06-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cbc06-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cbc06-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cbc06-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="cbc06-106">[out] Wskaźnik do wartości, która jest `true` Jeśli zarządzanych debuger jest dołączony do procesu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="cbc06-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbc06-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cbc06-107">Requirements</span></span>  
 <span data-ttu-id="cbc06-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbc06-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbc06-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cbc06-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cbc06-110">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cbc06-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cbc06-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbc06-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbc06-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cbc06-112">See Also</span></span>  
 [<span data-ttu-id="cbc06-113">IDebuggerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="cbc06-113">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)
