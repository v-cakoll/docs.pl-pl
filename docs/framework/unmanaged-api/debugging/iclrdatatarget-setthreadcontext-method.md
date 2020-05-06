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
ms.openlocfilehash: b8c4b4e585bba4df39a743273221f38ce14a9b9d
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860535"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="ebf2c-102">ICLRDataTarget::SetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="ebf2c-102">ICLRDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="ebf2c-103">Ustawia bieżący kontekst określonego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="ebf2c-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="ebf2c-104">Ta metoda jest wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="ebf2c-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebf2c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ebf2c-105">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebf2c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ebf2c-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="ebf2c-107">podczas Identyfikator systemu operacyjnego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="ebf2c-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="ebf2c-108">podczas Rozmiar kontekstu.</span><span class="sxs-lookup"><span data-stu-id="ebf2c-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="ebf2c-109">podczas Wskaźnik do buforu zawierającego kontekst.</span><span class="sxs-lookup"><span data-stu-id="ebf2c-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="ebf2c-110">Dane w `context` buforze będą w formacie struktury Win32 `CONTEXT` .</span><span class="sxs-lookup"><span data-stu-id="ebf2c-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="ebf2c-111">Kontekst określa dane rejestru specyficzne dla procesora, dlatego Definicja struktury Win32 `CONTEXT` zależy od architektury procesora.</span><span class="sxs-lookup"><span data-stu-id="ebf2c-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="ebf2c-112">Zapoznaj się z plikiem nagłówkowym WinNT. h, aby uzyskać definicję `CONTEXT` struktury Win32.</span><span class="sxs-lookup"><span data-stu-id="ebf2c-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ebf2c-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ebf2c-113">Remarks</span></span>  
 <span data-ttu-id="ebf2c-114">Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="ebf2c-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebf2c-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ebf2c-115">Requirements</span></span>  
 <span data-ttu-id="ebf2c-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebf2c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebf2c-117">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="ebf2c-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="ebf2c-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ebf2c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebf2c-119">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebf2c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebf2c-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ebf2c-120">See also</span></span>

- [<span data-ttu-id="ebf2c-121">ICLRDataTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ebf2c-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
