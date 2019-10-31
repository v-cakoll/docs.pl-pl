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
ms.openlocfilehash: cceafc8358ce2b0eafa62a3855c4eb1e96adae11
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113314"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="06f50-102">ICLRDataTarget::SetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="06f50-102">ICLRDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="06f50-103">Ustawia bieżący kontekst określonego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="06f50-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="06f50-104">Ta metoda jest wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="06f50-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06f50-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="06f50-105">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]   
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06f50-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="06f50-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="06f50-107">podczas Identyfikator systemu operacyjnego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="06f50-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="06f50-108">podczas Rozmiar kontekstu.</span><span class="sxs-lookup"><span data-stu-id="06f50-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="06f50-109">podczas Wskaźnik do buforu zawierającego kontekst.</span><span class="sxs-lookup"><span data-stu-id="06f50-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="06f50-110">Dane w buforze `context` będą w formacie struktury Win32 `CONTEXT`.</span><span class="sxs-lookup"><span data-stu-id="06f50-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="06f50-111">Kontekst określa dane rejestru specyficzne dla procesora, dlatego Definicja struktury `CONTEXT` Win32 zależy od architektury procesora.</span><span class="sxs-lookup"><span data-stu-id="06f50-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="06f50-112">Zapoznaj się z plikiem nagłówkowym WinNT. h, aby uzyskać definicję struktury `CONTEXT` Win32.</span><span class="sxs-lookup"><span data-stu-id="06f50-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06f50-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06f50-113">Remarks</span></span>  
 <span data-ttu-id="06f50-114">Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="06f50-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06f50-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="06f50-115">Requirements</span></span>  
 <span data-ttu-id="06f50-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06f50-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06f50-117">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="06f50-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="06f50-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="06f50-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06f50-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06f50-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06f50-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06f50-120">See also</span></span>

- [<span data-ttu-id="06f50-121">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="06f50-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
