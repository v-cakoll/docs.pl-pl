---
title: "ICLRDataTarget::GetTLSValue — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.GetTLSValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::GetTLSValue
helpviewer_keywords:
- GetTLSValue method [.NET Framework debugging]
- ICLRDataTarget::GetTLSValue method [.NET Framework debugging]
ms.assetid: 0d8a7730-edc9-4728-898f-41b219cf5a28
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a820ec7c0a00306266be432a8aceacb3d30d1b4f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetgettlsvalue-method"></a><span data-ttu-id="c8397-102">ICLRDataTarget::GetTLSValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="c8397-102">ICLRDataTarget::GetTLSValue Method</span></span>
<span data-ttu-id="c8397-103">Pobiera wartość z lokalny magazyn wątków (TLS) z określonego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="c8397-103">Gets a value from the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="c8397-104">Ta metoda jest wywoływana przez wspólne usługi dostępu do danych języka środowiska uruchomieniowego (języka wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="c8397-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8397-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c8397-105">Syntax</span></span>  
  
```  
HRESULT GetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [out] CLRDATA_ADDRESS   *value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8397-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c8397-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="c8397-107">[in] System operacyjny identyfikator wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="c8397-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="c8397-108">[in] Indeks lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="c8397-108">[in] The index of the location.</span></span> <span data-ttu-id="c8397-109">Ta wartość musi być prawidłowym indeksem w lokalnym magazynie określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="c8397-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="c8397-110">[out] Wskaźnik do `CLRDATA_ADDRESS` wartość określającą wartość zwracana z danej lokalizacji TLS.</span><span class="sxs-lookup"><span data-stu-id="c8397-110">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the value returned from the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8397-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c8397-111">Remarks</span></span>  
 <span data-ttu-id="c8397-112">Ta metoda jest implementowany przez twórcę debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c8397-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8397-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c8397-113">Requirements</span></span>  
 <span data-ttu-id="c8397-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8397-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8397-115">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="c8397-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c8397-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8397-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8397-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8397-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8397-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8397-118">See Also</span></span>  
 [<span data-ttu-id="c8397-119">ICLRDataTarget — interfejs</span><span class="sxs-lookup"><span data-stu-id="c8397-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
