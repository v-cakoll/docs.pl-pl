---
title: "ICorDebugAppDomain::IsAttached — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.IsAttached
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::IsAttached
helpviewer_keywords:
- IsAttached method [.NET Framework debugging]
- ICorDebugAppDomain::IsAttached method [.NET Framework debugging]
ms.assetid: af0c67c7-f53e-47c9-b84b-be50bd04903e
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a1af550de7198041a885a788d6b36349c8e1c091
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="1f788-102">ICorDebugAppDomain::IsAttached — Metoda</span><span class="sxs-lookup"><span data-stu-id="1f788-102">ICorDebugAppDomain::IsAttached Method</span></span>
<span data-ttu-id="1f788-103">Pobiera wartość wskazującą, czy debuger jest dołączony do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1f788-103">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f788-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f788-104">Syntax</span></span>  
  
```  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f788-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f788-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="1f788-106">[out] `true` Jeśli Debuger jest dołączony do domeny aplikacji; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="1f788-106">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f788-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f788-107">Remarks</span></span>  
 <span data-ttu-id="1f788-108">Nie można używać metod ICorDebugController, dopóki nie dołącza debuger do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1f788-108">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f788-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f788-109">Requirements</span></span>  
 <span data-ttu-id="1f788-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f788-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f788-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f788-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f788-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f788-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f788-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f788-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
