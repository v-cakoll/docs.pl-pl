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
ms.openlocfilehash: e6c4d5f8cc911198add176cab9c4b9b89128068e
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860624"
---
# <a name="iclrdatatargetgetpointersize-method"></a><span data-ttu-id="daef1-102">ICLRDataTarget::GetPointerSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="daef1-102">ICLRDataTarget::GetPointerSize Method</span></span>
<span data-ttu-id="daef1-103">Pobiera rozmiar (w bajtach) typu wskaźnika, który jest wykorzystywany przez proces docelowy.</span><span class="sxs-lookup"><span data-stu-id="daef1-103">Gets the size, in bytes, of the pointer type that the target process uses.</span></span> <span data-ttu-id="daef1-104">Ta metoda jest wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="daef1-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daef1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="daef1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPointerSize (  
    [out] ULONG32     *pointerSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="daef1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="daef1-106">Parameters</span></span>  
 `pointerSize`  
 <span data-ttu-id="daef1-107">określoną Wskaźnik do wartości całkowitej, która określa rozmiar (w bajtach) wskaźnika w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="daef1-107">[out] A pointer to an integer value that specifies the size, in bytes, of a pointer on the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="daef1-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="daef1-108">Remarks</span></span>  
 <span data-ttu-id="daef1-109">Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="daef1-109">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daef1-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="daef1-110">Requirements</span></span>  
 <span data-ttu-id="daef1-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="daef1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daef1-112">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="daef1-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="daef1-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="daef1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="daef1-114">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daef1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daef1-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="daef1-115">See also</span></span>

- [<span data-ttu-id="daef1-116">ICLRDataTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="daef1-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
