---
title: Środki zaradcze Nowy 64-bitowy kompilator JIT
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07f9ae01fae5e4badbc13670ee56a2f05e303c0c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779353"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a><span data-ttu-id="0802f-102">Środki zaradcze Nowy 64-bitowy kompilator JIT</span><span class="sxs-lookup"><span data-stu-id="0802f-102">Mitigation: New 64-bit JIT Compiler</span></span>
<span data-ttu-id="0802f-103">Począwszy od .NET Framework 4,6, środowisko uruchomieniowe zawiera nowy, 64-bitowy kompilator JIT dla kompilacji just in Time.</span><span class="sxs-lookup"><span data-stu-id="0802f-103">Starting with the .NET Framework 4.6, the runtime includes a new 64-bit JIT compiler for just-in-time compilation.</span></span> <span data-ttu-id="0802f-104">Ta zmiana nie ma wpływu na kompilację z 32-bitowym kompilatorem JIT.</span><span class="sxs-lookup"><span data-stu-id="0802f-104">This change does not affect compilation with the  32-bit JIT compiler.</span></span>  
  
## <a name="unexpected-behavior-or-exceptions"></a><span data-ttu-id="0802f-105">Nieoczekiwane zachowanie lub wyjątki</span><span class="sxs-lookup"><span data-stu-id="0802f-105">Unexpected behavior or exceptions</span></span>  
 <span data-ttu-id="0802f-106">W niektórych przypadkach kompilacja z nowym 64-bitowym kompilatorem JIT powoduje wyjątek czasu wykonywania lub zachowanie, które nie jest zaobserwowane podczas wykonywania kodu skompilowanego przez starszy, 64-bitowy kompilator JIT.</span><span class="sxs-lookup"><span data-stu-id="0802f-106">In some cases, compilation with the new 64-bit JIT compiler results in a runtime exception or in behavior that is not observed when executing code compiled by the older 64-bit JIT compiler.</span></span> <span data-ttu-id="0802f-107">Znane różnice obejmują następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="0802f-107">The known differences include the following:</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0802f-108">Wszystkie znane problemy zostały rozwiązane w nowym kompilatorze 64-bitowym, który został wystawiony .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="0802f-108">All of these known issues have been addressed in the new 64-bit compiler released with the .NET Framework 4.6.2.</span></span> <span data-ttu-id="0802f-109">Większość została również omówiona w wersjach usługi .NET Framework 4,6 i 4.6.1, które są dołączone do Windows Update.</span><span class="sxs-lookup"><span data-stu-id="0802f-109">Most have also been addressed in service releases of the .NET Framework 4.6 and 4.6.1 that are included with Windows Update.</span></span> <span data-ttu-id="0802f-110">Te problemy można wyeliminować, upewniając się, że wersja systemu Windows jest aktualna, lub przez uaktualnienie do .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="0802f-110">You can eliminate these issues by ensuring that your version of Windows is up to date, or by upgrading to the .NET Framework 4.6.2.</span></span>  
  
- <span data-ttu-id="0802f-111">W pewnych warunkach operacja rozpakowywania może zgłosić <xref:System.NullReferenceException> kompilacje wydania z włączoną optymalizacją.</span><span class="sxs-lookup"><span data-stu-id="0802f-111">Under certain conditions, an unboxing operation may throw a <xref:System.NullReferenceException> in Release builds with optimization turned on.</span></span>  
  
- <span data-ttu-id="0802f-112">W niektórych przypadkach wykonanie kodu produkcyjnego w dużej treści metody może spowodować wygenerowanie <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="0802f-112">In some cases, execution of production code in a large method body may throw a <xref:System.StackOverflowException>.</span></span>  
  
- <span data-ttu-id="0802f-113">W pewnych warunkach struktury przesłane do metody są traktowane jako typy referencyjne, a nie typy wartości w kompilacjach wydań.</span><span class="sxs-lookup"><span data-stu-id="0802f-113">Under certain conditions, structures passed to a method are treated as reference types rather than value types in Release builds.</span></span> <span data-ttu-id="0802f-114">Jednym z manifestów tego problemu jest to, że poszczególne elementy w kolekcji pojawiają się w nieoczekiwanej kolejności.</span><span class="sxs-lookup"><span data-stu-id="0802f-114">One of the manifestations of this issue is that the individual items in a collection appear in an unexpected order.</span></span>  
  
