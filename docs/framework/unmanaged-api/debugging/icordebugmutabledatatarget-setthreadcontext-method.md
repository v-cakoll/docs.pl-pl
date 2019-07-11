---
title: ICorDebugMutableDataTarget::SetThreadContext Method
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6629af393eeadb68292f8f2360ecb60c09a0cd03
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764615"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="1adba-102">ICorDebugMutableDataTarget::SetThreadContext Method</span><span class="sxs-lookup"><span data-stu-id="1adba-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="1adba-103">Ustawia kontekst (wartości rejestru) dla wątku.</span><span class="sxs-lookup"><span data-stu-id="1adba-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1adba-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1adba-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1adba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1adba-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="1adba-106">[in] Identyfikator wątku zdefiniowaną przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="1adba-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="1adba-107">[in] Rozmiar `pContext` bufor do zapisania.</span><span class="sxs-lookup"><span data-stu-id="1adba-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="1adba-108">[in] Wskaźnik do bajtów do zapisania.</span><span class="sxs-lookup"><span data-stu-id="1adba-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1adba-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1adba-109">Remarks</span></span>  
 <span data-ttu-id="1adba-110">`SetThreadContext` Metody aktualizacji bieżący kontekst wątku określonego przez system operacyjny zdefiniowane `dwThreadID` argumentu.</span><span class="sxs-lookup"><span data-stu-id="1adba-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="1adba-111">Format rekordu kontekstu jest określana przez platformę, wskazywanym przez [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="1adba-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="1adba-112">W przypadku Windows, jest to [KONTEKSTU](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) struktury.</span><span class="sxs-lookup"><span data-stu-id="1adba-112">On Windows, this is a [CONTEXT](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1adba-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1adba-113">Requirements</span></span>  
 <span data-ttu-id="1adba-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1adba-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1adba-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1adba-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1adba-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1adba-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1adba-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1adba-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1adba-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1adba-118">See also</span></span>

- [<span data-ttu-id="1adba-119">ICorDebugMutableDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="1adba-119">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="1adba-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1adba-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
