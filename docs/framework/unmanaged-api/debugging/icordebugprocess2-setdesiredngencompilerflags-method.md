---
title: ICorDebugProcess2::SetDesiredNGENCompilerFlags — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags method [.NET Framework debugging]
- SetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: 98320175-7c5e-4dbb-8683-86fa82e2641f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1cab24f949ddae55d5e699e6ad82851007504dd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475700"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a><span data-ttu-id="70455-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="70455-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="70455-103">Ustawia flagi, które muszą być osadzone w wstępnie skompilowanym obrazów w kolejności dla środowiska uruchomieniowego do załadowania tego obrazu do bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="70455-103">Sets the flags that must be embedded in a precompiled image in order for the runtime to load that image into the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70455-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="70455-104">Syntax</span></span>  
  
```  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70455-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70455-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="70455-106">[in] Wartość [cordebugjitcompilerflags —](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) wyliczenie, które określa flagi kompilatora używany do wybierania wstępnie skompilowanym prawidłowy obraz.</span><span class="sxs-lookup"><span data-stu-id="70455-106">[in] A value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that specifies the compiler flags used to select the correct pre-compiled image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70455-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="70455-107">Remarks</span></span>  
 <span data-ttu-id="70455-108">`SetDesiredNGENCompilerFlags` Metody określa flagi, które muszą być osadzone w wstępnie skompilowanym obrazów, tak, aby środowisko uruchomieniowe będzie załadować ten obraz do tego procesu.</span><span class="sxs-lookup"><span data-stu-id="70455-108">The `SetDesiredNGENCompilerFlags` method specifies the flags that must be embedded in a precompiled image so that the runtime will load that image into this process.</span></span> <span data-ttu-id="70455-109">Flag ustawionych przez tę metodę są używane tylko po to, aby wybrać prawidłowy obraz wstępnie skompilowane.</span><span class="sxs-lookup"><span data-stu-id="70455-109">The flags set by this method are used only to select the correct precompiled image.</span></span> <span data-ttu-id="70455-110">Jeśli istnieje nie takich obrazów, środowisko uruchomieniowe zamiast tego obciążenia obrazu języka intermediate language (MSIL) firmy Microsoft i kompilator just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="70455-110">If no such image exists, the runtime will load the Microsoft intermediate language (MSIL) image and the just-in-time (JIT) compiler instead.</span></span> <span data-ttu-id="70455-111">W takim przypadku należy nadal używać debugera [ICorDebugModule2::SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) metodę, aby ustawić flagi zgodnie z potrzebami dla kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="70455-111">In that case, the debugger must still use the [ICorDebugModule2::SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) method to set the flags as desired for the JIT compilation.</span></span>  
  
 <span data-ttu-id="70455-112">Jeśli obraz został załadowany, ale niektóre kompilacja JIT musi odbywać się obrazu (co będzie miało miejsce, jeśli obraz zawiera ogólne), flagi kompilatora określony przez `SetDesiredNGENCompilerFlags` metody będą stosowane dodatkowe kompilację JIT.</span><span class="sxs-lookup"><span data-stu-id="70455-112">If an image is loaded, but some JIT compiling must take place for that image (which will be the case if the image contains generics), the compiler flags specified by the `SetDesiredNGENCompilerFlags` method will apply to the extra JIT compilation.</span></span>  
  
 <span data-ttu-id="70455-113">`SetDesiredNGENCompilerFlags` Metoda musi zostać wywołane podczas [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="70455-113">The `SetDesiredNGENCompilerFlags` method must be called during the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="70455-114">Próbuje wywołać `SetDesiredNGENCompilerFlags` metoda później zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="70455-114">Attempts to call the `SetDesiredNGENCompilerFlags` method afterwards will fail.</span></span> <span data-ttu-id="70455-115">Ponadto próbuje ustawić flagi, które nie są zdefiniowane w `CorDebugJITCompilerFlags` wyliczenia lub czy nie jest dozwolony dla danego procesu zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="70455-115">Also, attempts to set flags that are either not defined in the `CorDebugJITCompilerFlags` enumeration or are not legal for the given process will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70455-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="70455-116">Requirements</span></span>  
 <span data-ttu-id="70455-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70455-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70455-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70455-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70455-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70455-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70455-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70455-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70455-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70455-121">See also</span></span>
- [<span data-ttu-id="70455-122">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="70455-122">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="70455-123">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="70455-123">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
