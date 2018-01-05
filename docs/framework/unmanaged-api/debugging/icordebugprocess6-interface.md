---
title: Interfejs ICorDebugProcess6
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9928018b7d4065fbf24b4c39f7ef2d121e66d7ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess6-interface"></a><span data-ttu-id="77e33-102">Interfejs ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="77e33-102">ICorDebugProcess6 Interface</span></span>
<span data-ttu-id="77e33-103">Logicznie rozszerza interfejs ICorDebugProcess, aby włączyć funkcje, takie jak dekodowania zdarzenia debugowania zarządzanego, które są zakodowane w zdarzenia debugowania natywnego wyjątków i dzielenia wirtualnych modułu.</span><span class="sxs-lookup"><span data-stu-id="77e33-103">Logically extends the ICorDebugProcess interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="77e33-104">Metody</span><span class="sxs-lookup"><span data-stu-id="77e33-104">Methods</span></span>  
  
|<span data-ttu-id="77e33-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="77e33-105">Method</span></span>|<span data-ttu-id="77e33-106">Opis</span><span class="sxs-lookup"><span data-stu-id="77e33-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="77e33-107">DecodeEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="77e33-107">DecodeEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)|<span data-ttu-id="77e33-108">Dekoduje zdarzenia debugowania zarządzanego, które zostały hermetyzowany w ładunku zdarzenia debugowania specjalnie przygotowany natywnego wyjątków.</span><span class="sxs-lookup"><span data-stu-id="77e33-108">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>|  
|[<span data-ttu-id="77e33-109">EnableVirtualModuleSplitting, metoda</span><span class="sxs-lookup"><span data-stu-id="77e33-109">EnableVirtualModuleSplitting Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)|<span data-ttu-id="77e33-110">Włącza lub wyłącza wirtualnego modułu dzielenia.</span><span class="sxs-lookup"><span data-stu-id="77e33-110">Enables or disables virtual module splitting.</span></span>|  
|[<span data-ttu-id="77e33-111">GetCode, metoda</span><span class="sxs-lookup"><span data-stu-id="77e33-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getcode-method.md)|<span data-ttu-id="77e33-112">Pobiera informacje o zarządzanego kodu pod adresem określonym kodem.</span><span class="sxs-lookup"><span data-stu-id="77e33-112">Gets information about the managed code at a particular code address.</span></span>|  
|[<span data-ttu-id="77e33-113">GetExportStepInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="77e33-113">GetExportStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)|<span data-ttu-id="77e33-114">Zawiera informacje dotyczące środowiska uruchomieniowego wyeksportowane funkcje ułatwiające krok za pomocą kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="77e33-114">Provides information on runtime exported functions to help step through managed code.</span></span>|  
|[<span data-ttu-id="77e33-115">MarkDebuggerAttached, metoda</span><span class="sxs-lookup"><span data-stu-id="77e33-115">MarkDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-markdebuggerattached-method.md)|<span data-ttu-id="77e33-116">Wewnętrzny stan klasy obiektu debugowanego zmiany, aby <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metoda w bibliotece klas programu .NET Framework zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="77e33-116">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>|  
|[<span data-ttu-id="77e33-117">ProcessStateChanged, metoda</span><span class="sxs-lookup"><span data-stu-id="77e33-117">ProcessStateChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)|<span data-ttu-id="77e33-118">Powiadamia [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) którym jest uruchomiony proces.</span><span class="sxs-lookup"><span data-stu-id="77e33-118">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77e33-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="77e33-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77e33-120">Interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="77e33-120">The interface is available with .NET Native only.</span></span> <span data-ttu-id="77e33-121">Próba wywołania `QueryInterface` można pobrać wskaźnika interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="77e33-121">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77e33-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="77e33-122">Requirements</span></span>  
 <span data-ttu-id="77e33-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77e33-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77e33-124">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77e33-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77e33-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77e33-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77e33-126">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77e33-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77e33-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77e33-127">See Also</span></span>  
 [<span data-ttu-id="77e33-128">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="77e33-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="77e33-129">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="77e33-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
