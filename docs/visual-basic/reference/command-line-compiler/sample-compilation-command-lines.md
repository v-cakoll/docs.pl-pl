---
title: "Kompilacja przykładów — wiersze poleceń (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e168d40a22ca3737bee18f966df95988a2736a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sample-compilation-command-lines-visual-basic"></a>Kompilacja przykładów — wiersze poleceń (Visual Basic)
Alternatywą wobec kompilowanie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programów z poziomu [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], będzie można kompilować z poziomu wiersza polecenia, aby utworzyć pliki pliku wykonywalnego (.exe) lub biblioteki dołączanej (dynamicznie dll).  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompletny zestaw opcje sterujące plików wejściowych i wyjściowych, zestawy i debugowania i opcje preprocesora obsługuje kompilatora wiersza polecenia. Każda opcja jest dostępna w dwóch formach wymienne: `-``option` i `/``option`. Ta dokumentacja zawiera tylko `/``option` formularza.  
  
 W poniższej tabeli przedstawiono niektóre przykładowe wiersze poleceń, które można modyfikować na własny użytek.  
  
|Do|Zastosowanie|  
|--------|---------|  
|Kompiluj File.vb i Utwórz File.exe|`vbc /reference:Microsoft.VisualBasic.dll File.vb`|  
|Kompiluj File.vb i Utwórz File.dll|`vbc /target:library File.vb`|  
|Kompiluj File.vb i Utwórz My.exe|`vbc /out:My.exe File.vb`|  
|Kompiluj wszystkie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pliki w bieżącym katalogu z optymalizacji i `DEBUG` symbol zdefiniowany, tworzenie File2.exe|`vbc /define:DEBUG=1 /optimize /out:File2.exe *.vb`|  
|Kompiluj wszystkie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] plików w bieżącym katalogu, tworzenie wersji debugowania File2.dll bez wyświetlanie logo lub ostrzeżenia|`vbc /target:library /out:File2.dll /nowarn /nologo /debug *.vb`|  
|Kompiluj wszystkie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] plików w bieżącym katalogu do Something.dll|`vbc /target:library /out:Something.dll *.vb`|  
  
 W przypadku kompilowania kodu w wierszu polecenia, należy jawnie odwołać Microsoft [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] biblioteki wykonawczej za pośrednictwem `/reference` — opcja kompilatora.  
  
> [!TIP]
>  Podczas tworzenia projektu za pomocą środowiska IDE programu Visual Studio, można wyświetlić informacje o skojarzonych **vbc** z jego — opcje kompilatora w oknie danych wyjściowych. Aby wyświetlić te informacje, otwórz [okno dialogowe Opcje, projekty i rozwiązania, kompilacji i uruchom](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), a następnie ustaw **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild** do **normalny** lub wyższy poziom szczegółowości. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
