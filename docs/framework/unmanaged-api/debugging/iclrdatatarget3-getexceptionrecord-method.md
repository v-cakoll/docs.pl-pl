---
title: ICLRDataTarget3::GetExceptionRecord — Metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6643c2af-2ee6-4789-aa25-1d8eaf500c94
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7966cfb6e775bee567221eef2a5d99b90399f322
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697917"
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a><span data-ttu-id="13947-102">ICLRDataTarget3::GetExceptionRecord — Metoda</span><span class="sxs-lookup"><span data-stu-id="13947-102">ICLRDataTarget3::GetExceptionRecord Method</span></span>
<span data-ttu-id="13947-103">Wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) w celu pobrania rekordu wyjątku skojarzonego z procesem docelowym.</span><span class="sxs-lookup"><span data-stu-id="13947-103">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span> <span data-ttu-id="13947-104">Na przykład dla elementu docelowego zrzutu jest to równoważne z rekordu wyjątku przekazaną za pomocą `ExceptionParam` argument [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) funkcji w Windows debugowania pomóc w bibliotece (DbgHelp).</span><span class="sxs-lookup"><span data-stu-id="13947-104">For example, for a dump target, this would be equivalent to the exception record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13947-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="13947-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13947-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="13947-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="13947-107">[in] Rozmiar buforu wejściowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="13947-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="13947-108">To musi być równa `sizeof(` [MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception)`)`.</span><span class="sxs-lookup"><span data-stu-id="13947-108">This must be equal to `sizeof(`[MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception)`)`.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="13947-109">[out] Wskaźnik do `ULONG32` typu, który odbiera liczbę bajtów, które rzeczywiście zapisanych w buforze.</span><span class="sxs-lookup"><span data-stu-id="13947-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="13947-110">[out] Wskaźnik do buforu pamięci, który otrzymuje kopię rekordu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="13947-110">[out] A pointer to a memory buffer that receives a copy of the exception record.</span></span> <span data-ttu-id="13947-111">Rekordu wyjątku jest zwracana jako [MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception) typu.</span><span class="sxs-lookup"><span data-stu-id="13947-111">The exception record is returned as a [MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13947-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="13947-112">Return Value</span></span>  
 <span data-ttu-id="13947-113">Wartość zwracana jest `S_OK` na powodzenie lub niepowodzenie `HRESULT` kod błędu.</span><span class="sxs-lookup"><span data-stu-id="13947-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="13947-114">`HRESULT` Mogą obejmować kody, ale nie są ograniczone do następujących:</span><span class="sxs-lookup"><span data-stu-id="13947-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="13947-115">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="13947-115">Return code</span></span>|<span data-ttu-id="13947-116">Opis</span><span class="sxs-lookup"><span data-stu-id="13947-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="13947-117">Metody powiodło się.</span><span class="sxs-lookup"><span data-stu-id="13947-117">Method succeeded.</span></span> <span data-ttu-id="13947-118">Rekordu wyjątku został skopiowany do buforu danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="13947-118">The exception record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="13947-119">Nie rekordu wyjątku jest skojarzony z obiektem docelowym.</span><span class="sxs-lookup"><span data-stu-id="13947-119">No exception record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="13947-120">Rozmiar buforu wejściowego nie jest równa `sizeof(MINIDUMP_EXCEPTION)`.</span><span class="sxs-lookup"><span data-stu-id="13947-120">The input buffer size is not equal to `sizeof(MINIDUMP_EXCEPTION)`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13947-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13947-121">Remarks</span></span>  
 <span data-ttu-id="13947-122">[MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception) jest strukturą, który został zdefiniowany w dbghelp.h i imagehlp.h w zestawie Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="13947-122">[MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception) is a structure defined in dbghelp.h and imagehlp.h in the Windows SDK.</span></span>  
  
 <span data-ttu-id="13947-123">Ta metoda jest implementowana przez moduł zapisujący debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="13947-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13947-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="13947-124">Requirements</span></span>  
 <span data-ttu-id="13947-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13947-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13947-126">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="13947-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="13947-127">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13947-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13947-128">**Wersje programu .NET framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="13947-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13947-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13947-129">See also</span></span>

- [<span data-ttu-id="13947-130">ICLRDataTarget3, interfejs</span><span class="sxs-lookup"><span data-stu-id="13947-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [<span data-ttu-id="13947-131">GetExceptionContextRecord, metoda</span><span class="sxs-lookup"><span data-stu-id="13947-131">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="13947-132">GetExceptionThreadID, metoda</span><span class="sxs-lookup"><span data-stu-id="13947-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
