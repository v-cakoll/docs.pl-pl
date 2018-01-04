---
title: Metoda ICorDebugProcess6::DecodeEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 753dce06d9481165bd2f0f1e49fe3c50fc6b3c40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess6decodeevent-method"></a><span data-ttu-id="4dc75-102">Metoda ICorDebugProcess6::DecodeEvent</span><span class="sxs-lookup"><span data-stu-id="4dc75-102">ICorDebugProcess6::DecodeEvent Method</span></span>
<span data-ttu-id="4dc75-103">Dekoduje zdarzenia debugowania zarządzanego, które zostały hermetyzowany w ładunku zdarzenia debugowania specjalnie przygotowany natywnego wyjątków.</span><span class="sxs-lookup"><span data-stu-id="4dc75-103">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dc75-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4dc75-104">Syntax</span></span>  
  
```  
HRESULT DecodeEvent(  
        [in, length_is(countBytes), size_is(countBytes)]  const BYTE pRecord[],  
        [in] DWORD countBytes,  
        [in] CorDebugRecordFormat format,  
        [in] DWORD dwFlags,   
        [in] DWORD dwThreadId,   
        [out] ICorDebugDebugEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4dc75-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4dc75-105">Parameters</span></span>  
 `pRecord`  
 <span data-ttu-id="4dc75-106">[in] Wskaźnik do tablicy typu byte ze zdarzenia debugowania natywnego wyjątek, który zawiera informacje dotyczące zdarzenia debugowania zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="4dc75-106">[in] A pointer to a byte array from a native exception debug event that includes information about a managed debug event.</span></span>  
  
 `countBytes`  
 <span data-ttu-id="4dc75-107">[in] Liczba elementów w `pRecord` tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="4dc75-107">[in] The number of elements in the `pRecord` byte array.</span></span>  
  
 `format`  
 <span data-ttu-id="4dc75-108">[in] A [CorDebugRecordFormat](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md) element członkowski wyliczenia Określa format zdarzeń debugowanie niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="4dc75-108">[in] A [CorDebugRecordFormat](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md) enumeration member that specifies the format of the unmanaged debug event.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="4dc75-109">[in] Pola bitowego, która jest zależna od architektury docelowej oraz określa dodatkowe informacje dotyczące zdarzenia debugowania.</span><span class="sxs-lookup"><span data-stu-id="4dc75-109">[in] A bit field that depends on the target architecture and that specifies additional information about the debug event.</span></span> <span data-ttu-id="4dc75-110">W systemie Windows, może być elementem członkowskim [CorDebugDecodeEventFlagsWindows](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="4dc75-110">For Windows systems, it can be a member of the [CorDebugDecodeEventFlagsWindows](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md) enumeration.</span></span>  
  
 `dwThreadId`  
 <span data-ttu-id="4dc75-111">[in] System operacyjny identyfikator wątku, w którym został zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="4dc75-111">[in] The operating system identifier of the thread on which the exception was thrown.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="4dc75-112">[out] Wskaźnik do adresu [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) obiekt, który reprezentuje zdarzenia dekodowane debugowania zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="4dc75-112">[out] A pointer to the address of an [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) object that represents a decoded managed debug event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4dc75-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4dc75-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4dc75-114">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4dc75-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dc75-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4dc75-115">Requirements</span></span>  
 <span data-ttu-id="4dc75-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4dc75-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dc75-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4dc75-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4dc75-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4dc75-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4dc75-119">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dc75-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dc75-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4dc75-120">See Also</span></span>  
 [<span data-ttu-id="4dc75-121">ICorDebugProcess6, interfejs</span><span class="sxs-lookup"><span data-stu-id="4dc75-121">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="4dc75-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4dc75-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
