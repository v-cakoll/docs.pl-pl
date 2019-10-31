---
title: Debugowanie — wyliczenia
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: 7948b78da1db5267ce53364af1e4a26ff73801e0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124328"
---
# <a name="debugging-enumerations"></a><span data-ttu-id="fccc1-102">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="fccc1-102">Debugging Enumerations</span></span>
<span data-ttu-id="fccc1-103">W tej sekcji opisano niezarządzane wyliczenia używane przez interfejs API debugowania.</span><span class="sxs-lookup"><span data-stu-id="fccc1-103">This section describes the unmanaged enumerations that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fccc1-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="fccc1-104">In This Section</span></span>  
 [<span data-ttu-id="fccc1-105">CLR_DEBUGGING_PROCESS_FLAGS, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-105">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 <span data-ttu-id="fccc1-106">Dostarcza wartości, które są używane przez metodę [ICLRDebugging:: OpenVirtualProcess —](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fccc1-106">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="fccc1-107">CLRDataEnumMemoryFlags, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-107">CLRDataEnumMemoryFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 <span data-ttu-id="fccc1-108">Wskazuje, które regiony pamięci są wywoływane przez wywołanie metody [ICLRDataEnumMemoryRegions:: EnumMemoryRegions —](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fccc1-108">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
 [<span data-ttu-id="fccc1-109">COR_PUB_ENUMPROCESS, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-109">COR_PUB_ENUMPROCESS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 <span data-ttu-id="fccc1-110">Identyfikuje typ procesu do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="fccc1-110">Identifies the type of process to be enumerated.</span></span>  
  
 [<span data-ttu-id="fccc1-111">CorDebugBlockingReason, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-111">CorDebugBlockingReason Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 <span data-ttu-id="fccc1-112">Określa przyczyny, dla których wątek może zostać zablokowany dla danego obiektu.</span><span class="sxs-lookup"><span data-stu-id="fccc1-112">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
 <span data-ttu-id="fccc1-113">CorDebugChainReason —</span><span class="sxs-lookup"><span data-stu-id="fccc1-113">CorDebugChainReason</span></span>  
 <span data-ttu-id="fccc1-114">Wskazuje przyczynę lub przyczyny inicjacji łańcucha wywołań.</span><span class="sxs-lookup"><span data-stu-id="fccc1-114">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
 [<span data-ttu-id="fccc1-115">CorDebugCodeInvokeKind, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-115">CorDebugCodeInvokeKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 <span data-ttu-id="fccc1-116">Opisuje sposób, w jaki wyeksportowana funkcja wywołuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="fccc1-116">Describes how an exported function invokes managed code.</span></span>  
  
 [<span data-ttu-id="fccc1-117">CorDebugCodeInvokePurpose, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-117">CorDebugCodeInvokePurpose Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 <span data-ttu-id="fccc1-118">Opisuje, dlaczego wyeksportowana funkcja wywołuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="fccc1-118">Describes why an exported function calls managed code.</span></span>  
  
 <span data-ttu-id="fccc1-119">CorDebugCreateProcessFlags —</span><span class="sxs-lookup"><span data-stu-id="fccc1-119">CorDebugCreateProcessFlags</span></span>  
 <span data-ttu-id="fccc1-120">Zapewnia dodatkowe opcje debugowania, których można użyć w wywołaniu metody [ICorDebug:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fccc1-120">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="fccc1-121">CorDebugDebugEventKind, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-121">CorDebugDebugEventKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 <span data-ttu-id="fccc1-122">Wskazuje typ zdarzenia, którego informacje są dekodowane przez metodę [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fccc1-122">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
 [<span data-ttu-id="fccc1-123">CorDebugDecodeEventFlagsWindows, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-123">CorDebugDecodeEventFlagsWindows Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 <span data-ttu-id="fccc1-124">Zawiera dodatkowe informacje na temat zdarzeń debugowania na platformie Windows.</span><span class="sxs-lookup"><span data-stu-id="fccc1-124">Provides additional information about debug events on the Windows platform.</span></span>  
  
 <span data-ttu-id="fccc1-125">CorDebugExceptionCallbackType —</span><span class="sxs-lookup"><span data-stu-id="fccc1-125">CorDebugExceptionCallbackType</span></span>  
 <span data-ttu-id="fccc1-126">Wskazuje typ wywołania zwrotnego, które jest wykonywane z [ICorDebugManagedCallback2:: Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fccc1-126">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
 [<span data-ttu-id="fccc1-127">CorDebugExceptionFlags, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-127">CorDebugExceptionFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 <span data-ttu-id="fccc1-128">Zawiera dodatkowe informacje o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="fccc1-128">Provides additional information about an exception.</span></span>  
  
 <span data-ttu-id="fccc1-129">CorDebugExceptionUnwindCallbackType —</span><span class="sxs-lookup"><span data-stu-id="fccc1-129">CorDebugExceptionUnwindCallbackType</span></span>  
 <span data-ttu-id="fccc1-130">Wskazuje zdarzenie, które jest sygnalizowane przez wywołanie zwrotne w fazie unwind.</span><span class="sxs-lookup"><span data-stu-id="fccc1-130">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 [<span data-ttu-id="fccc1-131">CorDebugGCType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-131">CorDebugGCType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 <span data-ttu-id="fccc1-132">Wskazuje, czy moduł wyrzucania elementów bezużytecznych jest uruchomiony na stacji roboczej lub na serwerze.</span><span class="sxs-lookup"><span data-stu-id="fccc1-132">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
 [<span data-ttu-id="fccc1-133">CorDebugGenerationTypes, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-133">CorDebugGenerationTypes Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 <span data-ttu-id="fccc1-134">Określa generowanie regionu pamięci na zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="fccc1-134">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
 <span data-ttu-id="fccc1-135">CorDebugHandleType —</span><span class="sxs-lookup"><span data-stu-id="fccc1-135">CorDebugHandleType</span></span>  
 <span data-ttu-id="fccc1-136">Wskazuje typ dojścia.</span><span class="sxs-lookup"><span data-stu-id="fccc1-136">Indicates the handle type.</span></span>  
  
 [<span data-ttu-id="fccc1-137">CorDebugIlToNativeMappingTypes, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-137">CorDebugIlToNativeMappingTypes Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 <span data-ttu-id="fccc1-138">Wskazuje, czy konkretny zakres instrukcji macierzystych odpowiada specjalnemu regionowi kodu.</span><span class="sxs-lookup"><span data-stu-id="fccc1-138">Indicates whether a particular range of native instructions corresponds to a special code region.</span></span>  
  
 <span data-ttu-id="fccc1-139">CorDebugIntercept —</span><span class="sxs-lookup"><span data-stu-id="fccc1-139">CorDebugIntercept</span></span>  
 <span data-ttu-id="fccc1-140">Wskazuje typy kodu, do którego można wykonać te działania.</span><span class="sxs-lookup"><span data-stu-id="fccc1-140">Indicates the types of code that can be stepped into.</span></span>  
  
 [<span data-ttu-id="fccc1-141">CorDebugInterfaceVersion, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-141">CorDebugInterfaceVersion Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 <span data-ttu-id="fccc1-142">Określa wersję .NET Framework lub wersję .NET Framework, w której został wprowadzony interfejs.</span><span class="sxs-lookup"><span data-stu-id="fccc1-142">Specifies either a version of the .NET Framework, or the version of the .NET Framework in which an interface was introduced.</span></span>  
  
 <span data-ttu-id="fccc1-143">CorDebugInternalFrameType —</span><span class="sxs-lookup"><span data-stu-id="fccc1-143">CorDebugInternalFrameType</span></span>  
 <span data-ttu-id="fccc1-144">Identyfikuje typ ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="fccc1-144">Identifies the type of stack frame.</span></span>  
  
 [<span data-ttu-id="fccc1-145">CorDebugJITCompilerFlags, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-145">CorDebugJITCompilerFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 <span data-ttu-id="fccc1-146">Zawiera wartości wpływające na zachowanie kompilatora zarządzanego (just-in-Time).</span><span class="sxs-lookup"><span data-stu-id="fccc1-146">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
 [<span data-ttu-id="fccc1-147">CorDebugJITCompilerFlagsDeprecated, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-147">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 <span data-ttu-id="fccc1-148">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="fccc1-148">Obsolete.</span></span> <span data-ttu-id="fccc1-149">Zamiast tego użyj `CORDEBUG_JIT_DEFAULT` elementu członkowskiego wyliczenia [CorDebugJITCompilerFlags —](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="fccc1-149">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
 <span data-ttu-id="fccc1-150">CorDebugMappingResult —</span><span class="sxs-lookup"><span data-stu-id="fccc1-150">CorDebugMappingResult</span></span>  
 <span data-ttu-id="fccc1-151">Zawiera szczegółowe informacje o sposobie uzyskiwania wartości wskaźnika instrukcji (IP).</span><span class="sxs-lookup"><span data-stu-id="fccc1-151">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
 [<span data-ttu-id="fccc1-152">CorDebugMDAFlags, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-152">CorDebugMDAFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 <span data-ttu-id="fccc1-153">Określa stan wątku, w którym jest uruchamiany Asystent debugowania zarządzanego (MDA).</span><span class="sxs-lookup"><span data-stu-id="fccc1-153">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
 [<span data-ttu-id="fccc1-154">CorDebugNGenPolicy, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-154">CorDebugNGenPolicy Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 <span data-ttu-id="fccc1-155">Zapewnia wartość określającą, czy debuger ładuje obrazy natywne (NGen) z pamięci podręcznej obrazów natywnych.</span><span class="sxs-lookup"><span data-stu-id="fccc1-155">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
 [<span data-ttu-id="fccc1-156">CorDebugPlatform, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-156">CorDebugPlatform Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 <span data-ttu-id="fccc1-157">Zapewnia wartości platformy docelowej, które są używane przez metodę [ICorDebugDataTarget:: GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fccc1-157">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
 [<span data-ttu-id="fccc1-158">CorDebugRecordFormat, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-158">CorDebugRecordFormat Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 <span data-ttu-id="fccc1-159">Opisuje format danych w tablicy bajtów, który zawiera informacje na temat natywnego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="fccc1-159">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
 <span data-ttu-id="fccc1-160">CorDebugRegister —</span><span class="sxs-lookup"><span data-stu-id="fccc1-160">CorDebugRegister</span></span>  
 <span data-ttu-id="fccc1-161">Określa rejestry skojarzone z daną architekturą procesora.</span><span class="sxs-lookup"><span data-stu-id="fccc1-161">Specifies the registers associated with a given processor architecture.</span></span>  
  
 [<span data-ttu-id="fccc1-162">CorDebugSetContextFlag, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-162">CorDebugSetContextFlag Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 <span data-ttu-id="fccc1-163">Wskazuje, czy kontekst pochodzi z aktywnej ramki (lub liściowej) na stosie czy został obliczony przez odróżnienie od innej ramki.</span><span class="sxs-lookup"><span data-stu-id="fccc1-163">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
 [<span data-ttu-id="fccc1-164">CorDebugStateChange, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-164">CorDebugStateChange Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 <span data-ttu-id="fccc1-165">Opisuje ilość danych buforowanych, które muszą zostać odrzucone na podstawie zmian w procesie.</span><span class="sxs-lookup"><span data-stu-id="fccc1-165">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
 <span data-ttu-id="fccc1-166">CorDebugStepReason —</span><span class="sxs-lookup"><span data-stu-id="fccc1-166">CorDebugStepReason</span></span>  
 <span data-ttu-id="fccc1-167">Wskazuje wynik pojedynczego kroku.</span><span class="sxs-lookup"><span data-stu-id="fccc1-167">Indicates the outcome of an individual step.</span></span>  
  
 <span data-ttu-id="fccc1-168">CorDebugThreadState —</span><span class="sxs-lookup"><span data-stu-id="fccc1-168">CorDebugThreadState</span></span>  
 <span data-ttu-id="fccc1-169">Określa stan wątku do debugowania.</span><span class="sxs-lookup"><span data-stu-id="fccc1-169">Specifies the state of a thread for debugging.</span></span>  
  
 <span data-ttu-id="fccc1-170">\>CorDebugUnmappedStop —</span><span class="sxs-lookup"><span data-stu-id="fccc1-170">\>CorDebugUnmappedStop</span></span>  
 <span data-ttu-id="fccc1-171">Określa typ niezamapowanego kodu, który może wyzwolić zatrzymanie w wykonaniu kodu przez stepper.</span><span class="sxs-lookup"><span data-stu-id="fccc1-171">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
 <span data-ttu-id="fccc1-172">CorDebugUserState —</span><span class="sxs-lookup"><span data-stu-id="fccc1-172">CorDebugUserState</span></span>  
 <span data-ttu-id="fccc1-173">Wskazuje stan użytkownika wątku.</span><span class="sxs-lookup"><span data-stu-id="fccc1-173">Indicates the user state of a thread.</span></span>  
  
 [<span data-ttu-id="fccc1-174">CorGCReferenceType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-174">CorGCReferenceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 <span data-ttu-id="fccc1-175">Określa źródło obiektu, które ma zostać pobrane jako elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="fccc1-175">Identifies the source of an object to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="fccc1-176">ILCodeKind, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-176">ILCodeKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 <span data-ttu-id="fccc1-177">Zawiera wartości, które określają, czy debuger może uzyskać dostęp do zmiennych lokalnych lub kodu dodanego w instrumentacji profilera ReJIT.</span><span class="sxs-lookup"><span data-stu-id="fccc1-177">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="fccc1-178">LoggingLevelEnum, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-178">LoggingLevelEnum Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 <span data-ttu-id="fccc1-179">Wskazuje poziom ważności komunikatu opisowego, który jest zapisywana w dzienniku zdarzeń, gdy zarządzany wątek rejestruje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="fccc1-179">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
 [<span data-ttu-id="fccc1-180">LogSwitchCallReason, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-180">LogSwitchCallReason Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 <span data-ttu-id="fccc1-181">Wskazuje operację wykonywaną na przełączniku debugowania/śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fccc1-181">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
 [<span data-ttu-id="fccc1-182">VariableLocationType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-182">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 <span data-ttu-id="fccc1-183">Wskazuje typ lokalizacji natywnej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="fccc1-183">Indicates the native location type of a variable.</span></span>  
  
 [<span data-ttu-id="fccc1-184">WriteableMetadataUpdateMode, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccc1-184">WriteableMetadataUpdateMode Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 <span data-ttu-id="fccc1-185">Zawiera wartości, które określają, czy aktualizacje w pamięci mają być widoczne dla debugera.</span><span class="sxs-lookup"><span data-stu-id="fccc1-185">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span> 

 <span data-ttu-id="fccc1-186">[ClrDataSourceType, Wyliczenie](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md) Dostarcza wartości, które są używane przez strukturę CLRDATA_IL_ADDRESS_MAP.</span><span class="sxs-lookup"><span data-stu-id="fccc1-186">[ClrDataSourceType Enumeration](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md) Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="fccc1-187">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="fccc1-187">Related Sections</span></span>  
 [<span data-ttu-id="fccc1-188">Klasy coclass debugowania</span><span class="sxs-lookup"><span data-stu-id="fccc1-188">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="fccc1-189">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="fccc1-189">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="fccc1-190">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="fccc1-190">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="fccc1-191">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="fccc1-191">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
