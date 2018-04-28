---
title: -errorreport
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5dc321f7f927d68a9f270076640cbc6d31d2f6d5
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="-errorreport"></a><span data-ttu-id="d1aa8-102">-errorreport</span><span class="sxs-lookup"><span data-stu-id="d1aa8-102">-errorreport</span></span>
<span data-ttu-id="d1aa8-103">Określa, jak kompilator Visual Basic powinien zgłosić wewnętrzne błędy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="d1aa8-103">Specifies how the Visual Basic compiler should report internal compiler errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1aa8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1aa8-104">Syntax</span></span>  
  
```  
-errorreport:{ prompt | queue | send | none }  
```  
  
## <a name="remarks"></a><span data-ttu-id="d1aa8-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1aa8-105">Remarks</span></span>  
 <span data-ttu-id="d1aa8-106">Ta opcja umożliwia dogodny zgłosić błąd wewnętrzny kompilatora Visual Basic (ICE) do zespołu Visual Basic w firmie Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d1aa8-106">This option provides a convenient way to report a Visual Basic internal compiler error (ICE) to the Visual Basic team at Microsoft.</span></span> <span data-ttu-id="d1aa8-107">Domyślnie kompilator wysyła żadnych informacji do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d1aa8-107">By default, the compiler sends no information to Microsoft.</span></span> <span data-ttu-id="d1aa8-108">Jednak jeśli wystąpi błąd wewnętrzny kompilatora, ta opcja umożliwia raportowanie błędów firmie Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d1aa8-108">However, if you do encounter an internal compiler error, this option allows you to report the error to Microsoft.</span></span> <span data-ttu-id="d1aa8-109">Te informacje pomagają zidentyfikować przyczynę pracownicy firmy Microsoft i może zwiększyć kolejnej wersji programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d1aa8-109">That information will help Microsoft engineers identify the cause and may help improve the next release of Visual Basic.</span></span>  
  
 <span data-ttu-id="d1aa8-110">Możliwość wysyłania raportów użytkownika zależy od uprawnień zasad komputera i użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d1aa8-110">A user's ability to send reports depends on machine and user policy permissions.</span></span>  
  
 <span data-ttu-id="d1aa8-111">W poniższej tabeli przedstawiono wpływ `-errorreport` opcji.</span><span class="sxs-lookup"><span data-stu-id="d1aa8-111">The following table summarizes the effect of the `-errorreport` option.</span></span>  
  
