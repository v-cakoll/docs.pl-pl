---
title: "ICLRDataTarget3::GetExceptionRecord — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICLRDataTarget3.GetExceptionRecord
api_location: mscordbi.dll
api_type: COM
ms.assetid: 6643c2af-2ee6-4789-aa25-1d8eaf500c94
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f8c9ac4ecc0cffda4038129b1244b81501e9a1f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a><span data-ttu-id="962e0-102">ICLRDataTarget3::GetExceptionRecord — Metoda</span><span class="sxs-lookup"><span data-stu-id="962e0-102">ICLRDataTarget3::GetExceptionRecord Method</span></span>
<span data-ttu-id="962e0-103">Wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) w celu pobrania rekordu wyjątku skojarzonego z procesem docelowym.</span><span class="sxs-lookup"><span data-stu-id="962e0-103">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span> <span data-ttu-id="962e0-104">Na przykład dla elementu docelowego zrzutu to równoważne rekordu wyjątku przekazano za pośrednictwem `ExceptionParam` argument [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360.aspx) funkcji w bibliotece systemu Windows debugowania pomocy (DbgHelp).</span><span class="sxs-lookup"><span data-stu-id="962e0-104">For example, for a dump target, this would be equivalent to the exception record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360.aspx) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="962e0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="962e0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="962e0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="962e0-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="962e0-107">[in] Rozmiar buforu wejściowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="962e0-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="962e0-108">To musi być równa `sizeof(` [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)`)`.</span><span class="sxs-lookup"><span data-stu-id="962e0-108">This must be equal to `sizeof(`[MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)`)`.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="962e0-109">[out] Wskaźnik do `ULONG32` typu, który odbiera liczba bajtów zapisana w buforze.</span><span class="sxs-lookup"><span data-stu-id="962e0-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="962e0-110">[out] Wskaźnik do buforu pamięci, który otrzyma kopię rekordu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="962e0-110">[out] A pointer to a memory buffer that receives a copy of the exception record.</span></span> <span data-ttu-id="962e0-111">Rekordu wyjątku jest zwracana jako [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) typu.</span><span class="sxs-lookup"><span data-stu-id="962e0-111">The exception record is returned as a [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="962e0-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="962e0-112">Return Value</span></span>  
 <span data-ttu-id="962e0-113">Wartość zwracana jest `S_OK` na powodzenie lub niepowodzenie `HRESULT` kod błędu.</span><span class="sxs-lookup"><span data-stu-id="962e0-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="962e0-114">`HRESULT` Mogą obejmować kody, ale nie są ograniczone do następujących:</span><span class="sxs-lookup"><span data-stu-id="962e0-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="962e0-115">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="962e0-115">Return code</span></span>|<span data-ttu-id="962e0-116">Opis</span><span class="sxs-lookup"><span data-stu-id="962e0-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="962e0-117">Metoda zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="962e0-117">Method succeeded.</span></span> <span data-ttu-id="962e0-118">Rekord wyjątek został skopiowany do buforu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="962e0-118">The exception record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="962e0-119">Nie rekordu wyjątku jest skojarzony z elementem docelowym.</span><span class="sxs-lookup"><span data-stu-id="962e0-119">No exception record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="962e0-120">Rozmiar buforu wejściowego nie jest równa `sizeof(MINIDUMP_EXCEPTION)`.</span><span class="sxs-lookup"><span data-stu-id="962e0-120">The input buffer size is not equal to `sizeof(MINIDUMP_EXCEPTION)`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="962e0-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="962e0-121">Remarks</span></span>  
 <span data-ttu-id="962e0-122">[MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) jest strukturą zdefiniowany w dbghelp.h i imagehlp.h w zestawie Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="962e0-122">[MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) is a structure defined in dbghelp.h and imagehlp.h in the Windows SDK.</span></span>  
  
 <span data-ttu-id="962e0-123">Ta metoda jest implementowany przez twórcę debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="962e0-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="962e0-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="962e0-124">Requirements</span></span>  
 <span data-ttu-id="962e0-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="962e0-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="962e0-126">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="962e0-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="962e0-127">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="962e0-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="962e0-128">**Wersje programu .NET framework:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="962e0-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="962e0-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="962e0-129">See Also</span></span>  
 [<span data-ttu-id="962e0-130">Iclrdatatarget3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="962e0-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [<span data-ttu-id="962e0-131">Metoda GetExceptionContextRecord</span><span class="sxs-lookup"><span data-stu-id="962e0-131">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)  
 [<span data-ttu-id="962e0-132">Metoda GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="962e0-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
