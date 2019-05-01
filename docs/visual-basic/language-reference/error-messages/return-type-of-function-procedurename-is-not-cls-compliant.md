---
title: Zwracany typ funkcji „<procedurename>” jest niezgodny ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords:
- BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
ms.openlocfilehash: 5e746981d10ba8e662aebf86f67f08856ba37199
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013749"
---
# <a name="return-type-of-function-procedurename-is-not-cls-compliant"></a>Zwracany typ funkcji "\<nazwaprocedury >' nie jest zgodny ze specyfikacją CLS
A `Function` procedura jest oznaczona jako `<CLSCompliant(True)>` , ale zwraca typ, który jest oznaczony jako `<CLSCompliant(False)>`, nie jest oznaczony jako lub nie kwalifikują się, ponieważ jest to typ niezgodne.  
  
 Procedury zachować zgodność z [niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS), jej używać tylko typów zgodnych ze specyfikacją CLS. Dotyczy to typy parametrów, typ zwracany i typy jego zmiennych lokalnych.  
  
 Następujące typy danych Visual Basic nie są zgodne ze specyfikacją CLS:  
  
- [SByte, typ danych](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [UInteger, typ danych](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [ULong, typ danych](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [UShort, typ danych](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Po zastosowaniu <xref:System.CLSCompliantAttribute> elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` aby wskazać, zgodności ani niezgodności. Nie istnieje domyślny dla tego parametru. Ponadto należy podać wartość.  
  
 Jeśli nie zastosujesz <xref:System.CLSCompliantAttribute> elementu, jest uznawane za niezgodne.  
  
 Domyślnie ta wiadomość jest ostrzeżenie. Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40027  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Jeśli `Function` procedury musi zwracać tego konkretnego typu, Usuń <xref:System.CLSCompliantAttribute>. Procedura nie może być zgodne ze specyfikacją CLS.  
  
- Jeśli `Function` procedury musi być zgodny ze specyfikacją CLS, Zmień typ zwracany do najbliższego typu zgodny ze specyfikacją CLS. Na przykład, zamiast z `UInteger` można użyć `Integer` Jeśli nie potrzebujesz zakres wartości ponad 2 147 483 647. Jeśli potrzebujesz rozszerzonej zakresu, można zastąpić `UInteger` z `Long`.  
  
- Jeśli są komunikowanie się z obiektami automatyzacji lub COM, należy pamiętać o tym, że niektóre typy mają różnych szerokościach danych niż w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Na przykład `int` często jest 16 bitów w innych środowiskach. Jeśli są Zwraca 16-bitową liczbę całkowitą do takiego składnika, Zadeklaruj go jako `Short` zamiast `Integer` w zarządzanym kodzie języka Visual Basic.