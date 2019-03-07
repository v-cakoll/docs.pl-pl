---
title: ICLRDataTarget::GetTLSValue — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetTLSValue
helpviewer_keywords:
- GetTLSValue method [.NET Framework debugging]
- ICLRDataTarget::GetTLSValue method [.NET Framework debugging]
ms.assetid: 0d8a7730-edc9-4728-898f-41b219cf5a28
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fbea1350c7749f67b7e0cc62378a8a520923ae8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502333"
---
# <a name="iclrdatatargetgettlsvalue-method"></a><span data-ttu-id="d7e61-102">ICLRDataTarget::GetTLSValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="d7e61-102">ICLRDataTarget::GetTLSValue Method</span></span>
<span data-ttu-id="d7e61-103">Pobiera wartość z magazynu lokalnego wątku (TLS) lub określony wątek w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="d7e61-103">Gets a value from the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="d7e61-104">Ta metoda jest wywoływana przez usługi dostępu do danych środowiska uruchomieniowego (języka wspólnego CLR) w usłudze common language.</span><span class="sxs-lookup"><span data-stu-id="d7e61-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7e61-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7e61-105">Syntax</span></span>  
  
```  
HRESULT GetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [out] CLRDATA_ADDRESS   *value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7e61-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7e61-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="d7e61-107">[in] Identyfikator systemu operacyjnego wątek w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="d7e61-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="d7e61-108">[in] Indeks lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="d7e61-108">[in] The index of the location.</span></span> <span data-ttu-id="d7e61-109">Ta wartość musi być prawidłowy indeks w lokalnym magazynie określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="d7e61-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="d7e61-110">[out] Wskaźnik do `CLRDATA_ADDRESS` wartość określa wartość zwracana z danej lokalizacji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d7e61-110">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the value returned from the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7e61-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d7e61-111">Remarks</span></span>  
 <span data-ttu-id="d7e61-112">Ta metoda jest implementowana przez moduł zapisujący debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d7e61-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7e61-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d7e61-113">Requirements</span></span>  
 <span data-ttu-id="d7e61-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7e61-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7e61-115">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="d7e61-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="d7e61-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7e61-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7e61-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7e61-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7e61-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7e61-118">See also</span></span>
- [<span data-ttu-id="d7e61-119">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="d7e61-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
