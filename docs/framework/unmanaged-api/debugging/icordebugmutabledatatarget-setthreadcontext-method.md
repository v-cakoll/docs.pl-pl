---
title: 'ICorDebugMutableDataTarget:: SetThreadContext —, Metoda'
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21a24b3ae3563db09f1f7e9229f388abf8de654c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038315"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="20f6f-102">ICorDebugMutableDataTarget:: SetThreadContext —, Metoda</span><span class="sxs-lookup"><span data-stu-id="20f6f-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="20f6f-103">Ustawia kontekst (wartości rejestru) dla wątku.</span><span class="sxs-lookup"><span data-stu-id="20f6f-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20f6f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="20f6f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20f6f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="20f6f-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="20f6f-106">podczas Identyfikator wątku zdefiniowanego przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="20f6f-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="20f6f-107">podczas Rozmiar `pContext` buforu, który ma zostać zapisany.</span><span class="sxs-lookup"><span data-stu-id="20f6f-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="20f6f-108">podczas Wskaźnik do bajtów do zapisania.</span><span class="sxs-lookup"><span data-stu-id="20f6f-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20f6f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="20f6f-109">Remarks</span></span>  
 <span data-ttu-id="20f6f-110">Metoda aktualizuje bieżący kontekst dla wątku określonego przez argument zdefiniowany `dwThreadID` przez system operacyjny. `SetThreadContext`</span><span class="sxs-lookup"><span data-stu-id="20f6f-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="20f6f-111">Format rekordu kontekstu jest określany przez platformę wskazywaną przez metodę [ICorDebugDataTarget:: GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) .</span><span class="sxs-lookup"><span data-stu-id="20f6f-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="20f6f-112">W systemie Windows jest to struktura [kontekstu](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) .</span><span class="sxs-lookup"><span data-stu-id="20f6f-112">On Windows, this is a [CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20f6f-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="20f6f-113">Requirements</span></span>  
 <span data-ttu-id="20f6f-114">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20f6f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20f6f-115">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20f6f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20f6f-116">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20f6f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20f6f-117">**.NET Framework wersje:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20f6f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20f6f-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20f6f-118">See also</span></span>

- [<span data-ttu-id="20f6f-119">ICorDebugMutableDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="20f6f-119">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="20f6f-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="20f6f-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
