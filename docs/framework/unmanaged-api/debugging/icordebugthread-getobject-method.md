---
title: ICorDebugThread::GetObject — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetObject method [.NET Framework debugging]
ms.assetid: 1590febe-96c2-4046-97db-d81d81d67e01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fa90aff73d94baf2cbf7d01f41710cb2aa10213
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178740"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="0a403-102">ICorDebugThread::GetObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="0a403-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="0a403-103">Pobiera wskaźnik interfejsu do wspólnym mianownikiem języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="0a403-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a403-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0a403-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a403-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a403-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="0a403-106">[out] Wskaźnik na adres obiektu interfejsu ICorDebugValue, który reprezentuje wątku środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="0a403-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a403-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0a403-107">Requirements</span></span>  
 <span data-ttu-id="0a403-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a403-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a403-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a403-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a403-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a403-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0a403-111">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0a403-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0a403-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a403-112">See also</span></span>

- <xref:System.Threading.Thread>
