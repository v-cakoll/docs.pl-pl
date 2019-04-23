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
ms.openlocfilehash: 0708a3b501a99b5f71be5ba4c6cc4ea2b754d12a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191344"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="61701-102">IDebuggerInfo::IsDebuggerAttached — Metoda</span><span class="sxs-lookup"><span data-stu-id="61701-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="61701-103">Pobiera wartość wskazującą, czy zarządzane debuger jest dołączony do tego procesu.</span><span class="sxs-lookup"><span data-stu-id="61701-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61701-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="61701-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61701-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="61701-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="61701-106">[out] Wskaźnik do wartości, która jest `true` w przypadku zarządzanych debugerów dołączonych do procesu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="61701-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61701-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="61701-107">Requirements</span></span>  
 <span data-ttu-id="61701-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61701-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61701-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="61701-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="61701-110">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="61701-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="61701-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61701-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61701-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61701-112">See also</span></span>

- [<span data-ttu-id="61701-113">IDebuggerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="61701-113">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)
