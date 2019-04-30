---
title: Debugowanie — wyliczenia
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5edd6dfb3dac05ce4614c43949f2ec4c19b5f742
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698515"
---
# <a name="debugging-enumerations"></a><span data-ttu-id="c8cb7-102">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c8cb7-102">Debugging Enumerations</span></span>
<span data-ttu-id="c8cb7-103">W tej sekcji opisano niezarządzane wyliczenia, których używa interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-103">This section describes the unmanaged enumerations that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c8cb7-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c8cb7-104">In This Section</span></span>  
 [<span data-ttu-id="c8cb7-105">CLR_DEBUGGING_PROCESS_FLAGS, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-105">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 <span data-ttu-id="c8cb7-106">Zawiera wartości, które są używane przez [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-106">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="c8cb7-107">CLRDataEnumMemoryFlags, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-107">CLRDataEnumMemoryFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 <span data-ttu-id="c8cb7-108">Wskazuje, które regiony pamięci wywołanie [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) powinna zawierać metodę.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-108">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
 [<span data-ttu-id="c8cb7-109">COR_PUB_ENUMPROCESS, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-109">COR_PUB_ENUMPROCESS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 <span data-ttu-id="c8cb7-110">Identyfikuje typ procesu do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-110">Identifies the type of process to be enumerated.</span></span>  
  
 [<span data-ttu-id="c8cb7-111">CorDebugBlockingReason, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-111">CorDebugBlockingReason Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 <span data-ttu-id="c8cb7-112">Określa przyczyny, dlaczego wątek może stać się zablokowany dla danego obiektu.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-112">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
 <span data-ttu-id="c8cb7-113">CorDebugChainReason</span><span class="sxs-lookup"><span data-stu-id="c8cb7-113">CorDebugChainReason</span></span>  
 <span data-ttu-id="c8cb7-114">Wskazuje powód lub powody do rozpoczęcia łańcuch wywołań.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-114">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
 [<span data-ttu-id="c8cb7-115">CorDebugCodeInvokeKind, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-115">CorDebugCodeInvokeKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 <span data-ttu-id="c8cb7-116">W tym artykule opisano, jak eksportowanych funkcji wywołuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-116">Describes how an exported function invokes managed code.</span></span>  
  
 [<span data-ttu-id="c8cb7-117">CorDebugCodeInvokePurpose, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-117">CorDebugCodeInvokePurpose Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 <span data-ttu-id="c8cb7-118">W tym artykule opisano, dlaczego eksportowanych funkcji wywołuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-118">Describes why an exported function calls managed code.</span></span>  
  
 <span data-ttu-id="c8cb7-119">CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="c8cb7-119">CorDebugCreateProcessFlags</span></span>  
 <span data-ttu-id="c8cb7-120">Zapewnia dodatkowe opcje debugowania, które mogą być używane w wywołaniu [icordebug::CreateProcess —](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-120">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="c8cb7-121">CorDebugDebugEventKind, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-121">CorDebugDebugEventKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 <span data-ttu-id="c8cb7-122">Określa typ zdarzenia, o których informacje jest dekodowana przy [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-122">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
 [<span data-ttu-id="c8cb7-123">CorDebugDecodeEventFlagsWindows, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-123">CorDebugDecodeEventFlagsWindows Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 <span data-ttu-id="c8cb7-124">Zawiera dodatkowe informacje na temat zdarzeń debugowania na platformie Windows.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-124">Provides additional information about debug events on the Windows platform.</span></span>  
  
 <span data-ttu-id="c8cb7-125">CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="c8cb7-125">CorDebugExceptionCallbackType</span></span>  
 <span data-ttu-id="c8cb7-126">Wskazuje typ wywołanie zwrotne, które zostało wprowadzone przy użyciu [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-126">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
 [<span data-ttu-id="c8cb7-127">CorDebugExceptionFlags, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-127">CorDebugExceptionFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 <span data-ttu-id="c8cb7-128">Zawiera dodatkowe informacje o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-128">Provides additional information about an exception.</span></span>  
  
 <span data-ttu-id="c8cb7-129">CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="c8cb7-129">CorDebugExceptionUnwindCallbackType</span></span>  
 <span data-ttu-id="c8cb7-130">Określa zdarzenie, które jest jest sygnalizowane przez wywołania zwrotnego w fazie unwind.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-130">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 [<span data-ttu-id="c8cb7-131">CorDebugGCType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-131">CorDebugGCType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 <span data-ttu-id="c8cb7-132">Wskazuje, czy moduł garbage collector jest uruchomiona na serwerze lub stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-132">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
 [<span data-ttu-id="c8cb7-133">CorDebugGenerationTypes, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-133">CorDebugGenerationTypes Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 <span data-ttu-id="c8cb7-134">Określa Generowanie region pamięci na stosie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-134">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
 <span data-ttu-id="c8cb7-135">CorDebugHandleType</span><span class="sxs-lookup"><span data-stu-id="c8cb7-135">CorDebugHandleType</span></span>  
 <span data-ttu-id="c8cb7-136">Wskazuje typ uchwytu.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-136">Indicates the handle type.</span></span>  
  
 [<span data-ttu-id="c8cb7-137">CorDebugIlToNativeMappingTypes, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-137">CorDebugIlToNativeMappingTypes Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 <span data-ttu-id="c8cb7-138">Wskazuje, czy określony zakres natywne instrukcje odnosi się do regionu specjalny kod.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-138">Indicates whether a particular range of native instructions corresponds to a special code region.</span></span>  
  
 <span data-ttu-id="c8cb7-139">CorDebugIntercept</span><span class="sxs-lookup"><span data-stu-id="c8cb7-139">CorDebugIntercept</span></span>  
 <span data-ttu-id="c8cb7-140">Wskazuje typy kodu, który może być zmieniana w.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-140">Indicates the types of code that can be stepped into.</span></span>  
  
 [<span data-ttu-id="c8cb7-141">CorDebugInterfaceVersion, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-141">CorDebugInterfaceVersion Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 <span data-ttu-id="c8cb7-142">Określa wersję programu .NET Framework lub wersji programu .NET Framework, w której wprowadzono interfejs.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-142">Specifies either a version of the .NET Framework, or the version of the .NET Framework in which an interface was introduced.</span></span>  
  
 <span data-ttu-id="c8cb7-143">CorDebugInternalFrameType</span><span class="sxs-lookup"><span data-stu-id="c8cb7-143">CorDebugInternalFrameType</span></span>  
 <span data-ttu-id="c8cb7-144">Określa typ ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-144">Identifies the type of stack frame.</span></span>  
  
 [<span data-ttu-id="c8cb7-145">CorDebugJITCompilerFlags, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-145">CorDebugJITCompilerFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 <span data-ttu-id="c8cb7-146">Zawiera wartości, które wpływają na zachowanie zarządzanych kompilator just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="c8cb7-146">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
 [<span data-ttu-id="c8cb7-147">CorDebugJITCompilerFlagsDeprecated, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-147">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 <span data-ttu-id="c8cb7-148">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-148">Obsolete.</span></span> <span data-ttu-id="c8cb7-149">Użyj `CORDEBUG_JIT_DEFAULT` członkiem [cordebugjitcompilerflags —](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) wyliczenia zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-149">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
 <span data-ttu-id="c8cb7-150">CorDebugMappingResult</span><span class="sxs-lookup"><span data-stu-id="c8cb7-150">CorDebugMappingResult</span></span>  
 <span data-ttu-id="c8cb7-151">Zawiera szczegółowe informacje, jak uzyskać była wartość wskaźnika instrukcji (IP).</span><span class="sxs-lookup"><span data-stu-id="c8cb7-151">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
 [<span data-ttu-id="c8cb7-152">CorDebugMDAFlags, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-152">CorDebugMDAFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 <span data-ttu-id="c8cb7-153">Określa stan wątku, na którym jest uruchamiany zarządzanego Asystenta debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="c8cb7-153">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
 [<span data-ttu-id="c8cb7-154">CorDebugNGenPolicy, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-154">CorDebugNGenPolicy Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 <span data-ttu-id="c8cb7-155">Zawiera wartość określającą, czy debuger wczytuje obrazów macierzystych (NGen) z pamięci podręcznej obrazów natywnych.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-155">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
 [<span data-ttu-id="c8cb7-156">CorDebugPlatform, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-156">CorDebugPlatform Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 <span data-ttu-id="c8cb7-157">Udostępnia wartości platformy docelowe, które są używane przez [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-157">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
 [<span data-ttu-id="c8cb7-158">CorDebugRecordFormat, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-158">CorDebugRecordFormat Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 <span data-ttu-id="c8cb7-159">W tym artykule opisano format danych w tablicy bajtowej, zawierający informacje o zdarzeniu debugowania natywnych wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-159">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
 <span data-ttu-id="c8cb7-160">CorDebugRegister</span><span class="sxs-lookup"><span data-stu-id="c8cb7-160">CorDebugRegister</span></span>  
 <span data-ttu-id="c8cb7-161">Określa rejestrów związane z architekturą procesora w danym.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-161">Specifies the registers associated with a given processor architecture.</span></span>  
  
 [<span data-ttu-id="c8cb7-162">CorDebugSetContextFlag, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-162">CorDebugSetContextFlag Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 <span data-ttu-id="c8cb7-163">Wskazuje, czy kontekst jest z aktywnej (lub liścia) ramek na stosie lub obliczeniu, odwijanie od innej ramki.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-163">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
 [<span data-ttu-id="c8cb7-164">CorDebugStateChange, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-164">CorDebugStateChange Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 <span data-ttu-id="c8cb7-165">W tym artykule opisano wielkość pamięci podręcznej danych, które muszą zostać odrzucone na podstawie zmian do procesu.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-165">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
 <span data-ttu-id="c8cb7-166">CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="c8cb7-166">CorDebugStepReason</span></span>  
 <span data-ttu-id="c8cb7-167">Wskazuje wynik pojedynczego kroku.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-167">Indicates the outcome of an individual step.</span></span>  
  
 <span data-ttu-id="c8cb7-168">CorDebugThreadState</span><span class="sxs-lookup"><span data-stu-id="c8cb7-168">CorDebugThreadState</span></span>  
 <span data-ttu-id="c8cb7-169">Określa stan wątku do debugowania.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-169">Specifies the state of a thread for debugging.</span></span>  
  
 <span data-ttu-id="c8cb7-170">\>CorDebugUnmappedStop</span><span class="sxs-lookup"><span data-stu-id="c8cb7-170">\>CorDebugUnmappedStop</span></span>  
 <span data-ttu-id="c8cb7-171">Określa typ niezamapowane kod, który możesz wyzwolić stepper zatrzymania wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-171">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
 <span data-ttu-id="c8cb7-172">CorDebugUserState</span><span class="sxs-lookup"><span data-stu-id="c8cb7-172">CorDebugUserState</span></span>  
 <span data-ttu-id="c8cb7-173">Wskazuje stan wątku użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-173">Indicates the user state of a thread.</span></span>  
  
 [<span data-ttu-id="c8cb7-174">CorGCReferenceType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-174">CorGCReferenceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 <span data-ttu-id="c8cb7-175">Określa źródło obiektu zebranych elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-175">Identifies the source of an object to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="c8cb7-176">ILCodeKind, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-176">ILCodeKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 <span data-ttu-id="c8cb7-177">Zawiera wartości, które określają, czy debuger jest w stanie uzyskać dostęp do zmiennych lokalnych lub kodzie dodanym w profilerze ReJIT instrumentacji.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-177">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="c8cb7-178">LoggingLevelEnum, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-178">LoggingLevelEnum Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 <span data-ttu-id="c8cb7-179">Wskazuje poziom ważności opisowy komunikat, który jest zapisywany w dzienniku zdarzeń, gdy wątków zarządzanych rejestruje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-179">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
 [<span data-ttu-id="c8cb7-180">LogSwitchCallReason, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-180">LogSwitchCallReason Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 <span data-ttu-id="c8cb7-181">Określa operację, która została wykonana w przełączniku debugowanie śledzenia.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-181">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
 [<span data-ttu-id="c8cb7-182">VariableLocationType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-182">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 <span data-ttu-id="c8cb7-183">Wskazuje typ lokalizacji natywnych zmienną.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-183">Indicates the native location type of a variable.</span></span>  
  
 [<span data-ttu-id="c8cb7-184">WriteableMetadataUpdateMode, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8cb7-184">WriteableMetadataUpdateMode Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 <span data-ttu-id="c8cb7-185">Zawiera wartości, które określają, czy aktualizacje metadanych w pamięci są widoczne dla debugera.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-185">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span> 

 <span data-ttu-id="c8cb7-186">[Wyliczenie ClrDataSourceType](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md) zawiera wartości, które są używane przez strukturę CLRDATA_IL_ADDRESS_MAP.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-186">[ClrDataSourceType Enumeration](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md) Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="c8cb7-187">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="c8cb7-187">Related Sections</span></span>  
 [<span data-ttu-id="c8cb7-188">Klasy coclass debugowania</span><span class="sxs-lookup"><span data-stu-id="c8cb7-188">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="c8cb7-189">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c8cb7-189">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="c8cb7-190">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="c8cb7-190">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="c8cb7-191">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="c8cb7-191">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
