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
ms.openlocfilehash: 73645265821d5854776e412f8eb0f33b36db00d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698177"
---
# <a name="iclrdatatargetgetpointersize-method"></a><span data-ttu-id="8c6c6-102">ICLRDataTarget::GetPointerSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="8c6c6-102">ICLRDataTarget::GetPointerSize Method</span></span>
<span data-ttu-id="8c6c6-103">Pobiera rozmiar w bajtach, typu wskaźnika, który używa procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="8c6c6-103">Gets the size, in bytes, of the pointer type that the target process uses.</span></span> <span data-ttu-id="8c6c6-104">Ta metoda jest wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="8c6c6-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c6c6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8c6c6-105">Syntax</span></span>  
  
```  
HRESULT GetPointerSize (  
    [out] ULONG32     *pointerSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c6c6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c6c6-106">Parameters</span></span>  
 `pointerSize`  
 <span data-ttu-id="8c6c6-107">[out] Wskaźnik do wartości całkowitej, która określa rozmiar w bajtach, wskaźnik w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="8c6c6-107">[out] A pointer to an integer value that specifies the size, in bytes, of a pointer on the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c6c6-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8c6c6-108">Remarks</span></span>  
 <span data-ttu-id="8c6c6-109">Ta metoda jest implementowana przez moduł zapisujący debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8c6c6-109">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c6c6-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8c6c6-110">Requirements</span></span>  
 <span data-ttu-id="8c6c6-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c6c6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c6c6-112">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="8c6c6-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="8c6c6-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c6c6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c6c6-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c6c6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c6c6-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c6c6-115">See also</span></span>

- [<span data-ttu-id="8c6c6-116">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="8c6c6-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
