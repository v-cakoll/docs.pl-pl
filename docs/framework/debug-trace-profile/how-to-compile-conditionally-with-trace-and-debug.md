---
title: 'Porady: kompilowanie warunkowe ze śledzeniem i debugowaniem'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- trace compiler options
- trace statements
- compiling source code, trace statements
- tracing [.NET Framework], enabling or disabling
- tracing [.NET Framework], compiling conditionally
- TRACE directive
- conditional compilation, tracing code
ms.assetid: 56d051c3-012c-42c1-9a58-7270edc624aa
caps.latest.revision: ''
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5e590888a56ed4c325e89eb828349f4f289815cd
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a><span data-ttu-id="f5c0a-102">Porady: kompilowanie warunkowe ze śledzeniem i debugowaniem</span><span class="sxs-lookup"><span data-stu-id="f5c0a-102">How to: Compile Conditionally with Trace and Debug</span></span>
<span data-ttu-id="f5c0a-103">Podczas debugowania aplikacji podczas tworzenia Twojej śledzenia i dane wyjściowe debugowania Przejdź w oknie danych wyjściowych w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-103">While you are debugging an application during development, both your tracing and debugging output go to the Output window in Visual Studio.</span></span> <span data-ttu-id="f5c0a-104">Jednak aby włączyć funkcje śledzenia do wdrożonej aplikacji, należy skompilować instrumentowanej aplikacji przy użyciu **śledzenia** dyrektywy kompilatora włączone.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-104">However, to include tracing features in a deployed application, you must compile your instrumented applications with the **TRACE** compiler directive enabled.</span></span> <span data-ttu-id="f5c0a-105">Dzięki temu kod śledzenia ma być kompilowana w wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-105">This allows tracing code to be compiled into the release version of your application.</span></span> <span data-ttu-id="f5c0a-106">Jeśli nie włączysz **śledzenia** dyrektywy, wszystkie kod śledzenia jest ignorowany podczas kompilacji i nie jest objęta kodu wykonywalnego, który zostanie wdrożony.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-106">If you do not enable the **TRACE** directive, all tracing code is ignored during compilation and is not included in the executable code that you will deploy.</span></span>  
  
 <span data-ttu-id="f5c0a-107">Śledzenie i debugowanie metody skojarzony atrybuty warunkowe.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-107">Both the tracing and debugging methods have associated conditional attributes.</span></span> <span data-ttu-id="f5c0a-108">Na przykład, jeśli atrybut warunkowej dla śledzenia jest **true**, wszystkie instrukcje śledzenia znajdują się w obrębie zestawu (pliku skompilowanego .exe lub .dll); Jeśli **śledzenia** atrybut conditional jest **false**, instrukcji śledzenia nie są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-108">For example, if the conditional attribute for tracing is **true**, all trace statements are included within an assembly (a compiled .exe file or .dll); if the **Trace** conditional attribute is **false**, the trace statements are not included.</span></span>  
  
 <span data-ttu-id="f5c0a-109">Można mieć **śledzenia** lub **debugowania** atrybut conditional włączone dla kompilacji, lub obie lub nie.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-109">You can have either the **Trace** or **Debug** conditional attribute turned on for a build, or both, or neither.</span></span> <span data-ttu-id="f5c0a-110">W związku z tym istnieją cztery typy kompilacji: **debugowania**, **śledzenia**, zarówno lub nie.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-110">Thus, there are four types of build: **Debug**, **Trace**, both, or neither.</span></span> <span data-ttu-id="f5c0a-111">Niektóre kompilacjami wydania w przypadku wdrożenia produkcyjnego może zawierać ani; kompilacje debugowania najbardziej zawiera oba.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-111">Some release builds for production deployment might contain neither; most debugging builds contain both.</span></span>  
  
 <span data-ttu-id="f5c0a-112">Ustawienia kompilatora dla aplikacji na kilka sposobów:</span><span class="sxs-lookup"><span data-stu-id="f5c0a-112">You can specify the compiler settings for your application in several ways:</span></span>  
  
-   <span data-ttu-id="f5c0a-113">Strony właściwości</span><span class="sxs-lookup"><span data-stu-id="f5c0a-113">The property pages</span></span>  
  
-   <span data-ttu-id="f5c0a-114">W wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="f5c0a-114">The command line</span></span>  
  
