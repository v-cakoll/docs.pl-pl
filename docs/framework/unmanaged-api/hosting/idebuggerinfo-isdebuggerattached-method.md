---
title: IDebuggerInfo::IsDebuggerAttached — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f381cc687b4c28dd58a02aea8cf931f569cf9611
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780522"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="464fd-102">IDebuggerInfo::IsDebuggerAttached — Metoda</span><span class="sxs-lookup"><span data-stu-id="464fd-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="464fd-103">Pobiera wartość wskazującą, czy zarządzane debuger jest dołączony do tego procesu.</span><span class="sxs-lookup"><span data-stu-id="464fd-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="464fd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="464fd-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="464fd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="464fd-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="464fd-106">[out] Wskaźnik do wartości, która jest `true` w przypadku zarządzanych debugerów dołączonych do procesu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="464fd-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="464fd-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="464fd-107">Requirements</span></span>  
 <span data-ttu-id="464fd-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="464fd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="464fd-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="464fd-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="464fd-110">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="464fd-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="464fd-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="464fd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="464fd-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="464fd-112">See also</span></span>

- [<span data-ttu-id="464fd-113">IDebuggerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="464fd-113">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)
