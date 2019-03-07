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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c2e1dc374a5205c774e4470363b38c604fa0862
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500502"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="6152a-102">ICLRDataTarget::GetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="6152a-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="6152a-103">Pobiera bieżący kontekst wykonywania dla danego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="6152a-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="6152a-104">Ta metoda jest wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="6152a-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6152a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6152a-105">Syntax</span></span>  
  
```  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]   
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6152a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6152a-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="6152a-107">[in] Identyfikator systemu operacyjnego wątek w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="6152a-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="6152a-108">[in] Flagi określające, które części kontekstu do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="6152a-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="6152a-109">Implementacja zwraca co najmniej te części kontekstu.</span><span class="sxs-lookup"><span data-stu-id="6152a-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="6152a-110">[in] Rozmiar kontekstu.</span><span class="sxs-lookup"><span data-stu-id="6152a-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="6152a-111">[out] Wskaźnik do buforu, w którym ma zostać umieszczona w kontekście.</span><span class="sxs-lookup"><span data-stu-id="6152a-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="6152a-112">Dane w `context` buforu musi być w formacie Win32 `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="6152a-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="6152a-113">Kontekst określa dane rejestru specyficznych dla procesora, więc definicji Win32 `CONTEXT` struktury jest zależna od architektury procesora.</span><span class="sxs-lookup"><span data-stu-id="6152a-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="6152a-114">Odwołuje się do pliku nagłówka pliku WinNT.h definicji Win32 `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="6152a-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6152a-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6152a-115">Remarks</span></span>  
 <span data-ttu-id="6152a-116">Ta metoda jest implementowana przez moduł zapisujący debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6152a-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6152a-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6152a-117">Requirements</span></span>  
 <span data-ttu-id="6152a-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6152a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6152a-119">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="6152a-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="6152a-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6152a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6152a-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6152a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6152a-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6152a-122">See also</span></span>
- [<span data-ttu-id="6152a-123">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="6152a-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
