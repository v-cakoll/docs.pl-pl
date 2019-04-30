---
title: ICLRDataTarget::SetTLSValue — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetTLSValue
helpviewer_keywords:
- ICLRDataTarget::SetTLSValue method [.NET Framework debugging]
- SetTLSValue method [.NET Framework debugging]
ms.assetid: 4a2d6a24-749a-47ad-9f01-4517203d3f35
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c0be35772b10d89f90da5b33f47aa781034b13a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698086"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="0a0f2-102">ICLRDataTarget::SetTLSValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="0a0f2-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="0a0f2-103">Ustawia wartość w pamięci lokalnej wątku (TLS) określony wątek w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="0a0f2-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="0a0f2-104">Ta metoda jest wywoływana przez usługi dostępu do danych środowiska uruchomieniowego (języka wspólnego CLR) w usłudze common language.</span><span class="sxs-lookup"><span data-stu-id="0a0f2-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a0f2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0a0f2-105">Syntax</span></span>  
  
```  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a0f2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a0f2-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="0a0f2-107">[in] Identyfikator systemu operacyjnego wątek w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="0a0f2-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="0a0f2-108">[in] Indeks lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="0a0f2-108">[in] The index of the location.</span></span> <span data-ttu-id="0a0f2-109">Ta wartość musi być prawidłowy indeks w lokalnym magazynie określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="0a0f2-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="0a0f2-110">[in] A `CLRDATA_ADDRESS` wartość, która określa wartości do umieszczenia w danej lokalizacji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="0a0f2-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a0f2-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0a0f2-111">Remarks</span></span>  
 <span data-ttu-id="0a0f2-112">Ta metoda jest implementowana przez moduł zapisujący debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0a0f2-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a0f2-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0a0f2-113">Requirements</span></span>  
 <span data-ttu-id="0a0f2-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a0f2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a0f2-115">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="0a0f2-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="0a0f2-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a0f2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a0f2-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a0f2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a0f2-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a0f2-118">See also</span></span>

- [<span data-ttu-id="0a0f2-119">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="0a0f2-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
