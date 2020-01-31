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
ms.openlocfilehash: b5f6a830cbe601443f03cd91a356c7e49450e7f3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793729"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="561ae-102">ICLRDataTarget::GetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="561ae-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="561ae-103">Pobiera bieżący kontekst wykonania dla danego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="561ae-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="561ae-104">Ta metoda jest wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="561ae-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="561ae-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="561ae-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]   
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="561ae-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="561ae-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="561ae-107">podczas Identyfikator systemu operacyjnego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="561ae-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="561ae-108">podczas Flagi określające, które części kontekstu mają być zwracane.</span><span class="sxs-lookup"><span data-stu-id="561ae-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="561ae-109">Implementacja zwróci co najmniej te części kontekstu.</span><span class="sxs-lookup"><span data-stu-id="561ae-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="561ae-110">podczas Rozmiar kontekstu.</span><span class="sxs-lookup"><span data-stu-id="561ae-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="561ae-111">określoną Wskaźnik do buforu, w którym ma zostać umieszczony kontekst.</span><span class="sxs-lookup"><span data-stu-id="561ae-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="561ae-112">Dane w buforze `context` muszą mieć format struktury `CONTEXT` Win32.</span><span class="sxs-lookup"><span data-stu-id="561ae-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="561ae-113">Kontekst określa dane rejestru specyficzne dla procesora, dlatego Definicja struktury `CONTEXT` Win32 zależy od architektury procesora.</span><span class="sxs-lookup"><span data-stu-id="561ae-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="561ae-114">Zapoznaj się z plikiem nagłówkowym WinNT. h, aby uzyskać definicję struktury `CONTEXT` Win32.</span><span class="sxs-lookup"><span data-stu-id="561ae-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="561ae-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="561ae-115">Remarks</span></span>  
 <span data-ttu-id="561ae-116">Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="561ae-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="561ae-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="561ae-117">Requirements</span></span>  
 <span data-ttu-id="561ae-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="561ae-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="561ae-119">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="561ae-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="561ae-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="561ae-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="561ae-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="561ae-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="561ae-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="561ae-122">See also</span></span>

- [<span data-ttu-id="561ae-123">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="561ae-123">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
