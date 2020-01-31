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
ms.openlocfilehash: 037e216cb93e3aa6fce28966fc724498024abd52
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789057"
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a><span data-ttu-id="c88b7-102">ICLRDataTarget3::GetExceptionRecord — Metoda</span><span class="sxs-lookup"><span data-stu-id="c88b7-102">ICLRDataTarget3::GetExceptionRecord Method</span></span>
<span data-ttu-id="c88b7-103">Wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) w celu pobrania rekordu wyjątku skojarzonego z procesem docelowym.</span><span class="sxs-lookup"><span data-stu-id="c88b7-103">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span> <span data-ttu-id="c88b7-104">Na przykład dla elementu docelowego zrzutu będzie to odpowiednik rekordu wyjątku przekazanego za pośrednictwem argumentu `ExceptionParam` do funkcji [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) w bibliotece pomocy debugowania systemu Windows (dbghelp).</span><span class="sxs-lookup"><span data-stu-id="c88b7-104">For example, for a dump target, this would be equivalent to the exception record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c88b7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c88b7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c88b7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c88b7-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="c88b7-107">podczas Rozmiar buforu wejściowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="c88b7-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="c88b7-108">Ta wartość musi być taka sama jak `sizeof(`[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception)`)`.</span><span class="sxs-lookup"><span data-stu-id="c88b7-108">This must be equal to `sizeof(`[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception)`)`.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="c88b7-109">określoną Wskaźnik do typu `ULONG32`, który odbiera liczbę bajtów rzeczywiście zapisywanych w buforze.</span><span class="sxs-lookup"><span data-stu-id="c88b7-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="c88b7-110">określoną Wskaźnik do bufora pamięci, który otrzymuje kopię rekordu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c88b7-110">[out] A pointer to a memory buffer that receives a copy of the exception record.</span></span> <span data-ttu-id="c88b7-111">Rekord wyjątku jest zwracany jako typ [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) .</span><span class="sxs-lookup"><span data-stu-id="c88b7-111">The exception record is returned as a [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c88b7-112">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="c88b7-112">Return Value</span></span>  
 <span data-ttu-id="c88b7-113">Wartość zwracana jest `S_OK` w przypadku sukcesu lub niepowodzenie `HRESULT` kod w przypadku niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="c88b7-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="c88b7-114">Kody `HRESULT` mogą zawierać, ale nie są ograniczone do następujących:</span><span class="sxs-lookup"><span data-stu-id="c88b7-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="c88b7-115">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="c88b7-115">Return code</span></span>|<span data-ttu-id="c88b7-116">Opis</span><span class="sxs-lookup"><span data-stu-id="c88b7-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="c88b7-117">Metoda powiodła się.</span><span class="sxs-lookup"><span data-stu-id="c88b7-117">Method succeeded.</span></span> <span data-ttu-id="c88b7-118">Rekord wyjątku został skopiowany do buforu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="c88b7-118">The exception record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="c88b7-119">Z elementem docelowym nie jest skojarzony żaden rekord wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c88b7-119">No exception record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="c88b7-120">Rozmiar buforu wejściowego nie jest równy `sizeof(MINIDUMP_EXCEPTION)`.</span><span class="sxs-lookup"><span data-stu-id="c88b7-120">The input buffer size is not equal to `sizeof(MINIDUMP_EXCEPTION)`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c88b7-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c88b7-121">Remarks</span></span>  
 <span data-ttu-id="c88b7-122">[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) to struktura zdefiniowana w dbghelp. h i Imagehlp. h w Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="c88b7-122">[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) is a structure defined in dbghelp.h and imagehlp.h in the Windows SDK.</span></span>  
  
 <span data-ttu-id="c88b7-123">Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="c88b7-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c88b7-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c88b7-124">Requirements</span></span>  
 <span data-ttu-id="c88b7-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c88b7-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c88b7-126">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="c88b7-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c88b7-127">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c88b7-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c88b7-128">**Wersje .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c88b7-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c88b7-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c88b7-129">See also</span></span>

- [<span data-ttu-id="c88b7-130">ICLRDataTarget3, interfejs</span><span class="sxs-lookup"><span data-stu-id="c88b7-130">ICLRDataTarget3 Interface</span></span>](iclrdatatarget3-interface.md)
- [<span data-ttu-id="c88b7-131">GetExceptionContextRecord, metoda</span><span class="sxs-lookup"><span data-stu-id="c88b7-131">GetExceptionContextRecord Method</span></span>](iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="c88b7-132">GetExceptionThreadID, metoda</span><span class="sxs-lookup"><span data-stu-id="c88b7-132">GetExceptionThreadID Method</span></span>](iclrdatatarget3-getexceptionthreadid-method.md)
