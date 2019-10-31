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
ms.openlocfilehash: 1425d48bb18d4161a1c96239b76b8315ae258705
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73112779"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="e61aa-102">ICLRDataTarget::SetTLSValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="e61aa-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="e61aa-103">Ustawia wartość w ramach wątku lokalnego magazynu (TLS) określonego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="e61aa-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="e61aa-104">Ta metoda jest wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="e61aa-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e61aa-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e61aa-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e61aa-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e61aa-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="e61aa-107">podczas Identyfikator systemu operacyjnego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="e61aa-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="e61aa-108">podczas Indeks lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="e61aa-108">[in] The index of the location.</span></span> <span data-ttu-id="e61aa-109">Ta wartość musi być prawidłowym indeksem w magazynie lokalnym określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="e61aa-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="e61aa-110">podczas Wartość `CLRDATA_ADDRESS`, która określa wartość do umieszczenia w danej lokalizacji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="e61aa-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e61aa-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e61aa-111">Remarks</span></span>  
 <span data-ttu-id="e61aa-112">Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="e61aa-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e61aa-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e61aa-113">Requirements</span></span>  
 <span data-ttu-id="e61aa-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e61aa-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e61aa-115">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="e61aa-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e61aa-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e61aa-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e61aa-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e61aa-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e61aa-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e61aa-118">See also</span></span>

- [<span data-ttu-id="e61aa-119">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="e61aa-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
