---
title: Interfejs ICorDebugProcess6
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 518c6ec99e4062bf8432809d3472baa395017da3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59147267"
---
# <a name="icordebugprocess6-interface"></a><span data-ttu-id="18e7f-102">Interfejs ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="18e7f-102">ICorDebugProcess6 Interface</span></span>
<span data-ttu-id="18e7f-103">Rozszerza logicznie icordebugprocess — interfejs, aby włączyć funkcje, takie jak dekodowanie zdarzenia debugowania zarządzanego, które są kodowane w zdarzeń debugowania natywnych wyjątków oraz wirtualnego modułu dzielenia.</span><span class="sxs-lookup"><span data-stu-id="18e7f-103">Logically extends the ICorDebugProcess interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="18e7f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="18e7f-104">Methods</span></span>  
  
|<span data-ttu-id="18e7f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="18e7f-105">Method</span></span>|<span data-ttu-id="18e7f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="18e7f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="18e7f-107">DecodeEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="18e7f-107">DecodeEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)|<span data-ttu-id="18e7f-108">Dekoduje zdarzenia debugowania zarządzanego, które zostały hermetyzowane w ładunku zdarzenia debugowania specjalnie przygotowane natywnych wyjątek.</span><span class="sxs-lookup"><span data-stu-id="18e7f-108">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>|  
|[<span data-ttu-id="18e7f-109">EnableVirtualModuleSplitting, metoda</span><span class="sxs-lookup"><span data-stu-id="18e7f-109">EnableVirtualModuleSplitting Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)|<span data-ttu-id="18e7f-110">Włącza lub wyłącza wirtualnego modułu dzielenia.</span><span class="sxs-lookup"><span data-stu-id="18e7f-110">Enables or disables virtual module splitting.</span></span>|  
|[<span data-ttu-id="18e7f-111">GetCode, metoda</span><span class="sxs-lookup"><span data-stu-id="18e7f-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getcode-method.md)|<span data-ttu-id="18e7f-112">Pobiera informacje o kodzie zarządzanym pod adresem określonym kodem.</span><span class="sxs-lookup"><span data-stu-id="18e7f-112">Gets information about the managed code at a particular code address.</span></span>|  
|[<span data-ttu-id="18e7f-113">GetExportStepInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="18e7f-113">GetExportStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)|<span data-ttu-id="18e7f-114">Zawiera informacje na temat funkcji środowiska uruchomieniowego wyeksportowane ułatwiające Przechodź przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="18e7f-114">Provides information on runtime exported functions to help step through managed code.</span></span>|  
|[<span data-ttu-id="18e7f-115">MarkDebuggerAttached, metoda</span><span class="sxs-lookup"><span data-stu-id="18e7f-115">MarkDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-markdebuggerattached-method.md)|<span data-ttu-id="18e7f-116">Zmienia stan wewnętrzny debugee tak, aby <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> zwraca metody w bibliotece klas programu .NET Framework `true`.</span><span class="sxs-lookup"><span data-stu-id="18e7f-116">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>|  
|[<span data-ttu-id="18e7f-117">ProcessStateChanged, metoda</span><span class="sxs-lookup"><span data-stu-id="18e7f-117">ProcessStateChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)|<span data-ttu-id="18e7f-118">Powiadamia [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , proces jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="18e7f-118">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18e7f-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="18e7f-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18e7f-120">Interfejs jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="18e7f-120">The interface is available with .NET Native only.</span></span> <span data-ttu-id="18e7f-121">Próba wywołania `QueryInterface` do pobrania wskaźnika interfejsu zwraca `E_NOINTERFACE` scenariuszach ICorDebug poza .NET Native.</span><span class="sxs-lookup"><span data-stu-id="18e7f-121">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18e7f-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="18e7f-122">Requirements</span></span>  
 <span data-ttu-id="18e7f-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18e7f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18e7f-124">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="18e7f-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18e7f-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18e7f-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18e7f-126">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18e7f-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18e7f-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="18e7f-127">See also</span></span>

- [<span data-ttu-id="18e7f-128">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="18e7f-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="18e7f-129">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="18e7f-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
