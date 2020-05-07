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
ms.openlocfilehash: 141dc8632812ab4a2ce82864cde56337025baa28
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860582"
---
# <a name="iclrdatatargetgettlsvalue-method"></a><span data-ttu-id="5273b-102">ICLRDataTarget::GetTLSValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="5273b-102">ICLRDataTarget::GetTLSValue Method</span></span>
<span data-ttu-id="5273b-103">Pobiera wartość z lokalnego magazynu wątków (TLS) określonego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="5273b-103">Gets a value from the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="5273b-104">Ta metoda jest wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="5273b-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5273b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5273b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [out] CLRDATA_ADDRESS   *value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5273b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5273b-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="5273b-107">podczas Identyfikator systemu operacyjnego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="5273b-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="5273b-108">podczas Indeks lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="5273b-108">[in] The index of the location.</span></span> <span data-ttu-id="5273b-109">Ta wartość musi być prawidłowym indeksem w magazynie lokalnym określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="5273b-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="5273b-110">określoną Wskaźnik do `CLRDATA_ADDRESS` wartości, która określa wartość zwracaną z danej lokalizacji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="5273b-110">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the value returned from the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5273b-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5273b-111">Remarks</span></span>  
 <span data-ttu-id="5273b-112">Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="5273b-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5273b-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5273b-113">Requirements</span></span>  
 <span data-ttu-id="5273b-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5273b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5273b-115">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="5273b-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5273b-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5273b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5273b-117">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5273b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5273b-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5273b-118">See also</span></span>

- [<span data-ttu-id="5273b-119">ICLRDataTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5273b-119">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
