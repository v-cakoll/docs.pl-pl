---
title: -platform (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
ms.openlocfilehash: d4cb4e219189deb6048692822c9245c5a03c5675
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-platform-c-compiler-options"></a>-platform (opcje kompilatora C#)
Określa, która wersja z środowiska uruchomieniowego języka wspólnego (CLR) można uruchomić zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-platform:string  
```  
  
#### <a name="parameters"></a>Parametry  
 `string`  
 anycpu (domyślna), anycpu32bitpreferred, ARM, x 64, x86 lub Itanium.  
  
## <a name="remarks"></a>Uwagi  
  
-   **anycpu** (ustawienie domyślne) kompiluje używanemu zestawowi można uruchomić na dowolnej platformie. Aplikacja działa jako procesu 64-bitowego, jeśli to możliwe i powraca do 32-bitowego, gdy tylko ten tryb jest dostępny.  
  
-   **anycpu32bitpreferred** kompiluje używanemu zestawowi można uruchomić na dowolnej platformie. Aplikacja działa w trybie 32-bitowych systemach, które obsługują zarówno 64-bitowe i 32-bitowych aplikacji. Można określić tę opcję tylko w przypadku projektów przeznaczonych .NET Framework 4.5.  
  
-   **ARM** kompiluje z zestawu do uruchomienia na komputerze, na które ma procesor Advanced RISC Machine (ARM).  
  
-   **x64** kompiluje z zestawu do uruchomienia na komputerze, który obsługuje zestaw instrukcji AMD64 lub EM64T przez 64-bitowym CLR.  
  
-   **x86** kompiluje z zestawu do uruchomienia przez środowisko CLR 32-bitowy, x86 zgodna.  
  
-   **Itanium** kompiluje z zestawu do uruchomienia w 64-bitowym CLR na komputerze z procesorem Itanium.  
  
 W 64-bitowym systemie operacyjnym Windows:  
  
-   Zestawy są kompilowane przy użyciu **-platform: x 86** wykonania na 32-bitowego środowiska CLR uruchomione w emulatorze WOW64.  
  
-   Biblioteki DLL są kompilowane przy użyciu **-platformy: anycpu** wykonuje w tej samej CLR jako proces, do którego został załadowany.  
  
-   Pliki wykonywalne, które są kompilowane przy użyciu **-platformy: anycpu** wykonania na 64-bitowym CLR.  
  
-   Pliki wykonywalne skompilowane z **-platform: anycpu32bitpreferred** wykonania na 32-bitowym CLR.  
  
 **Anycpu32bitpreferred** ustawienie jest prawidłowe tylko dla pliku wykonywalnego (. Pliki z rozszerzeniem EXE) który wymaga platformy .NET Framework 4.5.  
  
 Aby uzyskać więcej informacji dotyczących tworzenia aplikacji do uruchamiania w systemie Windows 64-bitowym systemie operacyjnym, zobacz [aplikacji 64-bitowych](../../../framework/64-bit-apps.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz **właściwości** strony dla projektu.  
  
2.  Kliknij przycisk **kompilacji** strony właściwości.  
  
3.  Modyfikowanie **platformy docelowej** właściwości oraz dla projektów przeznaczonych dla platformy .NET Framework 4.5, zaznacz lub wyczyść **preferowane jest 32-bitowych** pole wyboru.  
  
 **Uwaga - platformy** nie jest dostępna w środowisku projektowania w programie Visual C# Express.  
  
 Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie **-platformy** opcję, aby określić, że aplikacja powinien być wykonywany przez środowisko CLR 64-bitowym na 64-bitowym systemie operacyjnym Windows.  
  
```console  
csc -platform:anycpu filename.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
