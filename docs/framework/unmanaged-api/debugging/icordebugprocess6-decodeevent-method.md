---
title: Metoda ICorDebugProcess6::DecodeEvent
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a392e236f180771a9b05526a0db569f27f6f7d8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59230749"
---
# <a name="icordebugprocess6decodeevent-method"></a><span data-ttu-id="f07da-102">Metoda ICorDebugProcess6::DecodeEvent</span><span class="sxs-lookup"><span data-stu-id="f07da-102">ICorDebugProcess6::DecodeEvent Method</span></span>
<span data-ttu-id="f07da-103">Dekoduje zdarzenia debugowania zarządzanego, które zostały hermetyzowane w ładunku zdarzenia debugowania specjalnie przygotowane natywnych wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f07da-103">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f07da-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f07da-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f07da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f07da-105">Parameters</span></span>  
 `pRecord`  
 <span data-ttu-id="f07da-106">[in] Wskaźnik do tablicy typu byte ze zdarzenia debugowania natywnych wyjątek zawierającą informacje o zdarzeniu debugowania zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="f07da-106">[in] A pointer to a byte array from a native exception debug event that includes information about a managed debug event.</span></span>  
  
 `countBytes`  
 <span data-ttu-id="f07da-107">[in] Liczba elementów w `pRecord` tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="f07da-107">[in] The number of elements in the `pRecord` byte array.</span></span>  
  
 `format`  
 <span data-ttu-id="f07da-108">[in] A [CorDebugRecordFormat](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md) składowej wyliczenia, która określa format zdarzenia debugowania niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="f07da-108">[in] A [CorDebugRecordFormat](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md) enumeration member that specifies the format of the unmanaged debug event.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f07da-109">[in] Pole bitowe, która jest zależna od architektury docelowej oraz określa dodatkowe informacje na temat zdarzeń debugowania.</span><span class="sxs-lookup"><span data-stu-id="f07da-109">[in] A bit field that depends on the target architecture and that specifies additional information about the debug event.</span></span> <span data-ttu-id="f07da-110">Dla systemów Windows, może być członkiem [CorDebugDecodeEventFlagsWindows](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f07da-110">For Windows systems, it can be a member of the [CorDebugDecodeEventFlagsWindows](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md) enumeration.</span></span>  
  
 `dwThreadId`  
 <span data-ttu-id="f07da-111">[in] Identyfikator systemu operacyjnego wątku, na którym wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f07da-111">[in] The operating system identifier of the thread on which the exception was thrown.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="f07da-112">[out] Wskaźnik na adres [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) obiekt, który reprezentuje zdarzenie zdekodowany debugowania zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="f07da-112">[out] A pointer to the address of an [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) object that represents a decoded managed debug event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f07da-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f07da-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f07da-114">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f07da-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f07da-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f07da-115">Requirements</span></span>  
 <span data-ttu-id="f07da-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f07da-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f07da-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f07da-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f07da-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f07da-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f07da-119">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f07da-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f07da-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f07da-120">See also</span></span>

- [<span data-ttu-id="f07da-121">ICorDebugProcess6, interfejs</span><span class="sxs-lookup"><span data-stu-id="f07da-121">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="f07da-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f07da-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