|<span data-ttu-id="d1aa8-112">Opcja</span><span class="sxs-lookup"><span data-stu-id="d1aa8-112">Option</span></span>|<span data-ttu-id="d1aa8-113">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="d1aa8-113">Behavior</span></span>|  
|---|---|  
|`prompt`|<span data-ttu-id="d1aa8-114">Jeśli wystąpi błąd wewnętrzny kompilatora, okno dialogowe pojawia się, dzięki czemu można wyświetlić dokładne dane, które są zbierane przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="d1aa8-114">If an internal compiler error occurs, a dialog box comes up so that you can view the exact data that the compiler collected.</span></span> <span data-ttu-id="d1aa8-115">Można określić, czy istnieje żadnych poufnych informacji w raporcie o błędzie i podejmowania decyzji od tego, czy do wysłania do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d1aa8-115">You can determine if there is any sensitive information in the error report and make a decision on whether to send it to Microsoft.</span></span> <span data-ttu-id="d1aa8-116">Jeśli zdecydujesz się wysłać i umożliwienie ustawienia zasad komputera i użytkownika, kompilator wysyła dane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d1aa8-116">If you decide to send it, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span>|  
|`queue`|<span data-ttu-id="d1aa8-117">Kolejkuje raport o błędzie.</span><span class="sxs-lookup"><span data-stu-id="d1aa8-117">Queues the error report.</span></span> <span data-ttu-id="d1aa8-118">Podczas logowania się z uprawnieniami administratora, od czasu ostatniego zalogowania w może raportować zakończą się niepowodzeniem (zostanie nie się monit o wysłanie raportu błędów więcej niż raz na trzy dni).</span><span class="sxs-lookup"><span data-stu-id="d1aa8-118">When you log in with administrator privileges, you can report any failures since the last time you were logged in (you will not be prompted to send reports for failures more than once every three days).</span></span> <span data-ttu-id="d1aa8-119">Jest to domyślne zachowanie podczas `-errorreport` nie określono opcji.</span><span class="sxs-lookup"><span data-stu-id="d1aa8-119">This is the default behavior when the `-errorreport` option is not specified.</span></span>|  
|`send`|<span data-ttu-id="d1aa8-120">Jeśli wystąpi błąd wewnętrzny kompilatora i umożliwienie ustawienia zasad komputera i użytkownika, kompilator wysyła dane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d1aa8-120">If an internal compiler error occurs, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span><br /><br /> <span data-ttu-id="d1aa8-121">Opcja `-errorreport:send` próbuje automatyczne wysyłanie informacji o błędach do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d1aa8-121">The option `-errorreport:send` attempts to automatically send error information to Microsoft.</span></span> <span data-ttu-id="d1aa8-122">Ta opcja jest zależna od rejestru.</span><span class="sxs-lookup"><span data-stu-id="d1aa8-122">This option depends on the registry.</span></span> <span data-ttu-id="d1aa8-123">Aby uzyskać więcej informacji na temat ustawiania odpowiednie wartości w rejestrze, zobacz [jak włączyć automatyczne raportowanie błędów w programie Visual Studio 2008 wiersza polecenia narzędzia](http://go.microsoft.com/fwlink/?LinkID=184695).</span><span class="sxs-lookup"><span data-stu-id="d1aa8-123">For more information about setting the appropriate values in the registry, see [How to Turn on Automatic Error Reporting in Visual Studio 2008 Command-line Tools](http://go.microsoft.com/fwlink/?LinkID=184695).</span></span>|  
|`none`|<span data-ttu-id="d1aa8-124">Jeśli wystąpi błąd wewnętrzny kompilatora, go nie zostanie zbierane ani wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d1aa8-124">If an internal compiler error occurs, it will not be collected or sent to Microsoft.</span></span>|  
  
 <span data-ttu-id="d1aa8-125">Kompilator wysyła dane, które obejmuje stosu w momencie wystąpienia błędu, obejmujące niektóre kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="d1aa8-125">The compiler sends data that includes the stack at the time of the error, which usually includes some source code.</span></span> <span data-ttu-id="d1aa8-126">Jeśli `-errorreport` jest używany z [- bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) opcji, a następnie wysłaniu całego pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="d1aa8-126">If `-errorreport` is used with the [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, then the entire source file is sent.</span></span>  
  
 <span data-ttu-id="d1aa8-127">Ta opcja jest optymalna dla [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) opcja, ponieważ umożliwia pracownicy firmy Microsoft, aby łatwo odtwarzania błędu.</span><span class="sxs-lookup"><span data-stu-id="d1aa8-127">This option is best used with the [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, because it allows Microsoft engineers to more easily reproduce the error.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1aa8-128">`-errorreport` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="d1aa8-128">The `-errorreport` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1aa8-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="d1aa8-129">Example</span></span>  
 <span data-ttu-id="d1aa8-130">Poniższy kod próbuje skompilować `T2.vb`, jeśli kompilator napotkał błąd wewnętrzny kompilatora, monitów o wysłanie raportu o błędach do firmy Microsoft i.</span><span class="sxs-lookup"><span data-stu-id="d1aa8-130">The following code attempts to compile `T2.vb`, and if the compiler encounters an internal compiler error, it prompts you to send the error report to Microsoft.</span></span>  
  
```  
vbc -errorreport:prompt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1aa8-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1aa8-131">See Also</span></span>  
 [<span data-ttu-id="d1aa8-132">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d1aa8-132">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="d1aa8-133">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="d1aa8-133">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="d1aa8-134">-bugreport</span><span class="sxs-lookup"><span data-stu-id="d1aa8-134">-bugreport</span></span>](../../../visual-basic/reference/command-line-compiler/bugreport.md)
