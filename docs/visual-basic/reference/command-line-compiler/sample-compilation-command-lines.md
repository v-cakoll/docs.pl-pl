---
title: Kompilacja przykładów — wiersze poleceń (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
ms.openlocfilehash: b7879c23bc64269c793c21b61b84d6f0fd4bdc24
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046292"
---
# <a name="sample-compilation-command-lines-visual-basic"></a>Przykładowe wiersze poleceń kompilacji (Visual Basic)

Jako alternatywę do kompilowania Visual Basic programów z poziomu programu Visual Studio można kompilować z wiersza polecenia, aby tworzyć pliki wykonywalne (exe) lub pliki bibliotek dołączanych dynamicznie (. dll).

Kompilator wiersza polecenia Visual Basic obsługuje kompletny zestaw opcji kontrolujących pliki wejściowe i wyjściowe, zestawy oraz opcje debugowania i preprocesora. Każda opcja jest dostępna w dwóch niezmienionych formularzach `-option` : `/option`i. Ta dokumentacja zawiera tylko `-option` formularz.

Poniższa tabela zawiera listę przykładowych wierszy poleceń, które można modyfikować do własnych potrzeb.

|Zadanie|Zastosowanie|
|--------|---------|
|Kompiluj plik. vb i Utwórz plik. exe|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|
|Kompiluj plik. vb i Utwórz plik. dll|`vbc -target:library File.vb`|
|Kompiluj plik. vb i Utwórz my. exe|`vbc -out:My.exe File.vb`|
|Kompiluj plik. vb i Utwórz bibliotekę i zestaw odwołań o nazwie File. dll|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|Kompiluj wszystkie pliki Visual Basic w bieżącym katalogu z optymalizacjami na i `DEBUG` zdefiniowanym symbolem, wytwarzając plik2. exe|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|
|Kompiluj wszystkie pliki Visual Basic w bieżącym katalogu, generując wersję debugową plik2. dll bez wyświetlania logo lub ostrzeżeń|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|
|Kompiluj wszystkie pliki Visual Basic w bieżącym katalogu na coś. dll|`vbc -target:library -out:Something.dll *.vb`|

> [!TIP]
> Podczas kompilowania projektu przy użyciu programu Visual Studio IDE można wyświetlić informacje o skojarzonym poleceniu **VBC** z jego opcjami kompilatora w oknie danych wyjściowych. Aby wyświetlić te informacje, Otwórz okno [dialogowe Opcje, projekty i rozwiązania, skompiluj i uruchom](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), a następnie ustaw poziom szczegółowości **danych wyjściowych kompilacji projektu programu MSBuild** na **normalny** lub wyższy.

## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
