---
title: 'Łagodzenie: Nowy 64-bitowy kompilator JIT'
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
ms.openlocfilehash: 883aaf032bde632b08f965d3450cfbea4feb8e65
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181258"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a><span data-ttu-id="459bd-102">Łagodzenie: Nowy 64-bitowy kompilator JIT</span><span class="sxs-lookup"><span data-stu-id="459bd-102">Mitigation: New 64-bit JIT Compiler</span></span>
<span data-ttu-id="459bd-103">Począwszy od .NET Framework 4.6, środowisko wykonawcze zawiera nowy kompilator JIT 64-bitowy dla kompilacji just-in-time.</span><span class="sxs-lookup"><span data-stu-id="459bd-103">Starting with the .NET Framework 4.6, the runtime includes a new 64-bit JIT compiler for just-in-time compilation.</span></span> <span data-ttu-id="459bd-104">Ta zmiana nie wpływa na kompilację za pomocą 32-bitowego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="459bd-104">This change does not affect compilation with the  32-bit JIT compiler.</span></span>  
  
## <a name="unexpected-behavior-or-exceptions"></a><span data-ttu-id="459bd-105">Nieoczekiwane zachowanie lub wyjątki</span><span class="sxs-lookup"><span data-stu-id="459bd-105">Unexpected behavior or exceptions</span></span>  
 <span data-ttu-id="459bd-106">W niektórych przypadkach kompilacja z nowym kompilatorem JIT 64-bitowego powoduje wyjątek środowiska uruchomieniowego lub zachowanie, które nie jest obserwowane podczas wykonywania kodu skompilowanego przez starszy kompilator JIT 64-bitowego.</span><span class="sxs-lookup"><span data-stu-id="459bd-106">In some cases, compilation with the new 64-bit JIT compiler results in a runtime exception or in behavior that is not observed when executing code compiled by the older 64-bit JIT compiler.</span></span> <span data-ttu-id="459bd-107">Znane różnice są następujące:</span><span class="sxs-lookup"><span data-stu-id="459bd-107">The known differences include the following:</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="459bd-108">Wszystkie te znane problemy zostały rozwiązane w nowym kompilatorze 64-bitowym wydanym za pomocą programu .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="459bd-108">All of these known issues have been addressed in the new 64-bit compiler released with the .NET Framework 4.6.2.</span></span> <span data-ttu-id="459bd-109">Większość z nich została również omówiona w wersjach usług .NET Framework 4.6 i 4.6.1, które są dołączone do witryny Windows Update.</span><span class="sxs-lookup"><span data-stu-id="459bd-109">Most have also been addressed in service releases of the .NET Framework 4.6 and 4.6.1 that are included with Windows Update.</span></span> <span data-ttu-id="459bd-110">Można wyeliminować te problemy, upewniając się, że wersja systemu Windows jest aktualna lub uaktualniając ją do programu .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="459bd-110">You can eliminate these issues by ensuring that your version of Windows is up to date, or by upgrading to the .NET Framework 4.6.2.</span></span>  
  
- <span data-ttu-id="459bd-111">Pod pewnymi warunkami operacja rozpakowywania może zgłosić <xref:System.NullReferenceException> w wersji kompilacji z optymalizacji włączone.</span><span class="sxs-lookup"><span data-stu-id="459bd-111">Under certain conditions, an unboxing operation may throw a <xref:System.NullReferenceException> in Release builds with optimization turned on.</span></span>  
  
- <span data-ttu-id="459bd-112">W niektórych przypadkach wykonanie kodu produkcyjnego w <xref:System.StackOverflowException>treści dużej metody może spowodować rzut .</span><span class="sxs-lookup"><span data-stu-id="459bd-112">In some cases, execution of production code in a large method body may throw a <xref:System.StackOverflowException>.</span></span>  
  
- <span data-ttu-id="459bd-113">Pod pewnymi warunkami struktury przekazywane do metody są traktowane jako typy odwołań, a nie typy wartości w kompilacjach release.</span><span class="sxs-lookup"><span data-stu-id="459bd-113">Under certain conditions, structures passed to a method are treated as reference types rather than value types in Release builds.</span></span> <span data-ttu-id="459bd-114">Jednym z przejawów tego problemu jest to, że poszczególne elementy w kolekcji pojawiają się w nieoczekiwanej kolejności.</span><span class="sxs-lookup"><span data-stu-id="459bd-114">One of the manifestations of this issue is that the individual items in a collection appear in an unexpected order.</span></span>  
  
