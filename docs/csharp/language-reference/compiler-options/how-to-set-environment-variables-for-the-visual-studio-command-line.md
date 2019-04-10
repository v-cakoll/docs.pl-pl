---
title: 'Porady: ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio'
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
ms.openlocfilehash: 1c906a2274f57f5a89fb16198c8f6ed2e3a335e2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322124"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="bb150-102">Instrukcje: ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bb150-102">How to: Set Environment Variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="bb150-103">Plik VsDevCmd.bat ustawia odpowiednie zmienne środowiskowe umożliwiające kompilacji z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="bb150-103">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span>

> [!NOTE]
> <span data-ttu-id="bb150-104">Plik VsDevCmd.bat jest nowy plik dostarczane z programem Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="bb150-104">The VsDevCmd.bat file is a new file delivered with Visual Studio 2017.</span></span> <span data-ttu-id="bb150-105">Program Visual Studio 2015 i starsze wersje używane VSVARS32.bat, w tym samym celu.</span><span class="sxs-lookup"><span data-stu-id="bb150-105">Visual Studio 2015 and earlier versions used VSVARS32.bat for the same purpose.</span></span> <span data-ttu-id="bb150-106">Ten plik został zapisany w programie Visual Studio \Program Files\Microsoft\\*wersji*\Common7\Tools lub Program Files (x86) \Microsoft Visual Studio\\*wersji*\Common7\Tools.</span><span class="sxs-lookup"><span data-stu-id="bb150-106">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>
  
<span data-ttu-id="bb150-107">Jeśli bieżącą wersję programu Visual Studio jest zainstalowany na komputerze, który ma także wcześniejszej wersji programu Visual Studio, nie należy uruchamiać VsDevCmd.bat i VSVARS32. BAT z różnych wersji, w tym samym oknie wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="bb150-107">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="bb150-108">Zamiast tego należy uruchamiać polecenie dla każdej wersji w osobnym oknie.</span><span class="sxs-lookup"><span data-stu-id="bb150-108">Instead, you should run the command for each version in its own window.</span></span>
  
### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="bb150-109">Aby uruchomić VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="bb150-109">To run VsDevCmd.BAT</span></span>  
  
1. <span data-ttu-id="bb150-110">Z **Start** menu Otwórz **wiersz polecenia programisty dla programu VS 2017**.</span><span class="sxs-lookup"><span data-stu-id="bb150-110">From the **Start** menu, open the **Developer Command Prompt for VS 2017**.</span></span>  <span data-ttu-id="bb150-111">Jest on **programu Visual Studio 2017** folderu.</span><span class="sxs-lookup"><span data-stu-id="bb150-111">It's in the **Visual Studio 2017** folder.</span></span>
  
2. <span data-ttu-id="bb150-112">Zmiany do programu Visual Studio \Program Files\Microsoft\\*wersji*\\*oferty*\Common7\Tools lub \Program pliki (x86) \Microsoft Visual Studio\\ *Wersji*\\*oferty*podkatalogu \Common7\Tools instalacji.</span><span class="sxs-lookup"><span data-stu-id="bb150-112">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="bb150-113">(*Wersji* jest *2017* dla bieżącej wersji.</span><span class="sxs-lookup"><span data-stu-id="bb150-113">(*Version* is *2017* for the current version.</span></span> <span data-ttu-id="bb150-114">*Oferta* jest jednym z *Enterprise*, *Professional* lub *społeczności*.)</span><span class="sxs-lookup"><span data-stu-id="bb150-114">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>
  
3. <span data-ttu-id="bb150-115">Uruchom VsDevCmd.bat, wpisując **VsDevCmd**.</span><span class="sxs-lookup"><span data-stu-id="bb150-115">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="bb150-116">VsDevCmd.bat mogą się różnić między komputerami.</span><span class="sxs-lookup"><span data-stu-id="bb150-116">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="bb150-117">Nie zastępuj uszkodzony lub plik VsDevCmd.bat VsDevCmd.bat z innego komputera.</span><span class="sxs-lookup"><span data-stu-id="bb150-117">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="bb150-118">Zamiast tego Uruchom ponownie Instalatora, aby zastąpić brakujący plik.</span><span class="sxs-lookup"><span data-stu-id="bb150-118">Instead, rerun setup to replace the missing file.</span></span>  

### <a name="available-options-for-vsdevcmdbat"></a><span data-ttu-id="bb150-119">Dostępne opcje VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="bb150-119">Available options for VsDevCmd.BAT</span></span>

<span data-ttu-id="bb150-120">Aby wyświetlić dostępne opcje VsDevCmd.BAT, uruchom polecenie `-help` opcji:</span><span class="sxs-lookup"><span data-stu-id="bb150-120">To see the available options for VsDevCmd.BAT, run the command with the `-help` option:</span></span>
```console
VsDevCmd.bat -help
```

## <a name="see-also"></a><span data-ttu-id="bb150-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb150-121">See also</span></span>

- [<span data-ttu-id="bb150-122">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="bb150-122">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
