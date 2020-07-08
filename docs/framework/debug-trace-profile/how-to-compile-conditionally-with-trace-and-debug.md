---
title: 'Porady: kompilowanie warunkowe ze śledzeniem i debugowaniem'
description: Dowiedz się, jak kompilować warunkowo przy użyciu atrybutów warunkowych TRACE i DEBUG podczas kompilowania aplikacji .NET.
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
ms.openlocfilehash: 8758b793866ec0317f91d636476d33bd001ddd78
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051223"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a><span data-ttu-id="a84ea-103">Porady: kompilowanie warunkowe ze śledzeniem i debugowaniem</span><span class="sxs-lookup"><span data-stu-id="a84ea-103">How to: Compile Conditionally with Trace and Debug</span></span>
<span data-ttu-id="a84ea-104">Podczas debugowania aplikacji podczas opracowywania dane wyjściowe śledzenia i debugowania są przechodzą do okna danych wyjściowych w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a84ea-104">While you are debugging an application during development, both your tracing and debugging output go to the Output window in Visual Studio.</span></span> <span data-ttu-id="a84ea-105">Aby jednak uwzględnić funkcje śledzenia we wdrożonej aplikacji, należy skompilować aplikacje Instrumentacji przy włączonej dyrektywie kompilatora **śledzenia** .</span><span class="sxs-lookup"><span data-stu-id="a84ea-105">However, to include tracing features in a deployed application, you must compile your instrumented applications with the **TRACE** compiler directive enabled.</span></span> <span data-ttu-id="a84ea-106">Pozwala to na skompilowanie kodu śledzenia w wydanej wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a84ea-106">This allows tracing code to be compiled into the release version of your application.</span></span> <span data-ttu-id="a84ea-107">Jeśli nie włączysz dyrektywy **Trace** , cały kod śledzenia zostanie zignorowany podczas kompilacji i nie zostanie uwzględniony w kodzie wykonywalnym, który zostanie wdrożony.</span><span class="sxs-lookup"><span data-stu-id="a84ea-107">If you do not enable the **TRACE** directive, all tracing code is ignored during compilation and is not included in the executable code that you will deploy.</span></span>  
  
 <span data-ttu-id="a84ea-108">Obie metody śledzenia i debugowania mają skojarzone atrybuty warunkowe.</span><span class="sxs-lookup"><span data-stu-id="a84ea-108">Both the tracing and debugging methods have associated conditional attributes.</span></span> <span data-ttu-id="a84ea-109">Na przykład jeśli atrybut Conditional dla śledzenia ma **wartość true**, wszystkie instrukcje śledzenia są zawarte w zestawie (skompilowany plik exe lub. dll); Jeśli atrybut Conditional **śledzenia** ma **wartość false**, instrukcje Trace nie są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="a84ea-109">For example, if the conditional attribute for tracing is **true**, all trace statements are included within an assembly (a compiled .exe file or .dll); if the **Trace** conditional attribute is **false**, the trace statements are not included.</span></span>  
  
 <span data-ttu-id="a84ea-110">Można mieć włączony atrybut warunkowy **Trace** lub **Debug** dla kompilacji lub obu tych wartości.</span><span class="sxs-lookup"><span data-stu-id="a84ea-110">You can have either the **Trace** or **Debug** conditional attribute turned on for a build, or both, or neither.</span></span> <span data-ttu-id="a84ea-111">W tym celu istnieją cztery typy kompilacji: **Debug**, **Trace**, Both lub nie.</span><span class="sxs-lookup"><span data-stu-id="a84ea-111">Thus, there are four types of build: **Debug**, **Trace**, both, or neither.</span></span> <span data-ttu-id="a84ea-112">Niektóre kompilacje wydania dla wdrożenia produkcyjnego mogą nie zawierać żadnego z nich; Większość kompilacji debugowania zawiera oba elementy.</span><span class="sxs-lookup"><span data-stu-id="a84ea-112">Some release builds for production deployment might contain neither; most debugging builds contain both.</span></span>  
  
 <span data-ttu-id="a84ea-113">Ustawienia kompilatora dla aplikacji można określić na kilka sposobów:</span><span class="sxs-lookup"><span data-stu-id="a84ea-113">You can specify the compiler settings for your application in several ways:</span></span>  
  
- <span data-ttu-id="a84ea-114">Strony właściwości</span><span class="sxs-lookup"><span data-stu-id="a84ea-114">The property pages</span></span>  
  
