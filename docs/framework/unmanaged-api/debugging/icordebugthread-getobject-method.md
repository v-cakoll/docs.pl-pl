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
ms.openlocfilehash: ad2dd4cded6800ce016d821f8e3ffe01dcb6264b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418262"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="f28a0-102">ICorDebugThread::GetObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="f28a0-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="f28a0-103">Pobiera wskaźnika interfejsu do wspólnego języka wątku środowiska uruchomieniowego (języka wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="f28a0-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f28a0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f28a0-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f28a0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f28a0-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="f28a0-106">[out] Wskaźnik do adresu ICorDebugValue obiektu interfejsu, który reprezentuje wątku CLR.</span><span class="sxs-lookup"><span data-stu-id="f28a0-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f28a0-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f28a0-107">Requirements</span></span>  
 <span data-ttu-id="f28a0-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f28a0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f28a0-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f28a0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f28a0-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f28a0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f28a0-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f28a0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f28a0-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f28a0-112">See Also</span></span>  
 <xref:System.Threading.Thread>
