---
title: ICorDebugAppDomain::EnumerateBreakpoints — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateBreakpoints
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints method [.NET Framework debugging]
- EnumerateBreakpoints method [.NET Framework debugging]
ms.assetid: 206069c5-25cb-4794-9d69-67c5aa7ed0af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b00afc900a27aea94389ee81065ea22ae359440d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498344"
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a><span data-ttu-id="b6f3a-102">ICorDebugAppDomain::EnumerateBreakpoints — Metoda</span><span class="sxs-lookup"><span data-stu-id="b6f3a-102">ICorDebugAppDomain::EnumerateBreakpoints Method</span></span>
<span data-ttu-id="b6f3a-103">Pobiera moduł wyliczający dla wszystkich aktywnych punktów przerwania w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6f3a-103">Gets an enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6f3a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6f3a-104">Syntax</span></span>  
  
```  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6f3a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6f3a-105">Parameters</span></span>  
 `ppBreakpoints`  
 <span data-ttu-id="b6f3a-106">[out] Wskaźnik na adres icordebugbreakpointenum — obiekt, który jest moduł wyliczający aktywnymi punktami przerwania w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6f3a-106">[out] A pointer to the address of an ICorDebugBreakpointEnum object that is the enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6f3a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6f3a-107">Remarks</span></span>  
 <span data-ttu-id="b6f3a-108">Moduł wyliczający obejmuje wszystkie typy punktów przerwania, w tym punkty przerwania funkcji i punkty przerwania danych.</span><span class="sxs-lookup"><span data-stu-id="b6f3a-108">The enumerator includes all types of breakpoints, including function breakpoints and data breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6f3a-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6f3a-109">Requirements</span></span>  
 <span data-ttu-id="b6f3a-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6f3a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6f3a-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6f3a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6f3a-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6f3a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6f3a-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6f3a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
