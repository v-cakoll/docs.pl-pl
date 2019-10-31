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
ms.openlocfilehash: cbd6fa5f7935a57799d695c3ebb617d856e6dbd9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133175"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="84823-102">IDebuggerInfo::IsDebuggerAttached — Metoda</span><span class="sxs-lookup"><span data-stu-id="84823-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="84823-103">Pobiera wartość wskazującą, czy zarządzany debuger jest dołączony do tego procesu.</span><span class="sxs-lookup"><span data-stu-id="84823-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84823-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="84823-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84823-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84823-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="84823-106">określoną Wskaźnik do wartości, która jest `true`, jeśli zarządzany debuger jest dołączony do procesu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="84823-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84823-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84823-107">Requirements</span></span>  
 <span data-ttu-id="84823-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84823-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84823-109">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="84823-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="84823-110">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="84823-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="84823-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84823-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84823-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84823-112">See also</span></span>

- [<span data-ttu-id="84823-113">IDebuggerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="84823-113">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)
