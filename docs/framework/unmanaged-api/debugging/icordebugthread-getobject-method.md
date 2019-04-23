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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178740"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="a237a-102">ICorDebugThread::GetObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="a237a-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="a237a-103">Pobiera wskaźnik interfejsu do wspólnym mianownikiem języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="a237a-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a237a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a237a-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a237a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a237a-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="a237a-106">[out] Wskaźnik na adres obiektu interfejsu ICorDebugValue, który reprezentuje wątku środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="a237a-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a237a-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a237a-107">Requirements</span></span>  
 <span data-ttu-id="a237a-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a237a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a237a-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a237a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a237a-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a237a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a237a-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a237a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a237a-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a237a-112">See also</span></span>

- <xref:System.Threading.Thread>
