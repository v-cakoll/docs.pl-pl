---
title: ICLRDataTarget::Request — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.Request
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::Request
helpviewer_keywords:
- ICLRDataTarget::Request method [.NET Framework debugging]
- Request method [.NET Framework debugging]
ms.assetid: 4723bd1c-eddb-4ed2-897a-010024a47e01
topic_type:
- apiref
ms.openlocfilehash: 0a7e764d89dd42bcaf81da5cf6a16991b6b8a16e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793705"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="e5d7d-102">ICLRDataTarget::Request — Metoda</span><span class="sxs-lookup"><span data-stu-id="e5d7d-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="e5d7d-103">Wywoływane przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) do żądania operacji zgodnie z definicją w implementacji.</span><span class="sxs-lookup"><span data-stu-id="e5d7d-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5d7d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5d7d-104">Syntax</span></span>  
  
```cpp  
HRESULT Request (  
    [in] ULONG32            reqCode,  
    [in] ULONG32            inBufferSize,  
    [in, size_is(inBufferSize)]   
        BYTE                *inBuffer,  
    [in] ULONG32            outBufferSize,  
    [out, size_is(outBufferSize)]   
        BYTE                *outBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5d7d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5d7d-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="e5d7d-106">podczas Zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e5d7d-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="e5d7d-107">podczas Rozmiar buforu wejściowego, który jest używany w żądaniu przychodzącym.</span><span class="sxs-lookup"><span data-stu-id="e5d7d-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="e5d7d-108">podczas Bufor zawierający żądanie.</span><span class="sxs-lookup"><span data-stu-id="e5d7d-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="e5d7d-109">podczas Rozmiar buforu wyjściowego, który jest używany na potrzeby odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="e5d7d-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="e5d7d-110">określoną Bufor zawierający odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="e5d7d-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5d7d-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5d7d-111">Remarks</span></span>  
 <span data-ttu-id="e5d7d-112">Metoda `Request` ułatwia dodawanie nieokreślonych operacji niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="e5d7d-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="e5d7d-113">Oznacza to, że ta metoda zapewnia rozszerzalność bez konieczności zmiany definicji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e5d7d-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="e5d7d-114">Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="e5d7d-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5d7d-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5d7d-115">Requirements</span></span>  
 <span data-ttu-id="e5d7d-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5d7d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5d7d-117">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="e5d7d-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e5d7d-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e5d7d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5d7d-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5d7d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5d7d-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5d7d-120">See also</span></span>

- [<span data-ttu-id="e5d7d-121">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="e5d7d-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
