---
title: "Typ wartości opcjonalnej dla parametru opcjonalnego &lt;parametername&gt; nie jest zgodne ze specyfikacją CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords: BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 442ff2e4b582287e03f425dad98128726fe18c43
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="type-of-optional-value-for-optional-parameter-ltparameternamegt-is-not-cls-compliant"></a>Typ wartości opcjonalnej dla parametru opcjonalnego &lt;parametername&gt; nie jest zgodne ze specyfikacją CLS
Procedura jest oznaczony jako `<CLSCompliant(True)>` , ale deklaruje [opcjonalnie](../../../visual-basic/language-reference/modifiers/optional.md) parametru z wartością domyślną niezgodnego typu.  
  
 Procedury było zgodne z [niezależność od języka i elementy niezależne od języka](https://msdn.microsoft.com/library/12a7a7h3) (ze specyfikacją CLS), należy użyć tylko typów zgodnych ze specyfikacją CLS. Dotyczy to typy parametrów, typ zwracany i typy jego zmiennych lokalnych. Dotyczy także wartościami domyślnymi parametrów opcjonalnych.  
  
 Następujące [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] typy danych nie są zgodne ze specyfikacją CLS:  
  
-   [SByte — typ danych](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [Uinteger — typ danych](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [Ulong — typ danych](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [Ushort — typ danych](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Po zastosowaniu <xref:System.CLSCompliantAttribute> atrybut do elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` zgodności lub niezgodności. Nie jest domyślnie dla tego parametru, a należy podać wartość.  
  
 Jeśli nie mają zastosowania <xref:System.CLSCompliantAttribute> do elementu, jest uznawane za niezgodne.  
  
 Domyślnie ten komunikat jest ostrzeżenie. Aby uzyskać informacje na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40042  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli opcjonalny parametr musi mieć wartość domyślna tego typu konkretnego, usunąć <xref:System.CLSCompliantAttribute>. Procedura nie może być zgodne ze specyfikacją CLS.  
  
-   Jeśli procedura musi być zgodne ze specyfikacją CLS, należy zmienić typ wartość domyślną do najbliższego typu zgodne ze specyfikacją CLS. Na przykład zamiast z `UInteger` można użyć `Integer` Jeśli nie potrzebujesz zakres wartości powyżej 2 147 483 647. Jeśli potrzebujesz rozszerzonej zakresu, można zastąpić `UInteger` z `Long`.  
  
-   Jeśli użytkownik są relacje z obiektami automatyzacji lub COM, należy pamiętać, że niektóre typy szerokości danych innego niż w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Na przykład `int` jest często 16 bitów w innych środowiskach. Jeśli akceptujesz 16-bitową liczbę całkowitą z takich składników, Zadeklaruj ją jako `Short` zamiast `Integer` w sieci zarządzanej [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [\<PAVE za pośrednictwem > Pisanie kodu zgodne ze specyfikacją CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
