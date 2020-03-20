---
title: Debugowanie — wyliczenia
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: c37b6ff42b428184d301d63b6dbbd9d80a72bf3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179138"
---
# <a name="debugging-enumerations"></a><span data-ttu-id="b7648-102">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="b7648-102">Debugging Enumerations</span></span>
<span data-ttu-id="b7648-103">W tej sekcji opisano niezarządzane wyliczenia używane przez debugowanie interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="b7648-103">This section describes the unmanaged enumerations that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b7648-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b7648-104">In This Section</span></span>  
 [<span data-ttu-id="b7648-105">CLR_DEBUGGING_PROCESS_FLAGS, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b7648-105">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>](clr-debugging-process-flags-enumeration.md)  
 <span data-ttu-id="b7648-106">Zawiera wartości, które są używane przez [metodę ICLRDebugging::OpenVirtualProcess.](iclrdebugging-openvirtualprocess-method.md)</span><span class="sxs-lookup"><span data-stu-id="b7648-106">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="b7648-107">CLRDataEnumMemoryFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b7648-107">CLRDataEnumMemoryFlags Enumeration</span></span>](clrdataenummemoryflags-enumeration.md)  
 <span data-ttu-id="b7648-108">Wskazuje, które regiony pamięci wywołać [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) metoda powinna zawierać.</span><span class="sxs-lookup"><span data-stu-id="b7648-108">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
 [<span data-ttu-id="b7648-109">COR_PUB_ENUMPROCESS, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b7648-109">COR_PUB_ENUMPROCESS Enumeration</span></span>](cor-pub-enumprocess-enumeration.md)  
 <span data-ttu-id="b7648-110">Identyfikuje typ procesu, który ma być wyliczony.</span><span class="sxs-lookup"><span data-stu-id="b7648-110">Identifies the type of process to be enumerated.</span></span>  
  
 [<span data-ttu-id="b7648-111">CorDebugBlockingReason, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b7648-111">CorDebugBlockingReason Enumeration</span></span>](cordebugblockingreason-enumeration.md)  
 <span data-ttu-id="b7648-112">Określa powody, dla których wątek może zostać zablokowany na danym obiekcie.</span><span class="sxs-lookup"><span data-stu-id="b7648-112">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
 <span data-ttu-id="b7648-113">CorDebugChainReason</span><span class="sxs-lookup"><span data-stu-id="b7648-113">CorDebugChainReason</span></span>  
 <span data-ttu-id="b7648-114">Wskazuje przyczynę lub przyczyny rozpoczęcia łańcucha wywołań.</span><span class="sxs-lookup"><span data-stu-id="b7648-114">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
 [<span data-ttu-id="b7648-115">Wyliczenie CorDebugCodeInvokeKind</span><span class="sxs-lookup"><span data-stu-id="b7648-115">CorDebugCodeInvokeKind Enumeration</span></span>](cordebugcodeinvokekind-enumeration.md)  
 <span data-ttu-id="b7648-116">W tym artykule opisano, jak wyeksportowana funkcja wywołuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="b7648-116">Describes how an exported function invokes managed code.</span></span>  
  
 [<span data-ttu-id="b7648-117">CorDebugCodeInvokePurpose, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b7648-117">CorDebugCodeInvokePurpose Enumeration</span></span>](cordebugcodeinvokepurpose-enumeration.md)  
 <span data-ttu-id="b7648-118">Opisuje, dlaczego wyeksportowana funkcja wywołuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="b7648-118">Describes why an exported function calls managed code.</span></span>  
  
 <span data-ttu-id="b7648-119">CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="b7648-119">CorDebugCreateProcessFlags</span></span>  
 <span data-ttu-id="b7648-120">Udostępnia dodatkowe opcje debugowania, które mogą być używane w wywołaniu [metody ICorDebug::CreateProcess.](icordebug-createprocess-method.md)</span><span class="sxs-lookup"><span data-stu-id="b7648-120">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](icordebug-createprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="b7648-121">CorDebugDebugEventKind, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b7648-121">CorDebugDebugEventKind Enumeration</span></span>](cordebugdebugeventkind-enumeration.md)  
 <span data-ttu-id="b7648-122">Wskazuje typ zdarzenia, którego informacje są dekodowane przez [DecodeEvent](icordebugprocess6-decodeevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b7648-122">Indicates the type of event whose information is decoded by the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
 [<span data-ttu-id="b7648-123">Wyliczenie CorDebugDecodeEventFlagsWindows</span><span class="sxs-lookup"><span data-stu-id="b7648-123">CorDebugDecodeEventFlagsWindows Enumeration</span></span>](cordebugdecodeeventflagswindows-enumeration.md)  
 <span data-ttu-id="b7648-124">Zawiera dodatkowe informacje dotyczące zdarzeń debugowania na platformie Windows.</span><span class="sxs-lookup"><span data-stu-id="b7648-124">Provides additional information about debug events on the Windows platform.</span></span>  
  
 <span data-ttu-id="b7648-125">CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="b7648-125">CorDebugExceptionCallbackType</span></span>  
 <span data-ttu-id="b7648-126">Wskazuje typ wywołania zwrotnego, który jest wykonany ze zdarzenia [ICorDebugManagedCallback2::Exception.](icordebugmanagedcallback2-exception-method.md)</span><span class="sxs-lookup"><span data-stu-id="b7648-126">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
 [<span data-ttu-id="b7648-127">CorDebugExceptionFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b7648-127">CorDebugExceptionFlags Enumeration</span></span>](cordebugexceptionflags-enumeration.md)  
 <span data-ttu-id="b7648-128">Zawiera dodatkowe informacje o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b7648-128">Provides additional information about an exception.</span></span>  
  
 <span data-ttu-id="b7648-129">CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="b7648-129">CorDebugExceptionUnwindCallbackType</span></span>  
 <span data-ttu-id="b7648-130">Wskazuje zdarzenie, które jest sygnalizowane przez wywołanie zwrotne podczas fazy unwind.</span><span class="sxs-lookup"><span data-stu-id="b7648-130">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 [<span data-ttu-id="b7648-131">CorDebugGCType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b7648-131">CorDebugGCType Enumeration</span></span>](cordebuggctype-enumeration.md)  
 <span data-ttu-id="b7648-132">Wskazuje, czy moduł zbierający elementy bezużyteczne jest uruchomiony na stacji roboczej lub serwera.</span><span class="sxs-lookup"><span data-stu-id="b7648-132">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
 [<span data-ttu-id="b7648-133">CorDebugGenerationTypes, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b7648-133">CorDebugGenerationTypes Enumeration</span></span>](cordebuggenerationtypes-enumeration.md)  
 <span data-ttu-id="b7648-134">Określa generowanie regionu pamięci na zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="b7648-134">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
 <span data-ttu-id="b7648-135">CorDebugHandleType</span><span class="sxs-lookup"><span data-stu-id="b7648-135">CorDebugHandleType</span></span>  
 <span data-ttu-id="b7648-136">Wskazuje typ uchwytu.</span><span class="sxs-lookup"><span data-stu-id="b7648-136">Indicates the handle type.</span></span>  
  
 [<span data-ttu-id="b7648-137">CorDebugIlToNativeMappingTypes, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b7648-137">CorDebugIlToNativeMappingTypes Enumeration</span></span>](cordebugiltonativemappingtypes-enumeration.md)  
 <span data-ttu-id="b7648-138">Wskazuje, czy określony zakres instrukcji natywnych odpowiada specjalnemu regionowi kodu.</span><span class="sxs-lookup"><span data-stu-id="b7648-138">Indicates whether a particular range of native instructions corresponds to a special code region.</span></span>  
  
 <span data-ttu-id="b7648-139">CorDebugIntercept</span><span class="sxs-lookup"><span data-stu-id="b7648-139">CorDebugIntercept</span></span>  
 <span data-ttu-id="b7648-140">Wskazuje typy kodu, do których można wejść.</span><span class="sxs-lookup"><span data-stu-id="b7648-140">Indicates the types of code that can be stepped into.</span></span>  
  
 [<span data-ttu-id="b7648-141">CorDebugInterfaceVersion, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b7648-141">CorDebugInterfaceVersion Enumeration</span></span>](cordebuginterfaceversion-enumeration.md)  
 <span data-ttu-id="b7648-142">Określa wersję programu .NET Framework lub wersję programu .NET Framework, w której wprowadzono interfejs.</span><span class="sxs-lookup"><span data-stu-id="b7648-142">Specifies either a version of the .NET Framework, or the version of the .NET Framework in which an interface was introduced.</span></span>  
  
 <span data-ttu-id="b7648-143">CorDebugInternalFrameType</span><span class="sxs-lookup"><span data-stu-id="b7648-143">CorDebugInternalFrameType</span></span>  
 <span data-ttu-id="b7648-144">Identyfikuje typ ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="b7648-144">Identifies the type of stack frame.</span></span>  
  
 [<span data-ttu-id="b7648-145">CorDebugJITCompilerFlags, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b7648-145">CorDebugJITCompilerFlags Enumeration</span></span>](cordebugjitcompilerflags-enumeration.md)  
 <span data-ttu-id="b7648-146">Zawiera wartości, które wpływają na zachowanie kompilatora zarządzanego just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="b7648-146">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
 [<span data-ttu-id="b7648-147">CorDebugJITCompilerFlagsDeprecated, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b7648-147">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>](cordebugjitcompilerflagsdeprecated-enumeration.md)  
 <span data-ttu-id="b7648-148">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="b7648-148">Obsolete.</span></span> <span data-ttu-id="b7648-149">Zamiast `CORDEBUG_JIT_DEFAULT` tego należy użyć elementu członkowskiego [wyliczenia CorDebugJITCompilerFlags.](cordebugjitcompilerflags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="b7648-149">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
 <span data-ttu-id="b7648-150">CorDebugMappingResult</span><span class="sxs-lookup"><span data-stu-id="b7648-150">CorDebugMappingResult</span></span>  
 <span data-ttu-id="b7648-151">Zawiera szczegółowe informacje o tym, jak uzyskano wartość wskaźnika instrukcji (IP).</span><span class="sxs-lookup"><span data-stu-id="b7648-151">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
 [<span data-ttu-id="b7648-152">CorDebugMDAFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b7648-152">CorDebugMDAFlags Enumeration</span></span>](cordebugmdaflags-enumeration.md)  
 <span data-ttu-id="b7648-153">Określa stan wątku, na którym jest uruchamiany asystent debugowania zarządzanego (MDA).</span><span class="sxs-lookup"><span data-stu-id="b7648-153">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
 [<span data-ttu-id="b7648-154">CorDebugNGenPolicy, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b7648-154">CorDebugNGenPolicy Enumeration</span></span>](cordebugngenpolicy-enumeration.md)  
 <span data-ttu-id="b7648-155">Zapewnia wartość, która określa, czy debuger ładuje natywne obrazy (NGen) z pamięci podręcznej obrazu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="b7648-155">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
 [<span data-ttu-id="b7648-156">CorDebugPlatform, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b7648-156">CorDebugPlatform Enumeration</span></span>](cordebugplatform-enumeration.md)  
 <span data-ttu-id="b7648-157">Zawiera wartości platformy docelowej, które są używane przez [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b7648-157">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
 [<span data-ttu-id="b7648-158">Wyliczenie CorDebugRecordFormat</span><span class="sxs-lookup"><span data-stu-id="b7648-158">CorDebugRecordFormat Enumeration</span></span>](cordebugrecordformat-enumeration.md)  
 <span data-ttu-id="b7648-159">Opisuje format danych w tablicy bajtów, który zawiera informacje o zdarzeniu debugowania wyjątków natywnych.</span><span class="sxs-lookup"><span data-stu-id="b7648-159">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
 <span data-ttu-id="b7648-160">Rejestr CorDebug</span><span class="sxs-lookup"><span data-stu-id="b7648-160">CorDebugRegister</span></span>  
 <span data-ttu-id="b7648-161">Określa rejestry skojarzone z daną architekturą procesora.</span><span class="sxs-lookup"><span data-stu-id="b7648-161">Specifies the registers associated with a given processor architecture.</span></span>  
  
 [<span data-ttu-id="b7648-162">CorDebugSetContextFlag, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b7648-162">CorDebugSetContextFlag Enumeration</span></span>](cordebugsetcontextflag-enumeration.md)  
 <span data-ttu-id="b7648-163">Wskazuje, czy kontekst pochodzi z aktywnej (lub liścia) ramki na stosie lub został obliczony przez odwijanie z innej ramki.</span><span class="sxs-lookup"><span data-stu-id="b7648-163">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
 [<span data-ttu-id="b7648-164">CorDebugStateChange, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b7648-164">CorDebugStateChange Enumeration</span></span>](cordebugstatechange-enumeration.md)  
 <span data-ttu-id="b7648-165">W tym artykule opisano ilość danych w pamięci podręcznej, które muszą zostać odrzucone na podstawie zmian w procesie.</span><span class="sxs-lookup"><span data-stu-id="b7648-165">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
 <span data-ttu-id="b7648-166">CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="b7648-166">CorDebugStepReason</span></span>  
 <span data-ttu-id="b7648-167">Wskazuje wynik pojedynczego kroku.</span><span class="sxs-lookup"><span data-stu-id="b7648-167">Indicates the outcome of an individual step.</span></span>  
  
 <span data-ttu-id="b7648-168">CorDebugStan</span><span class="sxs-lookup"><span data-stu-id="b7648-168">CorDebugThreadState</span></span>  
 <span data-ttu-id="b7648-169">Określa stan wątku do debugowania.</span><span class="sxs-lookup"><span data-stu-id="b7648-169">Specifies the state of a thread for debugging.</span></span>  
  
 <span data-ttu-id="b7648-170">\>CorDebugUnmappedStop</span><span class="sxs-lookup"><span data-stu-id="b7648-170">\>CorDebugUnmappedStop</span></span>  
 <span data-ttu-id="b7648-171">Określa typ niezamapowanego kodu, który może wyzwolić zatrzymanie w wykonaniu kodu przez stepper.</span><span class="sxs-lookup"><span data-stu-id="b7648-171">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
 <span data-ttu-id="b7648-172">Stan CorDebugUser</span><span class="sxs-lookup"><span data-stu-id="b7648-172">CorDebugUserState</span></span>  
 <span data-ttu-id="b7648-173">Wskazuje stan użytkownika wątku.</span><span class="sxs-lookup"><span data-stu-id="b7648-173">Indicates the user state of a thread.</span></span>  
  
 [<span data-ttu-id="b7648-174">CorGCReferenceType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b7648-174">CorGCReferenceType Enumeration</span></span>](corgcreferencetype-enumeration.md)  
 <span data-ttu-id="b7648-175">Identyfikuje źródło obiektu, który ma być zbierany z modułem.</span><span class="sxs-lookup"><span data-stu-id="b7648-175">Identifies the source of an object to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="b7648-176">ILCodeKind, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b7648-176">ILCodeKind Enumeration</span></span>](ilcodekind-enumeration.md)  
 <span data-ttu-id="b7648-177">Zawiera wartości, które określają, czy debuger jest w stanie uzyskać dostęp do zmiennych lokalnych lub kodu dodanego w profiler Instrumentacji ReJIT.</span><span class="sxs-lookup"><span data-stu-id="b7648-177">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="b7648-178">LoggingLevelEnum — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b7648-178">LoggingLevelEnum Enumeration</span></span>](logginglevelenum-enumeration.md)  
 <span data-ttu-id="b7648-179">Wskazuje poziom ważności opisowego komunikatu, który jest zapisywany w dzienniku zdarzeń, gdy zarządzany wątek rejestruje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="b7648-179">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
 [<span data-ttu-id="b7648-180">LogSwitchCallReason, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b7648-180">LogSwitchCallReason Enumeration</span></span>](logswitchcallreason-enumeration.md)  
 <span data-ttu-id="b7648-181">Wskazuje operację, która została wykonana na debugowania/śledzenia przełącznika.</span><span class="sxs-lookup"><span data-stu-id="b7648-181">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
 [<span data-ttu-id="b7648-182">VariableLocationType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b7648-182">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)  
 <span data-ttu-id="b7648-183">Wskazuje natywny typ lokalizacji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b7648-183">Indicates the native location type of a variable.</span></span>  
  
 [<span data-ttu-id="b7648-184">Wyliczenie WriteableMetadataUpdateMode</span><span class="sxs-lookup"><span data-stu-id="b7648-184">WriteableMetadataUpdateMode Enumeration</span></span>](writeablemetadataupdatemode-enumeration.md)  
 <span data-ttu-id="b7648-185">Zawiera wartości, które określają, czy aktualizacje metadane w pamięci są widoczne dla debugera.</span><span class="sxs-lookup"><span data-stu-id="b7648-185">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>

 <span data-ttu-id="b7648-186">[Wyliczanie clrDataSourceType](clrdatasourcetype-enumeration.md) Zawiera wartości, które są używane przez CLRDATA_IL_ADDRESS_MAP struktury.</span><span class="sxs-lookup"><span data-stu-id="b7648-186">[ClrDataSourceType Enumeration](clrdatasourcetype-enumeration.md) Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="b7648-187">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="b7648-187">Related Sections</span></span>  
 [<span data-ttu-id="b7648-188">Klasy coclass debugowania</span><span class="sxs-lookup"><span data-stu-id="b7648-188">Debugging Coclasses</span></span>](debugging-coclasses.md)  
  
 [<span data-ttu-id="b7648-189">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="b7648-189">Debugging Interfaces</span></span>](debugging-interfaces.md)  
  
 [<span data-ttu-id="b7648-190">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="b7648-190">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)  
  
 [<span data-ttu-id="b7648-191">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="b7648-191">Debugging Structures</span></span>](debugging-structures.md)
