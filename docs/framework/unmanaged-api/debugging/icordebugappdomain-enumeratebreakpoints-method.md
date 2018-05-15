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
ms.openlocfilehash: cfd7ee890a7f2c3ea8cd3de9fbe830575c0ca10c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a><span data-ttu-id="cd837-102">ICorDebugAppDomain::EnumerateBreakpoints — Metoda</span><span class="sxs-lookup"><span data-stu-id="cd837-102">ICorDebugAppDomain::EnumerateBreakpoints Method</span></span>
<span data-ttu-id="cd837-103">Pobiera moduł wyliczający dla wszystkich aktywnych punktów przerwania w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cd837-103">Gets an enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd837-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd837-104">Syntax</span></span>  
  
```  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd837-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd837-105">Parameters</span></span>  
 `ppBreakpoints`  
 <span data-ttu-id="cd837-106">[out] Wskaźnik do adresu ICorDebugBreakpointEnum obiektu, który moduł wyliczający dla wszystkich aktywnych punktów przerwania w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cd837-106">[out] A pointer to the address of an ICorDebugBreakpointEnum object that is the enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd837-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd837-107">Remarks</span></span>  
 <span data-ttu-id="cd837-108">Moduł wyliczający obejmuje wszystkie typy punktów przerwania, w tym punkty przerwania funkcji i punkty przerwania danych.</span><span class="sxs-lookup"><span data-stu-id="cd837-108">The enumerator includes all types of breakpoints, including function breakpoints and data breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd837-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd837-109">Requirements</span></span>  
 <span data-ttu-id="cd837-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd837-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd837-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cd837-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd837-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd837-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd837-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd837-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