- <span data-ttu-id="a84ea-115">Wiersz polecenia</span><span class="sxs-lookup"><span data-stu-id="a84ea-115">The command line</span></span>  
  
- <span data-ttu-id="a84ea-116">**#CONST** (Visual Basic) i **#define** (dla języka C#)</span><span class="sxs-lookup"><span data-stu-id="a84ea-116">**#CONST** (for Visual Basic) and **#define** (for C#)</span></span>  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a><span data-ttu-id="a84ea-117">Aby zmienić ustawienia kompilacji w oknie dialogowym strony właściwości</span><span class="sxs-lookup"><span data-stu-id="a84ea-117">To change compile settings from the property pages dialog box</span></span>  
  
1. <span data-ttu-id="a84ea-118">Kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="a84ea-118">Right-click the project node in **Solution Explorer**.</span></span>  
  
2. <span data-ttu-id="a84ea-119">Wybierz **Właściwości** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="a84ea-119">Choose **Properties** from the shortcut menu.</span></span>  
  
    - <span data-ttu-id="a84ea-120">W Visual Basic kliknij kartę **kompilacja** w lewym okienku strony właściwości, a następnie kliknij przycisk **Zaawansowane opcje kompilacji** , aby wyświetlić okno dialogowe **Zaawansowane ustawienia kompilatora** .</span><span class="sxs-lookup"><span data-stu-id="a84ea-120">In Visual Basic, click the **Compile** tab in the left pane of the property page, then click the **Advanced Compile Options** button to display the **Advanced Compiler Settings** dialog box.</span></span> <span data-ttu-id="a84ea-121">Zaznacz pola wyboru dla ustawień kompilatora, które chcesz włączyć.</span><span class="sxs-lookup"><span data-stu-id="a84ea-121">Select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="a84ea-122">Usuń zaznaczenie pól wyboru dla ustawień, które chcesz wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="a84ea-122">Clear the check boxes for settings you want to disable.</span></span>  
  
    - <span data-ttu-id="a84ea-123">W języku C# kliknij kartę **kompilacja** w lewym okienku strony właściwości, a następnie zaznacz pola wyboru dla ustawień kompilatora, które chcesz włączyć.</span><span class="sxs-lookup"><span data-stu-id="a84ea-123">In C#, click the **Build** tab in the left pane of the property page, then select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="a84ea-124">Usuń zaznaczenie pól wyboru dla ustawień, które chcesz wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="a84ea-124">Clear the check boxes for settings you want to disable.</span></span>  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a><span data-ttu-id="a84ea-125">Aby skompilować kod Instrumentacji przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="a84ea-125">To compile instrumented code using the command line</span></span>  
  
