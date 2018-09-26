---
title: -errorreport (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: dcbb9467da87a82147176bb0feb00383aff2c77f
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47156523"
---
# <a name="-errorreport-c-compiler-options"></a><span data-ttu-id="fa4c5-102">-errorreport (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="fa4c5-102">-errorreport (C# Compiler Options)</span></span>
<span data-ttu-id="fa4c5-103">Ta opcja zapewnia wygodny sposób, aby zgłosić błąd wewnętrzny kompilatora C# do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fa4c5-103">This option provides a convenient way to report a C# internal compiler error to Microsoft.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa4c5-104">W systemach Windows Vista i systemu Windows Server 2008 ustawienia raportowania błędów, które dla programu Visual Studio nie zastępują ustawienia wprowadzone za pośrednictwem raportowania błędów Windows (WER).</span><span class="sxs-lookup"><span data-stu-id="fa4c5-104">On Windows Vista and Windows Server 2008, the error reporting settings that you make for Visual Studio do not override the settings made through Windows Error Reporting (WER).</span></span> <span data-ttu-id="fa4c5-105">Ustawienia raportowania błędów systemu Windows zawsze pierwszeństwo ustawienia raportowania błędów programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fa4c5-105">WER settings always take precedence over Visual Studio error reporting settings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa4c5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="fa4c5-106">Syntax</span></span>  
  
```console  
-errorreport:{ none | prompt | queue | send }  
```  
  
## <a name="arguments"></a><span data-ttu-id="fa4c5-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="fa4c5-107">Arguments</span></span>  
 <span data-ttu-id="fa4c5-108">**Brak**</span><span class="sxs-lookup"><span data-stu-id="fa4c5-108">**none**</span></span>  
 <span data-ttu-id="fa4c5-109">Raporty o błędach wewnętrznych kompilatora nie będą zbierane ani wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fa4c5-109">Reports about internal compiler errors will not be collected or sent to Microsoft.</span></span>  
  
 <span data-ttu-id="fa4c5-110">**wiersz**</span><span class="sxs-lookup"><span data-stu-id="fa4c5-110">**prompt**</span></span>  
 <span data-ttu-id="fa4c5-111">Monituje o wysłanie raportu po pojawieniu się błędu wewnętrznego kompilatora.</span><span class="sxs-lookup"><span data-stu-id="fa4c5-111">Prompts you to send a report when you receive an internal compiler error.</span></span> <span data-ttu-id="fa4c5-112">**wiersz** jest domyślną kolekcją podczas kompilowania aplikacji w środowisku programistycznym.</span><span class="sxs-lookup"><span data-stu-id="fa4c5-112">**prompt** is the default when you compile an application in the development environment.</span></span>  
  
 <span data-ttu-id="fa4c5-113">**kolejki**</span><span class="sxs-lookup"><span data-stu-id="fa4c5-113">**queue**</span></span>  
 <span data-ttu-id="fa4c5-114">Kolejkuje raport o błędach.</span><span class="sxs-lookup"><span data-stu-id="fa4c5-114">Queues the error report.</span></span> <span data-ttu-id="fa4c5-115">Po zalogowaniu się przy użyciu poświadczeń administracyjnych może zgłaszać błędów od czasu ostatniego zalogowania się.</span><span class="sxs-lookup"><span data-stu-id="fa4c5-115">When you log on with administrative credentials, you can report any failures since the last time that you were logged on.</span></span> <span data-ttu-id="fa4c5-116">Użytkownik nie jest monitowany o wysłanie raportu błędów więcej niż raz na trzy dni.</span><span class="sxs-lookup"><span data-stu-id="fa4c5-116">You will not be prompted to send reports for failures more than once every three days.</span></span> <span data-ttu-id="fa4c5-117">**kolejka** jest domyślną kolekcją podczas kompilowania aplikacji w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="fa4c5-117">**queue** is the default when you compile an application at the command line.</span></span>  
  
 <span data-ttu-id="fa4c5-118">**Wyślij**</span><span class="sxs-lookup"><span data-stu-id="fa4c5-118">**send**</span></span>  
 <span data-ttu-id="fa4c5-119">Automatycznie wysyła raporty błędów wewnętrznych kompilatora do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fa4c5-119">Automatically sends reports of internal compiler errors to Microsoft.</span></span> <span data-ttu-id="fa4c5-120">Aby włączyć tę opcję, musisz najpierw wyrazić zgodę na zasady zbierania danych firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fa4c5-120">To enable this option, you must first agree to the Microsoft data collection policy.</span></span> <span data-ttu-id="fa4c5-121">Po raz pierwszy należy określić **- errorreport: wysyłanie** na komputerze, wiadomość kompilatora odniesie Cię do witryny sieci Web, która zawiera zasady zbierania danych firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fa4c5-121">The first time that you specify **-errorreport:send** on a computer, a compiler message will refer you to a Web site that contains the Microsoft data collection policy.</span></span>  
    
## <a name="remarks"></a><span data-ttu-id="fa4c5-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fa4c5-122">Remarks</span></span>  
 <span data-ttu-id="fa4c5-123">Wewnętrzny błąd kompilatora (ICE) wyniki, gdy kompilator nie może przetworzyć pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="fa4c5-123">An internal compiler error (ICE) results when the compiler cannot process a source code file.</span></span> <span data-ttu-id="fa4c5-124">W przypadku ICE kompilator nie generuje plik wyjściowy lub przydatne diagnostyki, która służy do poprawienia kodu.</span><span class="sxs-lookup"><span data-stu-id="fa4c5-124">When an ICE occurs, the compiler does not produce an output file or any useful diagnostic that you can use to fix your code.</span></span>  
  
 <span data-ttu-id="fa4c5-125">W poprzednich wersjach po odebraniu ICE było zachęcani do skontaktuj się z pomocą techniczną firmy Microsoft, aby zgłosić problem.</span><span class="sxs-lookup"><span data-stu-id="fa4c5-125">In previous releases, when you received an ICE, you were encouraged to contact Microsoft Product Support Services to report the problem.</span></span> <span data-ttu-id="fa4c5-126">Za pomocą **- errorreport**, możesz podać informacje ICE do zespołu języka Visual C#.</span><span class="sxs-lookup"><span data-stu-id="fa4c5-126">By using **-errorreport**, you can provide ICE information to the Visual C# team.</span></span> <span data-ttu-id="fa4c5-127">Twoje raporty o błędach może zwiększyć kompilatora w przyszłych wersjach.</span><span class="sxs-lookup"><span data-stu-id="fa4c5-127">Your error reports can help improve future compiler releases.</span></span>  
  
 <span data-ttu-id="fa4c5-128">Zdolność użytkownika do wysyłania raportów zależy od uprawnienia zasad komputera i użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fa4c5-128">A user's ability to send reports depends on computer and user policy permissions.</span></span>  
  
 <span data-ttu-id="fa4c5-129">Aby uzyskać więcej informacji na temat debugera błędów zobacz [opis odzyskiwania po awarii. Watson dla narzędzia Windows (Drwtsn32.exe)](https://support.microsoft.com/help/308538/description-of-the-dr--watson-for-windows-drwtsn32-exe-tool).</span><span class="sxs-lookup"><span data-stu-id="fa4c5-129">For more information about error debugger, see [Description of the Dr. Watson for Windows (Drwtsn32.exe) Tool](https://support.microsoft.com/help/308538/description-of-the-dr--watson-for-windows-drwtsn32-exe-tool).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="fa4c5-130">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fa4c5-130">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="fa4c5-131">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="fa4c5-131">Open the project's **Properties** page.</span></span> <span data-ttu-id="fa4c5-132">Aby uzyskać więcej informacji, zobacz [Stroka kompilacji, Projektant projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="fa4c5-132">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="fa4c5-133">Kliknij przycisk **kompilacji** stronę właściwości.</span><span class="sxs-lookup"><span data-stu-id="fa4c5-133">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="fa4c5-134">Kliknij przycisk **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="fa4c5-134">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="fa4c5-135">Modyfikowanie **raportowanie wewnętrznych błędów kompilatora** właściwości.</span><span class="sxs-lookup"><span data-stu-id="fa4c5-135">Modify the **Internal Compiler Error Reporting** property.</span></span>  
  
 <span data-ttu-id="fa4c5-136">Aby dowiedzieć się, jak programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span><span class="sxs-lookup"><span data-stu-id="fa4c5-136">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa4c5-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa4c5-137">See Also</span></span>  

- [<span data-ttu-id="fa4c5-138">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="fa4c5-138">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
