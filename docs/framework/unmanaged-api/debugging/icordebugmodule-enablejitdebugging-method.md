---
title: ICorDebugModule::EnableJITDebugging — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableJITDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71722293bfb80a7e57393916560f922d970ea2ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415645"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="643c3-102">ICorDebugModule::EnableJITDebugging — Metoda</span><span class="sxs-lookup"><span data-stu-id="643c3-102">ICorDebugModule::EnableJITDebugging Method</span></span>
<span data-ttu-id="643c3-103">Określa, czy przy użyciu kompilatora just in time (JIT) zachowuje informacji debugowania dla metod w ramach tego modułu.</span><span class="sxs-lookup"><span data-stu-id="643c3-103">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="643c3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="643c3-104">Syntax</span></span>  
  
```  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="643c3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="643c3-105">Parameters</span></span>  
 `bTrackJITInfo`  
 <span data-ttu-id="643c3-106">[in] Ta wartość `true` umożliwiające kompilatora JIT zachować informacje dotyczące mapowania między wersji języka pośredniego (MSIL) firmy Microsoft i wersji kompilacji JIT każdej metody w tym module.</span><span class="sxs-lookup"><span data-stu-id="643c3-106">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="643c3-107">[in] Ta wartość `true` umożliwia generowanie kodu z niektórych optymalizacje JIT specyficzne dla debugowania przy użyciu kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="643c3-107">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="643c3-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="643c3-108">Remarks</span></span>  
 <span data-ttu-id="643c3-109">Debugowanie JIT jest włączone domyślnie dla wszystkich modułów, które są ładowane, gdy debuger jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="643c3-109">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="643c3-110">Programowo włączenie lub wyłączenie ustawienia zastępują ustawienia globalne.</span><span class="sxs-lookup"><span data-stu-id="643c3-110">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="643c3-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="643c3-111">Requirements</span></span>  
 <span data-ttu-id="643c3-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="643c3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="643c3-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="643c3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="643c3-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="643c3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="643c3-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="643c3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
