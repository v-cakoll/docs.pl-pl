---
title: -errorreport (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: dc876f609643b7112c0f54574bd202c7c19cb119
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924770"
---
# <a name="-errorreport-c-compiler-options"></a><span data-ttu-id="9fa88-102">-errorreport (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="9fa88-102">-errorreport (C# Compiler Options)</span></span>
<span data-ttu-id="9fa88-103">Ta opcja zapewnia wygodny sposób zgłaszania C# wewnętrznego błędu kompilatora firmie Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9fa88-103">This option provides a convenient way to report a C# internal compiler error to Microsoft.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9fa88-104">W systemach Windows Vista i Windows Server 2008 ustawienia raportowania błędów wprowadzone dla programu Visual Studio nie przesłaniają ustawień wprowadzonych za pomocą Raportowanie błędów systemu Windows (raportowanie błędów).</span><span class="sxs-lookup"><span data-stu-id="9fa88-104">On Windows Vista and Windows Server 2008, the error reporting settings that you make for Visual Studio do not override the settings made through Windows Error Reporting (WER).</span></span> <span data-ttu-id="9fa88-105">Ustawienia raportowanie błędów systemu Windows zawsze mają pierwszeństwo przed ustawieniami raportowania błędów programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9fa88-105">WER settings always take precedence over Visual Studio error reporting settings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fa88-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="9fa88-106">Syntax</span></span>  
  
```console  
-errorreport:{ none | prompt | queue | send }  
```  
  
## <a name="arguments"></a><span data-ttu-id="9fa88-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9fa88-107">Arguments</span></span>  
 <span data-ttu-id="9fa88-108">**dawaj**</span><span class="sxs-lookup"><span data-stu-id="9fa88-108">**none**</span></span>  
 <span data-ttu-id="9fa88-109">Raporty o błędach wewnętrznych kompilatora nie będą zbierane ani wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9fa88-109">Reports about internal compiler errors will not be collected or sent to Microsoft.</span></span>  
  
 <span data-ttu-id="9fa88-110">**pytać**</span><span class="sxs-lookup"><span data-stu-id="9fa88-110">**prompt**</span></span>  
 <span data-ttu-id="9fa88-111">Wyświetlany jest komunikat z prośbą o wysłanie raportu po otrzymaniu wewnętrznego błędu kompilatora.</span><span class="sxs-lookup"><span data-stu-id="9fa88-111">Prompts you to send a report when you receive an internal compiler error.</span></span> <span data-ttu-id="9fa88-112">**monit** jest wartością domyślną podczas kompilowania aplikacji w środowisku deweloperskim.</span><span class="sxs-lookup"><span data-stu-id="9fa88-112">**prompt** is the default when you compile an application in the development environment.</span></span>  
  
 <span data-ttu-id="9fa88-113">**niej**</span><span class="sxs-lookup"><span data-stu-id="9fa88-113">**queue**</span></span>  
 <span data-ttu-id="9fa88-114">Kolejkuje raport o błędach.</span><span class="sxs-lookup"><span data-stu-id="9fa88-114">Queues the error report.</span></span> <span data-ttu-id="9fa88-115">Po zalogowaniu się przy użyciu poświadczeń administracyjnych można zgłosić błędy od czasu ostatniego zalogowania.</span><span class="sxs-lookup"><span data-stu-id="9fa88-115">When you log on with administrative credentials, you can report any failures since the last time that you were logged on.</span></span> <span data-ttu-id="9fa88-116">Nie zostanie wyświetlony monit o wysłanie raportów pod kątem błędów więcej niż raz na trzy dni.</span><span class="sxs-lookup"><span data-stu-id="9fa88-116">You will not be prompted to send reports for failures more than once every three days.</span></span> <span data-ttu-id="9fa88-117">**Kolejka** jest wartością domyślną podczas kompilowania aplikacji w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="9fa88-117">**queue** is the default when you compile an application at the command line.</span></span>  
  
 <span data-ttu-id="9fa88-118">**Wyślij**</span><span class="sxs-lookup"><span data-stu-id="9fa88-118">**send**</span></span>  
 <span data-ttu-id="9fa88-119">Automatycznie wysyła raporty wewnętrznych błędów kompilatora do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9fa88-119">Automatically sends reports of internal compiler errors to Microsoft.</span></span> <span data-ttu-id="9fa88-120">Aby włączyć tę opcję, musisz najpierw wyrazić zgodę na zasady zbierania danych firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9fa88-120">To enable this option, you must first agree to the Microsoft data collection policy.</span></span> <span data-ttu-id="9fa88-121">Podczas pierwszego określania **errorReport: Send** na komputerze komunikat kompilatora odwołuje się do witryny sieci Web zawierającej zasady zbierania danych firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9fa88-121">The first time that you specify **-errorreport:send** on a computer, a compiler message will refer you to a Web site that contains the Microsoft data collection policy.</span></span>  
    
## <a name="remarks"></a><span data-ttu-id="9fa88-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9fa88-122">Remarks</span></span>  
 <span data-ttu-id="9fa88-123">Wewnętrzny błąd kompilatora (lodem) powstaje, gdy kompilator nie może przetworzyć pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="9fa88-123">An internal compiler error (ICE) results when the compiler cannot process a source code file.</span></span> <span data-ttu-id="9fa88-124">W przypadku wystąpienia lodu kompilator nie tworzy pliku wyjściowego ani żadnej przydatnej diagnostyki, której można użyć do naprawienia kodu.</span><span class="sxs-lookup"><span data-stu-id="9fa88-124">When an ICE occurs, the compiler does not produce an output file or any useful diagnostic that you can use to fix your code.</span></span>  
  
 <span data-ttu-id="9fa88-125">W poprzednich wersjach, gdy otrzymasz lód, zachęcamy do skontaktowania się z pomocą techniczną firmy Microsoft w celu zgłoszenia problemu.</span><span class="sxs-lookup"><span data-stu-id="9fa88-125">In previous releases, when you received an ICE, you were encouraged to contact Microsoft Product Support Services to report the problem.</span></span> <span data-ttu-id="9fa88-126">Za pomocą **-errorreport**, można dostarczyć informacje o lodem do zespołu wizualnego C# .</span><span class="sxs-lookup"><span data-stu-id="9fa88-126">By using **-errorreport**, you can provide ICE information to the Visual C# team.</span></span> <span data-ttu-id="9fa88-127">Raporty o błędach mogą pomóc w ulepszaniu przyszłych wersji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="9fa88-127">Your error reports can help improve future compiler releases.</span></span>  
  
 <span data-ttu-id="9fa88-128">Możliwość wysyłania raportów zależy od uprawnień komputera i użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9fa88-128">A user's ability to send reports depends on computer and user policy permissions.</span></span>  
  
 <span data-ttu-id="9fa88-129">Aby uzyskać więcej informacji o debugerze błędów [, zobacz Opis narzędzia Dr. Narzędzie](https://support.microsoft.com/help/308538/description-of-the-dr--watson-for-windows-drwtsn32-exe-tool)Watson dla systemu Windows (Drwtsn32. exe).</span><span class="sxs-lookup"><span data-stu-id="9fa88-129">For more information about error debugger, see [Description of the Dr. Watson for Windows (Drwtsn32.exe) Tool](https://support.microsoft.com/help/308538/description-of-the-dr--watson-for-windows-drwtsn32-exe-tool).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="9fa88-130">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9fa88-130">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="9fa88-131">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="9fa88-131">Open the project's **Properties** page.</span></span> <span data-ttu-id="9fa88-132">Aby uzyskać więcej informacji, zobacz [stronę Kompilacja, Projektant projektuC#()](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="9fa88-132">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="9fa88-133">Kliknij stronę właściwości **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="9fa88-133">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="9fa88-134">Kliknij przycisk **Zaawansowane** .</span><span class="sxs-lookup"><span data-stu-id="9fa88-134">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="9fa88-135">Zmodyfikuj właściwość **wewnętrznego raportowania błędów kompilatora** .</span><span class="sxs-lookup"><span data-stu-id="9fa88-135">Modify the **Internal Compiler Error Reporting** property.</span></span>  
  
 <span data-ttu-id="9fa88-136">Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>tę opcję kompilatora, zobacz.</span><span class="sxs-lookup"><span data-stu-id="9fa88-136">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fa88-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9fa88-137">See also</span></span>

- [<span data-ttu-id="9fa88-138">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="9fa88-138">C# Compiler Options</span></span>](./index.md)
