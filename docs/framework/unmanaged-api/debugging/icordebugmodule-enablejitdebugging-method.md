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
ms.openlocfilehash: 642c4fd600d10ef89a08aa32bef5c8e7455552c7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473833"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="0954a-102">ICorDebugModule::EnableJITDebugging — Metoda</span><span class="sxs-lookup"><span data-stu-id="0954a-102">ICorDebugModule::EnableJITDebugging Method</span></span>
<span data-ttu-id="0954a-103">Określa, czy kompilator just-in-time (JIT), zachowuje informacje o debugowaniu dla metod, w tym module.</span><span class="sxs-lookup"><span data-stu-id="0954a-103">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0954a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0954a-104">Syntax</span></span>  
  
```  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0954a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0954a-105">Parameters</span></span>  
 `bTrackJITInfo`  
 <span data-ttu-id="0954a-106">[in] Ustaw tę wartość na `true` umożliwiające kompilator JIT, aby zachować informacje dotyczące mapowania między wersji języka intermediate language (MSIL) firmy Microsoft i wersję kompilowanego dokładnie na czas każdej metody w tym module.</span><span class="sxs-lookup"><span data-stu-id="0954a-106">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="0954a-107">[in] Ustaw tę wartość na `true` umożliwiające kompilator JIT wygenerować kod z niektóre optymalizacje JIT specyficzne dla debugowania.</span><span class="sxs-lookup"><span data-stu-id="0954a-107">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0954a-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0954a-108">Remarks</span></span>  
 <span data-ttu-id="0954a-109">Debugowanie JIT jest domyślnie włączone dla wszystkich modułów, które są ładowane, gdy debuger jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="0954a-109">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="0954a-110">Programowe Włączanie lub wyłączanie ustawień zastępuje ustawienia globalne.</span><span class="sxs-lookup"><span data-stu-id="0954a-110">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0954a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0954a-111">Requirements</span></span>  
 <span data-ttu-id="0954a-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0954a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0954a-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0954a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0954a-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0954a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0954a-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0954a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
