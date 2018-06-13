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
ms.openlocfilehash: 94ba2b0cf7d88104eaadd434732edf3c1d4060e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422704"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a><span data-ttu-id="6eb0e-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="6eb0e-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="6eb0e-103">Ustawia flagi, które muszą być osadzone prekompilowany obrazu w kolejności środowiska uruchomieniowego do ładowania obrazu do bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-103">Sets the flags that must be embedded in a precompiled image in order for the runtime to load that image into the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eb0e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6eb0e-104">Syntax</span></span>  
  
```  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6eb0e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6eb0e-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="6eb0e-106">[in] Wartość [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) wyliczenia, która określa flagi kompilatora użyć, aby wybrać prawidłowy obraz wstępnie skompilowanym.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-106">[in] A value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that specifies the compiler flags used to select the correct pre-compiled image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6eb0e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6eb0e-107">Remarks</span></span>  
 <span data-ttu-id="6eb0e-108">`SetDesiredNGENCompilerFlags` Metody określa flagi, które musi być osadzony w prekompilowany obrazu, dzięki czemu środowiska uruchomieniowego załaduje obrazu do tego procesu.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-108">The `SetDesiredNGENCompilerFlags` method specifies the flags that must be embedded in a precompiled image so that the runtime will load that image into this process.</span></span> <span data-ttu-id="6eb0e-109">Flagi ustawione przez tę metodę są używane tylko w celu wybrania prawidłowy obraz wstępnie skompilowana.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-109">The flags set by this method are used only to select the correct precompiled image.</span></span> <span data-ttu-id="6eb0e-110">Jeśli istnieje nie tych obrazów, środowiska uruchomieniowego zamiast obciążenia obrazu język pośredni (MSIL) firmy Microsoft i przy użyciu kompilatora just in time (JIT).</span><span class="sxs-lookup"><span data-stu-id="6eb0e-110">If no such image exists, the runtime will load the Microsoft intermediate language (MSIL) image and the just-in-time (JIT) compiler instead.</span></span> <span data-ttu-id="6eb0e-111">W takim przypadku należy nadal używać debugera [ICorDebugModule2::SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) metody można ustawić flagi zgodnie z potrzebami dla kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-111">In that case, the debugger must still use the [ICorDebugModule2::SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) method to set the flags as desired for the JIT compilation.</span></span>  
  
 <span data-ttu-id="6eb0e-112">Jeśli obraz został załadowany, ale niektóre kompilacji JIT musi odbywać się do tego obrazu (co będzie miało miejsce, jeśli obraz zawiera ogólne) flagi kompilatora określony przez `SetDesiredNGENCompilerFlags` metoda będzie dotyczyć dodatkowe kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-112">If an image is loaded, but some JIT compiling must take place for that image (which will be the case if the image contains generics), the compiler flags specified by the `SetDesiredNGENCompilerFlags` method will apply to the extra JIT compilation.</span></span>  
  
 <span data-ttu-id="6eb0e-113">`SetDesiredNGENCompilerFlags` Metoda musi zostać wywołana podczas [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-113">The `SetDesiredNGENCompilerFlags` method must be called during the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="6eb0e-114">Próby wywołania `SetDesiredNGENCompilerFlags` metody później zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-114">Attempts to call the `SetDesiredNGENCompilerFlags` method afterwards will fail.</span></span> <span data-ttu-id="6eb0e-115">Ponadto próbuje ustawić flagi, które nie są zdefiniowane w `CorDebugJITCompilerFlags` wyliczenia lub czy nie jest dozwolony dla danego procesu zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-115">Also, attempts to set flags that are either not defined in the `CorDebugJITCompilerFlags` enumeration or are not legal for the given process will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6eb0e-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6eb0e-116">Requirements</span></span>  
 <span data-ttu-id="6eb0e-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6eb0e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6eb0e-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6eb0e-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6eb0e-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6eb0e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6eb0e-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6eb0e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eb0e-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6eb0e-121">See Also</span></span>  
 [<span data-ttu-id="6eb0e-122">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="6eb0e-122">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="6eb0e-123">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="6eb0e-123">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
