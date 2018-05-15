---
title: Metoda ICLRDataTarget3::GetExceptionThreadID
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionThreadID
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 307d6ac7-4a86-45f3-999d-6b47004a68f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c838c994144307e9c87e3a4628fa80bfcdbeb59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a><span data-ttu-id="e5770-102">Metoda ICLRDataTarget3::GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="e5770-102">ICLRDataTarget3::GetExceptionThreadID Method</span></span>
<span data-ttu-id="e5770-103">Metoda wywoływana przez wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) dostępu do usługi danych można uzyskać Identyfikatora wątku, który zgłosił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e5770-103">Called by the common language runtime (CLR) data access services to get the ID of the thread that threw the exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5770-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5770-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e5770-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5770-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="e5770-106">[out] Identyfikator wątku, który zgłosił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e5770-106">[out] The ID of the thread that threw the exception.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5770-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e5770-107">Return Value</span></span>  
 <span data-ttu-id="e5770-108">Wartość zwracana jest `S_OK` na powodzenie lub niepowodzenie `HRESULT` kod błędu.</span><span class="sxs-lookup"><span data-stu-id="e5770-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="e5770-109">`HRESULT` Mogą obejmować kody, ale nie są ograniczone do następujących:</span><span class="sxs-lookup"><span data-stu-id="e5770-109">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="e5770-110">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="e5770-110">Return code</span></span>|<span data-ttu-id="e5770-111">Opis</span><span class="sxs-lookup"><span data-stu-id="e5770-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="e5770-112">Metoda zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e5770-112">Method succeeded.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="e5770-113">Nie można odnaleźć Identyfikatora wątku prawidłowy wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e5770-113">Could not find a valid thread ID for the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5770-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5770-114">Remarks</span></span>  
 <span data-ttu-id="e5770-115">Ta metoda jest implementowany przez twórcę debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5770-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5770-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5770-116">Requirements</span></span>  
 <span data-ttu-id="e5770-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5770-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5770-118">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="e5770-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e5770-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5770-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5770-120">**Wersje programu .NET framework:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5770-120">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5770-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5770-121">See Also</span></span>  
 [<span data-ttu-id="e5770-122">ICLRDataTarget3, interfejs</span><span class="sxs-lookup"><span data-stu-id="e5770-122">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [<span data-ttu-id="e5770-123">GetExceptionContextRecord, metoda</span><span class="sxs-lookup"><span data-stu-id="e5770-123">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)  
 [<span data-ttu-id="e5770-124">GetExceptionRecord, metoda</span><span class="sxs-lookup"><span data-stu-id="e5770-124">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
