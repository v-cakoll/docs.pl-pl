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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ec7414b18b60a20eefcbf4ec742ddcc7b7a8f97
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066106"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a><span data-ttu-id="2f152-102">Metoda ICLRDataTarget3::GetExceptionContextRecord</span><span class="sxs-lookup"><span data-stu-id="2f152-102">ICLRDataTarget3::GetExceptionContextRecord Method</span></span>
<span data-ttu-id="2f152-103">Metoda wywoływana przez wspólnego języka wspólnego (CLR) usługi dostępu do danych w celu pobrania rekordu kontekstu skojarzonego z procesem docelowym.</span><span class="sxs-lookup"><span data-stu-id="2f152-103">Called by the common language runtime (CLR) data access services to retrieve the context record associated with the target process.</span></span> <span data-ttu-id="2f152-104">Na przykład dla elementu docelowego zrzutu jest to równoważne z rekordu kontekstu przekazaną za pomocą `ExceptionParam` argument [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) funkcji w Windows debugowania pomóc w bibliotece (DbgHelp).</span><span class="sxs-lookup"><span data-stu-id="2f152-104">For example, for a dump target, this would be equivalent to the context record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f152-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f152-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2f152-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f152-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="2f152-107">[in] Rozmiar buforu wejściowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="2f152-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="2f152-108">Musi to być wystarczająco duży, aby pomieścić rekordu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="2f152-108">This must be large enough to accommodate the context record.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="2f152-109">[out] Wskaźnik do `ULONG32` typu, który odbiera liczbę bajtów, które rzeczywiście zapisanych w buforze.</span><span class="sxs-lookup"><span data-stu-id="2f152-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="2f152-110">[out] Wskaźnik do buforu pamięci, który otrzymuje kopię rekordu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="2f152-110">[out] A pointer to a memory buffer that receives a copy of the context record.</span></span> <span data-ttu-id="2f152-111">Rekordu wyjątku jest zwracana jako [KONTEKSTU](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) typu.</span><span class="sxs-lookup"><span data-stu-id="2f152-111">The exception record is returned as a [CONTEXT](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f152-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2f152-112">Return Value</span></span>  
 <span data-ttu-id="2f152-113">Wartość zwracana jest `S_OK` na powodzenie lub niepowodzenie `HRESULT` kod błędu.</span><span class="sxs-lookup"><span data-stu-id="2f152-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="2f152-114">`HRESULT` Mogą obejmować kody, ale nie są ograniczone do następujących:</span><span class="sxs-lookup"><span data-stu-id="2f152-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="2f152-115">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="2f152-115">Return code</span></span>|<span data-ttu-id="2f152-116">Opis</span><span class="sxs-lookup"><span data-stu-id="2f152-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="2f152-117">Metody powiodło się.</span><span class="sxs-lookup"><span data-stu-id="2f152-117">Method succeeded.</span></span> <span data-ttu-id="2f152-118">Rekordu kontekstu został skopiowany do buforu danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="2f152-118">The context record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="2f152-119">Nie rekordu kontekstu jest skojarzony z obiektem docelowym.</span><span class="sxs-lookup"><span data-stu-id="2f152-119">No context record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="2f152-120">Rozmiar buforu wejściowego nie jest wystarczająco duży, aby pomieścić rekordu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="2f152-120">The input buffer size is not large enough to accommodate the context record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f152-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2f152-121">Remarks</span></span>  
 <span data-ttu-id="2f152-122">[KONTEKST](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) to struktura specyficzne dla platformy, zdefiniowane w nagłówki udostępnione przez zestaw Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="2f152-122">[CONTEXT](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) is a platform-specific structure defined in headers provided by the Windows SDK.</span></span>  
  
 <span data-ttu-id="2f152-123">Ta metoda jest implementowana przez moduł zapisujący debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2f152-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f152-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2f152-124">Requirements</span></span>  
 <span data-ttu-id="2f152-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f152-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f152-126">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="2f152-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="2f152-127">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f152-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f152-128">**Wersje programu .NET framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2f152-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f152-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f152-129">See also</span></span>
- [<span data-ttu-id="2f152-130">ICLRDataTarget3, interfejs</span><span class="sxs-lookup"><span data-stu-id="2f152-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [<span data-ttu-id="2f152-131">GetExceptionRecord, metoda</span><span class="sxs-lookup"><span data-stu-id="2f152-131">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
- [<span data-ttu-id="2f152-132">GetExceptionThreadID, metoda</span><span class="sxs-lookup"><span data-stu-id="2f152-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
