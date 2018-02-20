---
title: "Porada: Ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio"
ms.date: 09/29/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
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
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 298006629bedf33e4d2521a88c010fcce824585c
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2018
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>Porada: Ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio

Plik VsDevCmd.bat ustawienie zmiennych środowiskowych odpowiednie, aby włączyć kompilacji z wiersza polecenia. Aby uzyskać więcej informacji o VsDevCmd.bat, zobacz [artykułu bazy wiedzy Q248802](https://support.microsoft.com/help/248802/you-receive-the-out-of-environment-space-error-message-when-you-execut).  

> [!NOTE]
> Plik VsDevCmd.bat jest nowy plik oferowane przez program Visual Studio 2017 r. Visual Studio 2015 i wcześniejszych wersjach używane VSVARS32.bat do takiej obsługi. Ten plik został zapisany w Visual Studio \Program Files\Microsoft\\*wersji*\Common7\Tools lub Program Files (x86) \Microsoft Visual Studio\\*wersji*\Common7\Tools.
  
Jeśli bieżącą wersję programu Visual Studio jest zainstalowany na komputerze, który ma także wcześniejszej wersji programu Visual Studio, nie należy uruchamiać VsDevCmd.bat i VSVARS32. BAT z różnych wersji w oknie wiersza polecenia. Zamiast tego należy uruchomić polecenie dla każdej wersji w osobnym oknie.
  
### <a name="to-run-vsdevcmdbat"></a>Aby uruchomić VsDevCmd.BAT  
  
1.  Z **Start** menu, otwórz **wiersz polecenia dla programu VS 2017 deweloperów**.  Jest on **programu Visual Studio 2017** folderu.
  
2.  Zmiany do programu Visual Studio \Program Files\Microsoft\\*wersji*\\*oferty*\Common7\Tools lub \Program pliki (x86) \Microsoft Visual Studio\\ *Wersji*\\*oferty*podkatalogu \Common7\Tools instalacji.  (*Wersji* jest *2017* dla bieżącej wersji. *Oferta* jest jednym z *Enterprise*, *Professional* lub *społeczności*.)
  
3.  Uruchom VsDevCmd.bat wpisując **VsDevCmd**.  
  
    > [!CAUTION]
    >  VsDevCmd.bat może się różnić między komputerami. Nie zastępuj brakujących lub uszkodzonych plików VsDevCmd.bat VsDevCmd.bat z innego komputera. Zamiast tego Uruchom ponownie Instalatora, aby zastąpić brakujący plik.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