1. <span data-ttu-id="a84ea-126">Ustaw przełącznik kompilatora warunkowego w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="a84ea-126">Set a conditional compiler switch on the command line.</span></span> <span data-ttu-id="a84ea-127">Kompilator będzie zawierać kod śledzenia lub debugowania w pliku wykonywalnym.</span><span class="sxs-lookup"><span data-stu-id="a84ea-127">The compiler will include trace or debug code in the executable.</span></span>  
  
     <span data-ttu-id="a84ea-128">Na przykład następująca instrukcja kompilatora wprowadzona w wierszu polecenia będzie zawierać kod śledzenia w skompilowanym pliku wykonywalnym:</span><span class="sxs-lookup"><span data-stu-id="a84ea-128">For example, the following compiler instruction entered on the command line would include your tracing code in a compiled executable:</span></span>  
  
     <span data-ttu-id="a84ea-129">W przypadku Visual Basic: **vbc -r:System.dll-d:Trace = true-d:Debug = false WebApplication. vb**</span><span class="sxs-lookup"><span data-stu-id="a84ea-129">For Visual Basic: **vbc -r:System.dll -d:TRACE=TRUE -d:DEBUG=FALSE MyApplication.vb**</span></span>  
  
     <span data-ttu-id="a84ea-130">Dla języka C#: **csc -r:System.dll-d:Trace-d:Debug = FALSE MyApplication.cs**</span><span class="sxs-lookup"><span data-stu-id="a84ea-130">For C#: **csc -r:System.dll -d:TRACE -d:DEBUG=FALSE MyApplication.cs**</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="a84ea-131">Aby skompilować więcej niż jeden plik aplikacji, pozostaw puste miejsce między nazwami plików, na przykład **MyApplication1. vb MyApplication2. vb MyApplication3. vb** lub **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span><span class="sxs-lookup"><span data-stu-id="a84ea-131">To compile more than one application file, leave a blank space between the file names, for example, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** or **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span></span>  
  
     <span data-ttu-id="a84ea-132">Znaczenie dyrektyw kompilacji warunkowej używanych w powyższych przykładach jest następujące:</span><span class="sxs-lookup"><span data-stu-id="a84ea-132">The meaning of the conditional-compilation directives used in the above examples is as follows:</span></span>  
  
    |<span data-ttu-id="a84ea-133">Dyrektywę</span><span class="sxs-lookup"><span data-stu-id="a84ea-133">Directive</span></span>|<span data-ttu-id="a84ea-134">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="a84ea-134">Meaning</span></span>|  
    |---------------|-------------|  
    |`vbc`|<span data-ttu-id="a84ea-135">kompilator Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a84ea-135">Visual Basic compiler</span></span>|  
    |`csc`|<span data-ttu-id="a84ea-136">Kompilator języka C#</span><span class="sxs-lookup"><span data-stu-id="a84ea-136">C# compiler</span></span>|  
    |`-r:`|<span data-ttu-id="a84ea-137">Odwołuje się do zestawu zewnętrznego (EXE lub DLL)</span><span class="sxs-lookup"><span data-stu-id="a84ea-137">References an external assembly (EXE or DLL)</span></span>|  
    |`-d:`|<span data-ttu-id="a84ea-138">Definiuje symbol kompilacji warunkowej</span><span class="sxs-lookup"><span data-stu-id="a84ea-138">Defines a conditional compilation symbol</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="a84ea-139">Należy sprawdzić poprawność śledzenia lub debugowania przy użyciu wielkich liter.</span><span class="sxs-lookup"><span data-stu-id="a84ea-139">You must spell TRACE or DEBUG with uppercase letters.</span></span> <span data-ttu-id="a84ea-140">Aby uzyskać więcej informacji na temat poleceń kompilacji warunkowej, wprowadź `vbc /?` (dla Visual Basic) lub `csc /?` (dla języka C#) w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="a84ea-140">For more information about the conditional compilation commands, enter `vbc /?` (for Visual Basic) or `csc /?` (for C#) at the command prompt.</span></span> <span data-ttu-id="a84ea-141">Aby uzyskać więcej informacji, zobacz [Kompilowanie z wiersza polecenia](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) lub [wywoływanie kompilatora wiersza polecenia](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a84ea-141">For more information, see [Building from the Command Line](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) or [Invoking the Command-Line Compiler](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span></span>  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a><span data-ttu-id="a84ea-142">Aby przeprowadzić kompilację warunkową przy użyciu #CONST lub #define</span><span class="sxs-lookup"><span data-stu-id="a84ea-142">To perform conditional compilation using #CONST or #define</span></span>  
  
1. <span data-ttu-id="a84ea-143">Wpisz odpowiednią instrukcję dla języka programowania w górnej części pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="a84ea-143">Type the appropriate statement for your programming language at the top of the source code file.</span></span>  
  
    |<span data-ttu-id="a84ea-144">Język</span><span class="sxs-lookup"><span data-stu-id="a84ea-144">Language</span></span>|<span data-ttu-id="a84ea-145">Instrukcja</span><span class="sxs-lookup"><span data-stu-id="a84ea-145">Statement</span></span>|<span data-ttu-id="a84ea-146">Wynik</span><span class="sxs-lookup"><span data-stu-id="a84ea-146">Result</span></span>|  
    |--------------|---------------|------------|  
    |<span data-ttu-id="a84ea-147">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="a84ea-147">**Visual Basic**</span></span>|<span data-ttu-id="a84ea-148">**Śledzenie #CONST = true**</span><span class="sxs-lookup"><span data-stu-id="a84ea-148">**#CONST TRACE = true**</span></span>|<span data-ttu-id="a84ea-149">Włącza śledzenie</span><span class="sxs-lookup"><span data-stu-id="a84ea-149">Enables tracing</span></span>|  
    ||<span data-ttu-id="a84ea-150">**Śledzenie #CONST = FAŁSZ**</span><span class="sxs-lookup"><span data-stu-id="a84ea-150">**#CONST TRACE = false**</span></span>|<span data-ttu-id="a84ea-151">Wyłącza śledzenie</span><span class="sxs-lookup"><span data-stu-id="a84ea-151">Disables tracing</span></span>|  
    ||<span data-ttu-id="a84ea-152">**#CONST DEBUGUJ = true**</span><span class="sxs-lookup"><span data-stu-id="a84ea-152">**#CONST DEBUG = true**</span></span>|<span data-ttu-id="a84ea-153">Włącza debugowanie</span><span class="sxs-lookup"><span data-stu-id="a84ea-153">Enables debugging</span></span>|  
    ||<span data-ttu-id="a84ea-154">**Debugowanie #CONST = FAŁSZ**</span><span class="sxs-lookup"><span data-stu-id="a84ea-154">**#CONST DEBUG = false**</span></span>|<span data-ttu-id="a84ea-155">Wyłącza debugowanie</span><span class="sxs-lookup"><span data-stu-id="a84ea-155">Disables debugging</span></span>|  
    |<span data-ttu-id="a84ea-156">**C#**</span><span class="sxs-lookup"><span data-stu-id="a84ea-156">**C#**</span></span>|<span data-ttu-id="a84ea-157">**Śledzenie #define**</span><span class="sxs-lookup"><span data-stu-id="a84ea-157">**#define TRACE**</span></span>|<span data-ttu-id="a84ea-158">Włącza śledzenie</span><span class="sxs-lookup"><span data-stu-id="a84ea-158">Enables tracing</span></span>|  
    ||<span data-ttu-id="a84ea-159">**Śledzenie #undef**</span><span class="sxs-lookup"><span data-stu-id="a84ea-159">**#undef TRACE**</span></span>|<span data-ttu-id="a84ea-160">Wyłącza śledzenie</span><span class="sxs-lookup"><span data-stu-id="a84ea-160">Disables tracing</span></span>|  
    ||<span data-ttu-id="a84ea-161">**Debugowanie #define**</span><span class="sxs-lookup"><span data-stu-id="a84ea-161">**#define DEBUG**</span></span>|<span data-ttu-id="a84ea-162">Włącza debugowanie</span><span class="sxs-lookup"><span data-stu-id="a84ea-162">Enables debugging</span></span>|  
    ||<span data-ttu-id="a84ea-163">**Debugowanie #undef**</span><span class="sxs-lookup"><span data-stu-id="a84ea-163">**#undef DEBUG**</span></span>|<span data-ttu-id="a84ea-164">Wyłącza debugowanie</span><span class="sxs-lookup"><span data-stu-id="a84ea-164">Disables debugging</span></span>|  
  
### <a name="to-disable-tracing-or-debugging"></a><span data-ttu-id="a84ea-165">Aby wyłączyć śledzenie lub debugowanie</span><span class="sxs-lookup"><span data-stu-id="a84ea-165">To disable tracing or debugging</span></span>  
  
<span data-ttu-id="a84ea-166">Usuń dyrektywę kompilatora z kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="a84ea-166">Delete the compiler directive from your source code.</span></span>  
  
<span data-ttu-id="a84ea-167">\-oraz</span><span class="sxs-lookup"><span data-stu-id="a84ea-167">\- or -</span></span>  
  
<span data-ttu-id="a84ea-168">Dodaj komentarz do dyrektywy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="a84ea-168">Comment out the compiler directive.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a84ea-169">Gdy wszystko będzie gotowe do skompilowania, możesz wybrać opcję **Kompiluj** z menu **kompilacja** lub użyć metody wiersza polecenia, ale bez wpisywania znaków **d:** , aby zdefiniować symbole kompilacji warunkowej.</span><span class="sxs-lookup"><span data-stu-id="a84ea-169">When you are ready to compile, you can either choose **Build** from the **Build** menu, or use the command line method but without typing the **d:** to define conditional compilation symbols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a84ea-170">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a84ea-170">See also</span></span>

- [<span data-ttu-id="a84ea-171">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="a84ea-171">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="a84ea-172">Instrukcje: tworzenie, inicjowanie i konfigurowanie przełączników śledzenia</span><span class="sxs-lookup"><span data-stu-id="a84ea-172">How to: Create, Initialize and Configure Trace Switches</span></span>](how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="a84ea-173">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="a84ea-173">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="a84ea-174">Obiekty nasłuchujące śledzenia</span><span class="sxs-lookup"><span data-stu-id="a84ea-174">Trace Listeners</span></span>](trace-listeners.md)
- [<span data-ttu-id="a84ea-175">Porady: dodawanie instrukcji śledzenia do kodu aplikacji</span><span class="sxs-lookup"><span data-stu-id="a84ea-175">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="a84ea-176">Porada: ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a84ea-176">How to set environment variables for the Visual Studio Command Line</span></span>](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [<span data-ttu-id="a84ea-177">Instrukcje: Wywoływanie kompilatora z wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="a84ea-177">How to: Invoke the Command-Line Compiler</span></span>](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
