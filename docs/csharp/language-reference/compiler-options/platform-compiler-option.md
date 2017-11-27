---
title: -platform (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
caps.latest.revision: "46"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d03e12ae60b9a0145dcb58765ae00f756f84ca56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="platform-c-compiler-options"></a>/platform (opcje kompilatora C#)
Określa, która wersja środowisko uruchomieniowe języka wspólnego (CLR) można uruchomić zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
/platform:string  
```  
  
#### <a name="parameters"></a>Parametry  
 `string`  
 anycpu (domyślna), anycpu32bitpreferred, ARM, x 64, x86 lub Itanium.  
  
## <a name="remarks"></a>Uwagi  
  
-   **anycpu** (ustawienie domyślne) kompiluje używanemu zestawowi można uruchomić na dowolnej platformie. Aplikacja działa jako procesu 64-bitowego, jeśli to możliwe i powraca do 32-bitowego, gdy tylko ten tryb jest dostępny.  
  
-   **anycpu32bitpreferred** kompiluje używanemu zestawowi można uruchomić na dowolnej platformie. Aplikacja działa w trybie 32-bitowych systemach, które obsługują zarówno 64-bitowe i 32-bitowych aplikacji. Można określić tę opcję tylko w przypadku projektów przeznaczonych .NET Framework 4.5.  
  
-   **ARM** kompiluje z zestawu do uruchomienia na komputerze, na które ma procesor Advanced RISC Machine (ARM).  
  
-   **x64** kompiluje z zestawu do uruchomienia na komputerze, który obsługuje zestaw instrukcji AMD64 lub EM64T przez 64-bitowe środowisko uruchomieniowe języka wspólnego.  
  
-   **x86** kompiluje z zestawu do uruchomienia przez 32-bitowy, x86 zgodnego wykonywalnych języka wspólnego.  
  
-   **Itanium** kompiluje z zestawu do uruchomienia w 64-bitowego środowiska CLR na komputerze z procesorem Itanium.  
  
 W 64-bitowym systemie operacyjnym Windows:  
  
-   Zestawy są kompilowane przy użyciu **x 86** wykonania na 32-bitowego środowiska CLR uruchomione w emulatorze WOW64.  
  
-   Biblioteki DLL są kompilowane przy użyciu **/platform:anycpu** wykonuje w tej samej CLR jako proces, do którego został załadowany.  
  
-   Pliki wykonywalne, które są kompilowane przy użyciu **/platform:anycpu** wykonania na 64-bitowym CLR.  
  
-   Pliki wykonywalne skompilowane z **/platform: anycpu32bitpreferred** wykonania na 32-bitowym CLR.  
  
 **Anycpu32bitpreferred** ustawienie jest prawidłowe tylko dla pliku wykonywalnego (. Pliki z rozszerzeniem EXE) który wymaga platformy .NET Framework 4.5.  
  
 Aby uzyskać więcej informacji dotyczących tworzenia aplikacji do uruchamiania w systemie Windows 64-bitowym systemie operacyjnym, zobacz [aplikacji 64-bitowych](../../../framework/64-bit-apps.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz **właściwości** strony dla projektu.  
  
2.  Kliknij przycisk **kompilacji** strony właściwości.  
  
3.  Modyfikowanie **platformy docelowej** właściwości oraz dla projektów przeznaczonych dla platformy .NET Framework 4.5, zaznacz lub wyczyść **preferowane jest 32-bitowych** pole wyboru.  
  
 **Należy pamiętać, / platform** nie jest dostępna w środowisku projektowania w programie Visual C# Express.  
  
 Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie **/platform** opcję, aby określić, że aplikacja powinien być wykonywany przez środowisko CLR 64-bitowym na 64-bitowym systemie operacyjnym Windows.  
  
```console  
csc /platform:anycpu filename.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](index.md)  
 [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
