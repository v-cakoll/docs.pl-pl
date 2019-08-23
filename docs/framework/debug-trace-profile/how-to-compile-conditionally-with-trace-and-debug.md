---
title: 'Instrukcje: Kompilowanie warunkowe ze śledzeniem i debugowaniem'
ms.date: 03/30/2017
helpviewer_keywords:
- trace compiler options
- trace statements
- compiling source code, trace statements
- tracing [.NET Framework], enabling or disabling
- tracing [.NET Framework], compiling conditionally
- TRACE directive
- conditional compilation, tracing code
ms.assetid: 56d051c3-012c-42c1-9a58-7270edc624aa
author: mairaw
ms.author: mairaw
ms.openlocfilehash: df1f1c7e28464781a73a0939c3413f4c9d620d7d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942386"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a><span data-ttu-id="52852-102">Instrukcje: Kompilowanie warunkowe ze śledzeniem i debugowaniem</span><span class="sxs-lookup"><span data-stu-id="52852-102">How to: Compile Conditionally with Trace and Debug</span></span>
<span data-ttu-id="52852-103">Podczas debugowania aplikacji podczas opracowywania dane wyjściowe śledzenia i debugowania są przechodzą do okna danych wyjściowych w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="52852-103">While you are debugging an application during development, both your tracing and debugging output go to the Output window in Visual Studio.</span></span> <span data-ttu-id="52852-104">Aby jednak uwzględnić funkcje śledzenia we wdrożonej aplikacji, należy skompilować aplikacje Instrumentacji przy włączonej dyrektywie kompilatora **śledzenia** .</span><span class="sxs-lookup"><span data-stu-id="52852-104">However, to include tracing features in a deployed application, you must compile your instrumented applications with the **TRACE** compiler directive enabled.</span></span> <span data-ttu-id="52852-105">Pozwala to na skompilowanie kodu śledzenia w wydanej wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="52852-105">This allows tracing code to be compiled into the release version of your application.</span></span> <span data-ttu-id="52852-106">Jeśli nie włączysz dyrektywy **Trace** , cały kod śledzenia zostanie zignorowany podczas kompilacji i nie zostanie uwzględniony w kodzie wykonywalnym, który zostanie wdrożony.</span><span class="sxs-lookup"><span data-stu-id="52852-106">If you do not enable the **TRACE** directive, all tracing code is ignored during compilation and is not included in the executable code that you will deploy.</span></span>  
  
 <span data-ttu-id="52852-107">Obie metody śledzenia i debugowania mają skojarzone atrybuty warunkowe.</span><span class="sxs-lookup"><span data-stu-id="52852-107">Both the tracing and debugging methods have associated conditional attributes.</span></span> <span data-ttu-id="52852-108">Na przykład jeśli atrybut Conditional dla śledzenia ma **wartość true**, wszystkie instrukcje śledzenia są zawarte w zestawie (skompilowany plik exe lub. dll); Jeśli atrybut Conditional **śledzenia** ma **wartość false**, instrukcje Trace nie są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="52852-108">For example, if the conditional attribute for tracing is **true**, all trace statements are included within an assembly (a compiled .exe file or .dll); if the **Trace** conditional attribute is **false**, the trace statements are not included.</span></span>  
  
 <span data-ttu-id="52852-109">Można mieć włączony atrybut warunkowy **Trace** lub **Debug** dla kompilacji lub obu tych wartości.</span><span class="sxs-lookup"><span data-stu-id="52852-109">You can have either the **Trace** or **Debug** conditional attribute turned on for a build, or both, or neither.</span></span> <span data-ttu-id="52852-110">W ten sposób istnieją cztery typy kompilacji: **Debugowanie**, **śledzenie**, oba lub żadne z nich.</span><span class="sxs-lookup"><span data-stu-id="52852-110">Thus, there are four types of build: **Debug**, **Trace**, both, or neither.</span></span> <span data-ttu-id="52852-111">Niektóre kompilacje wydania dla wdrożenia produkcyjnego mogą nie zawierać żadnego z nich; Większość kompilacji debugowania zawiera oba elementy.</span><span class="sxs-lookup"><span data-stu-id="52852-111">Some release builds for production deployment might contain neither; most debugging builds contain both.</span></span>  
  
 <span data-ttu-id="52852-112">Ustawienia kompilatora dla aplikacji można określić na kilka sposobów:</span><span class="sxs-lookup"><span data-stu-id="52852-112">You can specify the compiler settings for your application in several ways:</span></span>  
  
