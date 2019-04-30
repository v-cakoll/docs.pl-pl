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
ms.openlocfilehash: 9eea7f76d386816aad060e9b99cea6b906a09ab9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662845"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>Instrukcje: ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio

Plik VsDevCmd.bat ustawia odpowiednie zmienne środowiskowe umożliwiające kompilacji z wiersza polecenia.

> [!NOTE]
> Plik VsDevCmd.bat jest nowy plik dostarczane z programem Visual Studio 2017. Program Visual Studio 2015 i starsze wersje używane VSVARS32.bat, w tym samym celu. Ten plik został zapisany w programie Visual Studio \Program Files\Microsoft\\*wersji*\Common7\Tools lub Program Files (x86) \Microsoft Visual Studio\\*wersji*\Common7\Tools.

Jeśli bieżącą wersję programu Visual Studio jest zainstalowany na komputerze, który ma także wcześniejszej wersji programu Visual Studio, nie należy uruchamiać VsDevCmd.bat i VSVARS32. BAT z różnych wersji, w tym samym oknie wiersza polecenia. Zamiast tego należy uruchamiać polecenie dla każdej wersji w osobnym oknie.

### <a name="to-run-vsdevcmdbat"></a>Aby uruchomić VsDevCmd.BAT

1. Z **Start** menu Otwórz **wiersz polecenia programisty dla programu VS 2017**.  Jest on **programu Visual Studio 2017** folderu.

2. Zmiany do programu Visual Studio \Program Files\Microsoft\\*wersji*\\*oferty*\Common7\Tools lub \Program pliki (x86) \Microsoft Visual Studio\\ *Wersji*\\*oferty*podkatalogu \Common7\Tools instalacji.  (*Wersji* jest *2017* dla bieżącej wersji. *Oferta* jest jednym z *Enterprise*, *Professional* lub *społeczności*.)

3. Uruchom VsDevCmd.bat, wpisując **VsDevCmd**.

    > [!CAUTION]
    > VsDevCmd.bat mogą się różnić między komputerami. Nie zastępuj uszkodzony lub plik VsDevCmd.bat VsDevCmd.bat z innego komputera. Zamiast tego Uruchom ponownie Instalatora, aby zastąpić brakujący plik.

### <a name="available-options-for-vsdevcmdbat"></a>Dostępne opcje VsDevCmd.BAT

Aby wyświetlić dostępne opcje VsDevCmd.BAT, uruchom polecenie `-help` opcji:

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a>Zobacz także

- [Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