-   <span data-ttu-id="f5c0a-115">**#CONST** (w języku Visual Basic) i **#define** (dla C#)</span><span class="sxs-lookup"><span data-stu-id="f5c0a-115">**#CONST** (for Visual Basic) and **#define** (for C#)</span></span>  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a><span data-ttu-id="f5c0a-116">Aby zmienić ustawienia kompilacji z okna dialogowego strony właściwości</span><span class="sxs-lookup"><span data-stu-id="f5c0a-116">To change compile settings from the property pages dialog box</span></span>  
  
1.  <span data-ttu-id="f5c0a-117">Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-117">Right-click the project node in **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="f5c0a-118">Wybierz **właściwości** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-118">Choose **Properties** from the shortcut menu.</span></span>  
  
    -   <span data-ttu-id="f5c0a-119">W języku Visual Basic, kliknij przycisk **skompilować** w okienku po lewej stronie właściwości, a następnie kliknij **zaawansowane opcje kompilacji** przycisk, aby wyświetlić **Zaawansowane ustawienia kompilatora**okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-119">In Visual Basic, click the **Compile** tab in the left pane of the property page, then click the **Advanced Compile Options** button to display the **Advanced Compiler Settings** dialog box.</span></span> <span data-ttu-id="f5c0a-120">Zaznacz pola wyboru dla ustawienia kompilatora, który chcesz włączyć.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-120">Select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="f5c0a-121">Wyczyść pola wyboru dla ustawień, które mają zostać wyłączone.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-121">Clear the check boxes for settings you want to disable.</span></span>  
  
    -   <span data-ttu-id="f5c0a-122">W języku C#, kliknij przycisk **kompilacji** w okienku po lewej stronie właściwości, a następnie zaznacz pola wyboru Ustawienia kompilatora, aby umożliwić.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-122">In C#, click the **Build** tab in the left pane of the property page, then select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="f5c0a-123">Wyczyść pola wyboru dla ustawień, które mają zostać wyłączone.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-123">Clear the check boxes for settings you want to disable.</span></span>  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a><span data-ttu-id="f5c0a-124">Aby skompilować kod instrumentowane przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="f5c0a-124">To compile instrumented code using the command line</span></span>  
  
