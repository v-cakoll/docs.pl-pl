---
title: ICLRDataTarget::SetThreadContext — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetThreadContext
helpviewer_keywords:
- SetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::SetThreadContext method [.NET Framework debugging]
ms.assetid: 103c8502-81fe-40d7-9c1e-9008d8fb19e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73697fdd19f2492aabdc0d76e8c1a27c917c85f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405541"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="e2211-102">ICLRDataTarget::SetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="e2211-102">ICLRDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="e2211-103">Ustawia bieżący kontekst określonego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="e2211-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="e2211-104">Ta metoda jest wywoływana przez wspólne usługi dostępu do danych języka środowiska uruchomieniowego (języka wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="e2211-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2211-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e2211-105">Syntax</span></span>  
  
```  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]   
         BYTE               *context  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2211-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2211-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="e2211-107">[in] System operacyjny identyfikator wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="e2211-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="e2211-108">[in] Rozmiar kontekstu.</span><span class="sxs-lookup"><span data-stu-id="e2211-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="e2211-109">[in] Wskaźnik do bufor zawierający kontekst.</span><span class="sxs-lookup"><span data-stu-id="e2211-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="e2211-110">Dane w `context` buforu będą w formacie Win32 `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="e2211-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="e2211-111">Kontekst określa dane rejestru specyficznych dla procesora, więc definicji Win32 `CONTEXT` struktury jest zależna od architektury procesora.</span><span class="sxs-lookup"><span data-stu-id="e2211-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="e2211-112">Zajrzyj do pliku nagłówka pliku WinNT.h definicji Win32 `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="e2211-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2211-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e2211-113">Remarks</span></span>  
 <span data-ttu-id="e2211-114">Ta metoda jest implementowany przez twórcę debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e2211-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2211-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e2211-115">Requirements</span></span>  
 <span data-ttu-id="e2211-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2211-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2211-117">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="e2211-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e2211-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2211-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2211-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2211-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2211-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e2211-120">See Also</span></span>  
 [<span data-ttu-id="e2211-121">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="e2211-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
