---
title: Metoda ICorDebugProcess6::DecodeEvent
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
ms.openlocfilehash: 7c163311f9ce8f3d98ce72f45165a5e517c6c0aa
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205515"
---
# <a name="icordebugprocess6decodeevent-method"></a><span data-ttu-id="298f5-102">Metoda ICorDebugProcess6::DecodeEvent</span><span class="sxs-lookup"><span data-stu-id="298f5-102">ICorDebugProcess6::DecodeEvent Method</span></span>
<span data-ttu-id="298f5-103">Dekoduje zarządzane zdarzenia debugowania, które zostały hermetyzowane w ładunku specjalnie spreparowanych zdarzeń debugowania wyjątku natywnego.</span><span class="sxs-lookup"><span data-stu-id="298f5-103">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="298f5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="298f5-104">Syntax</span></span>  
  
```cpp  
HRESULT DecodeEvent(  
        [in, length_is(countBytes), size_is(countBytes)]  const BYTE pRecord[],  
        [in] DWORD countBytes,  
        [in] CorDebugRecordFormat format,  
        [in] DWORD dwFlags,
        [in] DWORD dwThreadId,
        [out] ICorDebugDebugEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="298f5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="298f5-105">Parameters</span></span>  
 `pRecord`  
 <span data-ttu-id="298f5-106">podczas Wskaźnik do tablicy bajtów z natywnego zdarzenia debugowania wyjątku, który zawiera informacje o zarządzanym zdarzeniu debugowania.</span><span class="sxs-lookup"><span data-stu-id="298f5-106">[in] A pointer to a byte array from a native exception debug event that includes information about a managed debug event.</span></span>  
  
 `countBytes`  
 <span data-ttu-id="298f5-107">podczas Liczba elementów w `pRecord` tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="298f5-107">[in] The number of elements in the `pRecord` byte array.</span></span>  
  
 `format`  
 <span data-ttu-id="298f5-108">podczas Element członkowski wyliczenia [CorDebugRecordFormat](cordebugrecordformat-enumeration.md) , który określa format niezarządzanego zdarzenia debugowania.</span><span class="sxs-lookup"><span data-stu-id="298f5-108">[in] A [CorDebugRecordFormat](cordebugrecordformat-enumeration.md) enumeration member that specifies the format of the unmanaged debug event.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="298f5-109">podczas Pole bitowe, które zależy od architektury docelowej i określające dodatkowe informacje o zdarzeniu debugowania.</span><span class="sxs-lookup"><span data-stu-id="298f5-109">[in] A bit field that depends on the target architecture and that specifies additional information about the debug event.</span></span> <span data-ttu-id="298f5-110">W przypadku systemów Windows może być elementem członkowskim wyliczenia [CorDebugDecodeEventFlagsWindows](cordebugdecodeeventflagswindows-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="298f5-110">For Windows systems, it can be a member of the [CorDebugDecodeEventFlagsWindows](cordebugdecodeeventflagswindows-enumeration.md) enumeration.</span></span>  
  
 `dwThreadId`  
 <span data-ttu-id="298f5-111">podczas Identyfikator systemu operacyjnego wątku, w którym został zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="298f5-111">[in] The operating system identifier of the thread on which the exception was thrown.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="298f5-112">określoną Wskaźnik do adresu obiektu [ICorDebugDebugEvent](icordebugdebugevent-interface.md) , który reprezentuje zdekodowane zdarzenie debugowania zarządzane.</span><span class="sxs-lookup"><span data-stu-id="298f5-112">[out] A pointer to the address of an [ICorDebugDebugEvent](icordebugdebugevent-interface.md) object that represents a decoded managed debug event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="298f5-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="298f5-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="298f5-114">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="298f5-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="298f5-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="298f5-115">Requirements</span></span>  
 <span data-ttu-id="298f5-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="298f5-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="298f5-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="298f5-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="298f5-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="298f5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="298f5-119">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="298f5-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="298f5-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="298f5-120">See also</span></span>

- [<span data-ttu-id="298f5-121">Interfejs ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="298f5-121">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="298f5-122">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="298f5-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
