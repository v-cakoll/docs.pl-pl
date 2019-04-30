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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9687f6139d67a2387091367c2c72167e03be4eee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698294"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="5d019-102">ICLRDataTarget::GetCurrentThreadID — Metoda</span><span class="sxs-lookup"><span data-stu-id="5d019-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>
<span data-ttu-id="5d019-103">Pobiera identyfikator systemu operacyjnego dla bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="5d019-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d019-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d019-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d019-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d019-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="5d019-106">[out] Wskaźnik do systemu operacyjnego identyfikator bieżącego wątku dla procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="5d019-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d019-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d019-107">Remarks</span></span>  
 <span data-ttu-id="5d019-108">Jeśli nie bieżącego wątku dla procesu docelowego `GetCurrentThreadID` metoda może zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="5d019-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d019-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5d019-109">Requirements</span></span>  
 <span data-ttu-id="5d019-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d019-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d019-111">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="5d019-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5d019-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d019-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d019-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d019-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d019-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d019-114">See also</span></span>

- [<span data-ttu-id="5d019-115">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="5d019-115">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