- <span data-ttu-id="459bd-115">W pewnych warunkach <xref:System.UInt16> porównanie wartości z ich zestawem bitów jest niepoprawne, jeśli optymalizacja jest włączona.</span><span class="sxs-lookup"><span data-stu-id="459bd-115">Under certain conditions, the comparison of <xref:System.UInt16> values with their high bit set is incorrect if optimization is enabled.</span></span>  
  
- <span data-ttu-id="459bd-116">W pewnych warunkach, szczególnie podczas inicjowania <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> wartości tablicy, inicjowanie pamięci przez instrukcję IL może zainicjować pamięć z niepoprawną wartością.</span><span class="sxs-lookup"><span data-stu-id="459bd-116">Under certain conditions, particularly when initializing array values, memory initialization by the <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL instruction may initialize memory with an incorrect value.</span></span> <span data-ttu-id="459bd-117">Może to spowodować nieobsługiwał wyjątek lub niepoprawne dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="459bd-117">This can result either in an unhandled exception or incorrect output.</span></span>  
  
- <span data-ttu-id="459bd-118">W pewnych rzadkich warunkach test bitowy <xref:System.Boolean> warunkowy może zwrócić niepoprawną wartość lub zgłosić wyjątek, jeśli włączone są optymalizacje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="459bd-118">Under certain rare conditions, a conditional bit test can return the incorrect <xref:System.Boolean> value or throw an exception if compiler optimizations are enabled.</span></span>  
  
- <span data-ttu-id="459bd-119">Pod `if` pewnymi warunkami, jeśli instrukcja jest używana do `try` testowania warunku `try` przed wprowadzeniem bloku i `catch` w `finally` wyjściu z bloku, a ten sam warunek `if` jest `catch` oceniany w lub bloku, nowy kompilator JIT 64-bitowy usuwa warunek z lub `finally` bloku, gdy optymalizuje kod.</span><span class="sxs-lookup"><span data-stu-id="459bd-119">Under certain conditions, if an `if` statement is used to test for a condition before entering  a `try` block and in the exit from the `try` block, and the same condition is evaluated in the `catch` or `finally` block, the new 64-bit JIT compiler removes the `if` condition from the `catch` or `finally` block when it optimizes code.</span></span> <span data-ttu-id="459bd-120">W rezultacie kod wewnątrz `if` instrukcji `catch` w `finally` lub bloku jest wykonywany bezwarunkowo.</span><span class="sxs-lookup"><span data-stu-id="459bd-120">As a result, code inside the `if` statement in the `catch` or `finally` block is executed unconditionally.</span></span>  
  
<a name="General"></a>
## <a name="mitigation-of-known-issues"></a><span data-ttu-id="459bd-121">Łagodzenie znanych problemów</span><span class="sxs-lookup"><span data-stu-id="459bd-121">Mitigation of known issues</span></span>  
 <span data-ttu-id="459bd-122">Jeśli napotkasz problemy wymienione powyżej, możesz je rozwiązać, wykonując dowolną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="459bd-122">If you encounter the issues listed above, you can address them by doing any of the following:</span></span>  
  
- <span data-ttu-id="459bd-123">Uaktualnienie do programu .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="459bd-123">Upgrade to the .NET Framework 4.6.2.</span></span> <span data-ttu-id="459bd-124">Nowy kompilator 64-bitowy dołączony do programu .NET Framework 4.6.2 rozwiązuje każdy z tych znanych problemów.</span><span class="sxs-lookup"><span data-stu-id="459bd-124">The new 64-bit compiler included with the .NET Framework 4.6.2 addresses each of these known issues.</span></span>  
  
