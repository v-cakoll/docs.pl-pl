---
title: "ICorDebugThread::GetObject — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetObject
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetObject method [.NET Framework debugging]
ms.assetid: 1590febe-96c2-4046-97db-d81d81d67e01
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c7802b51a8012b46b1d0bd9de5fbe9d3c6ff0da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="65581-102">ICorDebugThread::GetObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="65581-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="65581-103">Pobiera wskaźnika interfejsu do wspólnego języka wątku środowiska uruchomieniowego (języka wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="65581-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65581-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65581-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65581-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65581-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="65581-106">[out] Wskaźnik do adresu ICorDebugValue obiektu interfejsu, który reprezentuje wątku CLR.</span><span class="sxs-lookup"><span data-stu-id="65581-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65581-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65581-107">Requirements</span></span>  
 <span data-ttu-id="65581-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65581-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65581-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65581-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65581-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65581-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65581-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65581-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65581-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65581-112">See Also</span></span>  
 <xref:System.Threading.Thread>
