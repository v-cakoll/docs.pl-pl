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
ms.openlocfilehash: 5c0fb023dd355f3a9c1ed846913f86b354592ed5
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860608"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="47eda-102">ICLRDataTarget::GetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="47eda-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="47eda-103">Pobiera bieżący kontekst wykonania dla danego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="47eda-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="47eda-104">Ta metoda jest wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="47eda-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47eda-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="47eda-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47eda-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="47eda-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="47eda-107">podczas Identyfikator systemu operacyjnego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="47eda-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="47eda-108">podczas Flagi określające, które części kontekstu mają być zwracane.</span><span class="sxs-lookup"><span data-stu-id="47eda-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="47eda-109">Implementacja zwróci co najmniej te części kontekstu.</span><span class="sxs-lookup"><span data-stu-id="47eda-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="47eda-110">podczas Rozmiar kontekstu.</span><span class="sxs-lookup"><span data-stu-id="47eda-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="47eda-111">określoną Wskaźnik do buforu, w którym ma zostać umieszczony kontekst.</span><span class="sxs-lookup"><span data-stu-id="47eda-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="47eda-112">Dane w `context` buforze muszą mieć format struktury Win32 `CONTEXT` .</span><span class="sxs-lookup"><span data-stu-id="47eda-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="47eda-113">Kontekst określa dane rejestru specyficzne dla procesora, dlatego Definicja struktury Win32 `CONTEXT` zależy od architektury procesora.</span><span class="sxs-lookup"><span data-stu-id="47eda-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="47eda-114">Zapoznaj się z plikiem nagłówkowym WinNT. h, aby uzyskać definicję `CONTEXT` struktury Win32.</span><span class="sxs-lookup"><span data-stu-id="47eda-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47eda-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="47eda-115">Remarks</span></span>  
 <span data-ttu-id="47eda-116">Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="47eda-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47eda-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="47eda-117">Requirements</span></span>  
 <span data-ttu-id="47eda-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47eda-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47eda-119">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="47eda-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="47eda-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="47eda-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47eda-121">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47eda-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47eda-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47eda-122">See also</span></span>

- [<span data-ttu-id="47eda-123">ICLRDataTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="47eda-123">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
