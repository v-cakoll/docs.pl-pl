---
title: -bugreport —
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 0383a5e369ee4a8146764c13b2f12f48ebe52190
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934580"
---
# <a name="-bugreport"></a><span data-ttu-id="c87ea-102">-bugreport —</span><span class="sxs-lookup"><span data-stu-id="c87ea-102">-bugreport</span></span>
<span data-ttu-id="c87ea-103">Tworzy plik, który można użyć, gdy plik jest raport o usterce.</span><span class="sxs-lookup"><span data-stu-id="c87ea-103">Creates a file that you can use when you file a bug report.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c87ea-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c87ea-104">Syntax</span></span>  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="c87ea-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c87ea-105">Arguments</span></span>  
  
|<span data-ttu-id="c87ea-106">Termin</span><span class="sxs-lookup"><span data-stu-id="c87ea-106">Term</span></span>|<span data-ttu-id="c87ea-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="c87ea-107">Definition</span></span>|  
|---|---|  
|`file`|<span data-ttu-id="c87ea-108">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="c87ea-108">Required.</span></span> <span data-ttu-id="c87ea-109">Nazwa pliku, który będzie zawierał raport o usterce.</span><span class="sxs-lookup"><span data-stu-id="c87ea-109">The name of the file that will contain your bug report.</span></span> <span data-ttu-id="c87ea-110">Nazwę pliku należy ująć w znaki cudzysłowu (""), jeśli nazwa zawiera spację.</span><span class="sxs-lookup"><span data-stu-id="c87ea-110">Enclose the file name in quotation marks (" ") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c87ea-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c87ea-111">Remarks</span></span>  
 <span data-ttu-id="c87ea-112">Poniższe informacje są dodawane do `file`:</span><span class="sxs-lookup"><span data-stu-id="c87ea-112">The following information is added to `file`:</span></span>  
  
-   <span data-ttu-id="c87ea-113">Kopiowanie wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c87ea-113">A copy of all source-code files in the compilation.</span></span>  
  
-   <span data-ttu-id="c87ea-114">Lista opcji kompilatora, używane w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c87ea-114">A list of the compiler options used in the compilation.</span></span>  
  
-   <span data-ttu-id="c87ea-115">Informacje o wersji dotyczące kompilatora, środowisko uruchomieniowe języka wspólnego i systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="c87ea-115">Version information about your compiler, common language runtime, and operating system.</span></span>  
  
-   <span data-ttu-id="c87ea-116">Kompilator dane wyjściowe, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="c87ea-116">Compiler output, if any.</span></span>  
  
-   <span data-ttu-id="c87ea-117">Opis problemu, dla którego jest wyświetlany monit.</span><span class="sxs-lookup"><span data-stu-id="c87ea-117">A description of the problem, for which you are prompted.</span></span>  
  
