---
title: ICorDebugModule2::SetJITCompilerFlags — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJITCompilerFlags
helpviewer_keywords:
- ICorDebugModule2::SetJITCompilerFlags method [.NET Framework debugging]
- SetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: ea574c84-c622-4589-9a14-b55771af5e06
topic_type:
- apiref
ms.openlocfilehash: f73919634ba15dfd16694676d1389875fc2d79bc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210192"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a><span data-ttu-id="3f212-102">ICorDebugModule2::SetJITCompilerFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="3f212-102">ICorDebugModule2::SetJITCompilerFlags Method</span></span>
<span data-ttu-id="3f212-103">Ustawia flagi kontrolujące kompilację just-in-Time (JIT) tej ICorDebugModule2.</span><span class="sxs-lookup"><span data-stu-id="3f212-103">Sets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f212-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f212-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f212-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3f212-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="3f212-106">podczas Bitowa kombinacja wartości wyliczenia [CorDebugJITCompilerFlags —](cordebugjitcompilerflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="3f212-106">[in] A bitwise combination of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f212-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3f212-107">Remarks</span></span>  
 <span data-ttu-id="3f212-108">Jeśli `dwFlags` wartość jest nieprawidłowa, metoda zakończy `SetJITCompilerFlags` się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="3f212-108">If the `dwFlags` value is invalid, the `SetJITCompilerFlags` method will fail.</span></span>  
  
 <span data-ttu-id="3f212-109">`SetJITCompilerFlags`Metodę można wywołać tylko z poziomu wywołania zwrotnego [ICorDebugManagedCallback:: LoadModule](icordebugmanagedcallback-loadmodule-method.md) dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="3f212-109">The `SetJITCompilerFlags` method can be called only from within the [ICorDebugManagedCallback::LoadModule](icordebugmanagedcallback-loadmodule-method.md) callback for this module.</span></span> <span data-ttu-id="3f212-110">Próbuje wywołać ją po `ICorDebugManagedCallback::LoadModule` dostarczeniu wywołania zwrotnego zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="3f212-110">Attempts to call it after the `ICorDebugManagedCallback::LoadModule` callback has been delivered will fail.</span></span>  
  
 <span data-ttu-id="3f212-111">Edytuj i Kontynuuj nie są obsługiwane na platformach 64-bitowych i Win9x.</span><span class="sxs-lookup"><span data-stu-id="3f212-111">Edit and Continue is not supported on 64-bit or Win9x platforms.</span></span> <span data-ttu-id="3f212-112">W związku z tym, jeśli wywołasz `SetJITCompilerFlags` metodę na jednej z tych dwóch platform z flagą CORDEBUG_JIT_ENABLE_ENC ustawioną w `dwFlags` , `SetJITCompilerFlags` Metoda i wszystkie metody specyficzne dla opcji Edytuj i Kontynuuj, takie jak [ICorDebugModule2:: ApplyChanges —](icordebugmodule2-applychanges-method.md), zakończą się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="3f212-112">Therefore, if you call the `SetJITCompilerFlags` method on either of these two platforms with the CORDEBUG_JIT_ENABLE_ENC flag set in `dwFlags`, the `SetJITCompilerFlags` method and all methods specific to Edit and Continue, such as [ICorDebugModule2::ApplyChanges](icordebugmodule2-applychanges-method.md), will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f212-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3f212-113">Requirements</span></span>  
 <span data-ttu-id="3f212-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f212-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f212-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3f212-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f212-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3f212-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f212-117">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f212-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
