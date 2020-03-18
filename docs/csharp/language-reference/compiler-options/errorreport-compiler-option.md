---
title: -errorreport (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: 52b58aac5e82d4228dfda9c4d77c1d1c5de3e0cd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253892"
---
# <a name="-errorreport-c-compiler-options"></a><span data-ttu-id="9b5ad-102">-errorreport (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="9b5ad-102">-errorreport (C# Compiler Options)</span></span>
<span data-ttu-id="9b5ad-103">Ta opcja zapewnia wygodny sposób zgłaszania błędu kompilatora wewnętrznego języka C# do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9b5ad-103">This option provides a convenient way to report a C# internal compiler error to Microsoft.</span></span>

> [!NOTE]
> <span data-ttu-id="9b5ad-104">W systemach Windows Vista i Windows Server 2008 ustawienia raportowania błędów wprowadzone w programie Visual Studio nie zastępują ustawień dokonanych za pomocą raportowania błędów systemu Windows (WER).</span><span class="sxs-lookup"><span data-stu-id="9b5ad-104">On Windows Vista and Windows Server 2008, the error reporting settings that you make for Visual Studio do not override the settings made through Windows Error Reporting (WER).</span></span> <span data-ttu-id="9b5ad-105">Ustawienia wer zawsze mają pierwszeństwo przed ustawieniami raportowania błędów programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9b5ad-105">WER settings always take precedence over Visual Studio error reporting settings.</span></span>

## <a name="syntax"></a><span data-ttu-id="9b5ad-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="9b5ad-106">Syntax</span></span>

```console
-errorreport:{ none | prompt | queue | send }
```

## <a name="arguments"></a><span data-ttu-id="9b5ad-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9b5ad-107">Arguments</span></span>
 <span data-ttu-id="9b5ad-108">**brak**</span><span class="sxs-lookup"><span data-stu-id="9b5ad-108">**none**</span></span>  
 <span data-ttu-id="9b5ad-109">Raporty dotyczące błędów wewnętrznego kompilatora nie będą zbierane ani wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9b5ad-109">Reports about internal compiler errors will not be collected or sent to Microsoft.</span></span>

 <span data-ttu-id="9b5ad-110">**monit** Monituje o wysłanie raportu po otrzymaniu wewnętrznego błędu kompilatora.</span><span class="sxs-lookup"><span data-stu-id="9b5ad-110">**prompt** Prompts you to send a report when you receive an internal compiler error.</span></span> <span data-ttu-id="9b5ad-111">**monit** jest domyślnym podczas kompilowania aplikacji w środowisku programistycznym.</span><span class="sxs-lookup"><span data-stu-id="9b5ad-111">**prompt** is the default when you compile an application in the development environment.</span></span>

 <span data-ttu-id="9b5ad-112">**kolejka** Kolejkuje raport o błędach.</span><span class="sxs-lookup"><span data-stu-id="9b5ad-112">**queue** Queues the error report.</span></span> <span data-ttu-id="9b5ad-113">Po zalogowaniu się przy użyciu poświadczeń administracyjnych można zgłaszać wszelkie błędy od czasu ostatniego logowania.</span><span class="sxs-lookup"><span data-stu-id="9b5ad-113">When you log on with administrative credentials, you can report any failures since the last time that you were logged on.</span></span> <span data-ttu-id="9b5ad-114">Nie będzie wyświetlany monit o wysyłanie raportów o błędach więcej niż raz na trzy dni.</span><span class="sxs-lookup"><span data-stu-id="9b5ad-114">You will not be prompted to send reports for failures more than once every three days.</span></span> <span data-ttu-id="9b5ad-115">**kolejka** jest domyślna podczas kompilowania aplikacji w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="9b5ad-115">**queue** is the default when you compile an application at the command line.</span></span>

 <span data-ttu-id="9b5ad-116">**wyślij** Automatycznie wysyła raporty o wewnętrznych błędach kompilatora do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9b5ad-116">**send** Automatically sends reports of internal compiler errors to Microsoft.</span></span> <span data-ttu-id="9b5ad-117">Aby włączyć tę opcję, należy najpierw wyrazić zgodę na zasady zbierania danych firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9b5ad-117">To enable this option, you must first agree to the Microsoft data collection policy.</span></span> <span data-ttu-id="9b5ad-118">Przy pierwszym określeniu **-errorreport:send** na komputerze komunikat kompilatora będzie odwoływać się do witryny sieci Web zawierającej zasady zbierania danych firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9b5ad-118">The first time that you specify **-errorreport:send** on a computer, a compiler message will refer you to a Web site that contains the Microsoft data collection policy.</span></span>

## <a name="remarks"></a><span data-ttu-id="9b5ad-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9b5ad-119">Remarks</span></span>
 <span data-ttu-id="9b5ad-120">Wewnętrzny błąd kompilatora (ICE) wyniki, gdy kompilator nie może przetworzyć pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="9b5ad-120">An internal compiler error (ICE) results when the compiler cannot process a source code file.</span></span> <span data-ttu-id="9b5ad-121">Gdy wystąpi ICE, kompilator nie generuje pliku wyjściowego lub żadnych przydatnych diagnostycznych, które można użyć do naprawy kodu.</span><span class="sxs-lookup"><span data-stu-id="9b5ad-121">When an ICE occurs, the compiler does not produce an output file or any useful diagnostic that you can use to fix your code.</span></span>

 <span data-ttu-id="9b5ad-122">W poprzednich wersjach po otrzymaniu urządzenia ICE zachęcano do skontaktowania się z pomocą techniczną firmy Microsoft w celu zgłoszenia problemu.</span><span class="sxs-lookup"><span data-stu-id="9b5ad-122">In previous releases, when you received an ICE, you were encouraged to contact Microsoft Product Support Services to report the problem.</span></span> <span data-ttu-id="9b5ad-123">Za pomocą **-errorreport**, można podać informacje ICE do zespołu Visual C#.</span><span class="sxs-lookup"><span data-stu-id="9b5ad-123">By using **-errorreport**, you can provide ICE information to the Visual C# team.</span></span> <span data-ttu-id="9b5ad-124">Raporty o błędach mogą pomóc w ulepszeniu przyszłych wersji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="9b5ad-124">Your error reports can help improve future compiler releases.</span></span>

 <span data-ttu-id="9b5ad-125">Możliwość wysyłania raportów przez użytkownika zależy od uprawnień do obsługi zasad komputera i użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9b5ad-125">A user's ability to send reports depends on computer and user policy permissions.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="9b5ad-126">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9b5ad-126">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="9b5ad-127">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="9b5ad-127">Open the project's **Properties** page.</span></span> <span data-ttu-id="9b5ad-128">Aby uzyskać więcej informacji, zobacz [Tworzenie strony, Projektant projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="9b5ad-128">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>

2. <span data-ttu-id="9b5ad-129">Kliknij stronę **Właściwości kompilacji.**</span><span class="sxs-lookup"><span data-stu-id="9b5ad-129">Click the **Build** property page.</span></span>

3. <span data-ttu-id="9b5ad-130">Kliknij przycisk **Zaawansowane.**</span><span class="sxs-lookup"><span data-stu-id="9b5ad-130">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="9b5ad-131">Zmodyfikuj właściwość **Raportowanie błędów kompilatora wewnętrznego.**</span><span class="sxs-lookup"><span data-stu-id="9b5ad-131">Modify the **Internal Compiler Error Reporting** property.</span></span>

 <span data-ttu-id="9b5ad-132">Aby uzyskać informacje dotyczące programowego ustawiania tej <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>opcji kompilatora, zobacz .</span><span class="sxs-lookup"><span data-stu-id="9b5ad-132">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b5ad-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9b5ad-133">See also</span></span>

- [<span data-ttu-id="9b5ad-134">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="9b5ad-134">C# Compiler Options</span></span>](./index.md)