1.  <span data-ttu-id="f5c0a-125">Ustawiona przełącznik warunkowego kompilatora w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-125">Set a conditional compiler switch on the command line.</span></span> <span data-ttu-id="f5c0a-126">Kompilator będzie zawierać śledzenia lub debugowania kodu w pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-126">The compiler will include trace or debug code in the executable.</span></span>  
  
     <span data-ttu-id="f5c0a-127">Na przykład następująca instrukcja kompilatora wprowadzona w wierszu polecenia obejmują kod śledzenia w skompilowanych pliku wykonywalnego:</span><span class="sxs-lookup"><span data-stu-id="f5c0a-127">For example, the following compiler instruction entered on the command line would include your tracing code in a compiled executable:</span></span>  
  
     <span data-ttu-id="f5c0a-128">W języku Visual Basic: **vbc-r:System.dll -d: śledzenia = TRUE -d: DEBUG = FALSE MyApplication.vb**</span><span class="sxs-lookup"><span data-stu-id="f5c0a-128">For Visual Basic: **vbc -r:System.dll -d:TRACE=TRUE -d:DEBUG=FALSE MyApplication.vb**</span></span>  
  
     <span data-ttu-id="f5c0a-129">Język C#: **csc-r:System.dll -d: śledzenia -d: DEBUG = FALSE MyApplication.cs**</span><span class="sxs-lookup"><span data-stu-id="f5c0a-129">For C#: **csc -r:System.dll -d:TRACE -d:DEBUG=FALSE MyApplication.cs**</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="f5c0a-130">Aby skompilować więcej niż jeden plik aplikacji, pozostaw puste miejsce między nazwami plików, na przykład **MyApplication1.vb MyApplication2.vb MyApplication3.vb** lub **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-130">To compile more than one application file, leave a blank space between the file names, for example, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** or **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span></span>  
  
     <span data-ttu-id="f5c0a-131">Znaczenie dyrektywy kompilacja warunkowa używane w powyższych przykładach wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="f5c0a-131">The meaning of the conditional-compilation directives used in the above examples is as follows:</span></span>  
  
    |<span data-ttu-id="f5c0a-132">Dyrektywy</span><span class="sxs-lookup"><span data-stu-id="f5c0a-132">Directive</span></span>|<span data-ttu-id="f5c0a-133">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f5c0a-133">Meaning</span></span>|  
    |---------------|-------------|  
    |`vbc`|<span data-ttu-id="f5c0a-134">kompilator Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f5c0a-134">Visual Basic compiler</span></span>|  
    |`csc`|<span data-ttu-id="f5c0a-135">Kompilator języka C#</span><span class="sxs-lookup"><span data-stu-id="f5c0a-135">C# compiler</span></span>|  
    |`-r:`|<span data-ttu-id="f5c0a-136">Odwołuje się do zestawu zewnętrzne (plik EXE lub DLL)</span><span class="sxs-lookup"><span data-stu-id="f5c0a-136">References an external assembly (EXE or DLL)</span></span>|  
    |`-d:`|<span data-ttu-id="f5c0a-137">Określa symbol kompilacji warunkowej</span><span class="sxs-lookup"><span data-stu-id="f5c0a-137">Defines a conditional compilation symbol</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="f5c0a-138">Należy pisowni śledzenia i debugowania z wielkich liter.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-138">You must spell TRACE or DEBUG with uppercase letters.</span></span> <span data-ttu-id="f5c0a-139">Aby uzyskać więcej informacji na temat poleceń kompilacji warunkowej, wprowadź `vbc /?` (w języku Visual Basic) lub `csc /?` (dla C#) w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-139">For more information about the conditional compilation commands, enter `vbc /?` (for Visual Basic) or `csc /?` (for C#) at the command prompt.</span></span> <span data-ttu-id="f5c0a-140">Aby uzyskać więcej informacji, zobacz [tworzenie z wiersza polecenia](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) lub [wywoływanie kompilatora wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="f5c0a-140">For more information, see [Building from the Command Line](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) or [Invoking the Command-Line Compiler](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span></span>  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a><span data-ttu-id="f5c0a-141">Do wykonania przy użyciu kompilacja warunkowa #CONST lub #define</span><span class="sxs-lookup"><span data-stu-id="f5c0a-141">To perform conditional compilation using #CONST or #define</span></span>  
  
1.  <span data-ttu-id="f5c0a-142">Wpisz odpowiedniej instrukcji języka programowania, w górnej części pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-142">Type the appropriate statement for your programming language at the top of the source code file.</span></span>  
  
    |<span data-ttu-id="f5c0a-143">Język</span><span class="sxs-lookup"><span data-stu-id="f5c0a-143">Language</span></span>|<span data-ttu-id="f5c0a-144">Instrukcja</span><span class="sxs-lookup"><span data-stu-id="f5c0a-144">Statement</span></span>|<span data-ttu-id="f5c0a-145">Wynik</span><span class="sxs-lookup"><span data-stu-id="f5c0a-145">Result</span></span>|  
    |--------------|---------------|------------|  
    |<span data-ttu-id="f5c0a-146">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="f5c0a-146">**Visual Basic**</span></span>|<span data-ttu-id="f5c0a-147">**#CONST śledzenia = true**</span><span class="sxs-lookup"><span data-stu-id="f5c0a-147">**#CONST TRACE = true**</span></span>|<span data-ttu-id="f5c0a-148">Umożliwia śledzenie</span><span class="sxs-lookup"><span data-stu-id="f5c0a-148">Enables tracing</span></span>|  
    ||<span data-ttu-id="f5c0a-149">**#CONST śledzenia = false**</span><span class="sxs-lookup"><span data-stu-id="f5c0a-149">**#CONST TRACE = false**</span></span>|<span data-ttu-id="f5c0a-150">Wyłącza śledzenie</span><span class="sxs-lookup"><span data-stu-id="f5c0a-150">Disables tracing</span></span>|  
    ||<span data-ttu-id="f5c0a-151">**#CONST debugowania = true**</span><span class="sxs-lookup"><span data-stu-id="f5c0a-151">**#CONST DEBUG = true**</span></span>|<span data-ttu-id="f5c0a-152">Włącza debugowanie</span><span class="sxs-lookup"><span data-stu-id="f5c0a-152">Enables debugging</span></span>|  
    ||<span data-ttu-id="f5c0a-153">**#CONST debugowania = false**</span><span class="sxs-lookup"><span data-stu-id="f5c0a-153">**#CONST DEBUG = false**</span></span>|<span data-ttu-id="f5c0a-154">Wyłącza debugowanie</span><span class="sxs-lookup"><span data-stu-id="f5c0a-154">Disables debugging</span></span>|  
    |<span data-ttu-id="f5c0a-155">**C#**</span><span class="sxs-lookup"><span data-stu-id="f5c0a-155">**C#**</span></span>|<span data-ttu-id="f5c0a-156">**#define śledzenia**</span><span class="sxs-lookup"><span data-stu-id="f5c0a-156">**#define TRACE**</span></span>|<span data-ttu-id="f5c0a-157">Umożliwia śledzenie</span><span class="sxs-lookup"><span data-stu-id="f5c0a-157">Enables tracing</span></span>|  
    ||<span data-ttu-id="f5c0a-158">**#undef śledzenia**</span><span class="sxs-lookup"><span data-stu-id="f5c0a-158">**#undef TRACE**</span></span>|<span data-ttu-id="f5c0a-159">Wyłącza śledzenie</span><span class="sxs-lookup"><span data-stu-id="f5c0a-159">Disables tracing</span></span>|  
    ||<span data-ttu-id="f5c0a-160">**#define debugowania**</span><span class="sxs-lookup"><span data-stu-id="f5c0a-160">**#define DEBUG**</span></span>|<span data-ttu-id="f5c0a-161">Włącza debugowanie</span><span class="sxs-lookup"><span data-stu-id="f5c0a-161">Enables debugging</span></span>|  
    ||<span data-ttu-id="f5c0a-162">**#undef debugowania**</span><span class="sxs-lookup"><span data-stu-id="f5c0a-162">**#undef DEBUG**</span></span>|<span data-ttu-id="f5c0a-163">Wyłącza debugowanie</span><span class="sxs-lookup"><span data-stu-id="f5c0a-163">Disables debugging</span></span>|  
  
### <a name="to-disable-tracing-or-debugging"></a><span data-ttu-id="f5c0a-164">Aby wyłączyć śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="f5c0a-164">To disable tracing or debugging</span></span>  
  
<span data-ttu-id="f5c0a-165">Usuń dyrektywy kompilatora w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-165">Delete the compiler directive from your source code.</span></span>  
  
<span data-ttu-id="f5c0a-166">\- lub -</span><span class="sxs-lookup"><span data-stu-id="f5c0a-166">\- or -</span></span>  
  
<span data-ttu-id="f5c0a-167">Komentarz dyrektywy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-167">Comment out the compiler directive.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5c0a-168">Gdy wszystko będzie gotowe skompilować, można wybrać **kompilacji** z **kompilacji** menu, lub użyj metody wiersza polecenia, ale bez wpisywania **d:** do definiowania warunkowe symbole kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f5c0a-168">When you are ready to compile, you can either choose **Build** from the **Build** menu, or use the command line method but without typing the **d:** to define conditional compilation symbols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5c0a-169">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5c0a-169">See Also</span></span>  
 [<span data-ttu-id="f5c0a-170">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="f5c0a-170">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [<span data-ttu-id="f5c0a-171">Instrukcje: tworzenie, inicjowanie i konfigurowanie przełączników śledzenia</span><span class="sxs-lookup"><span data-stu-id="f5c0a-171">How to: Create, Initialize and Configure Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)  
 [<span data-ttu-id="f5c0a-172">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="f5c0a-172">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [<span data-ttu-id="f5c0a-173">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="f5c0a-173">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)  
 [<span data-ttu-id="f5c0a-174">Instrukcje: Dodawanie instrukcji śledzenia do kodu aplikacji</span><span class="sxs-lookup"><span data-stu-id="f5c0a-174">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [<span data-ttu-id="f5c0a-175">Instrukcje: ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f5c0a-175">How to: Set Environment Variables for the Visual Studio Command Line</span></span>](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)  
 [<span data-ttu-id="f5c0a-176">Instrukcje: wywoływanie kompilatora z wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="f5c0a-176">How to: Invoke the Command-Line Compiler</span></span>](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
