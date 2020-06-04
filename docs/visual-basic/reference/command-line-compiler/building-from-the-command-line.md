---
title: Tworzenie z wiersza polecenia
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
ms.openlocfilehash: ec6ae3328c2042af950d1ee78a33d3de97219f10
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414301"
---
# <a name="building-from-the-command-line-visual-basic"></a>Tworzenie z wiersza polecenia (Visual Basic)

Projekt Visual Basic składa się z co najmniej jednego oddzielnego pliku źródłowego. Podczas procesu znanego jako kompilacja te pliki są łączone w jeden pakiet — pojedynczy plik wykonywalny, który może być uruchamiany jako aplikacja.

Visual Basic udostępnia kompilator wiersza polecenia jako alternatywę do kompilowania programów z poziomu zintegrowanego środowiska programistycznego (IDE) programu Visual Studio. Kompilator wiersza polecenia jest przeznaczony do sytuacji, w których nie jest wymagany pełny zestaw funkcji w środowisku IDE — na przykład podczas korzystania z programu lub zapisywania na komputerach z ograniczoną ilością pamięci systemowej lub miejscem do magazynowania.

Aby kompilować pliki źródłowe z poziomu środowiska IDE programu Visual Studio, wybierz polecenie **Kompiluj** z menu **kompilacja** .

> [!TIP]
> Podczas kompilowania plików projektu przy użyciu programu Visual Studio IDE można wyświetlić informacje o skojarzonym poleceniu **VBC** i jego przełącznikach w oknie danych wyjściowych. Aby wyświetlić te informacje, Otwórz okno [dialogowe Opcje, projekty i rozwiązania, skompiluj i uruchom](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), a następnie ustaw poziom szczegółowości **danych wyjściowych kompilacji projektu programu MSBuild** na **normalny** lub wyższy. Aby uzyskać więcej informacji, zobacz [jak: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](/visualstudio/ide/how-to-view-save-and-configure-build-log-files).

Pliki projektu (. vbproj) można kompilować w wierszu polecenia przy użyciu programu MSBuild. Aby uzyskać więcej informacji, zobacz informacje [dotyczące wiersza polecenia](/visualstudio/msbuild/msbuild-command-line-reference) i [Przewodnik: korzystanie z programu MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).

## <a name="in-this-section"></a>W tej sekcji

[Instrukcje: wywoływanie kompilatora wiersza polecenia](how-to-invoke-the-command-line-compiler.md) \
Opisuje sposób wywoływania kompilatora wiersza polecenia w wierszu systemu MS-DOS lub z określonego podkatalogu.

[Przykładowe wiersze poleceń kompilacji](sample-compilation-command-lines.md) \
Zawiera listę przykładowych wierszy poleceń, które można modyfikować do własnych potrzeb.

## <a name="related-sections"></a>Sekcje pokrewne

[Kompilator wiersza polecenia Visual Basic](index.md) \
Zawiera listy opcji kompilatora, zorganizowane w porządku alfabetycznym lub według przeznaczenie.

[Kompilacja warunkowa](../../programming-guide/program-structure/conditional-compilation.md) \
Opisuje sposób kompilowania określonych sekcji kodu.

[Kompilowanie i czyszczenie projektów i rozwiązań w programie Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) \
W tym artykule opisano sposób organizowania, co zostanie uwzględnione w różnych kompilacjach, wybrać właściwości projektu i upewnić się, że projekty kompilują się w poprawnej kolejności.
