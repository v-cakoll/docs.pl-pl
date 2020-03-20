---
title: ICLRDataTarget::GetThreadContext — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetThreadContext
helpviewer_keywords:
- ICLRDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: b9d8c3b5-3a2e-4225-95d4-dd052c4532c3
topic_type:
- apiref
ms.openlocfilehash: 3777ad4b12c7d0593c095c470aba81088137a859
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179178"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="3c9d7-102">ICLRDataTarget::GetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="3c9d7-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="3c9d7-103">Pobiera bieżącego kontekstu wykonywania dla danego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="3c9d7-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="3c9d7-104">Ta metoda jest wywoływana przez usługi dostępu do danych środowiska wykonawczego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="3c9d7-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c9d7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c9d7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c9d7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c9d7-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="3c9d7-107">[w] Identyfikator systemu operacyjnego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="3c9d7-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="3c9d7-108">[w] Flagi, które określają, które części kontekstu do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="3c9d7-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="3c9d7-109">Wdrożenie zwróci co najmniej te części kontekstu.</span><span class="sxs-lookup"><span data-stu-id="3c9d7-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="3c9d7-110">[w] Rozmiar kontekstu.</span><span class="sxs-lookup"><span data-stu-id="3c9d7-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="3c9d7-111">[na zewnątrz] Wskaźnik do buforu, w którym można umieścić kontekst.</span><span class="sxs-lookup"><span data-stu-id="3c9d7-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="3c9d7-112">Dane w `context` buforze muszą być w formacie `CONTEXT` struktury Win32.</span><span class="sxs-lookup"><span data-stu-id="3c9d7-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="3c9d7-113">Kontekst określa dane rejestru specyficzne dla procesora, więc `CONTEXT` definicja struktury Win32 zależy od architektury procesora.</span><span class="sxs-lookup"><span data-stu-id="3c9d7-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="3c9d7-114">Definicję struktury Win32 `CONTEXT` można znaleźć w pliku nagłówka WinNT.h.</span><span class="sxs-lookup"><span data-stu-id="3c9d7-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c9d7-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3c9d7-115">Remarks</span></span>  
 <span data-ttu-id="3c9d7-116">Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="3c9d7-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c9d7-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3c9d7-117">Requirements</span></span>  
 <span data-ttu-id="3c9d7-118">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c9d7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c9d7-119">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="3c9d7-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="3c9d7-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c9d7-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c9d7-121">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c9d7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c9d7-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3c9d7-122">See also</span></span>

- [<span data-ttu-id="3c9d7-123">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="3c9d7-123">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
