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
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>Porada: ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio

Plik VsDevCmd. bat ustawia odpowiednie zmienne środowiskowe, aby włączyć kompilacje w wierszu polecenia.

> [!NOTE]
> Program Visual Studio 2015 i starsze wersje używały VSVARS32. bat, a nie VsDevCmd. bat w tym samym celu. Ten plik był przechowywany w folderze \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools lub Program Files (x86) \Microsoft Visual Studio\\*wersja*\Common7\Tools.

Jeśli bieżąca wersja programu Visual Studio jest zainstalowana na komputerze, który ma również starszą wersję programu Visual Studio, nie należy uruchamiać VsDevCmd. bat i VSVARS32. BAT z różnych wersji w tym samym oknie wiersza polecenia. Zamiast tego należy uruchomić polecenie dla każdej wersji w osobnym oknie.

### <a name="to-run-vsdevcmdbat"></a>Aby uruchomić VsDevCmd. BAT

1. Z menu **Start** Otwórz **wiersz polecenia dla deweloperów dla programu vs 2019**.  Znajduje się w folderze **programu Visual Studio 2019** .

2. Przejdź do folderu \Program Files\Microsoft Visual Studio\\*wersja*\\*oferty*\Common7\Tools lub \Program Files (x86) \Microsoft Visual Studio\\*wersja*\\*oferowanie*\Common7\Tools podkatalogu instalacji.  (*Wersja* *2019* dla bieżącej wersji. *Oferta* jest jedną z *przedsiębiorstw*, *profesjonalistów* lub *społeczności*.)

3. Uruchom VsDevCmd. bat, wpisując **VsDevCmd**.

    > [!CAUTION]
    > VsDevCmd. bat może się różnić od komputera do komputera. Nie zamieniaj brakującego lub uszkodzonego pliku VsDevCmd. bat z VsDevCmd. bat z innego komputera. Zamiast tego ponownie uruchom Instalatora, aby zastąpić brakujący plik.

### <a name="available-options-for-vsdevcmdbat"></a>Dostępne opcje dla VsDevCmd. BAT

Aby wyświetlić dostępne opcje dla VsDevCmd. BAT, uruchom polecenie z opcją `-help`:

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a>Zobacz także

- [Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe](./command-line-building-with-csc-exe.md)
