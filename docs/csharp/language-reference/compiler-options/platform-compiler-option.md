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
ms.openlocfilehash: ae2305e0f5d3ca4de386d8e7933a1107450e0be4
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59341507"
---
# <a name="-platform-c-compiler-options"></a>-platform (opcje kompilatora C#)
Określa, która wersja środowiska uruchomieniowego języka w wspólnego (CLR) można uruchomić zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-platform:string  
```  
  
## <a name="parameters"></a>Parametry  
 `string`  
 (ustawienie domyślne) anycpu, anycpu32bitpreferred, ARM, x 64, x86 lub Itanium.  
  
## <a name="remarks"></a>Uwagi  
  
-   **anycpu** (ustawienie domyślne), kompiluje swoim zestawie, można uruchomić na dowolnej platformie. Aplikacja działa jako proces 64-bitowych, jeśli to możliwe i powraca do 32-bitowych, gdy ten tryb jest dostępny tylko.  
  
-   **anycpu32bitpreferred** kompiluje swoim zestawie, można uruchomić na dowolnej platformie. Aplikacja działa w trybie 32-bitowych w systemach, które obsługują aplikacje 32-bitowych i 64-bitowych. Można określić tę opcję, tylko dla projektów, których platformą docelową .NET Framework 4.5.  
  
-   **ARM** kompiluje zestaw do uruchomienia na komputerze, który ma procesor Advanced RISC Machine (ARM).  
  
-   **ARM64** kompiluje zestaw do uruchomienia w 64-bitowym CLR na komputerze, który ma procesor Advanced RISC Machine (ARM), który obsługuje A64 — zestaw instrukcji.  

-   **x64** kompiluje zestaw do uruchomienia w 64-bitowym CLR na komputerze, który obsługuje zestaw instrukcji AMD64 lub EM64T.  
  
-   **x86** kompiluje zestawu do uruchomienia przez środowisko CLR 32-bitowy, x86 zgodny.  
  
-   **Itanium** kompiluje zestaw do uruchomienia w 64-bitowym CLR na komputerze z procesorem Itanium.  
  
 W 64-bitowym systemie operacyjnym Windows:  
  
-   Zestawy skompilowane z **-platform: x 86** wykonania na 32-bitowe środowisko CLR, uruchamianie w emulatorze WOW64.  
  
-   Biblioteki DLL są kompilowane przy użyciu **— platforma: anycpu** wykonuje na tej samej CLR jako proces, do którego jest ładowany.  
  
-   Pliki wykonywalne, które są kompilowane przy użyciu **— platforma: anycpu** wykonania na 64-bitowe środowisko CLR.  
  
-   Pliki wykonywalne skompilowany przy użyciu **-platform: anycpu32bitpreferred** wykonania na 32-bitowe środowisko CLR.  
  
 **Anycpu32bitpreferred** ustawienie jest prawidłowy tylko w przypadku pliku wykonywalnego (. Pliki z rozszerzeniem EXE) która wymaga programu .NET Framework 4.5.  
  
 Aby uzyskać więcej informacji na temat tworzenia aplikacji, systemem Windows 64-bitowym systemie operacyjnym, zobacz [aplikacji 64-bitowych](../../../framework/64-bit-apps.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz **właściwości** strony dla projektu.  
  
2. Kliknij przycisk **kompilacji** stronę właściwości.  
  
3. Modyfikowanie **platformę docelową** właściwości oraz dla projektów przeznaczonych dla platformy .NET Framework 4.5, zaznacz lub wyczyść **Preferuj 32-bitowe** pole wyboru.  
  
 **Uwaga — Platforma** nie jest dostępna w środowisku deweloperskim w programie Visual C# Express.  
  
 Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać **— Platforma** opcję, aby określić, że aplikacja powinien być wykonywany przez środowisko CLR 64-bitowym na 64-bitowym systemie operacyjnym Windows.  
  
```console  
csc -platform:anycpu filename.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
