---
title: 'Środki zaradcze: Nowy kompilator JIT 64-bitowych'
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d3eb82cf9bac1e40947fb78882d18c5f09b0092
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690088"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a><span data-ttu-id="030ae-102">Środki zaradcze: Nowy kompilator JIT 64-bitowych</span><span class="sxs-lookup"><span data-stu-id="030ae-102">Mitigation: New 64-bit JIT Compiler</span></span>
<span data-ttu-id="030ae-103">Począwszy od programu .NET Framework 4.6, środowisko uruchomieniowe zawiera nowe 64-bitowego kompilatora JIT dla kompilacji just in time.</span><span class="sxs-lookup"><span data-stu-id="030ae-103">Starting with the .NET Framework 4.6, the runtime includes a new 64-bit JIT compiler for just-in-time compilation.</span></span> <span data-ttu-id="030ae-104">Ta zmiana nie ma wpływu na kompilacji z 32-bitowego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="030ae-104">This change does not affect compilation with the  32-bit JIT compiler.</span></span>  
  
## <a name="unexpected-behavior-or-exceptions"></a><span data-ttu-id="030ae-105">Wyjątki lub nieoczekiwane zachowanie</span><span class="sxs-lookup"><span data-stu-id="030ae-105">Unexpected behavior or exceptions</span></span>  
 <span data-ttu-id="030ae-106">W niektórych przypadkach kompilacji za pomocą nowego 64-bitowy kompilator JIT powoduje wyjątek czasu wykonywania, lub zachowanie, które nie zostanie wykryty podczas wykonywania kodu skompilowanego przez starsze 64-bitowego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="030ae-106">In some cases, compilation with the new 64-bit JIT compiler results in a runtime exception or in behavior that is not observed when executing code compiled by the older 64-bit JIT compiler.</span></span> <span data-ttu-id="030ae-107">Znane różnice są następujące:</span><span class="sxs-lookup"><span data-stu-id="030ae-107">The known differences include the following:</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="030ae-108">Rozwiązano wszystkich tych znanych problemów występujących w kompilator 64-bitowego wydania przy użyciu platformy .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="030ae-108">All of these known issues have been addressed in the new 64-bit compiler released with the .NET Framework 4.6.2.</span></span> <span data-ttu-id="030ae-109">Większość ma również problem ten został rozwiązany w wersjach usługi programu .NET Framework 4.6 i 4.6.1, które są dołączone do aktualizacji Windows.</span><span class="sxs-lookup"><span data-stu-id="030ae-109">Most have also been addressed in service releases of the .NET Framework 4.6 and 4.6.1 that are included with Windows Update.</span></span> <span data-ttu-id="030ae-110">Aby wyeliminować te problemy, zapewniając danej wersji systemu Windows jest aktualny, lub po uaktualnieniu do programu .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="030ae-110">You can eliminate these issues by ensuring that your version of Windows is up to date, or by upgrading to the .NET Framework 4.6.2.</span></span>  
  
-   <span data-ttu-id="030ae-111">W pewnych okolicznościach może zgłaszać operacja rozpakowania <xref:System.NullReferenceException> w kompilacjach wydania przy użyciu optymalizacji włączona.</span><span class="sxs-lookup"><span data-stu-id="030ae-111">Under certain conditions, an unboxing operation may throw a <xref:System.NullReferenceException> in Release builds with optimization turned on.</span></span>  
  
-   <span data-ttu-id="030ae-112">W niektórych przypadkach może zgłaszać wykonywania kodu produkcyjnego w treści metody dużych <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="030ae-112">In some cases, execution of production code in a large method body may throw a <xref:System.StackOverflowException>.</span></span>  
  
-   <span data-ttu-id="030ae-113">Pod pewnymi warunkami struktury przekazany do metody są traktowane jako typy odwołań, a nie typy wartości w wersji kompilacji.</span><span class="sxs-lookup"><span data-stu-id="030ae-113">Under certain conditions, structures passed to a method are treated as reference types rather than value types in Release builds.</span></span> <span data-ttu-id="030ae-114">Jednym z przejawy tego problemu jest to, czy poszczególnych elementów w kolekcji są wyświetlane w nieoczekiwanej kolejności.</span><span class="sxs-lookup"><span data-stu-id="030ae-114">One of the manifestations of this issue is that the individual items in a collection appear in an unexpected order.</span></span>  
  
