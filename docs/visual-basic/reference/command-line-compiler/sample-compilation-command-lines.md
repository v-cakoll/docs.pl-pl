---
title: Kompilacja przykładów — wiersze poleceń (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf20e2916efd2eb10065be22c319e34ddb2bda9a
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="sample-compilation-command-lines-visual-basic"></a>Polecenie kompilacja przykładów — wiersze (Visual Basic)
Alternatywą wobec kompilowanie programów Visual Basic z poziomu [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], będzie można kompilować z poziomu wiersza polecenia, aby utworzyć pliki pliku wykonywalnego (.exe) lub biblioteki dołączanej (dynamicznie dll).  
  
 Kompilator wiersza polecenia programu Visual Basic obsługuje pełny zestaw opcji kontroli danych wejściowych i wyjściowych plików, zestawy i debugowania i opcje preprocesora. Każda opcja jest dostępna w dwóch formach wymienne: `-option` i `/option`. Ta dokumentacja zawiera tylko `-option` formularza.  
  
 W poniższej tabeli przedstawiono niektóre przykładowe wiersze poleceń, które można modyfikować na własny użytek.  
  
|Do|Zastosowanie|  
|--------|---------|  
|Kompiluj File.vb i Utwórz File.exe|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|Kompiluj File.vb i Utwórz File.dll|`vbc -target:library File.vb`|  
|Kompiluj File.vb i Utwórz My.exe|`vbc -out:My.exe File.vb`|  
|Kompilowanie File.vb i tworzyć biblioteki oraz zestawu odwołania o nazwie File.dll|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|Kompiluj wszystkie pliki Visual Basic w bieżącym katalogu z optymalizacji na i `DEBUG` symbol zdefiniowany, tworzenie File2.exe|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|Kompiluj wszystkie pliki Visual Basic w bieżącym katalogu, tworzenie wersji debugowania File2.dll bez wyświetlanie logo lub ostrzeżenia|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|Kompiluj wszystkie pliki Visual Basic w bieżącym katalogu do Something.dll|`vbc -target:library -out:Something.dll *.vb`|  
  
> [!TIP]
>  Podczas tworzenia projektu za pomocą środowiska IDE programu Visual Studio, można wyświetlić informacje o skojarzonych **vbc** z jego — opcje kompilatora w oknie danych wyjściowych. Aby wyświetlić te informacje, otwórz [okno dialogowe Opcje, projekty i rozwiązania, kompilacji i uruchom](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), a następnie ustaw **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild** do **normalny** lub wyższy poziom szczegółowości.   
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
