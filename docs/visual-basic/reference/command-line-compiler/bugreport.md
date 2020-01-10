---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 829c19d2bce40a850d98f4973b1a4e4de31d8ce1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716816"
---
# <a name="-bugreport"></a><span data-ttu-id="6f4ef-102">-bugreport</span><span class="sxs-lookup"><span data-stu-id="6f4ef-102">-bugreport</span></span>
<span data-ttu-id="6f4ef-103">Tworzy plik, którego można użyć podczas tworzenia pliku raportu o usterce.</span><span class="sxs-lookup"><span data-stu-id="6f4ef-103">Creates a file that you can use when you file a bug report.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f4ef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6f4ef-104">Syntax</span></span>  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="6f4ef-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="6f4ef-105">Arguments</span></span>  
  
|<span data-ttu-id="6f4ef-106">Termin</span><span class="sxs-lookup"><span data-stu-id="6f4ef-106">Term</span></span>|<span data-ttu-id="6f4ef-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="6f4ef-107">Definition</span></span>|  
|---|---|  
|`file`|<span data-ttu-id="6f4ef-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="6f4ef-108">Required.</span></span> <span data-ttu-id="6f4ef-109">Nazwa pliku, który będzie zawierać raport o błędach.</span><span class="sxs-lookup"><span data-stu-id="6f4ef-109">The name of the file that will contain your bug report.</span></span> <span data-ttu-id="6f4ef-110">Nazwa pliku powinna być ujęta w cudzysłów (""), jeśli nazwa zawiera spację.</span><span class="sxs-lookup"><span data-stu-id="6f4ef-110">Enclose the file name in quotation marks (" ") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f4ef-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6f4ef-111">Remarks</span></span>  
 <span data-ttu-id="6f4ef-112">Następujące informacje są dodawane do `file`:</span><span class="sxs-lookup"><span data-stu-id="6f4ef-112">The following information is added to `file`:</span></span>  
  
- <span data-ttu-id="6f4ef-113">Kopia wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6f4ef-113">A copy of all source-code files in the compilation.</span></span>  
  
- <span data-ttu-id="6f4ef-114">Lista opcji kompilatora używanych w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6f4ef-114">A list of the compiler options used in the compilation.</span></span>  
  
- <span data-ttu-id="6f4ef-115">Informacje o wersji dotyczące kompilatora, środowiska uruchomieniowego języka wspólnego i systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="6f4ef-115">Version information about your compiler, common language runtime, and operating system.</span></span>  
  
- <span data-ttu-id="6f4ef-116">Dane wyjściowe kompilatora, jeśli istnieją.</span><span class="sxs-lookup"><span data-stu-id="6f4ef-116">Compiler output, if any.</span></span>  
  
- <span data-ttu-id="6f4ef-117">Opis problemu, dla którego zostanie wyświetlony monit.</span><span class="sxs-lookup"><span data-stu-id="6f4ef-117">A description of the problem, for which you are prompted.</span></span>  
  
