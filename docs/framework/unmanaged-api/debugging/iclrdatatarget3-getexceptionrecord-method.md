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
ms.openlocfilehash: 0ea4546dcde4afa0a9db2e64ae34415d0973391b
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860439"
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a><span data-ttu-id="a3605-102">ICLRDataTarget3::GetExceptionRecord — Metoda</span><span class="sxs-lookup"><span data-stu-id="a3605-102">ICLRDataTarget3::GetExceptionRecord Method</span></span>
<span data-ttu-id="a3605-103">Wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) w celu pobrania rekordu wyjątku skojarzonego z procesem docelowym.</span><span class="sxs-lookup"><span data-stu-id="a3605-103">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span> <span data-ttu-id="a3605-104">Na przykład dla elementu docelowego zrzutu będzie to odpowiednik rekordu wyjątku przekazanego za pośrednictwem `ExceptionParam` argumentu do funkcji [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) w bibliotece pomocy debugowania systemu Windows (dbghelp).</span><span class="sxs-lookup"><span data-stu-id="a3605-104">For example, for a dump target, this would be equivalent to the exception record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3605-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a3605-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3605-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a3605-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="a3605-107">podczas Rozmiar buforu wejściowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a3605-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="a3605-108">Ta wartość musi być równa `sizeof(` [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception)`)`.</span><span class="sxs-lookup"><span data-stu-id="a3605-108">This must be equal to `sizeof(`[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception)`)`.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="a3605-109">określoną Wskaźnik do `ULONG32` typu, który odbiera liczbę bajtów rzeczywiście zapisywanych w buforze.</span><span class="sxs-lookup"><span data-stu-id="a3605-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="a3605-110">określoną Wskaźnik do bufora pamięci, który otrzymuje kopię rekordu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a3605-110">[out] A pointer to a memory buffer that receives a copy of the exception record.</span></span> <span data-ttu-id="a3605-111">Rekord wyjątku jest zwracany jako typ [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) .</span><span class="sxs-lookup"><span data-stu-id="a3605-111">The exception record is returned as a [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3605-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a3605-112">Return Value</span></span>  
 <span data-ttu-id="a3605-113">Wartość zwracana jest `S_OK` w przypadku powodzenia lub kod błędu `HRESULT` w przypadku niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="a3605-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="a3605-114">`HRESULT` Kody mogą zawierać, ale nie są ograniczone do następujących:</span><span class="sxs-lookup"><span data-stu-id="a3605-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="a3605-115">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="a3605-115">Return code</span></span>|<span data-ttu-id="a3605-116">Opis</span><span class="sxs-lookup"><span data-stu-id="a3605-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="a3605-117">Metoda powiodła się.</span><span class="sxs-lookup"><span data-stu-id="a3605-117">Method succeeded.</span></span> <span data-ttu-id="a3605-118">Rekord wyjątku został skopiowany do buforu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="a3605-118">The exception record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="a3605-119">Z elementem docelowym nie jest skojarzony żaden rekord wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a3605-119">No exception record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="a3605-120">Rozmiar buforu wejściowego nie jest równy `sizeof(MINIDUMP_EXCEPTION)`.</span><span class="sxs-lookup"><span data-stu-id="a3605-120">The input buffer size is not equal to `sizeof(MINIDUMP_EXCEPTION)`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3605-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a3605-121">Remarks</span></span>  
 <span data-ttu-id="a3605-122">[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) to struktura zdefiniowana w dbghelp. h i Imagehlp. h w Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="a3605-122">[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) is a structure defined in dbghelp.h and imagehlp.h in the Windows SDK.</span></span>  
  
 <span data-ttu-id="a3605-123">Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="a3605-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3605-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a3605-124">Requirements</span></span>  
 <span data-ttu-id="a3605-125">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3605-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3605-126">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="a3605-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a3605-127">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a3605-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3605-128">**.NET Framework wersje:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a3605-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3605-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3605-129">See also</span></span>

- [<span data-ttu-id="a3605-130">ICLRDataTarget3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a3605-130">ICLRDataTarget3 Interface</span></span>](iclrdatatarget3-interface.md)
- [<span data-ttu-id="a3605-131">GetExceptionContextRecord, metoda</span><span class="sxs-lookup"><span data-stu-id="a3605-131">GetExceptionContextRecord Method</span></span>](iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="a3605-132">GetExceptionThreadID, metoda</span><span class="sxs-lookup"><span data-stu-id="a3605-132">GetExceptionThreadID Method</span></span>](iclrdatatarget3-getexceptionthreadid-method.md)
