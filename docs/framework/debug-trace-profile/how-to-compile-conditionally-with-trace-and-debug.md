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
ms.openlocfilehash: a010b2ee1de17741b2d0bdd6e7c50d5f602256ac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59298581"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a><span data-ttu-id="a1efd-102">Instrukcje: Kompilowanie warunkowe ze śledzeniem i debugowaniem</span><span class="sxs-lookup"><span data-stu-id="a1efd-102">How to: Compile Conditionally with Trace and Debug</span></span>
<span data-ttu-id="a1efd-103">Podczas debugowania aplikacji podczas tworzenia usługi śledzenia i dane wyjściowe debugowania przejdź do okna danych wyjściowych w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a1efd-103">While you are debugging an application during development, both your tracing and debugging output go to the Output window in Visual Studio.</span></span> <span data-ttu-id="a1efd-104">Jednak aby włączyć funkcje śledzenia do wdrożonej aplikacji, należy skompilować instrumentowanej aplikacji przy użyciu **śledzenia** dyrektywy kompilatora włączone.</span><span class="sxs-lookup"><span data-stu-id="a1efd-104">However, to include tracing features in a deployed application, you must compile your instrumented applications with the **TRACE** compiler directive enabled.</span></span> <span data-ttu-id="a1efd-105">Dzięki temu kod śledzenia jest kompilowana do wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a1efd-105">This allows tracing code to be compiled into the release version of your application.</span></span> <span data-ttu-id="a1efd-106">Jeśli nie włączysz **śledzenia** dyrektywy, cały kod śledzenia jest ignorowany podczas kompilacji, a nie znajduje się w kodzie pliku wykonywalnego, który zostanie wdrożony.</span><span class="sxs-lookup"><span data-stu-id="a1efd-106">If you do not enable the **TRACE** directive, all tracing code is ignored during compilation and is not included in the executable code that you will deploy.</span></span>  
  
 <span data-ttu-id="a1efd-107">Śledzenie i profilowanie metody skojarzony atrybuty warunkowe.</span><span class="sxs-lookup"><span data-stu-id="a1efd-107">Both the tracing and debugging methods have associated conditional attributes.</span></span> <span data-ttu-id="a1efd-108">Na przykład, jeśli warunkową atrybutu dla śledzenia jest **true**, wszystkie instrukcje śledzenia znajdują się w obrębie zestawu (plik skompilowanych .exe lub .dll); Jeśli **śledzenia** atrybut conditional jest **false**, instrukcji śledzenia nie są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="a1efd-108">For example, if the conditional attribute for tracing is **true**, all trace statements are included within an assembly (a compiled .exe file or .dll); if the **Trace** conditional attribute is **false**, the trace statements are not included.</span></span>  
  
 <span data-ttu-id="a1efd-109">Może mieć **śledzenia** lub **debugowania** atrybut conditional włączona dla kompilacji, lub obie lub nie.</span><span class="sxs-lookup"><span data-stu-id="a1efd-109">You can have either the **Trace** or **Debug** conditional attribute turned on for a build, or both, or neither.</span></span> <span data-ttu-id="a1efd-110">Dlatego istnieją cztery typy kompilacji: **Debugowanie**, **śledzenia**, obie lub nie.</span><span class="sxs-lookup"><span data-stu-id="a1efd-110">Thus, there are four types of build: **Debug**, **Trace**, both, or neither.</span></span> <span data-ttu-id="a1efd-111">Niektóre kompilacji wydania wdrożenia produkcyjnego może zawierać żadnego z tych celów; najbardziej debugujące kompilacje zawierać równocześnie.</span><span class="sxs-lookup"><span data-stu-id="a1efd-111">Some release builds for production deployment might contain neither; most debugging builds contain both.</span></span>  
  
 <span data-ttu-id="a1efd-112">Można określić ustawienia kompilatora dla aplikacji na kilka sposobów:</span><span class="sxs-lookup"><span data-stu-id="a1efd-112">You can specify the compiler settings for your application in several ways:</span></span>  
  
-   <span data-ttu-id="a1efd-113">Strony właściwości</span><span class="sxs-lookup"><span data-stu-id="a1efd-113">The property pages</span></span>  
  
-   <span data-ttu-id="a1efd-114">W wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="a1efd-114">The command line</span></span>  
  
