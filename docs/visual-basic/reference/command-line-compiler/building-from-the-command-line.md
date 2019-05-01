---
title: Tworzenie z wiersza polecenia (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 798baa90308c83e42b335635fb23a9983f5180fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61839387"
---
# <a name="building-from-the-command-line-visual-basic"></a>Tworzenie z wiersza polecenia (Visual Basic)
Projekt Visual Basic składa się z co najmniej jeden plik oddzielne źródło. W trakcie znane jako kompilacji te pliki są połączone razem w jednym pakiecie — pojedynczy plik wykonywalny, który może działać jako aplikacja.  
  
 Visual Basic zapewnia kompilatora wiersza polecenia jako alternatywę do kompilowania programów z w ramach programu Visual Studio zintegrowane środowisko programistyczne (IDE). Kompilator w wierszu polecenia jest przeznaczona dla sytuacji, w których nie wymagają pełnego zestawu funkcji w środowisku IDE — na przykład podczas są przy użyciu lub zapisywania dla komputerów z system ograniczoną pamięć lub miejsce do magazynowania.  
  
  Aby skompilować plików źródłowych z poziomu środowiska IDE programu Visual Studio, wybierz opcję **kompilacji** polecenia **kompilacji** menu.  
  
> [!TIP]
>  W przypadku tworzenia plików projektu za pomocą programu Visual Studio IDE, można wyświetlić informacje o skojarzonego **vbc** polecenia i jego przełączników w oknie danych wyjściowych. Aby wyświetlić te informacje, otwórz [okno dialogowe Opcje, projekty i rozwiązania, kompilacji i uruchomienia](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), a następnie ustaw **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild** do **normalny** lub wyższym poziomie szczegółowości. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](/visualstudio/ide/how-to-view-save-and-configure-build-log-files).  
  
 Pliki projektu (.vbproj) w wierszu polecenia można kompilować przy użyciu programu MSBuild. Aby uzyskać więcej informacji, zobacz [odwołanie do wiersza polecenia](/visualstudio/msbuild/msbuild-command-line-reference) i [instruktażu: Korzystanie z programu MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: wywoływanie kompilatora z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 Opisuje sposób wywoływanie kompilatora wiersza polecenia w trybie MS-DOS lub z określonego podkatalogu.  
  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 Zawiera listę przykładów — wiersze poleceń, które można modyfikować na własny użytek.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 Zawiera listę opcji kompilatora, uporządkowane alfabetycznie i według celu.  
  
 [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 Opisuje sposób skompilowania określonych sekcji kodu.  
  
 [Kompilowanie i czyszczenie projektów i rozwiązań w programie Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 Opisuje sposób organizowania, co zostanie uwzględniony w różne kompilacje, wybierz polecenie Właściwości projektu i upewnij się, że projekty są kompilowane w odpowiedniej kolejności.
