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
ms.openlocfilehash: d9b53bb7e34f037f3a165cc8bb59d25ff34ba7da
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507151"
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a><span data-ttu-id="778ff-102">Metoda ICLRDataTarget3::GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="778ff-102">ICLRDataTarget3::GetExceptionThreadID Method</span></span>
<span data-ttu-id="778ff-103">Metoda wywoływana przez wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) usługi dostępu do danych można uzyskać identyfikator wątku, który wygenerował wyjątek.</span><span class="sxs-lookup"><span data-stu-id="778ff-103">Called by the common language runtime (CLR) data access services to get the ID of the thread that threw the exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="778ff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="778ff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="778ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="778ff-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="778ff-106">[out] Identyfikator wątku, który wygenerował wyjątek.</span><span class="sxs-lookup"><span data-stu-id="778ff-106">[out] The ID of the thread that threw the exception.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="778ff-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="778ff-107">Return Value</span></span>  
 <span data-ttu-id="778ff-108">Wartość zwracana jest `S_OK` na powodzenie lub niepowodzenie `HRESULT` kod błędu.</span><span class="sxs-lookup"><span data-stu-id="778ff-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="778ff-109">`HRESULT` Mogą obejmować kody, ale nie są ograniczone do następujących:</span><span class="sxs-lookup"><span data-stu-id="778ff-109">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="778ff-110">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="778ff-110">Return code</span></span>|<span data-ttu-id="778ff-111">Opis</span><span class="sxs-lookup"><span data-stu-id="778ff-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="778ff-112">Metody powiodło się.</span><span class="sxs-lookup"><span data-stu-id="778ff-112">Method succeeded.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="778ff-113">Nie można odnaleźć Identyfikatora wątku prawidłowy dla wyjątku.</span><span class="sxs-lookup"><span data-stu-id="778ff-113">Could not find a valid thread ID for the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="778ff-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="778ff-114">Remarks</span></span>  
 <span data-ttu-id="778ff-115">Ta metoda jest implementowana przez moduł zapisujący debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="778ff-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="778ff-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="778ff-116">Requirements</span></span>  
 <span data-ttu-id="778ff-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="778ff-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="778ff-118">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="778ff-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="778ff-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="778ff-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="778ff-120">**Wersje programu .NET framework:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="778ff-120">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="778ff-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="778ff-121">See also</span></span>
- [<span data-ttu-id="778ff-122">ICLRDataTarget3, interfejs</span><span class="sxs-lookup"><span data-stu-id="778ff-122">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [<span data-ttu-id="778ff-123">GetExceptionContextRecord, metoda</span><span class="sxs-lookup"><span data-stu-id="778ff-123">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="778ff-124">GetExceptionRecord, metoda</span><span class="sxs-lookup"><span data-stu-id="778ff-124">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
