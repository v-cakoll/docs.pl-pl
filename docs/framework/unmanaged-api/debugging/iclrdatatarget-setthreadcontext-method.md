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
ms.openlocfilehash: d76a907434b12b85aaedeef169390ec6f0df724a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179129"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="313d3-102">ICLRDataTarget::SetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="313d3-102">ICLRDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="313d3-103">Ustawia bieżący kontekst określonego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="313d3-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="313d3-104">Ta metoda jest wywoływana przez usługi dostępu do danych wspólnego środowiska wykonawczego języka (CLR).</span><span class="sxs-lookup"><span data-stu-id="313d3-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="313d3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="313d3-105">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="313d3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="313d3-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="313d3-107">[w] Identyfikator systemu operacyjnego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="313d3-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="313d3-108">[w] Rozmiar kontekstu.</span><span class="sxs-lookup"><span data-stu-id="313d3-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="313d3-109">[w] Wskaźnik do buforu zawierającego kontekst.</span><span class="sxs-lookup"><span data-stu-id="313d3-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="313d3-110">Dane w `context` buforze będą w formacie struktury `CONTEXT` Win32.</span><span class="sxs-lookup"><span data-stu-id="313d3-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="313d3-111">Kontekst określa dane rejestru specyficzne dla procesora, więc `CONTEXT` definicja struktury Win32 zależy od architektury procesora.</span><span class="sxs-lookup"><span data-stu-id="313d3-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="313d3-112">Definicję struktury Win32 `CONTEXT` można znaleźć w pliku nagłówka WinNT.h.</span><span class="sxs-lookup"><span data-stu-id="313d3-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="313d3-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="313d3-113">Remarks</span></span>  
 <span data-ttu-id="313d3-114">Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="313d3-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="313d3-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="313d3-115">Requirements</span></span>  
 <span data-ttu-id="313d3-116">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="313d3-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="313d3-117">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="313d3-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="313d3-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="313d3-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="313d3-119">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="313d3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="313d3-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="313d3-120">See also</span></span>

- [<span data-ttu-id="313d3-121">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="313d3-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
