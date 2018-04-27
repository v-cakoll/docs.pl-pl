---
title: Tworzenie z wiersza polecenia (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers [Visual Basic], invoking from command line
- command-line builds
- compiling source code
- command-line compilers [Visual Basic], Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1fd4054838925267647986a5166fd88037b17fae
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="building-from-the-command-line-visual-basic"></a>Tworzenie z wiersza polecenia (Visual Basic)
Projekt Visual Basic składa się z jednego lub więcej plików oddzielne źródło. W trakcie znany jako kompilacji te pliki zostaną połączone razem w jednym pakiecie — pojedynczy plik wykonywalny, który może działać jako aplikacja.  
  
 Visual Basic zapewnia kompilatora wiersza polecenia zamiast kompilowanie programów z poziomu [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] zintegrowane środowisko programistyczne (IDE). Kompilator wiersza polecenia jest przeznaczony do sytuacji, w których nie wymagają pełnego zestawu funkcji w środowisku IDE — na przykład po są przy użyciu lub zapisywania w przypadku komputerów z ograniczoną systemu pamięć lub miejsce do magazynowania.  
  
  Aby skompilować plików źródłowych z poziomu [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] IDE, wybierz **kompilacji** polecenie **kompilacji** menu.  
  
> [!TIP]
>  Podczas tworzenia plików projektu za pomocą środowiska IDE programu Visual Studio, można wyświetlić informacje o skojarzonych **vbc** polecenia i jego przełączników w oknie danych wyjściowych. Aby wyświetlić te informacje, otwórz [okno dialogowe Opcje, projekty i rozwiązania, kompilacji i uruchom](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), a następnie ustaw **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild** do **normalny** lub wyższy poziom szczegółowości. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).  
  
 Pliki projektu (.vbproj) w wierszu polecenia można skompilować przy użyciu programu MSBuild. Aby uzyskać więcej informacji, zobacz [dotyczące wiersza polecenia](/visualstudio/msbuild/msbuild-command-line-reference) i [wskazówki: przy użyciu programu MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: wywoływanie kompilatora z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 Opisuje sposób wywoływanie kompilatora wiersza polecenia w wierszu polecenia systemu MS-DOS lub z określonego podkatalogu.  
  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 Lista przykładów — wiersze poleceń, które można modyfikować na własny użytek.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 Zawiera listę opcji kompilatora, uporządkowane alfabetycznie lub według celu.  
  
 [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 Opisuje sposób kompilowania poszczególnych sekcji kodu.  
  
 [Kompilowanie i czyszczenie projektów i rozwiązań w programie Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 Opisuje sposób organizowania co mają być uwzględnieni w różnych wersjach, wybierz polecenie Właściwości projektu i upewnij się, że projekty kompilacji w odpowiedniej kolejności.
