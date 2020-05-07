---
title: ICLRDataTarget::GetCurrentThreadID — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetCurrentThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::GetCurrentThreadID method [.NET Framework debugging]
ms.assetid: dc9a0a6c-d592-4fb7-86ed-62684da3b0e1
topic_type:
- apiref
ms.openlocfilehash: c75c55b64ff20728bc5695d0ddfe1b4f6deda4a6
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860650"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="fd7d2-102">ICLRDataTarget::GetCurrentThreadID — Metoda</span><span class="sxs-lookup"><span data-stu-id="fd7d2-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>
<span data-ttu-id="fd7d2-103">Pobiera identyfikator systemu operacyjnego dla bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="fd7d2-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd7d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd7d2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd7d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fd7d2-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="fd7d2-106">określoną Wskaźnik do identyfikatora systemu operacyjnego bieżącego wątku dla procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="fd7d2-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd7d2-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fd7d2-107">Remarks</span></span>  
 <span data-ttu-id="fd7d2-108">Jeśli nie ma bieżącego wątku dla procesu docelowego, `GetCurrentThreadID` Metoda może zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="fd7d2-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd7d2-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fd7d2-109">Requirements</span></span>  
 <span data-ttu-id="fd7d2-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd7d2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd7d2-111">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="fd7d2-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="fd7d2-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fd7d2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd7d2-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd7d2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd7d2-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd7d2-114">See also</span></span>

- [<span data-ttu-id="fd7d2-115">ICLRDataTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fd7d2-115">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
