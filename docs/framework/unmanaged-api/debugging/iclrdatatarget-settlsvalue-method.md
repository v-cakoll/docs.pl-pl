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
ms.openlocfilehash: 6e6e157c7176a0f4f1ad3c585977e2cfb31c33d8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793688"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="825ad-102">ICLRDataTarget::SetTLSValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="825ad-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="825ad-103">Ustawia wartość w ramach wątku lokalnego magazynu (TLS) określonego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="825ad-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="825ad-104">Ta metoda jest wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="825ad-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="825ad-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="825ad-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="825ad-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="825ad-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="825ad-107">podczas Identyfikator systemu operacyjnego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="825ad-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="825ad-108">podczas Indeks lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="825ad-108">[in] The index of the location.</span></span> <span data-ttu-id="825ad-109">Ta wartość musi być prawidłowym indeksem w magazynie lokalnym określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="825ad-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="825ad-110">podczas Wartość `CLRDATA_ADDRESS`, która określa wartość do umieszczenia w danej lokalizacji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="825ad-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="825ad-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="825ad-111">Remarks</span></span>  
 <span data-ttu-id="825ad-112">Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="825ad-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="825ad-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="825ad-113">Requirements</span></span>  
 <span data-ttu-id="825ad-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="825ad-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="825ad-115">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="825ad-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="825ad-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="825ad-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="825ad-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="825ad-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="825ad-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="825ad-118">See also</span></span>

- [<span data-ttu-id="825ad-119">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="825ad-119">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