-   <span data-ttu-id="030ae-115">W pewnych okolicznościach porównanie <xref:System.UInt16> wartości za pomocą ich zestaw wysokobitowych jest nieprawidłowy, gdy Optymalizacja jest włączona.</span><span class="sxs-lookup"><span data-stu-id="030ae-115">Under certain conditions, the comparison of <xref:System.UInt16> values with their high bit set is incorrect if optimization is enabled.</span></span>  
  
-   <span data-ttu-id="030ae-116">Pod pewnymi warunkami, szczególnie podczas inicjowania tablicy wartości, inicjowanie pamięci przez <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> instrukcja IL może zainicjować pamięci o nieprawidłowej wartości.</span><span class="sxs-lookup"><span data-stu-id="030ae-116">Under certain conditions, particularly when initializing array values, memory initialization by the <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL instruction may initialize memory with an incorrect value.</span></span> <span data-ttu-id="030ae-117">Może to spowodować w nieobsługiwany wyjątek lub nieprawidłowych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="030ae-117">This can result either in an unhandled exception or incorrect output.</span></span>  
  
-   <span data-ttu-id="030ae-118">W pewnych okolicznościach rzadkich test warunkowy bit może zwracać nieprawidłowe <xref:System.Boolean> wartość lub zgłosić wyjątek, jeśli są włączone optymalizacje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="030ae-118">Under certain rare conditions, a conditional bit test can return the incorrect <xref:System.Boolean> value or throw an exception if compiler optimizations are enabled.</span></span>  
  
-   <span data-ttu-id="030ae-119">Pod pewnymi warunkami Jeśli `if` instrukcja jest używane do testowania dla warunku przed wejściem `try` bloku i wyjścia z `try` bloku, a tym samym stanie, które jest obliczane w `catch` lub `finally` bloku, Nowa Usuwa 64-bitowy kompilator JIT `if` warunku z `catch` lub `finally` zablokować, jeśli optymalizuje kod.</span><span class="sxs-lookup"><span data-stu-id="030ae-119">Under certain conditions, if an `if` statement is used to test for a condition before entering  a `try` block and in the exit from the `try` block, and the same condition is evaluated in the `catch` or `finally` block, the new 64-bit JIT compiler removes the `if` condition from the `catch` or `finally` block when it optimizes code.</span></span> <span data-ttu-id="030ae-120">W rezultacie kod wewnątrz `if` instrukcji w `catch` lub `finally` bezwarunkowo wykonaniu bloku.</span><span class="sxs-lookup"><span data-stu-id="030ae-120">As a result, code inside the `if` statement in the `catch` or `finally` block is executed unconditionally.</span></span>  
  
<a name="General"></a>   
## <a name="mitigation-of-known-issues"></a><span data-ttu-id="030ae-121">Ograniczenie znane problemy</span><span class="sxs-lookup"><span data-stu-id="030ae-121">Mitigation of known issues</span></span>  
 <span data-ttu-id="030ae-122">Jeśli wystąpią problemy z wymienionych powyżej, można je rozwiązać, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="030ae-122">If you encounter the issues listed above, you can address them by doing any of the following:</span></span>  
  
-   <span data-ttu-id="030ae-123">Uaktualnianie do programu .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="030ae-123">Upgrade to the .NET Framework 4.6.2.</span></span> <span data-ttu-id="030ae-124">Kompilator 64-bitowych dołączone do programu .NET Framework 4.6.2 dotyczy każdego z tych znanych problemów.</span><span class="sxs-lookup"><span data-stu-id="030ae-124">The new 64-bit compiler included with the .NET Framework 4.6.2 addresses each of these known issues.</span></span>  
  