- <span data-ttu-id="0802f-115">W pewnych warunkach porównanie <xref:System.UInt16> wartości z ich dużym zestawem bitowym jest nieprawidłowe, jeśli Optymalizacja jest włączona.</span><span class="sxs-lookup"><span data-stu-id="0802f-115">Under certain conditions, the comparison of <xref:System.UInt16> values with their high bit set is incorrect if optimization is enabled.</span></span>  
  
- <span data-ttu-id="0802f-116">W określonych warunkach, szczególnie podczas inicjowania wartości tablicowych, Inicjalizacja pamięci <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> przez instrukcję Il może inicjować pamięć z nieprawidłową wartością.</span><span class="sxs-lookup"><span data-stu-id="0802f-116">Under certain conditions, particularly when initializing array values, memory initialization by the <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL instruction may initialize memory with an incorrect value.</span></span> <span data-ttu-id="0802f-117">Może to spowodować nieobsługiwany wyjątek lub nieprawidłowe dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="0802f-117">This can result either in an unhandled exception or incorrect output.</span></span>  
  
- <span data-ttu-id="0802f-118">W niektórych rzadkich warunkach alternatywny test bitowy może zwrócić niepoprawną <xref:System.Boolean> wartość lub zgłosić wyjątek, jeśli Optymalizacja kompilatora jest włączona.</span><span class="sxs-lookup"><span data-stu-id="0802f-118">Under certain rare conditions, a conditional bit test can return the incorrect <xref:System.Boolean> value or throw an exception if compiler optimizations are enabled.</span></span>  
  
- <span data-ttu-id="0802f-119">W pewnych warunkach, jeśli `if` instrukcja jest używana do testowania warunku przed `try` wprowadzeniem bloku i wyjścia z `try` bloku, `catch` a ten sam warunek jest obliczany w bloku lub `finally` , nowy 64-bitowy kompilator JIT usuwa `if` warunek `catch` z bloku lub `finally` , gdy optymalizuje kod.</span><span class="sxs-lookup"><span data-stu-id="0802f-119">Under certain conditions, if an `if` statement is used to test for a condition before entering  a `try` block and in the exit from the `try` block, and the same condition is evaluated in the `catch` or `finally` block, the new 64-bit JIT compiler removes the `if` condition from the `catch` or `finally` block when it optimizes code.</span></span> <span data-ttu-id="0802f-120">W związku z tym kod wewnątrz `if` instrukcji `catch` w bloku lub `finally` jest wykonywany bezwarunkowo.</span><span class="sxs-lookup"><span data-stu-id="0802f-120">As a result, code inside the `if` statement in the `catch` or `finally` block is executed unconditionally.</span></span>  
  
<a name="General"></a>   
## <a name="mitigation-of-known-issues"></a><span data-ttu-id="0802f-121">Eliminowanie znanych problemów</span><span class="sxs-lookup"><span data-stu-id="0802f-121">Mitigation of known issues</span></span>  
 <span data-ttu-id="0802f-122">Jeśli napotkasz wymienione powyżej problemy, możesz je rozwiązać, wykonując jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="0802f-122">If you encounter the issues listed above, you can address them by doing any of the following:</span></span>  
  
- <span data-ttu-id="0802f-123">Uaktualnij do .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="0802f-123">Upgrade to the .NET Framework 4.6.2.</span></span> <span data-ttu-id="0802f-124">Nowy kompilator 64-bitowy dołączony do .NET Framework 4.6.2 odnosi się do każdego z tych znanych problemów.</span><span class="sxs-lookup"><span data-stu-id="0802f-124">The new 64-bit compiler included with the .NET Framework 4.6.2 addresses each of these known issues.</span></span>  
  
- <span data-ttu-id="0802f-125">Upewnij się, że wersja systemu Windows jest aktualna, uruchamiając Windows Update.</span><span class="sxs-lookup"><span data-stu-id="0802f-125">Ensure that your version of Windows is up to date by running Windows Update.</span></span> <span data-ttu-id="0802f-126">Aktualizacje usługi dla .NET Framework 4,6 i 4.6.1 odnoszą się do każdego z tych problemów <xref:System.NullReferenceException> , z wyjątkiem w przypadku operacji rozpakowywania.</span><span class="sxs-lookup"><span data-stu-id="0802f-126">Service updates to the .NET Framework 4.6 and 4.6.1 address each of these issues except the <xref:System.NullReferenceException> in an unboxing operation.</span></span>  
  
