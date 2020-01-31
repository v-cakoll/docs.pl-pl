---
title: Interfejs ICorDebugProcess6
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
ms.openlocfilehash: 73ef1a64deaf5420246fc1ab3e9f88ba5bf049a5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792232"
---
# <a name="icordebugprocess6-interface"></a><span data-ttu-id="5db73-102">Interfejs ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="5db73-102">ICorDebugProcess6 Interface</span></span>
<span data-ttu-id="5db73-103">Logicznie rozszerza interfejs ICorDebugProcess w celu włączenia takich funkcji, jak dekodowanie zdarzeń debugowania zarządzanego, które są kodowane w natywnych zdarzeniach debugowania wyjątków i dzielenia modułu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="5db73-103">Logically extends the ICorDebugProcess interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5db73-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5db73-104">Methods</span></span>  
  
|<span data-ttu-id="5db73-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5db73-105">Method</span></span>|<span data-ttu-id="5db73-106">Opis</span><span class="sxs-lookup"><span data-stu-id="5db73-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5db73-107">DecodeEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="5db73-107">DecodeEvent Method</span></span>](icordebugprocess6-decodeevent-method.md)|<span data-ttu-id="5db73-108">Dekoduje zarządzane zdarzenia debugowania, które zostały hermetyzowane w ładunku specjalnie spreparowanych zdarzeń debugowania wyjątku natywnego.</span><span class="sxs-lookup"><span data-stu-id="5db73-108">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>|  
|[<span data-ttu-id="5db73-109">EnableVirtualModuleSplitting, metoda</span><span class="sxs-lookup"><span data-stu-id="5db73-109">EnableVirtualModuleSplitting Method</span></span>](icordebugprocess6-enablevirtualmodulesplitting-method.md)|<span data-ttu-id="5db73-110">Włącza lub wyłącza dzielenie modułu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="5db73-110">Enables or disables virtual module splitting.</span></span>|  
|[<span data-ttu-id="5db73-111">GetCode, metoda</span><span class="sxs-lookup"><span data-stu-id="5db73-111">GetCode Method</span></span>](icordebugprocess6-getcode-method.md)|<span data-ttu-id="5db73-112">Pobiera informacje o zarządzanym kodzie pod określonym adresem kodu.</span><span class="sxs-lookup"><span data-stu-id="5db73-112">Gets information about the managed code at a particular code address.</span></span>|  
|[<span data-ttu-id="5db73-113">GetExportStepInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="5db73-113">GetExportStepInfo Method</span></span>](icordebugprocess6-getexportstepinfo-method.md)|<span data-ttu-id="5db73-114">Zawiera informacje dotyczące funkcji wyeksportowanych przez środowisko uruchomieniowe, które ułatwiają przechodzenie przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="5db73-114">Provides information on runtime exported functions to help step through managed code.</span></span>|  
|[<span data-ttu-id="5db73-115">MarkDebuggerAttached, metoda</span><span class="sxs-lookup"><span data-stu-id="5db73-115">MarkDebuggerAttached Method</span></span>](icordebugprocess6-markdebuggerattached-method.md)|<span data-ttu-id="5db73-116">Zmienia wewnętrzny stan debugee, tak aby Metoda <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> w .NET Frameworkej bibliotece klas zwracała `true`.</span><span class="sxs-lookup"><span data-stu-id="5db73-116">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>|  
|[<span data-ttu-id="5db73-117">ProcessStateChanged, metoda</span><span class="sxs-lookup"><span data-stu-id="5db73-117">ProcessStateChanged Method</span></span>](icordebugprocess6-processstatechanged-method.md)|<span data-ttu-id="5db73-118">Powiadamia [ICorDebug](icordebug-interface.md) o tym, że proces jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="5db73-118">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5db73-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5db73-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5db73-120">Interfejs jest dostępny tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5db73-120">The interface is available with .NET Native only.</span></span> <span data-ttu-id="5db73-121">Podjęto próbę wywołania `QueryInterface`, aby pobrać wskaźnik interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5db73-121">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5db73-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5db73-122">Requirements</span></span>  
 <span data-ttu-id="5db73-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5db73-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5db73-124">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5db73-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5db73-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5db73-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5db73-126">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5db73-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5db73-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5db73-127">See also</span></span>

- [<span data-ttu-id="5db73-128">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="5db73-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5db73-129">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="5db73-129">Debugging</span></span>](index.md)