- <span data-ttu-id="459bd-125">Upewnij się, że twoja wersja systemu Windows jest aktualna, uruchamiając usługę Windows Update.</span><span class="sxs-lookup"><span data-stu-id="459bd-125">Ensure that your version of Windows is up to date by running Windows Update.</span></span> <span data-ttu-id="459bd-126">Aktualizacje usługi do .NET Framework 4.6 i 4.6.1 <xref:System.NullReferenceException> rozwiązać każdy z tych problemów, z wyjątkiem w operacji rozpakowywania.</span><span class="sxs-lookup"><span data-stu-id="459bd-126">Service updates to the .NET Framework 4.6 and 4.6.1 address each of these issues except the <xref:System.NullReferenceException> in an unboxing operation.</span></span>  
  
- <span data-ttu-id="459bd-127">Skompiluj ze starszym 64-bitowym kompilatorem JIT.</span><span class="sxs-lookup"><span data-stu-id="459bd-127">Compile with the older 64-bit JIT compiler.</span></span> <span data-ttu-id="459bd-128">Zobacz [łagodzenia innych problemów](#Other) sekcji, aby uzyskać więcej informacji na temat sposobu wykonania tej sprawy.</span><span class="sxs-lookup"><span data-stu-id="459bd-128">See the [Mitigation of other issues](#Other) section for more information on how to do this.</span></span>  
  
<a name="Other"></a>
## <a name="mitigation-of-other-issues"></a><span data-ttu-id="459bd-129">Łagodzenie innych problemów</span><span class="sxs-lookup"><span data-stu-id="459bd-129">Mitigation of other issues</span></span>  
 <span data-ttu-id="459bd-130">Jeśli wystąpi jakakolwiek inna różnica w zachowaniu między kodem skompilowanym ze starszym kompilatorem 64-bitowym a nowym 64-bitowym kompilatorem JIT lub między wersjami debugowania i wersji aplikacji, które są skompilowane z nowym 64-bitowym kompilatorem JIT, możesz wykonać następujące czynności: , aby skompilować aplikację ze starszym 64-bitowym kompilatorem JIT:</span><span class="sxs-lookup"><span data-stu-id="459bd-130">If you encounter any other difference in behavior between code compiled with the older 64-bit compiler and the new 64-bit JIT compiler, or between the debug and release versions of your app that are both compiled with the new 64-bit JIT compiler, you can do the following to compile your app with the older 64-bit JIT compiler:</span></span>  
  
- <span data-ttu-id="459bd-131">Na podstawie dla aplikacji można dodać [ \<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) element do pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="459bd-131">On a per-application basis, you can add the [\<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) element to your application's configuration file.</span></span> <span data-ttu-id="459bd-132">Następujące wyłącza kompilacji z nowym kompilatorem JIT 64-bit i zamiast tego używa starszego kompilatora JIT 64-bit.</span><span class="sxs-lookup"><span data-stu-id="459bd-132">The following disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- <span data-ttu-id="459bd-133">Na podstawie dla użytkownika można dodać `REG_DWORD` wartość `useLegacyJit` o `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` nazwie do klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="459bd-133">On a per-user basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="459bd-134">Wartość 1 umożliwia starszy kompilator JIT 64-bitowy; wartość 0 wyłącza go i włącza nowy kompilator JIT 64-bitowy.</span><span class="sxs-lookup"><span data-stu-id="459bd-134">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
- <span data-ttu-id="459bd-135">Na podstawie na komputerze można dodać `REG_DWORD` wartość `useLegacyJit` o `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` nazwie do klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="459bd-135">On a per-machine basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="459bd-136">Wartość 1 umożliwia starszy kompilator JIT 64-bitowy; wartość 0 wyłącza go i włącza nowy kompilator JIT 64-bitowy.</span><span class="sxs-lookup"><span data-stu-id="459bd-136">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
 <span data-ttu-id="459bd-137">Możesz również poinformować nas o problemie, zgłaszając błąd w [usłudze Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span><span class="sxs-lookup"><span data-stu-id="459bd-137">You can also let us know about the problem by reporting a bug on [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="459bd-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="459bd-138">See also</span></span>

- [<span data-ttu-id="459bd-139">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="459bd-139">Application compatibility</span></span>](application-compatibility.md)
- [<span data-ttu-id="459bd-140">\<useLegacyJit> Element</span><span class="sxs-lookup"><span data-stu-id="459bd-140">\<useLegacyJit> Element</span></span>](../configure-apps/file-schema/runtime/uselegacyjit-element.md)