- <span data-ttu-id="52852-113">Strony właściwości</span><span class="sxs-lookup"><span data-stu-id="52852-113">The property pages</span></span>  
  
- <span data-ttu-id="52852-114">Wiersz polecenia</span><span class="sxs-lookup"><span data-stu-id="52852-114">The command line</span></span>  
  
- <span data-ttu-id="52852-115">**#CONST** (w przypadku Visual Basic) i **#define** ( C#dla)</span><span class="sxs-lookup"><span data-stu-id="52852-115">**#CONST** (for Visual Basic) and **#define** (for C#)</span></span>  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a><span data-ttu-id="52852-116">Aby zmienić ustawienia kompilacji w oknie dialogowym strony właściwości</span><span class="sxs-lookup"><span data-stu-id="52852-116">To change compile settings from the property pages dialog box</span></span>  
  
1. <span data-ttu-id="52852-117">Kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="52852-117">Right-click the project node in **Solution Explorer**.</span></span>  
  
2. <span data-ttu-id="52852-118">Wybierz **Właściwości** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="52852-118">Choose **Properties** from the shortcut menu.</span></span>  
  
    - <span data-ttu-id="52852-119">W Visual Basic kliknij kartę **kompilacja** w lewym okienku strony właściwości, a następnie kliknij przycisk **Zaawansowane opcje kompilacji** , aby wyświetlić okno dialogowe **Zaawansowane ustawienia kompilatora** .</span><span class="sxs-lookup"><span data-stu-id="52852-119">In Visual Basic, click the **Compile** tab in the left pane of the property page, then click the **Advanced Compile Options** button to display the **Advanced Compiler Settings** dialog box.</span></span> <span data-ttu-id="52852-120">Zaznacz pola wyboru dla ustawień kompilatora, które chcesz włączyć.</span><span class="sxs-lookup"><span data-stu-id="52852-120">Select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="52852-121">Usuń zaznaczenie pól wyboru dla ustawień, które chcesz wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="52852-121">Clear the check boxes for settings you want to disable.</span></span>  
  
    - <span data-ttu-id="52852-122">W C#programie kliknij kartę **kompilacja** w lewym okienku strony właściwości, a następnie zaznacz pola wyboru dla ustawień kompilatora, które chcesz włączyć.</span><span class="sxs-lookup"><span data-stu-id="52852-122">In C#, click the **Build** tab in the left pane of the property page, then select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="52852-123">Usuń zaznaczenie pól wyboru dla ustawień, które chcesz wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="52852-123">Clear the check boxes for settings you want to disable.</span></span>  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a><span data-ttu-id="52852-124">Aby skompilować kod Instrumentacji przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="52852-124">To compile instrumented code using the command line</span></span>  
  
