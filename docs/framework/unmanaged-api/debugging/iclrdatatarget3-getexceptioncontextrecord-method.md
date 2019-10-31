---
title: Metoda ICLRDataTarget3::GetExceptionContextRecord
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetContextRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type:
- apiref
ms.openlocfilehash: 5a090b7c4801e6b2baf56f1d80e7e52f2aaa9293
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73112303"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a><span data-ttu-id="82b10-102">Metoda ICLRDataTarget3::GetExceptionContextRecord</span><span class="sxs-lookup"><span data-stu-id="82b10-102">ICLRDataTarget3::GetExceptionContextRecord Method</span></span>
<span data-ttu-id="82b10-103">Wywoływane przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) do pobierania rekordu kontekstu skojarzonego z procesem docelowym.</span><span class="sxs-lookup"><span data-stu-id="82b10-103">Called by the common language runtime (CLR) data access services to retrieve the context record associated with the target process.</span></span> <span data-ttu-id="82b10-104">Na przykład dla elementu docelowego zrzutu będzie to odpowiednik rekordu kontekstu przekazanego za pośrednictwem argumentu `ExceptionParam` do funkcji [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) w bibliotece pomocy debugowania systemu Windows (dbghelp).</span><span class="sxs-lookup"><span data-stu-id="82b10-104">For example, for a dump target, this would be equivalent to the context record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82b10-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="82b10-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82b10-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="82b10-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="82b10-107">podczas Rozmiar buforu wejściowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="82b10-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="82b10-108">Musi być wystarczająco duży, aby pomieścić rekord kontekstu.</span><span class="sxs-lookup"><span data-stu-id="82b10-108">This must be large enough to accommodate the context record.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="82b10-109">określoną Wskaźnik do typu `ULONG32`, który odbiera liczbę bajtów rzeczywiście zapisywanych w buforze.</span><span class="sxs-lookup"><span data-stu-id="82b10-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="82b10-110">określoną Wskaźnik do bufora pamięci, który otrzymuje kopię rekordu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="82b10-110">[out] A pointer to a memory buffer that receives a copy of the context record.</span></span> <span data-ttu-id="82b10-111">Rekord wyjątku jest zwracany jako typ [kontekstu](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) .</span><span class="sxs-lookup"><span data-stu-id="82b10-111">The exception record is returned as a [CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82b10-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="82b10-112">Return Value</span></span>  
 <span data-ttu-id="82b10-113">Wartość zwracana jest `S_OK` w przypadku sukcesu lub niepowodzenie `HRESULT` kod w przypadku niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="82b10-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="82b10-114">Kody `HRESULT` mogą zawierać, ale nie są ograniczone do następujących:</span><span class="sxs-lookup"><span data-stu-id="82b10-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="82b10-115">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="82b10-115">Return code</span></span>|<span data-ttu-id="82b10-116">Opis</span><span class="sxs-lookup"><span data-stu-id="82b10-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="82b10-117">Metoda powiodła się.</span><span class="sxs-lookup"><span data-stu-id="82b10-117">Method succeeded.</span></span> <span data-ttu-id="82b10-118">Rekord kontekstu został skopiowany do buforu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="82b10-118">The context record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="82b10-119">Żaden rekord kontekstu nie jest skojarzony z elementem docelowym.</span><span class="sxs-lookup"><span data-stu-id="82b10-119">No context record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="82b10-120">Rozmiar buforu wejściowego nie jest wystarczająco duży, aby pomieścić rekord kontekstu.</span><span class="sxs-lookup"><span data-stu-id="82b10-120">The input buffer size is not large enough to accommodate the context record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82b10-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="82b10-121">Remarks</span></span>  
 <span data-ttu-id="82b10-122">[Kontekst](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) jest strukturą specyficzną dla platformy zdefiniowaną w nagłówkach dostarczonych przez Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="82b10-122">[CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) is a platform-specific structure defined in headers provided by the Windows SDK.</span></span>  
  
 <span data-ttu-id="82b10-123">Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="82b10-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82b10-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="82b10-124">Requirements</span></span>  
 <span data-ttu-id="82b10-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82b10-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82b10-126">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="82b10-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="82b10-127">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="82b10-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82b10-128">**Wersje .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="82b10-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82b10-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82b10-129">See also</span></span>

- [<span data-ttu-id="82b10-130">ICLRDataTarget3, interfejs</span><span class="sxs-lookup"><span data-stu-id="82b10-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [<span data-ttu-id="82b10-131">GetExceptionRecord, metoda</span><span class="sxs-lookup"><span data-stu-id="82b10-131">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
- [<span data-ttu-id="82b10-132">GetExceptionThreadID, metoda</span><span class="sxs-lookup"><span data-stu-id="82b10-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
