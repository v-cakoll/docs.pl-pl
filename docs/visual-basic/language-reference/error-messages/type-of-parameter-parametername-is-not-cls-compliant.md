---
title: Typ parametru &#39; &lt;parametername&gt; &#39; nie jest zgodne ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40028
- bc40028
helpviewer_keywords:
- BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
ms.openlocfilehash: 13a4e35cd27ed5aa135cec77c4415f223cba70f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596060"
---
# <a name="type-of-parameter-39ltparameternamegt39-is-not-cls-compliant"></a>Typ parametru &#39; &lt;parametername&gt; &#39; nie jest zgodne ze specyfikacją CLS
Procedura jest oznaczony jako `<CLSCompliant(True)>` , ale deklaruje parametr typu, który jest oznaczony jako `<CLSCompliant(False)>`, nie jest oznaczony jako lub nie kwalifikuje się, ponieważ jest to typ niezgodne.  
  
 Procedury było zgodne z [niezależność od języka i elementy niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (ze specyfikacją CLS), należy użyć tylko typów zgodnych ze specyfikacją CLS. Dotyczy to typy parametrów, typ zwracany i typy jego zmiennych lokalnych.  
  
 Następujące typy danych Visual Basic nie są zgodne ze specyfikacją CLS:  
  
-   [SByte, typ danych](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger, typ danych](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong, typ danych](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort, typ danych](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Po zastosowaniu <xref:System.CLSCompliantAttribute> do elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` zgodności lub niezgodności. Nie jest domyślnie dla tego parametru, a należy podać wartość.  
  
 Jeśli nie mają zastosowania <xref:System.CLSCompliantAttribute> do elementu, jest uznawane za niezgodne.  
  
 Domyślnie ten komunikat jest ostrzeżenie. Aby uzyskać informacje na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40028  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli procedury należy wykonać parametr tego typu konkretnego, usunąć <xref:System.CLSCompliantAttribute>. Procedura nie może być zgodne ze specyfikacją CLS.  
  
-   Jeśli procedura musi być zgodne ze specyfikacją CLS, należy zmienić typ tego parametru do najbliższego typu zgodne ze specyfikacją CLS. Na przykład zamiast z `UInteger` można użyć `Integer` Jeśli nie potrzebujesz zakres wartości powyżej 2 147 483 647. Jeśli potrzebujesz rozszerzonej zakresu, można zastąpić `UInteger` z `Long`.  
  
-   Jeśli użytkownik są relacje z obiektami automatyzacji lub COM, należy pamiętać, że niektóre typy szerokości danych innego niż w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Na przykład `int` jest często 16 bitów w innych środowiskach. Jeśli akceptujesz 16-bitową liczbę całkowitą z takich składników, Zadeklaruj ją jako `Short` zamiast `Integer` w zarządzanym kodzie języka Visual Basic.