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
ms.openlocfilehash: 35515d7c2b82ec2c42461406363964e0b60eb243
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785468"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="5b942-102">ICLRDataTarget::GetCurrentThreadID — Metoda</span><span class="sxs-lookup"><span data-stu-id="5b942-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>
<span data-ttu-id="5b942-103">Pobiera identyfikator systemu operacyjnego dla bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="5b942-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b942-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5b942-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b942-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b942-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="5b942-106">określoną Wskaźnik do identyfikatora systemu operacyjnego bieżącego wątku dla procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="5b942-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b942-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5b942-107">Remarks</span></span>  
 <span data-ttu-id="5b942-108">Jeśli nie ma bieżącego wątku dla procesu docelowego, Metoda `GetCurrentThreadID` może zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="5b942-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b942-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5b942-109">Requirements</span></span>  
 <span data-ttu-id="5b942-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b942-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b942-111">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="5b942-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5b942-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5b942-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b942-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b942-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b942-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b942-114">See also</span></span>

- [<span data-ttu-id="5b942-115">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="5b942-115">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
