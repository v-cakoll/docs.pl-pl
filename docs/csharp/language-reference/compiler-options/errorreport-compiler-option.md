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
ms.openlocfilehash: 52b58aac5e82d4228dfda9c4d77c1d1c5de3e0cd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253892"
---
# <a name="-errorreport-c-compiler-options"></a><span data-ttu-id="42129-102">-errorreport (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="42129-102">-errorreport (C# Compiler Options)</span></span>
<span data-ttu-id="42129-103">Ta opcja zapewnia wygodny sposób zgłaszania C# wewnętrznego błędu kompilatora firmie Microsoft.</span><span class="sxs-lookup"><span data-stu-id="42129-103">This option provides a convenient way to report a C# internal compiler error to Microsoft.</span></span>

> [!NOTE]
> <span data-ttu-id="42129-104">W systemach Windows Vista i Windows Server 2008 ustawienia raportowania błędów wprowadzone dla programu Visual Studio nie przesłaniają ustawień wprowadzonych za pomocą Raportowanie błędów systemu Windows (raportowanie błędów).</span><span class="sxs-lookup"><span data-stu-id="42129-104">On Windows Vista and Windows Server 2008, the error reporting settings that you make for Visual Studio do not override the settings made through Windows Error Reporting (WER).</span></span> <span data-ttu-id="42129-105">Ustawienia raportowanie błędów systemu Windows zawsze mają pierwszeństwo przed ustawieniami raportowania błędów programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="42129-105">WER settings always take precedence over Visual Studio error reporting settings.</span></span>

## <a name="syntax"></a><span data-ttu-id="42129-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="42129-106">Syntax</span></span>

```console
-errorreport:{ none | prompt | queue | send }
```

## <a name="arguments"></a><span data-ttu-id="42129-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="42129-107">Arguments</span></span>
 <span data-ttu-id="42129-108">**dawaj**</span><span class="sxs-lookup"><span data-stu-id="42129-108">**none**</span></span>  
 <span data-ttu-id="42129-109">Raporty o błędach wewnętrznych kompilatora nie będą zbierane ani wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="42129-109">Reports about internal compiler errors will not be collected or sent to Microsoft.</span></span>

 <span data-ttu-id="42129-110">**Monituj** Wyświetlany jest komunikat z prośbą o wysłanie raportu po otrzymaniu wewnętrznego błędu kompilatora.</span><span class="sxs-lookup"><span data-stu-id="42129-110">**prompt** Prompts you to send a report when you receive an internal compiler error.</span></span> <span data-ttu-id="42129-111">**monit** jest wartością domyślną podczas kompilowania aplikacji w środowisku deweloperskim.</span><span class="sxs-lookup"><span data-stu-id="42129-111">**prompt** is the default when you compile an application in the development environment.</span></span>

 <span data-ttu-id="42129-112">**Kolejka** Kolejkuje raport o błędach.</span><span class="sxs-lookup"><span data-stu-id="42129-112">**queue** Queues the error report.</span></span> <span data-ttu-id="42129-113">Po zalogowaniu się przy użyciu poświadczeń administracyjnych można zgłosić błędy od czasu ostatniego zalogowania.</span><span class="sxs-lookup"><span data-stu-id="42129-113">When you log on with administrative credentials, you can report any failures since the last time that you were logged on.</span></span> <span data-ttu-id="42129-114">Nie zostanie wyświetlony monit o wysłanie raportów pod kątem błędów więcej niż raz na trzy dni.</span><span class="sxs-lookup"><span data-stu-id="42129-114">You will not be prompted to send reports for failures more than once every three days.</span></span> <span data-ttu-id="42129-115">**Kolejka** jest wartością domyślną podczas kompilowania aplikacji w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="42129-115">**queue** is the default when you compile an application at the command line.</span></span>

 <span data-ttu-id="42129-116">**Wyślij** Automatycznie wysyła raporty wewnętrznych błędów kompilatora do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="42129-116">**send** Automatically sends reports of internal compiler errors to Microsoft.</span></span> <span data-ttu-id="42129-117">Aby włączyć tę opcję, musisz najpierw wyrazić zgodę na zasady zbierania danych firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="42129-117">To enable this option, you must first agree to the Microsoft data collection policy.</span></span> <span data-ttu-id="42129-118">Podczas pierwszego określania **errorReport: Send** na komputerze komunikat kompilatora odwołuje się do witryny sieci Web zawierającej zasady zbierania danych firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="42129-118">The first time that you specify **-errorreport:send** on a computer, a compiler message will refer you to a Web site that contains the Microsoft data collection policy.</span></span>

## <a name="remarks"></a><span data-ttu-id="42129-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="42129-119">Remarks</span></span>
 <span data-ttu-id="42129-120">Wewnętrzny błąd kompilatora (lodem) powstaje, gdy kompilator nie może przetworzyć pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="42129-120">An internal compiler error (ICE) results when the compiler cannot process a source code file.</span></span> <span data-ttu-id="42129-121">W przypadku wystąpienia lodu kompilator nie tworzy pliku wyjściowego ani żadnej przydatnej diagnostyki, której można użyć do naprawienia kodu.</span><span class="sxs-lookup"><span data-stu-id="42129-121">When an ICE occurs, the compiler does not produce an output file or any useful diagnostic that you can use to fix your code.</span></span>

 <span data-ttu-id="42129-122">W poprzednich wersjach, gdy otrzymasz lód, zachęcamy do skontaktowania się z pomocą techniczną firmy Microsoft w celu zgłoszenia problemu.</span><span class="sxs-lookup"><span data-stu-id="42129-122">In previous releases, when you received an ICE, you were encouraged to contact Microsoft Product Support Services to report the problem.</span></span> <span data-ttu-id="42129-123">Za pomocą **-errorreport**, można dostarczyć informacje o lodem do zespołu wizualnego C# .</span><span class="sxs-lookup"><span data-stu-id="42129-123">By using **-errorreport**, you can provide ICE information to the Visual C# team.</span></span> <span data-ttu-id="42129-124">Raporty o błędach mogą pomóc w ulepszaniu przyszłych wersji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="42129-124">Your error reports can help improve future compiler releases.</span></span>

 <span data-ttu-id="42129-125">Możliwość wysyłania raportów zależy od uprawnień komputera i użytkownika.</span><span class="sxs-lookup"><span data-stu-id="42129-125">A user's ability to send reports depends on computer and user policy permissions.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="42129-126">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="42129-126">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="42129-127">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="42129-127">Open the project's **Properties** page.</span></span> <span data-ttu-id="42129-128">Aby uzyskać więcej informacji, zobacz [stronę Kompilacja, Projektant projektuC#()](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="42129-128">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>

2. <span data-ttu-id="42129-129">Kliknij stronę właściwości **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="42129-129">Click the **Build** property page.</span></span>

3. <span data-ttu-id="42129-130">Kliknij przycisk **Zaawansowane** .</span><span class="sxs-lookup"><span data-stu-id="42129-130">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="42129-131">Zmodyfikuj właściwość **wewnętrznego raportowania błędów kompilatora** .</span><span class="sxs-lookup"><span data-stu-id="42129-131">Modify the **Internal Compiler Error Reporting** property.</span></span>

 <span data-ttu-id="42129-132">Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>tę opcję kompilatora, zobacz.</span><span class="sxs-lookup"><span data-stu-id="42129-132">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="42129-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42129-133">See also</span></span>

- [<span data-ttu-id="42129-134">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="42129-134">C# Compiler Options</span></span>](./index.md)