- <span data-ttu-id="6f4ef-118">Opis sposobu, w jaki sądzisz, że problem powinien zostać rozwiązany, dla którego zostanie wyświetlony monit.</span><span class="sxs-lookup"><span data-stu-id="6f4ef-118">A description of how you think the problem should be fixed, for which you are prompted.</span></span>  
  
 <span data-ttu-id="6f4ef-119">Ze względu na to, że kopia wszystkich plików kodu źródłowego jest dołączona do `file`, warto odtworzyć defekt kodu (podejrzane) w najkrótszym możliwym programie.</span><span class="sxs-lookup"><span data-stu-id="6f4ef-119">Because a copy of all source-code files is included in `file`, you may want to reproduce the (suspected) code defect in the shortest possible program.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6f4ef-120">Opcja `-bugreport` tworzy plik, który zawiera potencjalnie poufne informacje.</span><span class="sxs-lookup"><span data-stu-id="6f4ef-120">The `-bugreport` option produces a file that contains potentially sensitive information.</span></span> <span data-ttu-id="6f4ef-121">Obejmuje to bieżący czas, wersję kompilatora, wersję .NET Framework, wersję systemu operacyjnego, nazwę użytkownika, argumenty wiersza polecenia, za pomocą których kompilator został uruchomiony, wszystkie kod źródłowy oraz binarną postać dowolnego przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="6f4ef-121">This includes current time, compiler version, .NET Framework version, OS version, user name, the command-line arguments with which the compiler was run, all source code, and the binary form of any referenced assembly.</span></span> <span data-ttu-id="6f4ef-122">Dostęp do tej opcji można uzyskać, określając opcje wiersza polecenia w pliku Web. config po stronie serwera dla kompilacji aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6f4ef-122">This option can be accessed by specifying command-line options in the Web.config file for a server-side compilation of an ASP.NET application.</span></span> <span data-ttu-id="6f4ef-123">Aby tego uniknąć, należy zmodyfikować plik Machine. config, aby nie zezwalać użytkownikom na kompilowanie na serwerze.</span><span class="sxs-lookup"><span data-stu-id="6f4ef-123">To prevent this, modify the Machine.config file to disallow users from compiling on the server.</span></span>  
  
 <span data-ttu-id="6f4ef-124">Jeśli ta opcja jest używana z `-errorreport:prompt`, `-errorreport:queue`lub `-errorreport:send`, a aplikacja napotka wewnętrzny błąd kompilatora, informacje w `file` są wysyłane do firmy Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="6f4ef-124">If this option is used with `-errorreport:prompt`, `-errorreport:queue`, or `-errorreport:send`, and your application encounters an internal compiler error, the information in `file` is sent to Microsoft Corporation.</span></span> <span data-ttu-id="6f4ef-125">Te informacje ułatwią inżynierom firmy Microsoft Identyfikowanie przyczyny błędu i mogą pomóc w ulepszaniu kolejnej wersji Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6f4ef-125">That information will help Microsoft engineers identify the cause of the error and may help improve the next release of Visual Basic.</span></span> <span data-ttu-id="6f4ef-126">Domyślnie żadne informacje nie są wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6f4ef-126">By default, no information is sent to Microsoft.</span></span> <span data-ttu-id="6f4ef-127">Jednak podczas kompilowania aplikacji przy użyciu `-errorreport:queue`, która jest domyślnie włączona, aplikacja zbiera raporty o błędach.</span><span class="sxs-lookup"><span data-stu-id="6f4ef-127">However, when you compile an application by using `-errorreport:queue`, which is enabled by default, the application collects its error reports.</span></span> <span data-ttu-id="6f4ef-128">Po zalogowaniu się administratora komputera w systemie raportowanie błędów zostanie wyświetlone okno podręczne, które umożliwi administratorowi przekazanie do firmy Microsoft wszelkich raportów o błędach, które wystąpiły od momentu zalogowania.</span><span class="sxs-lookup"><span data-stu-id="6f4ef-128">Then, when the computer's administrator logs in, the error reporting system displays a pop-up window that enables the administrator to forward to Microsoft any error reports that occurred since the logon.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f4ef-129">Opcja `-bugreport` nie jest dostępna w środowisku deweloperskim programu Visual Studio; jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="6f4ef-129">The `-bugreport` option is not available from within the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f4ef-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="6f4ef-130">Example</span></span>  
 <span data-ttu-id="6f4ef-131">Poniższy przykład kompiluje `T2.vb` i umieszcza wszystkie informacje o raportowaniu błędów w `Problem.txt`pliku.</span><span class="sxs-lookup"><span data-stu-id="6f4ef-131">The following example compiles `T2.vb` and puts all bug-reporting information in the file `Problem.txt`.</span></span>  
  
```console  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f4ef-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f4ef-132">See also</span></span>

- [<span data-ttu-id="6f4ef-133">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6f4ef-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="6f4ef-134">-Debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f4ef-134">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)
- [<span data-ttu-id="6f4ef-135">-errorreport</span><span class="sxs-lookup"><span data-stu-id="6f4ef-135">-errorreport</span></span>](../../../visual-basic/reference/command-line-compiler/errorreport.md)
- [<span data-ttu-id="6f4ef-136">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="6f4ef-136">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- <span data-ttu-id="6f4ef-137">[Element trustLevel dla securityPolicy (ASP.NET Schema Settings)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6f4ef-137">[trustLevel Element for securityPolicy (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span></span>