- <span data-ttu-id="0802f-127">Kompiluj ze starszym 64-bitowym kompilatorem JIT.</span><span class="sxs-lookup"><span data-stu-id="0802f-127">Compile with the older 64-bit JIT compiler.</span></span> <span data-ttu-id="0802f-128">Więcej informacji o tym, jak to zrobić, znajduje się w sekcji [eliminowanie innych problemów](#Other) .</span><span class="sxs-lookup"><span data-stu-id="0802f-128">See the [Mitigation of other issues](#Other) section for more information on how to do this.</span></span>  
  
<a name="Other"></a>   
## <a name="mitigation-of-other-issues"></a><span data-ttu-id="0802f-129">Eliminowanie innych problemów</span><span class="sxs-lookup"><span data-stu-id="0802f-129">Mitigation of other issues</span></span>  
 <span data-ttu-id="0802f-130">Jeśli wystąpią inne różnice w zachowaniu kodu skompilowanego ze starszym kompilatorem 64-bitowym i nowym 64-bitowym kompilatorem JIT lub między wersjami Debug i Release aplikacji, które są kompilowane przy użyciu nowego, 64-bitowego kompilatora JIT, można wykonać następujące czynności Aby skompilować aplikację ze starszym 64-bitowym kompilatorem JIT:</span><span class="sxs-lookup"><span data-stu-id="0802f-130">If you encounter any other difference in behavior between code compiled with the older 64-bit compiler and the new 64-bit JIT compiler, or between the debug and release versions of your app that are both compiled with the new 64-bit JIT compiler, you can do the following to compile your app with the older 64-bit JIT compiler:</span></span>  
  
- <span data-ttu-id="0802f-131">Dla poszczególnych aplikacji można dodać [ \<element useLegacyJit >](../configure-apps/file-schema/runtime/uselegacyjit-element.md) do pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0802f-131">On a per-application basis, you can add the [\<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) element to your application's configuration file.</span></span> <span data-ttu-id="0802f-132">Następujące wyłączenie kompilacji z nowym 64-bitowym kompilatorem JIT, a zamiast tego używa starszego, 64-bitowego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="0802f-132">The following disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- <span data-ttu-id="0802f-133">Dla poszczególnych użytkowników można dodać `REG_DWORD` wartość o nazwie `useLegacyJit` do `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="0802f-133">On a per-user basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="0802f-134">Wartość 1 powoduje włączenie starszego 64-bitowego kompilatora JIT; wartość 0 powoduje wyłączenie i włączenie nowego kompilatora 64-bitowego JIT.</span><span class="sxs-lookup"><span data-stu-id="0802f-134">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
- <span data-ttu-id="0802f-135">Dla poszczególnych maszyn można dodać `REG_DWORD` wartość o nazwie `useLegacyJit` do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="0802f-135">On a per-machine basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="0802f-136">Wartość 1 powoduje włączenie starszego 64-bitowego kompilatora JIT; wartość 0 powoduje wyłączenie i włączenie nowego kompilatora 64-bitowego JIT.</span><span class="sxs-lookup"><span data-stu-id="0802f-136">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
 <span data-ttu-id="0802f-137">Możesz również poinformować nas o problemie, zgłaszając usterkę w witrynie [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span><span class="sxs-lookup"><span data-stu-id="0802f-137">You can also let us know about the problem by reporting a bug on [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0802f-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0802f-138">See also</span></span>

- [<span data-ttu-id="0802f-139">Zmiany środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="0802f-139">Runtime Changes</span></span>](runtime-changes-in-the-net-framework-4-6.md)
- [<span data-ttu-id="0802f-140">\<useLegacyJit> Element</span><span class="sxs-lookup"><span data-stu-id="0802f-140">\<useLegacyJit> Element</span></span>](../configure-apps/file-schema/runtime/uselegacyjit-element.md)