1. <span data-ttu-id="52852-125">Ustaw przełącznik kompilatora warunkowego w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="52852-125">Set a conditional compiler switch on the command line.</span></span> <span data-ttu-id="52852-126">Kompilator będzie zawierać kod śledzenia lub debugowania w pliku wykonywalnym.</span><span class="sxs-lookup"><span data-stu-id="52852-126">The compiler will include trace or debug code in the executable.</span></span>  
  
     <span data-ttu-id="52852-127">Na przykład następująca instrukcja kompilatora wprowadzona w wierszu polecenia będzie zawierać kod śledzenia w skompilowanym pliku wykonywalnym:</span><span class="sxs-lookup"><span data-stu-id="52852-127">For example, the following compiler instruction entered on the command line would include your tracing code in a compiled executable:</span></span>  
  
     <span data-ttu-id="52852-128">Dla Visual Basic: **VBC-r:System.dll-d:Trace = true-d:Debug = false WebApplication. vb**</span><span class="sxs-lookup"><span data-stu-id="52852-128">For Visual Basic: **vbc -r:System.dll -d:TRACE=TRUE -d:DEBUG=FALSE MyApplication.vb**</span></span>  
  
     <span data-ttu-id="52852-129">Dla C#: **CSC-r:System.dll-d:Trace-d:Debug = false MyApplication.cs**</span><span class="sxs-lookup"><span data-stu-id="52852-129">For C#: **csc -r:System.dll -d:TRACE -d:DEBUG=FALSE MyApplication.cs**</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="52852-130">Aby skompilować więcej niż jeden plik aplikacji, pozostaw puste miejsce między nazwami plików, na przykład **MyApplication1. vb MyApplication2. vb MyApplication3. vb** lub **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span><span class="sxs-lookup"><span data-stu-id="52852-130">To compile more than one application file, leave a blank space between the file names, for example, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** or **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span></span>  
  
     <span data-ttu-id="52852-131">Znaczenie dyrektyw kompilacji warunkowej używanych w powyższych przykładach jest następujące:</span><span class="sxs-lookup"><span data-stu-id="52852-131">The meaning of the conditional-compilation directives used in the above examples is as follows:</span></span>  
  
    |<span data-ttu-id="52852-132">— Dyrektywa</span><span class="sxs-lookup"><span data-stu-id="52852-132">Directive</span></span>|<span data-ttu-id="52852-133">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="52852-133">Meaning</span></span>|  
    |---------------|-------------|  
    |`vbc`|<span data-ttu-id="52852-134">kompilator Visual Basic</span><span class="sxs-lookup"><span data-stu-id="52852-134">Visual Basic compiler</span></span>|  
    |`csc`|<span data-ttu-id="52852-135">C#Compiler</span><span class="sxs-lookup"><span data-stu-id="52852-135">C# compiler</span></span>|  
    |`-r:`|<span data-ttu-id="52852-136">Odwołuje się do zestawu zewnętrznego (EXE lub DLL)</span><span class="sxs-lookup"><span data-stu-id="52852-136">References an external assembly (EXE or DLL)</span></span>|  
    |`-d:`|<span data-ttu-id="52852-137">Definiuje symbol kompilacji warunkowej</span><span class="sxs-lookup"><span data-stu-id="52852-137">Defines a conditional compilation symbol</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="52852-138">Należy sprawdzić poprawność śledzenia lub debugowania przy użyciu wielkich liter.</span><span class="sxs-lookup"><span data-stu-id="52852-138">You must spell TRACE or DEBUG with uppercase letters.</span></span> <span data-ttu-id="52852-139">Aby uzyskać więcej informacji na temat poleceń kompilacji warunkowej `vbc /?` , wprowadź (for Visual Basic `csc /?` ) lub C#(for) w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="52852-139">For more information about the conditional compilation commands, enter `vbc /?` (for Visual Basic) or `csc /?` (for C#) at the command prompt.</span></span> <span data-ttu-id="52852-140">Aby uzyskać więcej informacji, zobacz [Kompilowanie z wiersza polecenia](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) lub wywoływanie [kompilatora wiersza polecenia](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="52852-140">For more information, see [Building from the Command Line](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) or [Invoking the Command-Line Compiler](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span></span>  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a><span data-ttu-id="52852-141">Aby przeprowadzić kompilację warunkową przy użyciu #CONST lub #define</span><span class="sxs-lookup"><span data-stu-id="52852-141">To perform conditional compilation using #CONST or #define</span></span>  
  
