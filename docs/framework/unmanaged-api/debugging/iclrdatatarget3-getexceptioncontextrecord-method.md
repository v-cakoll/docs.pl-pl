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
ms.openlocfilehash: 4c2e645222553f4000b300fa4f010ff81ff44d23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a><span data-ttu-id="13195-102">Metoda ICLRDataTarget3::GetExceptionContextRecord</span><span class="sxs-lookup"><span data-stu-id="13195-102">ICLRDataTarget3::GetExceptionContextRecord Method</span></span>
<span data-ttu-id="13195-103">Metoda wywoływana przez wspólne języka wspólnego (CLR) danych dostęp do usługi można pobrać rekordu kontekstu skojarzonych z procesem docelowym.</span><span class="sxs-lookup"><span data-stu-id="13195-103">Called by the common language runtime (CLR) data access services to retrieve the context record associated with the target process.</span></span> <span data-ttu-id="13195-104">Na przykład dla elementu docelowego zrzutu to równoważne rekordu kontekstu przekazano za pośrednictwem `ExceptionParam` argument [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360\(v=vs.85\).aspx) funkcji w bibliotece systemu Windows debugowania pomocy (DbgHelp).</span><span class="sxs-lookup"><span data-stu-id="13195-104">For example, for a dump target, this would be equivalent to the context record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360\(v=vs.85\).aspx) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13195-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="13195-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13195-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="13195-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="13195-107">[in] Rozmiar buforu wejściowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="13195-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="13195-108">Musi to być wystarczająco duży, aby pomieścić rekordu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="13195-108">This must be large enough to accommodate the context record.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="13195-109">[out] Wskaźnik do `ULONG32` typu, który odbiera liczba bajtów zapisana w buforze.</span><span class="sxs-lookup"><span data-stu-id="13195-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="13195-110">[out] Wskaźnik do buforu pamięci, który otrzyma kopię rekordu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="13195-110">[out] A pointer to a memory buffer that receives a copy of the context record.</span></span> <span data-ttu-id="13195-111">Rekordu wyjątku jest zwracana jako [KONTEKSTU](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) typu.</span><span class="sxs-lookup"><span data-stu-id="13195-111">The exception record is returned as a [CONTEXT](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13195-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="13195-112">Return Value</span></span>  
 <span data-ttu-id="13195-113">Wartość zwracana jest `S_OK` na powodzenie lub niepowodzenie `HRESULT` kod błędu.</span><span class="sxs-lookup"><span data-stu-id="13195-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="13195-114">`HRESULT` Mogą obejmować kody, ale nie są ograniczone do następujących:</span><span class="sxs-lookup"><span data-stu-id="13195-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="13195-115">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="13195-115">Return code</span></span>|<span data-ttu-id="13195-116">Opis</span><span class="sxs-lookup"><span data-stu-id="13195-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="13195-117">Metoda zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="13195-117">Method succeeded.</span></span> <span data-ttu-id="13195-118">Rekordu kontekstu został skopiowany do buforu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="13195-118">The context record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="13195-119">Nie rekordu kontekstu jest skojarzony z elementem docelowym.</span><span class="sxs-lookup"><span data-stu-id="13195-119">No context record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="13195-120">Rozmiar buforu wejściowego nie jest wystarczająco duży, aby pomieścić rekordu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="13195-120">The input buffer size is not large enough to accommodate the context record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13195-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13195-121">Remarks</span></span>  
 <span data-ttu-id="13195-122">[KONTEKST](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) jest strukturą specyficzne dla platformy zdefiniowane w nagłówki udostępnione przez zestaw Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="13195-122">[CONTEXT](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) is a platform-specific structure defined in headers provided by the Windows SDK.</span></span>  
  
 <span data-ttu-id="13195-123">Ta metoda jest implementowany przez twórcę debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="13195-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13195-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="13195-124">Requirements</span></span>  
 <span data-ttu-id="13195-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13195-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13195-126">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="13195-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="13195-127">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13195-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13195-128">**Wersje programu .NET framework:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13195-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13195-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13195-129">See Also</span></span>  
 [<span data-ttu-id="13195-130">Iclrdatatarget3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="13195-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [<span data-ttu-id="13195-131">GetExceptionRecord — metoda</span><span class="sxs-lookup"><span data-stu-id="13195-131">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)  
 [<span data-ttu-id="13195-132">Metoda GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="13195-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