-   <span data-ttu-id="a1efd-115">**#CONST** (dla języka Visual Basic) i **#define** (dla C#)</span><span class="sxs-lookup"><span data-stu-id="a1efd-115">**#CONST** (for Visual Basic) and **#define** (for C#)</span></span>  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a><span data-ttu-id="a1efd-116">Aby zmienić ustawienia kompilacji z okna dialogowego strony właściwości</span><span class="sxs-lookup"><span data-stu-id="a1efd-116">To change compile settings from the property pages dialog box</span></span>  
  
1. <span data-ttu-id="a1efd-117">Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="a1efd-117">Right-click the project node in **Solution Explorer**.</span></span>  
  
2. <span data-ttu-id="a1efd-118">Wybierz **właściwości** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="a1efd-118">Choose **Properties** from the shortcut menu.</span></span>  
  
    -   <span data-ttu-id="a1efd-119">W języku Visual Basic, kliknij przycisk **skompilować** w lewym okienku na stronie właściwości, a następnie kliknij **zaawansowane opcje kompilacji** przycisk, aby wyświetlić **Zaawansowane ustawienia kompilatora**okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="a1efd-119">In Visual Basic, click the **Compile** tab in the left pane of the property page, then click the **Advanced Compile Options** button to display the **Advanced Compiler Settings** dialog box.</span></span> <span data-ttu-id="a1efd-120">Zaznacz pole wyboru, jeśli dla ustawienia kompilatora, który chcesz włączyć.</span><span class="sxs-lookup"><span data-stu-id="a1efd-120">Select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="a1efd-121">Wyczyść pola wyboru dla ustawień, które chcesz wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="a1efd-121">Clear the check boxes for settings you want to disable.</span></span>  
  
    -   <span data-ttu-id="a1efd-122">W C#, kliknij przycisk **kompilacji** tabulator w lewym okienku na stronie właściwości, a następnie zaznacz pole wyboru, aby włączyć ustawienia kompilatora.</span><span class="sxs-lookup"><span data-stu-id="a1efd-122">In C#, click the **Build** tab in the left pane of the property page, then select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="a1efd-123">Wyczyść pola wyboru dla ustawień, które chcesz wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="a1efd-123">Clear the check boxes for settings you want to disable.</span></span>  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a><span data-ttu-id="a1efd-124">Aby skompilować kod instrumentowanych przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="a1efd-124">To compile instrumented code using the command line</span></span>  
  
