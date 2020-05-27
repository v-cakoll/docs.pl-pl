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
ms.openlocfilehash: 95b7a2f6d35104c3353853549dacc783355feb5b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805331"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="92b7a-102">IDebuggerInfo::IsDebuggerAttached — Metoda</span><span class="sxs-lookup"><span data-stu-id="92b7a-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="92b7a-103">Pobiera wartość wskazującą, czy zarządzany debuger jest dołączony do tego procesu.</span><span class="sxs-lookup"><span data-stu-id="92b7a-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92b7a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="92b7a-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92b7a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92b7a-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="92b7a-106">określoną Wskaźnik do wartości, która jest w `true` przypadku dołączenia zarządzanego debugera do procesu; w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="92b7a-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92b7a-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="92b7a-107">Requirements</span></span>  
 <span data-ttu-id="92b7a-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92b7a-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92b7a-109">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="92b7a-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92b7a-110">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="92b7a-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92b7a-111">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92b7a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92b7a-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="92b7a-112">See also</span></span>

- [<span data-ttu-id="92b7a-113">IDebuggerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="92b7a-113">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)
