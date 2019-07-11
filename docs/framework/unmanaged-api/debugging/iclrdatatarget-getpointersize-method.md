---
title: ICLRDataTarget::GetPointerSize — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetPointerSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetPointerSize
helpviewer_keywords:
- GetPointerSize method [.NET Framework debugging]
- ICLRDataTarget::GetPointerSize method [.NET Framework debugging]
ms.assetid: 51d9f4a4-81a7-4527-8537-5212bdb05c70
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54abcd357c6f26f54432b39bfcb4a0d63afabfe4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738715"
---
# <a name="iclrdatatargetgetpointersize-method"></a><span data-ttu-id="fb9df-102">ICLRDataTarget::GetPointerSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="fb9df-102">ICLRDataTarget::GetPointerSize Method</span></span>
<span data-ttu-id="fb9df-103">Pobiera rozmiar w bajtach, typu wskaźnika, który używa procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="fb9df-103">Gets the size, in bytes, of the pointer type that the target process uses.</span></span> <span data-ttu-id="fb9df-104">Ta metoda jest wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="fb9df-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb9df-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb9df-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPointerSize (  
    [out] ULONG32     *pointerSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb9df-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb9df-106">Parameters</span></span>  
 `pointerSize`  
 <span data-ttu-id="fb9df-107">[out] Wskaźnik do wartości całkowitej, która określa rozmiar w bajtach, wskaźnik w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="fb9df-107">[out] A pointer to an integer value that specifies the size, in bytes, of a pointer on the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb9df-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb9df-108">Remarks</span></span>  
 <span data-ttu-id="fb9df-109">Ta metoda jest implementowana przez moduł zapisujący debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fb9df-109">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb9df-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fb9df-110">Requirements</span></span>  
 <span data-ttu-id="fb9df-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb9df-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb9df-112">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="fb9df-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="fb9df-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb9df-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb9df-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb9df-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb9df-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb9df-115">See also</span></span>

- [<span data-ttu-id="fb9df-116">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="fb9df-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
