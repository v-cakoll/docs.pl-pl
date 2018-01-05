---
title: "ICorDebugModule::EnableJITDebugging — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.EnableJITDebugging
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a699f32d8ec4b2418c6af815c22f35470bede3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="83fa5-102">ICorDebugModule::EnableJITDebugging — Metoda</span><span class="sxs-lookup"><span data-stu-id="83fa5-102">ICorDebugModule::EnableJITDebugging Method</span></span>
<span data-ttu-id="83fa5-103">Określa, czy przy użyciu kompilatora just in time (JIT) zachowuje informacji debugowania dla metod w ramach tego modułu.</span><span class="sxs-lookup"><span data-stu-id="83fa5-103">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83fa5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="83fa5-104">Syntax</span></span>  
  
```  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83fa5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83fa5-105">Parameters</span></span>  
 `bTrackJITInfo`  
 <span data-ttu-id="83fa5-106">[in] Ta wartość `true` umożliwiające kompilatora JIT zachować informacje dotyczące mapowania między wersji języka pośredniego (MSIL) firmy Microsoft i wersji kompilacji JIT każdej metody w tym module.</span><span class="sxs-lookup"><span data-stu-id="83fa5-106">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="83fa5-107">[in] Ta wartość `true` umożliwia generowanie kodu z niektórych optymalizacje JIT specyficzne dla debugowania przy użyciu kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="83fa5-107">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83fa5-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="83fa5-108">Remarks</span></span>  
 <span data-ttu-id="83fa5-109">Debugowanie JIT jest włączone domyślnie dla wszystkich modułów, które są ładowane, gdy debuger jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="83fa5-109">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="83fa5-110">Programowo włączenie lub wyłączenie ustawienia zastępują ustawienia globalne.</span><span class="sxs-lookup"><span data-stu-id="83fa5-110">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83fa5-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="83fa5-111">Requirements</span></span>  
 <span data-ttu-id="83fa5-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83fa5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83fa5-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83fa5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83fa5-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83fa5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83fa5-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83fa5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
