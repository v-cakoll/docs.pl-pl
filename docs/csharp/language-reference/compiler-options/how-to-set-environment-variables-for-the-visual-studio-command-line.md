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
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75342366"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="db396-102">Porada: ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="db396-102">How to set environment variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="db396-103">Plik VsDevCmd. bat ustawia odpowiednie zmienne środowiskowe, aby włączyć kompilacje w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="db396-103">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span>

> [!NOTE]
> <span data-ttu-id="db396-104">Program Visual Studio 2015 i starsze wersje używały VSVARS32. bat, a nie VsDevCmd. bat w tym samym celu.</span><span class="sxs-lookup"><span data-stu-id="db396-104">Visual Studio 2015 and earlier versions used VSVARS32.bat, not VsDevCmd.bat for the same purpose.</span></span> <span data-ttu-id="db396-105">Ten plik był przechowywany w folderze \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools lub Program Files (x86) \Microsoft Visual Studio\\*wersja*\Common7\Tools.</span><span class="sxs-lookup"><span data-stu-id="db396-105">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>

<span data-ttu-id="db396-106">Jeśli bieżąca wersja programu Visual Studio jest zainstalowana na komputerze, który ma również starszą wersję programu Visual Studio, nie należy uruchamiać VsDevCmd. bat i VSVARS32. BAT z różnych wersji w tym samym oknie wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="db396-106">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="db396-107">Zamiast tego należy uruchomić polecenie dla każdej wersji w osobnym oknie.</span><span class="sxs-lookup"><span data-stu-id="db396-107">Instead, you should run the command for each version in its own window.</span></span>

### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="db396-108">Aby uruchomić VsDevCmd. BAT</span><span class="sxs-lookup"><span data-stu-id="db396-108">To run VsDevCmd.BAT</span></span>

1. <span data-ttu-id="db396-109">Z menu **Start** Otwórz **wiersz polecenia dla deweloperów dla programu vs 2019**.</span><span class="sxs-lookup"><span data-stu-id="db396-109">From the **Start** menu, open the **Developer Command Prompt for VS 2019**.</span></span>  <span data-ttu-id="db396-110">Znajduje się w folderze **programu Visual Studio 2019** .</span><span class="sxs-lookup"><span data-stu-id="db396-110">It's in the **Visual Studio 2019** folder.</span></span>

2. <span data-ttu-id="db396-111">Przejdź do folderu \Program Files\Microsoft Visual Studio\\*wersja*\\*oferty*\Common7\Tools lub \Program Files (x86) \Microsoft Visual Studio\\*wersja*\\*oferowanie*\Common7\Tools podkatalogu instalacji.</span><span class="sxs-lookup"><span data-stu-id="db396-111">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="db396-112">(*Wersja* *2019* dla bieżącej wersji.</span><span class="sxs-lookup"><span data-stu-id="db396-112">(*Version* is *2019* for the current version.</span></span> <span data-ttu-id="db396-113">*Oferta* jest jedną z *przedsiębiorstw*, *profesjonalistów* lub *społeczności*.)</span><span class="sxs-lookup"><span data-stu-id="db396-113">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>

3. <span data-ttu-id="db396-114">Uruchom VsDevCmd. bat, wpisując **VsDevCmd**.</span><span class="sxs-lookup"><span data-stu-id="db396-114">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="db396-115">VsDevCmd. bat może się różnić od komputera do komputera.</span><span class="sxs-lookup"><span data-stu-id="db396-115">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="db396-116">Nie zamieniaj brakującego lub uszkodzonego pliku VsDevCmd. bat z VsDevCmd. bat z innego komputera.</span><span class="sxs-lookup"><span data-stu-id="db396-116">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="db396-117">Zamiast tego ponownie uruchom Instalatora, aby zastąpić brakujący plik.</span><span class="sxs-lookup"><span data-stu-id="db396-117">Instead, rerun setup to replace the missing file.</span></span>

### <a name="available-options-for-vsdevcmdbat"></a><span data-ttu-id="db396-118">Dostępne opcje dla VsDevCmd. BAT</span><span class="sxs-lookup"><span data-stu-id="db396-118">Available options for VsDevCmd.BAT</span></span>

<span data-ttu-id="db396-119">Aby wyświetlić dostępne opcje dla VsDevCmd. BAT, uruchom polecenie z opcją `-help`:</span><span class="sxs-lookup"><span data-stu-id="db396-119">To see the available options for VsDevCmd.BAT, run the command with the `-help` option:</span></span>

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a><span data-ttu-id="db396-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db396-120">See also</span></span>

- [<span data-ttu-id="db396-121">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="db396-121">Command-line Building With csc.exe</span></span>](./command-line-building-with-csc-exe.md)
