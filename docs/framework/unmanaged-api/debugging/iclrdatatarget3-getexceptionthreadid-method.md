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
ms.openlocfilehash: d59bd3b8c427996fe5e44e95aeff51deb1da984a
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066379"
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a><span data-ttu-id="6a3ea-102">Metoda ICLRDataTarget3::GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="6a3ea-102">ICLRDataTarget3::GetExceptionThreadID Method</span></span>
<span data-ttu-id="6a3ea-103">Metoda wywoływana przez wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) usługi dostępu do danych można uzyskać identyfikator wątku, który wygenerował wyjątek.</span><span class="sxs-lookup"><span data-stu-id="6a3ea-103">Called by the common language runtime (CLR) data access services to get the ID of the thread that threw the exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a3ea-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a3ea-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a3ea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a3ea-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="6a3ea-106">[out] Identyfikator wątku, który wygenerował wyjątek.</span><span class="sxs-lookup"><span data-stu-id="6a3ea-106">[out] The ID of the thread that threw the exception.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a3ea-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6a3ea-107">Return Value</span></span>  
 <span data-ttu-id="6a3ea-108">Wartość zwracana jest `S_OK` na powodzenie lub niepowodzenie `HRESULT` kod błędu.</span><span class="sxs-lookup"><span data-stu-id="6a3ea-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="6a3ea-109">`HRESULT` Mogą obejmować kody, ale nie są ograniczone do następujących:</span><span class="sxs-lookup"><span data-stu-id="6a3ea-109">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="6a3ea-110">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="6a3ea-110">Return code</span></span>|<span data-ttu-id="6a3ea-111">Opis</span><span class="sxs-lookup"><span data-stu-id="6a3ea-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="6a3ea-112">Metody powiodło się.</span><span class="sxs-lookup"><span data-stu-id="6a3ea-112">Method succeeded.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="6a3ea-113">Nie można odnaleźć Identyfikatora wątku prawidłowy dla wyjątku.</span><span class="sxs-lookup"><span data-stu-id="6a3ea-113">Could not find a valid thread ID for the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a3ea-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6a3ea-114">Remarks</span></span>  
 <span data-ttu-id="6a3ea-115">Ta metoda jest implementowana przez moduł zapisujący debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6a3ea-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a3ea-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6a3ea-116">Requirements</span></span>  
 <span data-ttu-id="6a3ea-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a3ea-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a3ea-118">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="6a3ea-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="6a3ea-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a3ea-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a3ea-120">**Wersje programu .NET framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6a3ea-120">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a3ea-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a3ea-121">See also</span></span>
- [<span data-ttu-id="6a3ea-122">ICLRDataTarget3, interfejs</span><span class="sxs-lookup"><span data-stu-id="6a3ea-122">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [<span data-ttu-id="6a3ea-123">GetExceptionContextRecord, metoda</span><span class="sxs-lookup"><span data-stu-id="6a3ea-123">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="6a3ea-124">GetExceptionRecord, metoda</span><span class="sxs-lookup"><span data-stu-id="6a3ea-124">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
