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
ms.openlocfilehash: c4c3214c4998afa23032347e08007f2f1933bba8
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181124"
---
# <a name="sample-compilation-command-lines-visual-basic"></a>Przykładowe wiersze poleceń kompilacji (Visual Basic)
Jako alternatywę do kompilowania programów Visual Basic z poziomu programu Visual Studio można kompilować z poziomu wiersza polecenia, aby wygenerować pliki wykonywalne (.exe) lub biblioteka dołączana dynamicznie (dll).  
  
 Kompilator wiersza polecenia programu Visual Basic obsługuje kompletny zestaw opcji, które kontroli danych wejściowych i wyjściowych plików, zestawów oraz debugowania i opcje preprocesora. Każda opcja jest dostępna w dwóch formach wymienne: `-option` i `/option`. Ta dokumentacja zawiera tylko `-option` formularza.  
  
 W poniższej tabeli wymieniono niektóre przykładowe wiersze poleceń, które można modyfikować na własny użytek.  
  
|Zadanie|Zastosowanie|  
|--------|---------|  
|Skompilować File.vb i utworzyć File.exe|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|Skompilować File.vb i utworzyć File.dll|`vbc -target:library File.vb`|  
|Skompilować File.vb i utworzyć My.exe|`vbc -out:My.exe File.vb`|  
|Skompilować File.vb i tworzyć biblioteki oraz o nazwie File.dll zestawu odwołania|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|Kompiluj wszystkie pliki języka Visual Basic w bieżącym katalogu, z optymalizacjami na i `DEBUG` symbol zdefiniowany, tworzenie File2.exe|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|Kompiluj wszystkie pliki języka Visual Basic w bieżącym katalogu, tworzenie wersji debugowania File2.dll bez wyświetlania logo lub ostrzeżenia|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|Kompiluj wszystkie pliki języka Visual Basic w bieżącym katalogu Something.dll|`vbc -target:library -out:Something.dll *.vb`|  
  
> [!TIP]
>  Gdy tworzysz projekt za pomocą środowiska IDE programu Visual Studio można wyświetlić informacje o skojarzonego **vbc** swoich opcje kompilatora w oknie danych wyjściowych polecenia. Aby wyświetlić te informacje, otwórz [okno dialogowe Opcje, projekty i rozwiązania, kompilacji i uruchomienia](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), a następnie ustaw **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild** do **normalny** lub wyższym poziomie szczegółowości.   
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
