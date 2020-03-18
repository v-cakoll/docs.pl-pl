---
title: 'Porada: ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio'
ms.date: 12/20/2019
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
ms.openlocfilehash: 99e2a837877494dd4c7e0106047bce3cc39a9282
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75342366"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="66c07-102">Porada: ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="66c07-102">How to set environment variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="66c07-103">Plik VsDevCmd.bat ustawia odpowiednie zmienne środowiskowe, aby włączyć kompilacje wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="66c07-103">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span>

> [!NOTE]
> <span data-ttu-id="66c07-104">Visual Studio 2015 i wcześniejsze wersje używane VSVARS32.bat, nie VsDevCmd.bat w tym samym celu.</span><span class="sxs-lookup"><span data-stu-id="66c07-104">Visual Studio 2015 and earlier versions used VSVARS32.bat, not VsDevCmd.bat for the same purpose.</span></span> <span data-ttu-id="66c07-105">Ten plik był przechowywany w folderze\\\Program Files\Microsoft Visual Studio*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span><span class="sxs-lookup"><span data-stu-id="66c07-105">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>

<span data-ttu-id="66c07-106">Jeśli bieżąca wersja programu Visual Studio jest zainstalowana na komputerze, który ma również wcześniejszą wersję programu Visual Studio, nie należy uruchamiać vsdevcmd.bat i VSVARS32. BAT z różnych wersji w tym samym oknie wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="66c07-106">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="66c07-107">Zamiast tego należy uruchomić polecenie dla każdej wersji w swoim własnym oknie.</span><span class="sxs-lookup"><span data-stu-id="66c07-107">Instead, you should run the command for each version in its own window.</span></span>

### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="66c07-108">Aby uruchomić vsdevcmd.BAT</span><span class="sxs-lookup"><span data-stu-id="66c07-108">To run VsDevCmd.BAT</span></span>

1. <span data-ttu-id="66c07-109">Z menu **Start** otwórz **wiersz polecenia dewelopera dla programu VS 2019**.</span><span class="sxs-lookup"><span data-stu-id="66c07-109">From the **Start** menu, open the **Developer Command Prompt for VS 2019**.</span></span>  <span data-ttu-id="66c07-110">Znajduje się w folderze **Visual Studio 2019.**</span><span class="sxs-lookup"><span data-stu-id="66c07-110">It's in the **Visual Studio 2019** folder.</span></span>

2. <span data-ttu-id="66c07-111">Zmień na \Program Files\Microsoft\\Visual Studio*Version*\\*Offering*\Common7\Tools or \Program\\Files (x86)\Microsoft Visual Studio*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span><span class="sxs-lookup"><span data-stu-id="66c07-111">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="66c07-112">(*Wersja* jest *2019* dla bieżącej wersji.</span><span class="sxs-lookup"><span data-stu-id="66c07-112">(*Version* is *2019* for the current version.</span></span> <span data-ttu-id="66c07-113">*Oferta* jest jednym z *Przedsiębiorstw,* *Zawodowych* lub *Społeczności*.)</span><span class="sxs-lookup"><span data-stu-id="66c07-113">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>

3. <span data-ttu-id="66c07-114">Uruchom VsDevCmd.bat wpisując **VsDevCmd**.</span><span class="sxs-lookup"><span data-stu-id="66c07-114">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="66c07-115">VsDevCmd.bat może się różnić w zależności od komputera.</span><span class="sxs-lookup"><span data-stu-id="66c07-115">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="66c07-116">Nie należy zastępować brakującego lub uszkodzonego pliku VsDevCmd.bat na vsdevcmd.bat z innego komputera.</span><span class="sxs-lookup"><span data-stu-id="66c07-116">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="66c07-117">Zamiast tego uruchom ponownie instalatora, aby zastąpić brakujący plik.</span><span class="sxs-lookup"><span data-stu-id="66c07-117">Instead, rerun setup to replace the missing file.</span></span>

### <a name="available-options-for-vsdevcmdbat"></a><span data-ttu-id="66c07-118">Dostępne opcje dla VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="66c07-118">Available options for VsDevCmd.BAT</span></span>

<span data-ttu-id="66c07-119">Aby wyświetlić dostępne opcje dla VsDevCmd.BAT, `-help` uruchom polecenie z opcją:</span><span class="sxs-lookup"><span data-stu-id="66c07-119">To see the available options for VsDevCmd.BAT, run the command with the `-help` option:</span></span>

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a><span data-ttu-id="66c07-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66c07-120">See also</span></span>

- [<span data-ttu-id="66c07-121">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="66c07-121">Command-line Building With csc.exe</span></span>](./command-line-building-with-csc-exe.md)
