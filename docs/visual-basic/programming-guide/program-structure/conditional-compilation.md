---
title: Kompilacja warunkowa w Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 559380dc9baceb2fba4dca782e83f335f1bcd92d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="conditional-compilation-in-visual-basic"></a>Kompilacja warunkowa w Visual Basic
W *kompilacja warunkowa*, konkretnego bloki kodu w programie są kompilowane selektywnie, podczas gdy inne są ignorowane.  
  
 Na przykład można zapisać debugowania instrukcji, które porównania szybkość różne podejścia do tego samego zadania programowania, lub może być do zlokalizowania aplikacji dla wielu języków. Kompilacja warunkowa instrukcje są przeznaczone do uruchamiania w czasie kompilacji nie w czasie wykonywania.  
  
 Oznaczenia bloki kodu do skompilowania warunkowo z `#If...Then...#Else` dyrektywy. Na przykład, aby utworzyć język niemiecki i francuski wersje tej samej aplikacji w taki sam kod źródłowy, osadzić segmenty kodu specyficzne dla platformy w `#If...Then` instrukcje przy użyciu wstępnie zdefiniowanych stałe `FrenchVersion` i `GermanVersion`. W poniższym przykładzie pokazano sposób:  
  
 [!code-vb[VbVbalrConditionalComp#5](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/conditional-compilation_1.vb)]  
  
 Jeśli ustawisz wartość `FrenchVersion` Stała kompilacji warunkowej na `True` w czasie kompilacji jest skompilowany kod warunkowego Francuska wersja językowa. Jeśli ustawisz wartość `GermanVersion` stała przeznaczona do `True`, kompilator używa niemiecka wersja językowa. Jeśli nie ustawiono `True`, kod w ciągu ostatnich `Else` blokowanie działa.  
  
> [!NOTE]
>  Autocompletion spowoduje nieprawidłowe działanie podczas edytowania kodu i użycie dyrektywy warunkowej kompilacji, jeśli kod nie jest częścią bieżącej gałęzi.  
  
## <a name="declaring-conditional-compilation-constants"></a>Deklarowanie stałych kompilacja warunkowa  
 Kompilacja warunkowa stałe można ustawić w jeden z trzech sposobów:  
  
-   W **Projektant projektu**  
  
-   W wierszu polecenia, korzystając z wiersza polecenia kompilatora  
  
-   W kodzie  
  
 Kompilacja warunkowa stałe ma specjalne zakresu i nie można uzyskać dostępu z standardowego kodu. Zakres Stała kompilacji warunkowej zależy od sposobu jest ustawiona. W poniższej tabeli wymieniono zakresu stałe zadeklarowane za pomocą każdego z trzech sposobów wymienionych powyżej.  
  
|Ustawianie stałej|Zakres stała|  
|---|---|  
|**Projektant projektu**|Publicznego do wszystkich plików w projekcie|  
|Wiersz polecenia|Publiczny, aby wszystkie pliki przekazywane do wiersza polecenia kompilatora|  
|`#Const`instrukcji w code|Prywatny do pliku, w którym jest zadeklarowana|  
  
|Aby ustawić stałe w Projektancie projektu|  
|---|  
|— Przed utworzeniem pliku wykonywalnego, należy ustawić stałe **projektanta projektu** , postępując zgodnie z krokami opisanymi w [właściwościami Zarządzanie projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties).|  
  
|Aby ustawić stałe w wierszu polecenia|  
|---|  
|-Użyj **/d** przełącznik, aby wprowadzić stałe kompilacja warunkowa, jak w poniższym przykładzie:<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     Miejsce nie jest wymagany między **/d** przełącznika i pierwszy stałą. Aby uzyskać więcej informacji, zobacz [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).<br />     Deklaracje wiersza polecenia zastąpienia w deklaracjach **projektanta projektu**, ale nie usuwaj je. Argumenty ustawione **projektanta projektu** będą obowiązywać przez kolejne kompilacje.<br />     Podczas zapisywania stałe w kodu, Brak reguł strict klienckiemu, ich umieszczania, ponieważ ich zakres jest cały moduł, w którym jest zadeklarowany.|  
  
|Aby ustawić stałe w kodzie|  
|---|  
|-Umieść stałe w bloku deklaracji modułu, w którym są używane. Dzięki temu kodu organizowane i łatwiejsze do odczytania.|  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|---|---|  
|[Struktura programu i konwencje związane z kodami](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|Zawiera sugestie dotyczące dzięki kodu można łatwo odczytać i obsługa.|  
  
## <a name="reference"></a>Tematy pomocy  
 [#Const-dyrektywa](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [#If... Then... #Else — dyrektywy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
