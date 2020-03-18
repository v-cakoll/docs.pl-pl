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
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>Porada: ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio

Plik VsDevCmd.bat ustawia odpowiednie zmienne środowiskowe, aby włączyć kompilacje wiersza polecenia.

> [!NOTE]
> Visual Studio 2015 i wcześniejsze wersje używane VSVARS32.bat, nie VsDevCmd.bat w tym samym celu. Ten plik był przechowywany w folderze\\\Program Files\Microsoft Visual Studio*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.

Jeśli bieżąca wersja programu Visual Studio jest zainstalowana na komputerze, który ma również wcześniejszą wersję programu Visual Studio, nie należy uruchamiać vsdevcmd.bat i VSVARS32. BAT z różnych wersji w tym samym oknie wiersza polecenia. Zamiast tego należy uruchomić polecenie dla każdej wersji w swoim własnym oknie.

### <a name="to-run-vsdevcmdbat"></a>Aby uruchomić vsdevcmd.BAT

1. Z menu **Start** otwórz **wiersz polecenia dewelopera dla programu VS 2019**.  Znajduje się w folderze **Visual Studio 2019.**

2. Zmień na \Program Files\Microsoft\\Visual Studio*Version*\\*Offering*\Common7\Tools or \Program\\Files (x86)\Microsoft Visual Studio*Version*\\*Offering*\Common7\Tools subdirectory of your installation.  (*Wersja* jest *2019* dla bieżącej wersji. *Oferta* jest jednym z *Przedsiębiorstw,* *Zawodowych* lub *Społeczności*.)

3. Uruchom VsDevCmd.bat wpisując **VsDevCmd**.

    > [!CAUTION]
    > VsDevCmd.bat może się różnić w zależności od komputera. Nie należy zastępować brakującego lub uszkodzonego pliku VsDevCmd.bat na vsdevcmd.bat z innego komputera. Zamiast tego uruchom ponownie instalatora, aby zastąpić brakujący plik.

### <a name="available-options-for-vsdevcmdbat"></a>Dostępne opcje dla VsDevCmd.BAT

Aby wyświetlić dostępne opcje dla VsDevCmd.BAT, `-help` uruchom polecenie z opcją:

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a>Zobacz też

- [Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe](./command-line-building-with-csc-exe.md)
