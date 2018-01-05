---
title: Metoda ICLRDataTarget3::GetExceptionContextRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICLRDataTarget3.GetContextRecord
api_location: mscordbi.dll
api_type: COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 517e2a692c3b67a85bc24437dd5fbaedd5fc7254
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a><span data-ttu-id="de7c9-102">Metoda ICLRDataTarget3::GetExceptionContextRecord</span><span class="sxs-lookup"><span data-stu-id="de7c9-102">ICLRDataTarget3::GetExceptionContextRecord Method</span></span>
<span data-ttu-id="de7c9-103">Metoda wywoływana przez wspólne języka wspólnego (CLR) danych dostęp do usługi można pobrać rekordu kontekstu skojarzonych z procesem docelowym.</span><span class="sxs-lookup"><span data-stu-id="de7c9-103">Called by the common language runtime (CLR) data access services to retrieve the context record associated with the target process.</span></span> <span data-ttu-id="de7c9-104">Na przykład dla elementu docelowego zrzutu to równoważne rekordu kontekstu przekazano za pośrednictwem `ExceptionParam` argument [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360\(v=vs.85\).aspx) funkcji w bibliotece systemu Windows debugowania pomocy (DbgHelp).</span><span class="sxs-lookup"><span data-stu-id="de7c9-104">For example, for a dump target, this would be equivalent to the context record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360\(v=vs.85\).aspx) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de7c9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="de7c9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de7c9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="de7c9-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="de7c9-107">[in] Rozmiar buforu wejściowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="de7c9-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="de7c9-108">Musi to być wystarczająco duży, aby pomieścić rekordu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="de7c9-108">This must be large enough to accommodate the context record.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="de7c9-109">[out] Wskaźnik do `ULONG32` typu, który odbiera liczba bajtów zapisana w buforze.</span><span class="sxs-lookup"><span data-stu-id="de7c9-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="de7c9-110">[out] Wskaźnik do buforu pamięci, który otrzyma kopię rekordu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="de7c9-110">[out] A pointer to a memory buffer that receives a copy of the context record.</span></span> <span data-ttu-id="de7c9-111">Rekordu wyjątku jest zwracana jako [KONTEKSTU](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) typu.</span><span class="sxs-lookup"><span data-stu-id="de7c9-111">The exception record is returned as a [CONTEXT](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de7c9-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="de7c9-112">Return Value</span></span>  
 <span data-ttu-id="de7c9-113">Wartość zwracana jest `S_OK` na powodzenie lub niepowodzenie `HRESULT` kod błędu.</span><span class="sxs-lookup"><span data-stu-id="de7c9-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="de7c9-114">`HRESULT` Mogą obejmować kody, ale nie są ograniczone do następujących:</span><span class="sxs-lookup"><span data-stu-id="de7c9-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="de7c9-115">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="de7c9-115">Return code</span></span>|<span data-ttu-id="de7c9-116">Opis</span><span class="sxs-lookup"><span data-stu-id="de7c9-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="de7c9-117">Metoda zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="de7c9-117">Method succeeded.</span></span> <span data-ttu-id="de7c9-118">Rekordu kontekstu został skopiowany do buforu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="de7c9-118">The context record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="de7c9-119">Nie rekordu kontekstu jest skojarzony z elementem docelowym.</span><span class="sxs-lookup"><span data-stu-id="de7c9-119">No context record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="de7c9-120">Rozmiar buforu wejściowego nie jest wystarczająco duży, aby pomieścić rekordu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="de7c9-120">The input buffer size is not large enough to accommodate the context record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de7c9-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="de7c9-121">Remarks</span></span>  
 <span data-ttu-id="de7c9-122">[KONTEKST](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) jest strukturą specyficzne dla platformy zdefiniowane w nagłówki udostępnione przez zestaw Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="de7c9-122">[CONTEXT](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) is a platform-specific structure defined in headers provided by the Windows SDK.</span></span>  
  
 <span data-ttu-id="de7c9-123">Ta metoda jest implementowany przez twórcę debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="de7c9-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de7c9-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="de7c9-124">Requirements</span></span>  
 <span data-ttu-id="de7c9-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de7c9-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de7c9-126">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="de7c9-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="de7c9-127">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de7c9-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de7c9-128">**Wersje programu .NET framework:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de7c9-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de7c9-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="de7c9-129">See Also</span></span>  
 [<span data-ttu-id="de7c9-130">ICLRDataTarget3, interfejs</span><span class="sxs-lookup"><span data-stu-id="de7c9-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [<span data-ttu-id="de7c9-131">GetExceptionRecord, metoda</span><span class="sxs-lookup"><span data-stu-id="de7c9-131">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)  
 [<span data-ttu-id="de7c9-132">GetExceptionThreadID, metoda</span><span class="sxs-lookup"><span data-stu-id="de7c9-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
