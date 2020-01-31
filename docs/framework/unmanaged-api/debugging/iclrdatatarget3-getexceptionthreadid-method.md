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
ms.openlocfilehash: 961e74551ae7fc170e443c632ca11598f1494a39
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785204"
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a><span data-ttu-id="0e205-102">Metoda ICLRDataTarget3::GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="0e205-102">ICLRDataTarget3::GetExceptionThreadID Method</span></span>
<span data-ttu-id="0e205-103">Wywoływane przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR), aby uzyskać identyfikator wątku, który wywołał wyjątek.</span><span class="sxs-lookup"><span data-stu-id="0e205-103">Called by the common language runtime (CLR) data access services to get the ID of the thread that threw the exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e205-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0e205-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e205-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0e205-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="0e205-106">określoną Identyfikator wątku, który wywołał wyjątek.</span><span class="sxs-lookup"><span data-stu-id="0e205-106">[out] The ID of the thread that threw the exception.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e205-107">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="0e205-107">Return Value</span></span>  
 <span data-ttu-id="0e205-108">Wartość zwracana jest `S_OK` w przypadku sukcesu lub niepowodzenie `HRESULT` kod w przypadku niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="0e205-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="0e205-109">Kody `HRESULT` mogą zawierać, ale nie są ograniczone do następujących:</span><span class="sxs-lookup"><span data-stu-id="0e205-109">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="0e205-110">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="0e205-110">Return code</span></span>|<span data-ttu-id="0e205-111">Opis</span><span class="sxs-lookup"><span data-stu-id="0e205-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="0e205-112">Metoda powiodła się.</span><span class="sxs-lookup"><span data-stu-id="0e205-112">Method succeeded.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="0e205-113">Nie można znaleźć prawidłowego identyfikatora wątku dla wyjątku.</span><span class="sxs-lookup"><span data-stu-id="0e205-113">Could not find a valid thread ID for the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e205-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0e205-114">Remarks</span></span>  
 <span data-ttu-id="0e205-115">Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="0e205-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e205-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0e205-116">Requirements</span></span>  
 <span data-ttu-id="0e205-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e205-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e205-118">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="0e205-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="0e205-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0e205-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e205-120">**Wersje .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0e205-120">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e205-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e205-121">See also</span></span>

- [<span data-ttu-id="0e205-122">ICLRDataTarget3, interfejs</span><span class="sxs-lookup"><span data-stu-id="0e205-122">ICLRDataTarget3 Interface</span></span>](iclrdatatarget3-interface.md)
- [<span data-ttu-id="0e205-123">GetExceptionContextRecord, metoda</span><span class="sxs-lookup"><span data-stu-id="0e205-123">GetExceptionContextRecord Method</span></span>](iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="0e205-124">GetExceptionRecord, metoda</span><span class="sxs-lookup"><span data-stu-id="0e205-124">GetExceptionRecord Method</span></span>](iclrdatatarget3-getexceptionrecord-method.md)