-   <span data-ttu-id="030ae-125">Upewnij się, że Twoja wersja programu Windows bądź na bieżąco, uruchamiając Windows Update.</span><span class="sxs-lookup"><span data-stu-id="030ae-125">Ensure that your version of Windows is up to date by running Windows Update.</span></span> <span data-ttu-id="030ae-126">Aktualizacje usług .NET Framework 4.6 i 4.6.1 dotyczą każdego z tych problemów, z wyjątkiem <xref:System.NullReferenceException> w operacja rozpakowania.</span><span class="sxs-lookup"><span data-stu-id="030ae-126">Service updates to the .NET Framework 4.6 and 4.6.1 address each of these issues except the <xref:System.NullReferenceException> in an unboxing operation.</span></span>  
  
-   <span data-ttu-id="030ae-127">Kompiluj przy użyciu starszych 64-bitowego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="030ae-127">Compile with the older 64-bit JIT compiler.</span></span> <span data-ttu-id="030ae-128">Zobacz [ograniczenia inne problemy z](#Other) sekcji, aby uzyskać więcej informacji na temat sposobu wykonania tego zadania.</span><span class="sxs-lookup"><span data-stu-id="030ae-128">See the [Mitigation of other issues](#Other) section for more information on how to do this.</span></span>  
  
<a name="Other"></a>   
## <a name="mitigation-of-other-issues"></a><span data-ttu-id="030ae-129">Ograniczenie inne problemy</span><span class="sxs-lookup"><span data-stu-id="030ae-129">Mitigation of other issues</span></span>  
 <span data-ttu-id="030ae-130">Jeśli występują inne różnice w zachowaniu między kodu skompilowanego za pomocą starszego kompilatora 64-bitowych i nowe 64-bitowy kompilator JIT lub debug i release wersje aplikacji, które przy użyciu nowego 64-bitowy kompilator JIT są kompilowane, można wykonaj następujące czynności Aby skompilować aplikację przy użyciu starszych 64-bitowy kompilator JIT:</span><span class="sxs-lookup"><span data-stu-id="030ae-130">If you encounter any other difference in behavior between code compiled with the older 64-bit compiler and the new 64-bit JIT compiler, or between the debug and release versions of your app that are both compiled with the new 64-bit JIT compiler, you can do the following to compile your app with the older 64-bit JIT compiler:</span></span>  
  
-   <span data-ttu-id="030ae-131">Na podstawie poszczególnych aplikacji można dodać [ \<useLegacyJit >](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) element do pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="030ae-131">On a per-application basis, you can add the [\<useLegacyJit>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) element to your application's configuration file.</span></span> <span data-ttu-id="030ae-132">Następujące wyłącza kompilacji za pomocą nowego 64-bitowy kompilator JIT i zamiast tego używa starszej wersji 64-bitowego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="030ae-132">The following disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
-   <span data-ttu-id="030ae-133">Na poszczególnych użytkowników, możesz dodać `REG_DWORD` wartość o nazwie `useLegacyJit` do `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="030ae-133">On a per-user basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="030ae-134">Wartość 1 umożliwia starszej wersji 64-bitowy kompilator JIT; wartość 0 wyłącza je i włącza nowe 64-bitowego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="030ae-134">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
-   <span data-ttu-id="030ae-135">Na poszczególnych komputerach, można dodać `REG_DWORD` wartość o nazwie `useLegacyJit` do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="030ae-135">On a per-machine basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="030ae-136">Wartość 1 umożliwia starszej wersji 64-bitowy kompilator JIT; wartość 0 wyłącza je i włącza nowe 64-bitowego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="030ae-136">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
 <span data-ttu-id="030ae-137">Możesz również dać nam znać o problemie przez raportowanie błędów na [witryny Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span><span class="sxs-lookup"><span data-stu-id="030ae-137">You can also let us know about the problem by reporting a bug on [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="030ae-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="030ae-138">See also</span></span>
- [<span data-ttu-id="030ae-139">Zmiany środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="030ae-139">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
- [<span data-ttu-id="030ae-140">\<useLegacyJit> Element</span><span class="sxs-lookup"><span data-stu-id="030ae-140">\<useLegacyJit> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)
