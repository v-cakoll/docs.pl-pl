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
ms.openlocfilehash: 0d34577f0f785bc851646423b8cd732ab4d1dae0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113862"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="a6435-102">ICLRDataTarget::GetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="a6435-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="a6435-103">Pobiera bieżący kontekst wykonania dla danego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="a6435-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="a6435-104">Ta metoda jest wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="a6435-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6435-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6435-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]   
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6435-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6435-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="a6435-107">podczas Identyfikator systemu operacyjnego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="a6435-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="a6435-108">podczas Flagi określające, które części kontekstu mają być zwracane.</span><span class="sxs-lookup"><span data-stu-id="a6435-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="a6435-109">Implementacja zwróci co najmniej te części kontekstu.</span><span class="sxs-lookup"><span data-stu-id="a6435-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="a6435-110">podczas Rozmiar kontekstu.</span><span class="sxs-lookup"><span data-stu-id="a6435-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="a6435-111">określoną Wskaźnik do buforu, w którym ma zostać umieszczony kontekst.</span><span class="sxs-lookup"><span data-stu-id="a6435-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="a6435-112">Dane w buforze `context` muszą mieć format struktury `CONTEXT` Win32.</span><span class="sxs-lookup"><span data-stu-id="a6435-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="a6435-113">Kontekst określa dane rejestru specyficzne dla procesora, dlatego Definicja struktury `CONTEXT` Win32 zależy od architektury procesora.</span><span class="sxs-lookup"><span data-stu-id="a6435-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="a6435-114">Zapoznaj się z plikiem nagłówkowym WinNT. h, aby uzyskać definicję struktury `CONTEXT` Win32.</span><span class="sxs-lookup"><span data-stu-id="a6435-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6435-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a6435-115">Remarks</span></span>  
 <span data-ttu-id="a6435-116">Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="a6435-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6435-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a6435-117">Requirements</span></span>  
 <span data-ttu-id="a6435-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6435-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6435-119">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="a6435-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a6435-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a6435-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6435-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6435-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6435-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6435-122">See also</span></span>

- [<span data-ttu-id="a6435-123">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="a6435-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