1. <span data-ttu-id="52852-142">Wpisz odpowiednią instrukcję dla języka programowania w górnej części pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="52852-142">Type the appropriate statement for your programming language at the top of the source code file.</span></span>  
  
    |<span data-ttu-id="52852-143">Język</span><span class="sxs-lookup"><span data-stu-id="52852-143">Language</span></span>|<span data-ttu-id="52852-144">Instrukcja</span><span class="sxs-lookup"><span data-stu-id="52852-144">Statement</span></span>|<span data-ttu-id="52852-145">Wynik</span><span class="sxs-lookup"><span data-stu-id="52852-145">Result</span></span>|  
    |--------------|---------------|------------|  
    |<span data-ttu-id="52852-146">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="52852-146">**Visual Basic**</span></span>|<span data-ttu-id="52852-147">**Śledzenie #CONST = true**</span><span class="sxs-lookup"><span data-stu-id="52852-147">**#CONST TRACE = true**</span></span>|<span data-ttu-id="52852-148">Włącza śledzenie</span><span class="sxs-lookup"><span data-stu-id="52852-148">Enables tracing</span></span>|  
    ||<span data-ttu-id="52852-149">**Śledzenie #CONST = FAŁSZ**</span><span class="sxs-lookup"><span data-stu-id="52852-149">**#CONST TRACE = false**</span></span>|<span data-ttu-id="52852-150">Wyłącza śledzenie</span><span class="sxs-lookup"><span data-stu-id="52852-150">Disables tracing</span></span>|  
    ||<span data-ttu-id="52852-151">**#CONST DEBUGUJ = true**</span><span class="sxs-lookup"><span data-stu-id="52852-151">**#CONST DEBUG = true**</span></span>|<span data-ttu-id="52852-152">Włącza debugowanie</span><span class="sxs-lookup"><span data-stu-id="52852-152">Enables debugging</span></span>|  
    ||<span data-ttu-id="52852-153">**Debugowanie #CONST = FAŁSZ**</span><span class="sxs-lookup"><span data-stu-id="52852-153">**#CONST DEBUG = false**</span></span>|<span data-ttu-id="52852-154">Wyłącza debugowanie</span><span class="sxs-lookup"><span data-stu-id="52852-154">Disables debugging</span></span>|  
    |<span data-ttu-id="52852-155">**C#**</span><span class="sxs-lookup"><span data-stu-id="52852-155">**C#**</span></span>|<span data-ttu-id="52852-156">**Śledzenie #define**</span><span class="sxs-lookup"><span data-stu-id="52852-156">**#define TRACE**</span></span>|<span data-ttu-id="52852-157">Włącza śledzenie</span><span class="sxs-lookup"><span data-stu-id="52852-157">Enables tracing</span></span>|  
    ||<span data-ttu-id="52852-158">**Śledzenie #undef**</span><span class="sxs-lookup"><span data-stu-id="52852-158">**#undef TRACE**</span></span>|<span data-ttu-id="52852-159">Wyłącza śledzenie</span><span class="sxs-lookup"><span data-stu-id="52852-159">Disables tracing</span></span>|  
    ||<span data-ttu-id="52852-160">**Debugowanie #define**</span><span class="sxs-lookup"><span data-stu-id="52852-160">**#define DEBUG**</span></span>|<span data-ttu-id="52852-161">Włącza debugowanie</span><span class="sxs-lookup"><span data-stu-id="52852-161">Enables debugging</span></span>|  
    ||<span data-ttu-id="52852-162">**Debugowanie #undef**</span><span class="sxs-lookup"><span data-stu-id="52852-162">**#undef DEBUG**</span></span>|<span data-ttu-id="52852-163">Wyłącza debugowanie</span><span class="sxs-lookup"><span data-stu-id="52852-163">Disables debugging</span></span>|  
  
### <a name="to-disable-tracing-or-debugging"></a><span data-ttu-id="52852-164">Aby wyłączyć śledzenie lub debugowanie</span><span class="sxs-lookup"><span data-stu-id="52852-164">To disable tracing or debugging</span></span>  
  
<span data-ttu-id="52852-165">Usuń dyrektywę kompilatora z kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="52852-165">Delete the compiler directive from your source code.</span></span>  
  
<span data-ttu-id="52852-166">\- lub —</span><span class="sxs-lookup"><span data-stu-id="52852-166">\- or -</span></span>  
  
<span data-ttu-id="52852-167">Dodaj komentarz do dyrektywy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="52852-167">Comment out the compiler directive.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52852-168">Gdy wszystko będzie gotowe do skompilowania, możesz wybrać opcję **Kompiluj** z menu **kompilacja** lub użyć metody wiersza polecenia, ale bez wpisywania znaków **d:** , aby zdefiniować symbole kompilacji warunkowej.</span><span class="sxs-lookup"><span data-stu-id="52852-168">When you are ready to compile, you can either choose **Build** from the **Build** menu, or use the command line method but without typing the **d:** to define conditional compilation symbols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52852-169">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52852-169">See also</span></span>

- [<span data-ttu-id="52852-170">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="52852-170">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="52852-171">Instrukcje: Tworzenie, inicjowanie i konfigurowanie przełączników śledzenia</span><span class="sxs-lookup"><span data-stu-id="52852-171">How to: Create, Initialize and Configure Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="52852-172">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="52852-172">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="52852-173">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="52852-173">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [<span data-ttu-id="52852-174">Instrukcje: Dodawanie instrukcji śledzenia do kodu aplikacji</span><span class="sxs-lookup"><span data-stu-id="52852-174">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="52852-175">Instrukcje: Ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="52852-175">How to: Set Environment Variables for the Visual Studio Command Line</span></span>](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [<span data-ttu-id="52852-176">Instrukcje: wywoływanie kompilatora z wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="52852-176">How to: Invoke the Command-Line Compiler</span></span>](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
