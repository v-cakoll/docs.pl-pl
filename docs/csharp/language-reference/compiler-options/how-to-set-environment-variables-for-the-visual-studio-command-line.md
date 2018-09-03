---
title: 'Porada: Ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio'
ms.date: 09/29/2017
f1_keywords:
- cs.build.commandline
helpviewer_keywords:
- csc.exe, command-line builds
- Visual C#, command-line builds
- command-line compilers, Visual C#
- Vsvars32.bat
- builds [C#], command-line
- compilers, invoking from command line
- Vcvars32.bat file
- command line [C#], building from
- Visual C# compiler, enabling
- compiling source code, from command line
ms.assetid: 7ec09480-5612-4f6a-8d00-ad90ea9bca5d
ms.openlocfilehash: 77375e428fe0563c0b533ca97abd21070e850682
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43466741"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="6552b-102">Porada: Ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6552b-102">How to: Set Environment Variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="6552b-103">Plik VsDevCmd.bat ustawia odpowiednie zmienne środowiskowe umożliwiające kompilacji z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="6552b-103">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span> <span data-ttu-id="6552b-104">Aby uzyskać więcej informacji na temat VsDevCmd.bat zobacz [artykuł bazy wiedzy Q248802](https://support.microsoft.com/help/248802/you-receive-the-out-of-environment-space-error-message-when-you-execut).</span><span class="sxs-lookup"><span data-stu-id="6552b-104">For more information about VsDevCmd.bat, see [Knowledge Base article Q248802](https://support.microsoft.com/help/248802/you-receive-the-out-of-environment-space-error-message-when-you-execut).</span></span>  

> [!NOTE]
> <span data-ttu-id="6552b-105">Plik VsDevCmd.bat jest nowy plik dostarczane z programem Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="6552b-105">The VsDevCmd.bat file is a new file delivered with Visual Studio 2017.</span></span> <span data-ttu-id="6552b-106">Program Visual Studio 2015 i starsze wersje używane VSVARS32.bat, w tym samym celu.</span><span class="sxs-lookup"><span data-stu-id="6552b-106">Visual Studio 2015 and earlier versions used VSVARS32.bat for the same purpose.</span></span> <span data-ttu-id="6552b-107">Ten plik został zapisany w programie Visual Studio \Program Files\Microsoft\\*wersji*\Common7\Tools lub Program Files (x86) \Microsoft Visual Studio\\*wersji*\Common7\Tools.</span><span class="sxs-lookup"><span data-stu-id="6552b-107">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>
  
<span data-ttu-id="6552b-108">Jeśli bieżącą wersję programu Visual Studio jest zainstalowany na komputerze, który ma także wcześniejszej wersji programu Visual Studio, nie należy uruchamiać VsDevCmd.bat i VSVARS32. BAT z różnych wersji, w tym samym oknie wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="6552b-108">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="6552b-109">Zamiast tego należy uruchamiać polecenie dla każdej wersji w osobnym oknie.</span><span class="sxs-lookup"><span data-stu-id="6552b-109">Instead, you should run the command for each version in its own window.</span></span>
  
### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="6552b-110">Aby uruchomić VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="6552b-110">To run VsDevCmd.BAT</span></span>  
  
1.  <span data-ttu-id="6552b-111">Z **Start** menu Otwórz **wiersz polecenia programisty dla programu VS 2017**.</span><span class="sxs-lookup"><span data-stu-id="6552b-111">From the **Start** menu, open the **Developer Command Prompt for VS 2017**.</span></span>  <span data-ttu-id="6552b-112">Jest on **programu Visual Studio 2017** folderu.</span><span class="sxs-lookup"><span data-stu-id="6552b-112">It's in the **Visual Studio 2017** folder.</span></span>
  
2.  <span data-ttu-id="6552b-113">Zmiany do programu Visual Studio \Program Files\Microsoft\\*wersji*\\*oferty*\Common7\Tools lub \Program pliki (x86) \Microsoft Visual Studio\\ *Wersji*\\*oferty*podkatalogu \Common7\Tools instalacji.</span><span class="sxs-lookup"><span data-stu-id="6552b-113">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="6552b-114">(*Wersji* jest *2017* dla bieżącej wersji.</span><span class="sxs-lookup"><span data-stu-id="6552b-114">(*Version* is *2017* for the current version.</span></span> <span data-ttu-id="6552b-115">*Oferta* jest jednym z *Enterprise*, *Professional* lub *społeczności*.)</span><span class="sxs-lookup"><span data-stu-id="6552b-115">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>
  
3.  <span data-ttu-id="6552b-116">Uruchom VsDevCmd.bat, wpisując **VsDevCmd**.</span><span class="sxs-lookup"><span data-stu-id="6552b-116">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="6552b-117">VsDevCmd.bat mogą się różnić między komputerami.</span><span class="sxs-lookup"><span data-stu-id="6552b-117">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="6552b-118">Nie zastępuj uszkodzony lub plik VsDevCmd.bat VsDevCmd.bat z innego komputera.</span><span class="sxs-lookup"><span data-stu-id="6552b-118">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="6552b-119">Zamiast tego Uruchom ponownie Instalatora, aby zastąpić brakujący plik.</span><span class="sxs-lookup"><span data-stu-id="6552b-119">Instead, rerun setup to replace the missing file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6552b-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6552b-120">See Also</span></span>  

- [<span data-ttu-id="6552b-121">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="6552b-121">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
