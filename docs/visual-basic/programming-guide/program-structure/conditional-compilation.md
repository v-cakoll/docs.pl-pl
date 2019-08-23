---
title: Kompilacja warunkowa w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 1bee64568ff92468e29226a395f7e5335387e256
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945584"
---
# <a name="conditional-compilation-in-visual-basic"></a>Kompilacja warunkowa w Visual Basic
W *kompilacji warunkowej*poszczególne bloki kodu w programie są kompilowane wybiórczo, podczas gdy inne są ignorowane.  
  
 Na przykład możesz chcieć napisać instrukcje debugowania, które porównują szybkość różnych podejść do tego samego zadania programistycznego, lub można zlokalizować aplikację dla wielu języków. Instrukcje kompilacji warunkowej są przeznaczone do uruchamiania w czasie kompilacji, a nie w czasie wykonywania.  
  
 Należy zauważyć, `#If...Then...#Else` że bloki kodu mają być warunkowo kompilowane z dyrektywą. Aby na przykład utworzyć wersje językowe języka francuskiego i niemieckiego tej samej aplikacji z tego samego kodu źródłowego, segmenty kodu specyficzne dla platformy można osadzić `#If...Then` w instrukcjach korzystających `FrenchVersion` ze `GermanVersion`wstępnie zdefiniowanych stałych i. W poniższym przykładzie pokazano, jak:  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 Jeśli ustawisz wartość `FrenchVersion` stałej kompilacji warunkowej na `True` w czasie kompilacji, zostanie skompilowany kod warunkowy dla wersji francuskiej. Jeśli wartość `GermanVersion` stała jest ustawiona na `True`, kompilator używa wersji niemieckiej. Jeśli żaden z nich nie `True`jest ustawiony na, kod w `Else` ostatnim bloku zostanie uruchomiony.  
  
> [!NOTE]
> Funkcja autouzupełniania nie będzie działać podczas edytowania kodu i stosowania dyrektyw warunkowej kompilacji, jeśli kod nie jest częścią bieżącej gałęzi.  
  
## <a name="declaring-conditional-compilation-constants"></a>Deklarowanie stałych kompilacji warunkowej  
 Stałe kompilacji warunkowej można ustawić na jeden z trzech sposobów:  
  
- W **projektancie projektu**  
  
- W wierszu polecenia przy użyciu kompilatora wiersza polecenia  
  
- W kodzie  
  
 Stałe kompilacji warunkowej mają specjalny zakres i nie można uzyskać do niego dostępu z poziomu kodu standardowego. Zakres stałej kompilacji warunkowej zależy od sposobu jej ustawienia. W poniższej tabeli wymieniono zakres stałych zadeklarowanych przy użyciu każdego z trzech sposobów wymienionych powyżej.  
  
|Jak stała jest ustawiona|Zakres stałej|  
|---|---|  
|**Projektant projektu**|Publiczny dla wszystkich plików w projekcie|  
|Wiersz polecenia|Publiczny dla wszystkich plików przesłanych do kompilatora wiersza polecenia|  
|`#Const`Instrukcja w kodzie|Prywatny do pliku, w którym jest zadeklarowany|  
  
|Aby ustawić stałe w projektancie projektu|  
|---|  
|-Przed utworzeniem pliku wykonywalnego Ustaw stałe w **projektancie projektu** , wykonując kroki opisane w temacie [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties).|  
  
|Aby ustawić stałe w wierszu polecenia|  
|---|  
|-Użyj **/d** przełącznika, aby wprowadzić stałe kompilacji warunkowej, jak w poniższym przykładzie:<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     Między przełącznikiem **/d** i pierwszą stałą nie jest wymagane żadne miejsce. Aby uzyskać więcej informacji, zobacz [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).<br />     Deklaracje wiersza polecenia przesłaniają deklaracje wprowadzone w **projektancie projektu**, ale nie są wymazywane. Argumenty ustawione w **projektancie projektu** obowiązują dla kolejnych kompilacji.<br />     Podczas pisania stałych w samym kodzie nie istnieją ścisłe reguły dotyczące ich umieszczania, ponieważ ich zakresem jest cały moduł, w którym są one zadeklarowane.|  
  
|Aby ustawić stałe w kodzie|  
|---|  
|— Umieść stałe w bloku deklaracji modułu, w którym są używane. Dzięki temu kod jest zorganizowany i łatwiejszy do czytania.|  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|---|---|  
|[Konwencje dotyczące struktury programów i kodu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|Zawiera sugestie ułatwiające odczytywanie i konserwowanie kodu.|  
  
## <a name="reference"></a>Tematy pomocy  
 [#Const, dyrektywa](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [#If...Then...#Else, dyrektywy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