1. <span data-ttu-id="a1efd-125">Ustaw przełącznik warunkowe kompilatora w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="a1efd-125">Set a conditional compiler switch on the command line.</span></span> <span data-ttu-id="a1efd-126">Kompilator będzie zawierać śledzenia lub możliwe jest debugowanie kodu w pliku wykonywalnym.</span><span class="sxs-lookup"><span data-stu-id="a1efd-126">The compiler will include trace or debug code in the executable.</span></span>  
  
     <span data-ttu-id="a1efd-127">Na przykład następująca instrukcja kompilatora wprowadzone w wierszu polecenia zawierałoby kod śledzenia w skompilowany plik wykonywalny:</span><span class="sxs-lookup"><span data-stu-id="a1efd-127">For example, the following compiler instruction entered on the command line would include your tracing code in a compiled executable:</span></span>  
  
     <span data-ttu-id="a1efd-128">Dla języka Visual Basic: **vbc — r:System.dll -d: ŚLEDZENIE = TRUE -d: DEBUG = FALSE MyApplication.vb**</span><span class="sxs-lookup"><span data-stu-id="a1efd-128">For Visual Basic: **vbc -r:System.dll -d:TRACE=TRUE -d:DEBUG=FALSE MyApplication.vb**</span></span>  
  
     <span data-ttu-id="a1efd-129">Aby uzyskać C#: **csc — r:System.dll -d: śledzenia -d: DEBUG = FALSE MyApplication.cs**</span><span class="sxs-lookup"><span data-stu-id="a1efd-129">For C#: **csc -r:System.dll -d:TRACE -d:DEBUG=FALSE MyApplication.cs**</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="a1efd-130">Aby skompilować więcej niż jeden plik w aplikacji, pozostaw puste miejsce między nazwy plików, na przykład **MyApplication1.vb MyApplication2.vb MyApplication3.vb** lub **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span><span class="sxs-lookup"><span data-stu-id="a1efd-130">To compile more than one application file, leave a blank space between the file names, for example, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** or **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span></span>  
  
     <span data-ttu-id="a1efd-131">Znaczenie dyrektywy kompilacji warunkowej używanych w powyższych przykładach jest następujące:</span><span class="sxs-lookup"><span data-stu-id="a1efd-131">The meaning of the conditional-compilation directives used in the above examples is as follows:</span></span>  
  
    |<span data-ttu-id="a1efd-132">— Dyrektywa</span><span class="sxs-lookup"><span data-stu-id="a1efd-132">Directive</span></span>|<span data-ttu-id="a1efd-133">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="a1efd-133">Meaning</span></span>|  
    |---------------|-------------|  
    |`vbc`|<span data-ttu-id="a1efd-134">kompilator Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a1efd-134">Visual Basic compiler</span></span>|  
    |`csc`|<span data-ttu-id="a1efd-135">C#Kompilator</span><span class="sxs-lookup"><span data-stu-id="a1efd-135">C# compiler</span></span>|  
    |`-r:`|<span data-ttu-id="a1efd-136">Odwołuje się do zestawu zewnętrznego (EXE lub DLL)</span><span class="sxs-lookup"><span data-stu-id="a1efd-136">References an external assembly (EXE or DLL)</span></span>|  
    |`-d:`|<span data-ttu-id="a1efd-137">Definiuje symbol kompilacji warunkowej</span><span class="sxs-lookup"><span data-stu-id="a1efd-137">Defines a conditional compilation symbol</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="a1efd-138">Należy pisowni śledzenia i debugowania przy użyciu wielkich liter.</span><span class="sxs-lookup"><span data-stu-id="a1efd-138">You must spell TRACE or DEBUG with uppercase letters.</span></span> <span data-ttu-id="a1efd-139">Aby uzyskać więcej informacji na temat poleceń kompilacji warunkowej, wprowadź `vbc /?` (dla języka Visual Basic) lub `csc /?` (dla C#) w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="a1efd-139">For more information about the conditional compilation commands, enter `vbc /?` (for Visual Basic) or `csc /?` (for C#) at the command prompt.</span></span> <span data-ttu-id="a1efd-140">Aby uzyskać więcej informacji, zobacz [tworzenie z wiersza polecenia](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) lub [wywoływanie kompilatora wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a1efd-140">For more information, see [Building from the Command Line](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) or [Invoking the Command-Line Compiler](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span></span>  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a><span data-ttu-id="a1efd-141">Do wykonania kompilacji warunkowej przy użyciu #CONST lub #define</span><span class="sxs-lookup"><span data-stu-id="a1efd-141">To perform conditional compilation using #CONST or #define</span></span>  
  
1. <span data-ttu-id="a1efd-142">Wpisz odpowiedniej instrukcji dla języka programowania, w górnej części pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="a1efd-142">Type the appropriate statement for your programming language at the top of the source code file.</span></span>  
  
    |<span data-ttu-id="a1efd-143">Język</span><span class="sxs-lookup"><span data-stu-id="a1efd-143">Language</span></span>|<span data-ttu-id="a1efd-144">Instrukcja</span><span class="sxs-lookup"><span data-stu-id="a1efd-144">Statement</span></span>|<span data-ttu-id="a1efd-145">Wynik</span><span class="sxs-lookup"><span data-stu-id="a1efd-145">Result</span></span>|  
    |--------------|---------------|------------|  
    |<span data-ttu-id="a1efd-146">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="a1efd-146">**Visual Basic**</span></span>|<span data-ttu-id="a1efd-147">**# ŚLEDZENIA CONST = true**</span><span class="sxs-lookup"><span data-stu-id="a1efd-147">**#CONST TRACE = true**</span></span>|<span data-ttu-id="a1efd-148">Umożliwia włączenie śledzenia</span><span class="sxs-lookup"><span data-stu-id="a1efd-148">Enables tracing</span></span>|  
    ||<span data-ttu-id="a1efd-149">**# ŚLEDZENIA CONST = false**</span><span class="sxs-lookup"><span data-stu-id="a1efd-149">**#CONST TRACE = false**</span></span>|<span data-ttu-id="a1efd-150">Wyłącza śledzenie</span><span class="sxs-lookup"><span data-stu-id="a1efd-150">Disables tracing</span></span>|  
    ||<span data-ttu-id="a1efd-151">**#CONST debugowania = true**</span><span class="sxs-lookup"><span data-stu-id="a1efd-151">**#CONST DEBUG = true**</span></span>|<span data-ttu-id="a1efd-152">Włącza debugowanie</span><span class="sxs-lookup"><span data-stu-id="a1efd-152">Enables debugging</span></span>|  
    ||<span data-ttu-id="a1efd-153">**#CONST debugowania = false**</span><span class="sxs-lookup"><span data-stu-id="a1efd-153">**#CONST DEBUG = false**</span></span>|<span data-ttu-id="a1efd-154">Wyłącza debugowanie</span><span class="sxs-lookup"><span data-stu-id="a1efd-154">Disables debugging</span></span>|  
    |<span data-ttu-id="a1efd-155">**C#**</span><span class="sxs-lookup"><span data-stu-id="a1efd-155">**C#**</span></span>|<span data-ttu-id="a1efd-156">**#define śledzenia**</span><span class="sxs-lookup"><span data-stu-id="a1efd-156">**#define TRACE**</span></span>|<span data-ttu-id="a1efd-157">Umożliwia włączenie śledzenia</span><span class="sxs-lookup"><span data-stu-id="a1efd-157">Enables tracing</span></span>|  
    ||<span data-ttu-id="a1efd-158">**#undef TRACE**</span><span class="sxs-lookup"><span data-stu-id="a1efd-158">**#undef TRACE**</span></span>|<span data-ttu-id="a1efd-159">Wyłącza śledzenie</span><span class="sxs-lookup"><span data-stu-id="a1efd-159">Disables tracing</span></span>|  
    ||<span data-ttu-id="a1efd-160">**#define debugowania**</span><span class="sxs-lookup"><span data-stu-id="a1efd-160">**#define DEBUG**</span></span>|<span data-ttu-id="a1efd-161">Włącza debugowanie</span><span class="sxs-lookup"><span data-stu-id="a1efd-161">Enables debugging</span></span>|  
    ||<span data-ttu-id="a1efd-162">**#undef DEBUG**</span><span class="sxs-lookup"><span data-stu-id="a1efd-162">**#undef DEBUG**</span></span>|<span data-ttu-id="a1efd-163">Wyłącza debugowanie</span><span class="sxs-lookup"><span data-stu-id="a1efd-163">Disables debugging</span></span>|  
  
### <a name="to-disable-tracing-or-debugging"></a><span data-ttu-id="a1efd-164">Aby wyłączyć śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="a1efd-164">To disable tracing or debugging</span></span>  
  
<span data-ttu-id="a1efd-165">Usuń dyrektywy kompilatora z kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="a1efd-165">Delete the compiler directive from your source code.</span></span>  
  
<span data-ttu-id="a1efd-166">\- lub —</span><span class="sxs-lookup"><span data-stu-id="a1efd-166">\- or -</span></span>  
  
<span data-ttu-id="a1efd-167">Dyrektywy kompilatora w komentarz.</span><span class="sxs-lookup"><span data-stu-id="a1efd-167">Comment out the compiler directive.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1efd-168">Gdy wszystko jest gotowe do kompilowania, możesz wybrać **kompilacji** z **kompilacji** menu lub użyć metody wiersza polecenia, ale bez wpisywania **d:** do definiowania warunkowe symbole kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a1efd-168">When you are ready to compile, you can either choose **Build** from the **Build** menu, or use the command line method but without typing the **d:** to define conditional compilation symbols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1efd-169">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1efd-169">See also</span></span>

- [<span data-ttu-id="a1efd-170">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="a1efd-170">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="a1efd-171">Instrukcje: Tworzenie, inicjowanie i konfigurowanie przełączników śledzenia</span><span class="sxs-lookup"><span data-stu-id="a1efd-171">How to: Create, Initialize and Configure Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="a1efd-172">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="a1efd-172">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="a1efd-173">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="a1efd-173">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [<span data-ttu-id="a1efd-174">Instrukcje: Dodawanie instrukcji śledzenia do kodu aplikacji</span><span class="sxs-lookup"><span data-stu-id="a1efd-174">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="a1efd-175">Instrukcje: Ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a1efd-175">How to: Set Environment Variables for the Visual Studio Command Line</span></span>](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [<span data-ttu-id="a1efd-176">Instrukcje: wywoływanie kompilatora z wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="a1efd-176">How to: Invoke the Command-Line Compiler</span></span>](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
