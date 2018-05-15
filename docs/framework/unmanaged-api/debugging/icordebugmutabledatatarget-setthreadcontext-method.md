---
title: ICorDebugMutableDataTarget::SetThreadContext — metoda
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05f0c0d23b4885f2d6fd351fdf845a25c899228e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="bc0ff-102">ICorDebugMutableDataTarget::SetThreadContext — metoda</span><span class="sxs-lookup"><span data-stu-id="bc0ff-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="bc0ff-103">Ustawia kontekst wątku (wartości rejestru).</span><span class="sxs-lookup"><span data-stu-id="bc0ff-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc0ff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc0ff-104">Syntax</span></span>  
  
```  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc0ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc0ff-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="bc0ff-106">[in] Identyfikator wątku zdefiniowane przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="bc0ff-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="bc0ff-107">[in] Rozmiar `pContext` buforu do zapisania.</span><span class="sxs-lookup"><span data-stu-id="bc0ff-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="bc0ff-108">[in] Wskaźnik do bajtów do zapisania.</span><span class="sxs-lookup"><span data-stu-id="bc0ff-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc0ff-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc0ff-109">Remarks</span></span>  
 <span data-ttu-id="bc0ff-110">`SetThreadContext` Metody aktualizacji bieżący kontekst wątku określony przez system operacyjny zdefiniowane `dwThreadID` argumentu.</span><span class="sxs-lookup"><span data-stu-id="bc0ff-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="bc0ff-111">Format rekordu kontekstu jest określany przez platformy wskazywaną przez [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="bc0ff-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="bc0ff-112">W systemie Windows, to [KONTEKSTU](http://msdn.microsoft.com/library/windows/desktop/ms679284.aspx) struktury.</span><span class="sxs-lookup"><span data-stu-id="bc0ff-112">On Windows, this is a [CONTEXT](http://msdn.microsoft.com/library/windows/desktop/ms679284.aspx) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc0ff-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bc0ff-113">Requirements</span></span>  
 <span data-ttu-id="bc0ff-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc0ff-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc0ff-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc0ff-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc0ff-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc0ff-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc0ff-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc0ff-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc0ff-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc0ff-118">See Also</span></span>  
 [<span data-ttu-id="bc0ff-119">ICorDebugMutableDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="bc0ff-119">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [<span data-ttu-id="bc0ff-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bc0ff-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
