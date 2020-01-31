---
title: Debugowanie — wyliczenia
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: a83b1aa0b2cc068ed2f73dca04083b1085d45201
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789160"
---
# <a name="debugging-enumerations"></a><span data-ttu-id="97a9c-102">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="97a9c-102">Debugging Enumerations</span></span>
<span data-ttu-id="97a9c-103">W tej sekcji opisano niezarządzane wyliczenia używane przez interfejs API debugowania.</span><span class="sxs-lookup"><span data-stu-id="97a9c-103">This section describes the unmanaged enumerations that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="97a9c-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="97a9c-104">In This Section</span></span>  
 [<span data-ttu-id="97a9c-105">CLR_DEBUGGING_PROCESS_FLAGS, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-105">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>](clr-debugging-process-flags-enumeration.md)  
 <span data-ttu-id="97a9c-106">Dostarcza wartości, które są używane przez metodę [ICLRDebugging:: OpenVirtualProcess —](iclrdebugging-openvirtualprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="97a9c-106">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="97a9c-107">CLRDataEnumMemoryFlags, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-107">CLRDataEnumMemoryFlags Enumeration</span></span>](clrdataenummemoryflags-enumeration.md)  
 <span data-ttu-id="97a9c-108">Wskazuje, które regiony pamięci są wywoływane przez wywołanie metody [ICLRDataEnumMemoryRegions:: EnumMemoryRegions —](iclrdataenummemoryregions-enummemoryregions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="97a9c-108">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
 [<span data-ttu-id="97a9c-109">COR_PUB_ENUMPROCESS, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-109">COR_PUB_ENUMPROCESS Enumeration</span></span>](cor-pub-enumprocess-enumeration.md)  
 <span data-ttu-id="97a9c-110">Identyfikuje typ procesu do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="97a9c-110">Identifies the type of process to be enumerated.</span></span>  
  
 [<span data-ttu-id="97a9c-111">CorDebugBlockingReason, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-111">CorDebugBlockingReason Enumeration</span></span>](cordebugblockingreason-enumeration.md)  
 <span data-ttu-id="97a9c-112">Określa przyczyny, dla których wątek może zostać zablokowany dla danego obiektu.</span><span class="sxs-lookup"><span data-stu-id="97a9c-112">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
 <span data-ttu-id="97a9c-113">CorDebugChainReason</span><span class="sxs-lookup"><span data-stu-id="97a9c-113">CorDebugChainReason</span></span>  
 <span data-ttu-id="97a9c-114">Wskazuje przyczynę lub przyczyny inicjacji łańcucha wywołań.</span><span class="sxs-lookup"><span data-stu-id="97a9c-114">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
 [<span data-ttu-id="97a9c-115">CorDebugCodeInvokeKind, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-115">CorDebugCodeInvokeKind Enumeration</span></span>](cordebugcodeinvokekind-enumeration.md)  
 <span data-ttu-id="97a9c-116">Opisuje sposób, w jaki wyeksportowana funkcja wywołuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="97a9c-116">Describes how an exported function invokes managed code.</span></span>  
  
 [<span data-ttu-id="97a9c-117">CorDebugCodeInvokePurpose, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-117">CorDebugCodeInvokePurpose Enumeration</span></span>](cordebugcodeinvokepurpose-enumeration.md)  
 <span data-ttu-id="97a9c-118">Opisuje, dlaczego wyeksportowana funkcja wywołuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="97a9c-118">Describes why an exported function calls managed code.</span></span>  
  
 <span data-ttu-id="97a9c-119">CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="97a9c-119">CorDebugCreateProcessFlags</span></span>  
 <span data-ttu-id="97a9c-120">Zapewnia dodatkowe opcje debugowania, których można użyć w wywołaniu metody [ICorDebug:: CreateProcess](icordebug-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="97a9c-120">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](icordebug-createprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="97a9c-121">CorDebugDebugEventKind, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-121">CorDebugDebugEventKind Enumeration</span></span>](cordebugdebugeventkind-enumeration.md)  
 <span data-ttu-id="97a9c-122">Wskazuje typ zdarzenia, którego informacje są dekodowane przez metodę [DecodeEvent](icordebugprocess6-decodeevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="97a9c-122">Indicates the type of event whose information is decoded by the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
 [<span data-ttu-id="97a9c-123">CorDebugDecodeEventFlagsWindows, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-123">CorDebugDecodeEventFlagsWindows Enumeration</span></span>](cordebugdecodeeventflagswindows-enumeration.md)  
 <span data-ttu-id="97a9c-124">Zawiera dodatkowe informacje na temat zdarzeń debugowania na platformie Windows.</span><span class="sxs-lookup"><span data-stu-id="97a9c-124">Provides additional information about debug events on the Windows platform.</span></span>  
  
 <span data-ttu-id="97a9c-125">CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="97a9c-125">CorDebugExceptionCallbackType</span></span>  
 <span data-ttu-id="97a9c-126">Wskazuje typ wywołania zwrotnego, które jest wykonywane z [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md) zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="97a9c-126">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
 [<span data-ttu-id="97a9c-127">CorDebugExceptionFlags, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-127">CorDebugExceptionFlags Enumeration</span></span>](cordebugexceptionflags-enumeration.md)  
 <span data-ttu-id="97a9c-128">Zawiera dodatkowe informacje o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="97a9c-128">Provides additional information about an exception.</span></span>  
  
 <span data-ttu-id="97a9c-129">CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="97a9c-129">CorDebugExceptionUnwindCallbackType</span></span>  
 <span data-ttu-id="97a9c-130">Wskazuje zdarzenie, które jest sygnalizowane przez wywołanie zwrotne w fazie unwind.</span><span class="sxs-lookup"><span data-stu-id="97a9c-130">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 [<span data-ttu-id="97a9c-131">CorDebugGCType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-131">CorDebugGCType Enumeration</span></span>](cordebuggctype-enumeration.md)  
 <span data-ttu-id="97a9c-132">Wskazuje, czy moduł wyrzucania elementów bezużytecznych jest uruchomiony na stacji roboczej lub na serwerze.</span><span class="sxs-lookup"><span data-stu-id="97a9c-132">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
 [<span data-ttu-id="97a9c-133">CorDebugGenerationTypes, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-133">CorDebugGenerationTypes Enumeration</span></span>](cordebuggenerationtypes-enumeration.md)  
 <span data-ttu-id="97a9c-134">Określa generowanie regionu pamięci na zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="97a9c-134">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
 <span data-ttu-id="97a9c-135">CorDebugHandleType</span><span class="sxs-lookup"><span data-stu-id="97a9c-135">CorDebugHandleType</span></span>  
 <span data-ttu-id="97a9c-136">Wskazuje typ dojścia.</span><span class="sxs-lookup"><span data-stu-id="97a9c-136">Indicates the handle type.</span></span>  
  
 [<span data-ttu-id="97a9c-137">CorDebugIlToNativeMappingTypes, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-137">CorDebugIlToNativeMappingTypes Enumeration</span></span>](cordebugiltonativemappingtypes-enumeration.md)  
 <span data-ttu-id="97a9c-138">Wskazuje, czy konkretny zakres instrukcji macierzystych odpowiada specjalnemu regionowi kodu.</span><span class="sxs-lookup"><span data-stu-id="97a9c-138">Indicates whether a particular range of native instructions corresponds to a special code region.</span></span>  
  
 <span data-ttu-id="97a9c-139">CorDebugIntercept</span><span class="sxs-lookup"><span data-stu-id="97a9c-139">CorDebugIntercept</span></span>  
 <span data-ttu-id="97a9c-140">Wskazuje typy kodu, do którego można wykonać te działania.</span><span class="sxs-lookup"><span data-stu-id="97a9c-140">Indicates the types of code that can be stepped into.</span></span>  
  
 [<span data-ttu-id="97a9c-141">CorDebugInterfaceVersion, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-141">CorDebugInterfaceVersion Enumeration</span></span>](cordebuginterfaceversion-enumeration.md)  
 <span data-ttu-id="97a9c-142">Określa wersję .NET Framework lub wersję .NET Framework, w której został wprowadzony interfejs.</span><span class="sxs-lookup"><span data-stu-id="97a9c-142">Specifies either a version of the .NET Framework, or the version of the .NET Framework in which an interface was introduced.</span></span>  
  
 <span data-ttu-id="97a9c-143">CorDebugInternalFrameType</span><span class="sxs-lookup"><span data-stu-id="97a9c-143">CorDebugInternalFrameType</span></span>  
 <span data-ttu-id="97a9c-144">Identyfikuje typ ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="97a9c-144">Identifies the type of stack frame.</span></span>  
  
 [<span data-ttu-id="97a9c-145">CorDebugJITCompilerFlags, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-145">CorDebugJITCompilerFlags Enumeration</span></span>](cordebugjitcompilerflags-enumeration.md)  
 <span data-ttu-id="97a9c-146">Zawiera wartości wpływające na zachowanie kompilatora zarządzanego (just-in-Time).</span><span class="sxs-lookup"><span data-stu-id="97a9c-146">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
 [<span data-ttu-id="97a9c-147">CorDebugJITCompilerFlagsDeprecated, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-147">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>](cordebugjitcompilerflagsdeprecated-enumeration.md)  
 <span data-ttu-id="97a9c-148">{1&gt;Nieaktualne.&lt;1}</span><span class="sxs-lookup"><span data-stu-id="97a9c-148">Obsolete.</span></span> <span data-ttu-id="97a9c-149">Zamiast tego użyj `CORDEBUG_JIT_DEFAULT` elementu członkowskiego wyliczenia [CorDebugJITCompilerFlags —](cordebugjitcompilerflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="97a9c-149">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
 <span data-ttu-id="97a9c-150">CorDebugMappingResult</span><span class="sxs-lookup"><span data-stu-id="97a9c-150">CorDebugMappingResult</span></span>  
 <span data-ttu-id="97a9c-151">Zawiera szczegółowe informacje o sposobie uzyskiwania wartości wskaźnika instrukcji (IP).</span><span class="sxs-lookup"><span data-stu-id="97a9c-151">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
 [<span data-ttu-id="97a9c-152">CorDebugMDAFlags, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-152">CorDebugMDAFlags Enumeration</span></span>](cordebugmdaflags-enumeration.md)  
 <span data-ttu-id="97a9c-153">Określa stan wątku, w którym jest uruchamiany Asystent debugowania zarządzanego (MDA).</span><span class="sxs-lookup"><span data-stu-id="97a9c-153">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
 [<span data-ttu-id="97a9c-154">CorDebugNGenPolicy, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-154">CorDebugNGenPolicy Enumeration</span></span>](cordebugngenpolicy-enumeration.md)  
 <span data-ttu-id="97a9c-155">Zapewnia wartość określającą, czy debuger ładuje obrazy natywne (NGen) z pamięci podręcznej obrazów natywnych.</span><span class="sxs-lookup"><span data-stu-id="97a9c-155">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
 [<span data-ttu-id="97a9c-156">CorDebugPlatform, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-156">CorDebugPlatform Enumeration</span></span>](cordebugplatform-enumeration.md)  
 <span data-ttu-id="97a9c-157">Zapewnia wartości platformy docelowej, które są używane przez metodę [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) .</span><span class="sxs-lookup"><span data-stu-id="97a9c-157">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
 [<span data-ttu-id="97a9c-158">CorDebugRecordFormat, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-158">CorDebugRecordFormat Enumeration</span></span>](cordebugrecordformat-enumeration.md)  
 <span data-ttu-id="97a9c-159">Opisuje format danych w tablicy bajtów, który zawiera informacje na temat natywnego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="97a9c-159">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
 <span data-ttu-id="97a9c-160">CorDebugRegister</span><span class="sxs-lookup"><span data-stu-id="97a9c-160">CorDebugRegister</span></span>  
 <span data-ttu-id="97a9c-161">Określa rejestry skojarzone z daną architekturą procesora.</span><span class="sxs-lookup"><span data-stu-id="97a9c-161">Specifies the registers associated with a given processor architecture.</span></span>  
  
 [<span data-ttu-id="97a9c-162">CorDebugSetContextFlag, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-162">CorDebugSetContextFlag Enumeration</span></span>](cordebugsetcontextflag-enumeration.md)  
 <span data-ttu-id="97a9c-163">Wskazuje, czy kontekst pochodzi z aktywnej ramki (lub liściowej) na stosie czy został obliczony przez odróżnienie od innej ramki.</span><span class="sxs-lookup"><span data-stu-id="97a9c-163">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
 [<span data-ttu-id="97a9c-164">CorDebugStateChange, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-164">CorDebugStateChange Enumeration</span></span>](cordebugstatechange-enumeration.md)  
 <span data-ttu-id="97a9c-165">Opisuje ilość danych buforowanych, które muszą zostać odrzucone na podstawie zmian w procesie.</span><span class="sxs-lookup"><span data-stu-id="97a9c-165">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
 <span data-ttu-id="97a9c-166">CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="97a9c-166">CorDebugStepReason</span></span>  
 <span data-ttu-id="97a9c-167">Wskazuje wynik pojedynczego kroku.</span><span class="sxs-lookup"><span data-stu-id="97a9c-167">Indicates the outcome of an individual step.</span></span>  
  
 <span data-ttu-id="97a9c-168">CorDebugThreadState</span><span class="sxs-lookup"><span data-stu-id="97a9c-168">CorDebugThreadState</span></span>  
 <span data-ttu-id="97a9c-169">Określa stan wątku do debugowania.</span><span class="sxs-lookup"><span data-stu-id="97a9c-169">Specifies the state of a thread for debugging.</span></span>  
  
 <span data-ttu-id="97a9c-170">\>CorDebugUnmappedStop</span><span class="sxs-lookup"><span data-stu-id="97a9c-170">\>CorDebugUnmappedStop</span></span>  
 <span data-ttu-id="97a9c-171">Określa typ niezamapowanego kodu, który może wyzwolić zatrzymanie w wykonaniu kodu przez stepper.</span><span class="sxs-lookup"><span data-stu-id="97a9c-171">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
 <span data-ttu-id="97a9c-172">CorDebugUserState</span><span class="sxs-lookup"><span data-stu-id="97a9c-172">CorDebugUserState</span></span>  
 <span data-ttu-id="97a9c-173">Wskazuje stan użytkownika wątku.</span><span class="sxs-lookup"><span data-stu-id="97a9c-173">Indicates the user state of a thread.</span></span>  
  
 [<span data-ttu-id="97a9c-174">CorGCReferenceType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-174">CorGCReferenceType Enumeration</span></span>](corgcreferencetype-enumeration.md)  
 <span data-ttu-id="97a9c-175">Określa źródło obiektu, które ma zostać pobrane jako elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="97a9c-175">Identifies the source of an object to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="97a9c-176">ILCodeKind, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-176">ILCodeKind Enumeration</span></span>](ilcodekind-enumeration.md)  
 <span data-ttu-id="97a9c-177">Zawiera wartości, które określają, czy debuger może uzyskać dostęp do zmiennych lokalnych lub kodu dodanego w instrumentacji profilera ReJIT.</span><span class="sxs-lookup"><span data-stu-id="97a9c-177">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="97a9c-178">LoggingLevelEnum, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-178">LoggingLevelEnum Enumeration</span></span>](logginglevelenum-enumeration.md)  
 <span data-ttu-id="97a9c-179">Wskazuje poziom ważności komunikatu opisowego, który jest zapisywana w dzienniku zdarzeń, gdy zarządzany wątek rejestruje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="97a9c-179">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
 [<span data-ttu-id="97a9c-180">LogSwitchCallReason, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-180">LogSwitchCallReason Enumeration</span></span>](logswitchcallreason-enumeration.md)  
 <span data-ttu-id="97a9c-181">Wskazuje operację wykonywaną na przełączniku debugowania/śledzenia.</span><span class="sxs-lookup"><span data-stu-id="97a9c-181">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
 [<span data-ttu-id="97a9c-182">VariableLocationType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-182">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)  
 <span data-ttu-id="97a9c-183">Wskazuje typ lokalizacji natywnej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="97a9c-183">Indicates the native location type of a variable.</span></span>  
  
 [<span data-ttu-id="97a9c-184">WriteableMetadataUpdateMode, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97a9c-184">WriteableMetadataUpdateMode Enumeration</span></span>](writeablemetadataupdatemode-enumeration.md)  
 <span data-ttu-id="97a9c-185">Zawiera wartości, które określają, czy aktualizacje w pamięci mają być widoczne dla debugera.</span><span class="sxs-lookup"><span data-stu-id="97a9c-185">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span> 

 <span data-ttu-id="97a9c-186">[ClrDataSourceType, Wyliczenie](clrdatasourcetype-enumeration.md) Dostarcza wartości, które są używane przez strukturę CLRDATA_IL_ADDRESS_MAP.</span><span class="sxs-lookup"><span data-stu-id="97a9c-186">[ClrDataSourceType Enumeration](clrdatasourcetype-enumeration.md) Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="97a9c-187">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="97a9c-187">Related Sections</span></span>  
 [<span data-ttu-id="97a9c-188">Klasy coclass debugowania</span><span class="sxs-lookup"><span data-stu-id="97a9c-188">Debugging Coclasses</span></span>](debugging-coclasses.md)  
  
 [<span data-ttu-id="97a9c-189">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="97a9c-189">Debugging Interfaces</span></span>](debugging-interfaces.md)  
  
 [<span data-ttu-id="97a9c-190">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="97a9c-190">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)  
  
 [<span data-ttu-id="97a9c-191">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="97a9c-191">Debugging Structures</span></span>](debugging-structures.md)
