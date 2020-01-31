---
title: 'ICorDebugMutableDataTarget:: SetThreadContext —, Metoda'
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
ms.openlocfilehash: 063c7954543174caece6f3dcbe005a4b2d059c64
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792846"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="e0255-102">ICorDebugMutableDataTarget:: SetThreadContext —, Metoda</span><span class="sxs-lookup"><span data-stu-id="e0255-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="e0255-103">Ustawia kontekst (wartości rejestru) dla wątku.</span><span class="sxs-lookup"><span data-stu-id="e0255-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0255-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e0255-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0255-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0255-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="e0255-106">podczas Identyfikator wątku zdefiniowanego przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="e0255-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="e0255-107">podczas Rozmiar bufora `pContext`, który ma zostać zapisany.</span><span class="sxs-lookup"><span data-stu-id="e0255-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="e0255-108">podczas Wskaźnik do bajtów do zapisania.</span><span class="sxs-lookup"><span data-stu-id="e0255-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0255-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e0255-109">Remarks</span></span>  
 <span data-ttu-id="e0255-110">Metoda `SetThreadContext` aktualizuje bieżący kontekst dla wątku określonego przez argument `dwThreadID` zdefiniowanego przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="e0255-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="e0255-111">Format rekordu kontekstu jest określany przez platformę wskazywaną przez metodę [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e0255-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="e0255-112">W systemie Windows jest to struktura [kontekstu](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) .</span><span class="sxs-lookup"><span data-stu-id="e0255-112">On Windows, this is a [CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0255-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e0255-113">Requirements</span></span>  
 <span data-ttu-id="e0255-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0255-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0255-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e0255-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0255-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e0255-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0255-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0255-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0255-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0255-118">See also</span></span>

- [<span data-ttu-id="e0255-119">ICorDebugMutableDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="e0255-119">ICorDebugMutableDataTarget Interface</span></span>](icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="e0255-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e0255-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