-   <span data-ttu-id="c87ea-118">Opis sposobu Twoim zdaniem ten problem należy ustalić, dla którego jest wyświetlany monit.</span><span class="sxs-lookup"><span data-stu-id="c87ea-118">A description of how you think the problem should be fixed, for which you are prompted.</span></span>  
  
 <span data-ttu-id="c87ea-119">Ponieważ kopiowanie wszystkich plików kodu źródłowego jest uwzględniony w `file`, może zajść potrzeba odtworzenia kodu (podejrzanych) wada najkrótszej program możliwe.</span><span class="sxs-lookup"><span data-stu-id="c87ea-119">Because a copy of all source-code files is included in `file`, you may want to reproduce the (suspected) code defect in the shortest possible program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c87ea-120">`-bugreport` Opcja tworzy plik, który zawiera potencjalnie poufne informacje.</span><span class="sxs-lookup"><span data-stu-id="c87ea-120">The `-bugreport` option produces a file that contains potentially sensitive information.</span></span> <span data-ttu-id="c87ea-121">Obejmuje to bieżący czas, wersja kompilatora [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] wersji, wersji systemu operacyjnego, nazwę użytkownika, argumenty wiersza polecenia za pomocą których kompilator zostało uruchomione, każdy kod źródłowy i binarną formę dowolnego odwołanie do zestawu.</span><span class="sxs-lookup"><span data-stu-id="c87ea-121">This includes current time, compiler version, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] version, OS version, user name, the command-line arguments with which the compiler was run, all source code, and the binary form of any referenced assembly.</span></span> <span data-ttu-id="c87ea-122">Ta opcja może zostać oceniony przez określenie opcji wiersza polecenia w pliku Web.config dla kompilacji po stronie serwera [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c87ea-122">This option can be accessed by specifying command-line options in the Web.config file for a server-side compilation of an [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] application.</span></span> <span data-ttu-id="c87ea-123">Aby tego uniknąć, należy zmodyfikować plik Machine.config, aby uniemożliwić użytkownikom kompilacji na serwerze.</span><span class="sxs-lookup"><span data-stu-id="c87ea-123">To prevent this, modify the Machine.config file to disallow users from compiling on the server.</span></span>  
  
 <span data-ttu-id="c87ea-124">Jeśli ta opcja jest używana z `-errorreport:prompt`, `-errorreport:queue`, lub `-errorreport:send`, i aplikacji wystąpi błąd wewnętrzny kompilatora, informacje zawarte w `file` są wysyłane do firmy Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="c87ea-124">If this option is used with `-errorreport:prompt`, `-errorreport:queue`, or `-errorreport:send`, and your application encounters an internal compiler error, the information in `file` is sent to Microsoft Corporation.</span></span> <span data-ttu-id="c87ea-125">Te informacje pomagają inżynierów firmy Microsoft, Zidentyfikuj przyczynę błędu i może poprawić kolejnej wersji programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c87ea-125">That information will help Microsoft engineers identify the cause of the error and may help improve the next release of Visual Basic.</span></span> <span data-ttu-id="c87ea-126">Domyślnie żadne informacje nie są wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c87ea-126">By default, no information is sent to Microsoft.</span></span> <span data-ttu-id="c87ea-127">Jednakże, gdy kompilujesz aplikację za pomocą `-errorreport:queue`, która jest domyślnie włączone, aplikacja zbiera raporty o błędach.</span><span class="sxs-lookup"><span data-stu-id="c87ea-127">However, when you compile an application by using `-errorreport:queue`, which is enabled by default, the application collects its error reports.</span></span> <span data-ttu-id="c87ea-128">Następnie kiedy loguje administratora komputera, systemu raportowania błędów wyświetli okno wyskakujące z umożliwiająca administratorowi przesłać do firmy Microsoft raporty o wszelkich błędach, które od czasu logowania.</span><span class="sxs-lookup"><span data-stu-id="c87ea-128">Then, when the computer's administrator logs in, the error reporting system displays a pop-up window that enables the administrator to forward to Microsoft any error reports that occurred since the logon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c87ea-129">`/bugreport` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilacji z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="c87ea-129">The `/bugreport` option is not available from within the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c87ea-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="c87ea-130">Example</span></span>  
 <span data-ttu-id="c87ea-131">Poniższy przykład kompiluje `T2.vb` i umieszczenie wszystkich informacji usługi raportowania błędów w pliku `Problem.txt`.</span><span class="sxs-lookup"><span data-stu-id="c87ea-131">The following example compiles `T2.vb` and puts all bug-reporting information in the file `Problem.txt`.</span></span>  
  
```  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c87ea-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c87ea-132">See Also</span></span>  
 [<span data-ttu-id="c87ea-133">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c87ea-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="c87ea-134">-debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c87ea-134">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [<span data-ttu-id="c87ea-135">-errorreport</span><span class="sxs-lookup"><span data-stu-id="c87ea-135">-errorreport</span></span>](../../../visual-basic/reference/command-line-compiler/errorreport.md)  
 [<span data-ttu-id="c87ea-136">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="c87ea-136">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="c87ea-137">trustLevel elementu dla securityPolicy (ASP.NET Settings Schema)</span><span class="sxs-lookup"><span data-stu-id="c87ea-137">trustLevel Element for securityPolicy (ASP.NET Settings Schema)</span></span>](http://msdn.microsoft.com/library/729ab04c-03da-4ee5-86b1-be9d08a09369)
