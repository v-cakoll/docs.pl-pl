---
title: Kompilacja warunkowa w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 4698435cb2ab15d16d8a8a898a01a9ffbc4f69c2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64639812"
---
# <a name="conditional-compilation-in-visual-basic"></a>Kompilacja warunkowa w Visual Basic
W *kompilacji warunkowej*, określonych bloków kodu w programie są kompilowane selektywnie, podczas gdy inne są ignorowane.  
  
 Na przykład możesz chcieć napisać debugowania instrukcje pozwalające porównać szybkość różne podejścia do tego samego zadania programowania lub możesz chcieć Lokalizuj aplikację dla wielu języków. Instrukcje kompilacji warunkowej są zaprojektowane do uruchamiania w czasie kompilacji, a nie w czasie wykonywania.  
  
 Oznaczenia bloki kodu, aby warunkowo być skompilowana przy użyciu `#If...Then...#Else` dyrektywy. Na przykład, aby utworzyć język niemiecki i francuski wersji tej samej aplikacji w taki sam kod źródłowy, osadzanie segmenty kodu specyficznego dla platformy w `#If...Then` instrukcji przy użyciu wstępnie zdefiniowanych stałych `FrenchVersion` i `GermanVersion`. Poniższy przykład pokazuje, jak:  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 Jeśli ustawisz wartość `FrenchVersion` Stała kompilacji warunkowej do `True` w czasie kompilacji jest skompilowany kod warunkowy Francuska wersja językowa. Jeśli ustawisz wartość `GermanVersion` stała przeznaczona do `True`, kompilator używa niemiecka wersja językowa. Jeśli nie ustawiono `True`, kod w ciągu ostatnich `Else` block przebiegów.  
  
> [!NOTE]
>  Automatycznego uzupełniania będzie działanie podczas edytowania kodu i za pomocą dyrektywy kompilacji warunkowej, jeśli kod nie jest częścią bieżącej gałęzi.  
  
## <a name="declaring-conditional-compilation-constants"></a>Deklarowanie stałych kompilacji warunkowej  
 Stałe kompilacji warunkowej można ustawić w jeden z trzech sposobów:  
  
- W **Projektant projektu**  
  
- W wierszu polecenia, korzystając z wiersza polecenia kompilatora  
  
- W kodzie  
  
 Stałe kompilacji warunkowej mają specjalne zakres i nie są dostępne od standardowego kodu. Zakres Stała kompilacji warunkowej jest zależna od sposób, który jest ustawiony. W poniższej tabeli wymieniono zakres stałe zadeklarowane za pomocą każdego z trzech sposobów wymienionych powyżej.  
  
|Ustawianie — stała|Zakres — stała|  
|---|---|  
|**Projektant projektu**|Publiczne do wszystkich plików w projekcie|  
|Wiersz polecenia|Publiczne do wszystkich plików przekazywane do wiersza polecenia kompilatora|  
|`#Const` instrukcji w kodzie|Prywatne dla pliku, w której jest zadeklarowana|  
  
|Aby ustawić stałe w Projektancie projektu|  
|---|  
|— Przed utworzeniem pliku wykonywalnego, należy ustawić stałe w **projektanta projektu** postępując zgodnie z krokami opisanymi w [właściwościami Zarządzanie projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties).|  
  
|Aby ustawić stałe w wierszu polecenia|  
|---|  
|-Użyj **/d** przełącznik, aby wprowadzić stałe kompilacji warunkowej, jak w poniższym przykładzie:<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     Miejsce nie jest wymagany między **/d** przełącznika i pierwszy stałą. Aby uzyskać więcej informacji, zobacz [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).<br />     Deklaracje wiersza polecenia zastępują wprowadzonego w deklaracji **projektanta projektu**, ale nie usuwaj je. Argumenty ustawione **projektanta projektu** będą używane w kolejnych kompilacjach.<br />     Podczas pisania stałe w sam kod, Brak reguł strict do ich umieszczania ich zakres jest cały moduł, w którym są one zgłoszone.|  
  
|Aby ustawić stałe w kodzie|  
|---|  
|— Umieść stałych w bloku deklaracja modułu, w którym są używane. Dzięki temu kod zorganizowany i łatwiejsza do odczytania.|  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|---|---|  
|[Konwencje dotyczące struktury programów i kodu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|Zawiera sugestie dotyczące wprowadzania kodu można łatwo odczytać i obsługa.|  
  
## <a name="reference"></a>Tematy pomocy  
 [#Const, dyrektywa](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [#If...Then...#Else, dyrektywy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
