---
title: "Debugowanie — wyliczenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
caps.latest.revision: "27"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c24882f2bd9819043bbc786bd2e5f35129a92744
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="debugging-enumerations"></a><span data-ttu-id="c2996-102">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c2996-102">Debugging Enumerations</span></span>
<span data-ttu-id="c2996-103">W tej sekcji opisano niezarządzane wyliczenia, które używa interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="c2996-103">This section describes the unmanaged enumerations that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c2996-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c2996-104">In This Section</span></span>  
 [<span data-ttu-id="c2996-105">Clr_debugging_process_flags — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c2996-105">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 <span data-ttu-id="c2996-106">Udostępnia wartości, które są używane przez [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c2996-106">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="c2996-107">CLRDataEnumMemoryFlags — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c2996-107">CLRDataEnumMemoryFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 <span data-ttu-id="c2996-108">Wskazuje, które regiony pamięci wywołanie [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) metoda powinna zawierać.</span><span class="sxs-lookup"><span data-stu-id="c2996-108">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
 [<span data-ttu-id="c2996-109">COR_PUB_ENUMPROCESS — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c2996-109">COR_PUB_ENUMPROCESS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 <span data-ttu-id="c2996-110">Określa typ procesu, które mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="c2996-110">Identifies the type of process to be enumerated.</span></span>  
  
 [<span data-ttu-id="c2996-111">CorDebugBlockingReason — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c2996-111">CorDebugBlockingReason Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 <span data-ttu-id="c2996-112">Określa przyczyny, dlaczego wątek może stać się zablokowane na dany obiekt.</span><span class="sxs-lookup"><span data-stu-id="c2996-112">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
 <span data-ttu-id="c2996-113">CorDebugChainReason</span><span class="sxs-lookup"><span data-stu-id="c2996-113">CorDebugChainReason</span></span>  
 <span data-ttu-id="c2996-114">Wskazuje powód lub powody rozpoczęcia łańcuch wywołań.</span><span class="sxs-lookup"><span data-stu-id="c2996-114">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
 [<span data-ttu-id="c2996-115">Wyliczenie CorDebugCodeInvokeKind</span><span class="sxs-lookup"><span data-stu-id="c2996-115">CorDebugCodeInvokeKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 <span data-ttu-id="c2996-116">W tym artykule opisano, jak wyeksportowanej funkcji wywołuje kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="c2996-116">Describes how an exported function invokes managed code.</span></span>  
  
 [<span data-ttu-id="c2996-117">Wyliczenie CorDebugCodeInvokePurpose</span><span class="sxs-lookup"><span data-stu-id="c2996-117">CorDebugCodeInvokePurpose Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 <span data-ttu-id="c2996-118">Opisuje, dlaczego wyeksportowanej funkcji wywołania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="c2996-118">Describes why an exported function calls managed code.</span></span>  
  
 <span data-ttu-id="c2996-119">CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="c2996-119">CorDebugCreateProcessFlags</span></span>  
 <span data-ttu-id="c2996-120">Udostępnia dodatkowe opcje debugowania, które mogą być używane w wywołaniu [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c2996-120">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="c2996-121">Wyliczenie CorDebugDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="c2996-121">CorDebugDebugEventKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 <span data-ttu-id="c2996-122">Wskazuje typ zdarzenia, których dane są dekodowane przez [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c2996-122">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
 [<span data-ttu-id="c2996-123">Wyliczenie CorDebugDecodeEventFlagsWindows</span><span class="sxs-lookup"><span data-stu-id="c2996-123">CorDebugDecodeEventFlagsWindows Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 <span data-ttu-id="c2996-124">Zawiera dodatkowe informacje o zdarzeniach debugowania na platformie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c2996-124">Provides additional information about debug events on the Windows platform.</span></span>  
  
 <span data-ttu-id="c2996-125">CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="c2996-125">CorDebugExceptionCallbackType</span></span>  
 <span data-ttu-id="c2996-126">Wskazuje typ wywołania zwrotnego, które zostało utworzone z [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c2996-126">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
 [<span data-ttu-id="c2996-127">CorDebugExceptionFlags — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c2996-127">CorDebugExceptionFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 <span data-ttu-id="c2996-128">Zawiera dodatkowe informacje o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c2996-128">Provides additional information about an exception.</span></span>  
  
 <span data-ttu-id="c2996-129">CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="c2996-129">CorDebugExceptionUnwindCallbackType</span></span>  
 <span data-ttu-id="c2996-130">Wskazuje sygnalizowane trwa przez wywołanie zwrotne w fazie unwind zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="c2996-130">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 [<span data-ttu-id="c2996-131">Cordebuggctype — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c2996-131">CorDebugGCType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 <span data-ttu-id="c2996-132">Wskazuje, czy moduł zbierający elementy bezużyteczne jest uruchomiona na serwerze lub stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="c2996-132">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
 [<span data-ttu-id="c2996-133">Cordebuggenerationtypes — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c2996-133">CorDebugGenerationTypes Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 <span data-ttu-id="c2996-134">Określa Generowanie obszaru pamięci na stercie zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="c2996-134">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
 <span data-ttu-id="c2996-135">CorDebugHandleType</span><span class="sxs-lookup"><span data-stu-id="c2996-135">CorDebugHandleType</span></span>  
 <span data-ttu-id="c2996-136">Wskazuje typ dojścia.</span><span class="sxs-lookup"><span data-stu-id="c2996-136">Indicates the handle type.</span></span>  
  
 [<span data-ttu-id="c2996-137">Cordebugiltonativemappingtypes — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c2996-137">CorDebugIlToNativeMappingTypes Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 <span data-ttu-id="c2996-138">Wskazuje, czy określony zakres natywnego instrukcje odpowiada specjalne kodu regionu.</span><span class="sxs-lookup"><span data-stu-id="c2996-138">Indicates whether a particular range of native instructions corresponds to a special code region.</span></span>  
  
 <span data-ttu-id="c2996-139">CorDebugIntercept</span><span class="sxs-lookup"><span data-stu-id="c2996-139">CorDebugIntercept</span></span>  
 <span data-ttu-id="c2996-140">Wskazuje typy kodu, które można podjąć w.</span><span class="sxs-lookup"><span data-stu-id="c2996-140">Indicates the types of code that can be stepped into.</span></span>  
  
 [<span data-ttu-id="c2996-141">CorDebugInterfaceVersion — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c2996-141">CorDebugInterfaceVersion Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 <span data-ttu-id="c2996-142">Określa wersję systemu .NET Framework lub wersji programu .NET Framework, w którym wprowadzono interfejs.</span><span class="sxs-lookup"><span data-stu-id="c2996-142">Specifies either a version of the .NET Framework, or the version of the .NET Framework in which an interface was introduced.</span></span>  
  
 <span data-ttu-id="c2996-143">CorDebugInternalFrameType</span><span class="sxs-lookup"><span data-stu-id="c2996-143">CorDebugInternalFrameType</span></span>  
 <span data-ttu-id="c2996-144">Określa typ ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="c2996-144">Identifies the type of stack frame.</span></span>  
  
 [<span data-ttu-id="c2996-145">CorDebugJITCompilerFlags — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c2996-145">CorDebugJITCompilerFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 <span data-ttu-id="c2996-146">Zawiera wartości, które wpływają na zachowanie zarządzanych kompilatora just in time (JIT).</span><span class="sxs-lookup"><span data-stu-id="c2996-146">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
 [<span data-ttu-id="c2996-147">CorDebugJITCompilerFlagsDeprecated — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c2996-147">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 <span data-ttu-id="c2996-148">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="c2996-148">Obsolete.</span></span> <span data-ttu-id="c2996-149">Użyj `CORDEBUG_JIT_DEFAULT` członkiem [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) wyliczenie zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="c2996-149">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
 <span data-ttu-id="c2996-150">CorDebugMappingResult</span><span class="sxs-lookup"><span data-stu-id="c2996-150">CorDebugMappingResult</span></span>  
 <span data-ttu-id="c2996-151">Zawiera szczegółowe informacje o sposobie uzyskano wartość wskaźnika instrukcji (IP).</span><span class="sxs-lookup"><span data-stu-id="c2996-151">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
 [<span data-ttu-id="c2996-152">CorDebugMDAFlags — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c2996-152">CorDebugMDAFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 <span data-ttu-id="c2996-153">Określa stan wątku, na którym jest uruchamiany zarządzany Asystent debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="c2996-153">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
 [<span data-ttu-id="c2996-154">Cordebugngenpolicy — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c2996-154">CorDebugNGenPolicy Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 <span data-ttu-id="c2996-155">Zawiera wartość, która określa, czy debuger ładuje obrazów natywnych (NGen) z pamięci podręcznej obrazów natywnych.</span><span class="sxs-lookup"><span data-stu-id="c2996-155">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
 [<span data-ttu-id="c2996-156">Wyliczenie CorDebugPlatform</span><span class="sxs-lookup"><span data-stu-id="c2996-156">CorDebugPlatform Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 <span data-ttu-id="c2996-157">Udostępnia wartości platform docelowych, które są używane przez [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c2996-157">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
 [<span data-ttu-id="c2996-158">Wyliczenie CorDebugRecordFormat</span><span class="sxs-lookup"><span data-stu-id="c2996-158">CorDebugRecordFormat Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 <span data-ttu-id="c2996-159">Opisuje format danych w tablicy bajtów, który zawiera informacje dotyczące zdarzenia debugowania natywnego wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c2996-159">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
 <span data-ttu-id="c2996-160">CorDebugRegister</span><span class="sxs-lookup"><span data-stu-id="c2996-160">CorDebugRegister</span></span>  
 <span data-ttu-id="c2996-161">Określa, rejestruje skojarzony z danym procesor.</span><span class="sxs-lookup"><span data-stu-id="c2996-161">Specifies the registers associated with a given processor architecture.</span></span>  
  
 [<span data-ttu-id="c2996-162">CorDebugSetContextFlag — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c2996-162">CorDebugSetContextFlag Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 <span data-ttu-id="c2996-163">Wskazuje, czy kontekst jest z aktywnego (lub typu liść) ramek na stosie lub został obliczony przy odwijanie od innej ramki.</span><span class="sxs-lookup"><span data-stu-id="c2996-163">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
 [<span data-ttu-id="c2996-164">Wyliczenie CorDebugStateChange</span><span class="sxs-lookup"><span data-stu-id="c2996-164">CorDebugStateChange Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 <span data-ttu-id="c2996-165">W tym artykule opisano wielkość pamięci podręcznej danych, które muszą zostać odrzucone na podstawie zmian do procesu.</span><span class="sxs-lookup"><span data-stu-id="c2996-165">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
 <span data-ttu-id="c2996-166">CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="c2996-166">CorDebugStepReason</span></span>  
 <span data-ttu-id="c2996-167">Wskazuje wynik pojedynczego kroku.</span><span class="sxs-lookup"><span data-stu-id="c2996-167">Indicates the outcome of an individual step.</span></span>  
  
 <span data-ttu-id="c2996-168">CorDebugThreadState</span><span class="sxs-lookup"><span data-stu-id="c2996-168">CorDebugThreadState</span></span>  
 <span data-ttu-id="c2996-169">Określa stan wątku do debugowania.</span><span class="sxs-lookup"><span data-stu-id="c2996-169">Specifies the state of a thread for debugging.</span></span>  
  
 <span data-ttu-id="c2996-170">\>CorDebugUnmappedStop</span><span class="sxs-lookup"><span data-stu-id="c2996-170">\>CorDebugUnmappedStop</span></span>  
 <span data-ttu-id="c2996-171">Określa typ Niemapowane kodu, które mogą wyzwalać zatrzymania wykonywania kodu przez stepper.</span><span class="sxs-lookup"><span data-stu-id="c2996-171">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
 <span data-ttu-id="c2996-172">CorDebugUserState</span><span class="sxs-lookup"><span data-stu-id="c2996-172">CorDebugUserState</span></span>  
 <span data-ttu-id="c2996-173">Wskazuje stan użytkownika wątku.</span><span class="sxs-lookup"><span data-stu-id="c2996-173">Indicates the user state of a thread.</span></span>  
  
 [<span data-ttu-id="c2996-174">Corgcreferencetype — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c2996-174">CorGCReferenceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 <span data-ttu-id="c2996-175">Określa źródło obiektu być zbierane z pamięci.</span><span class="sxs-lookup"><span data-stu-id="c2996-175">Identifies the source of an object to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="c2996-176">Wyliczenie ILCodeKind</span><span class="sxs-lookup"><span data-stu-id="c2996-176">ILCodeKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 <span data-ttu-id="c2996-177">Zawiera wartości, które określają, czy debuger jest w stanie uzyskać dostęp do zmiennych lokalnych lub kodzie dodanym w ReJIT Instrumentacji profilera.</span><span class="sxs-lookup"><span data-stu-id="c2996-177">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="c2996-178">LoggingLevelEnum — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c2996-178">LoggingLevelEnum Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 <span data-ttu-id="c2996-179">Wskazuje poziom ważności opisowym komunikatem, które są zapisywane w dzienniku zdarzeń, gdy zarządzanego wątku rejestruje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="c2996-179">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
 [<span data-ttu-id="c2996-180">LogSwitchCallReason — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c2996-180">LogSwitchCallReason Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 <span data-ttu-id="c2996-181">Wskazuje działanie zostało wykonane na przełączniku debugowania śledzenia.</span><span class="sxs-lookup"><span data-stu-id="c2996-181">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
 [<span data-ttu-id="c2996-182">VariableLocationType — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c2996-182">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 <span data-ttu-id="c2996-183">Wskazuje typ macierzysty lokalizacji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c2996-183">Indicates the native location type of a variable.</span></span>  
  
 [<span data-ttu-id="c2996-184">Wyliczenie WriteableMetadataUpdateMode</span><span class="sxs-lookup"><span data-stu-id="c2996-184">WriteableMetadataUpdateMode Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 <span data-ttu-id="c2996-185">Zawiera wartości, które określają, czy aktualizacje metadanych w pamięci są widoczne dla debugera.</span><span class="sxs-lookup"><span data-stu-id="c2996-185">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c2996-186">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="c2996-186">Related Sections</span></span>  
 [<span data-ttu-id="c2996-187">Klasy coclass debugowania</span><span class="sxs-lookup"><span data-stu-id="c2996-187">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="c2996-188">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="c2996-188">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="c2996-189">Statyczne funkcje globalne debugowania</span><span class="sxs-lookup"><span data-stu-id="c2996-189">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="c2996-190">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="c2996-190">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
