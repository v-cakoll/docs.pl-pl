---
title: Typ parametru „<parametername>” jest niezgodny ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40028
- bc40028
helpviewer_keywords:
- BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
ms.openlocfilehash: e7cf058ef5e6b007a39213aa0ca5748a3b77458a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590641"
---
# <a name="type-of-parameter-parametername-is-not-cls-compliant"></a>Typ parametru "\<parametername >' nie jest zgodny ze specyfikacją CLS
Procedura jest oznaczona jako `<CLSCompliant(True)>` , ale deklaruje parametr o typie, który jest oznaczony jako `<CLSCompliant(False)>`, nie jest oznaczony jako lub nie kwalifikują się, ponieważ jest to typ niezgodne.  
  
 Procedury zachować zgodność z [niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS), jej używać tylko typów zgodnych ze specyfikacją CLS. Dotyczy to typy parametrów, typ zwracany i typy jego zmiennych lokalnych.  
  
 Następujące typy danych Visual Basic nie są zgodne ze specyfikacją CLS:  
  
- [SByte, typ danych](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [UInteger, typ danych](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [ULong, typ danych](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [UShort, typ danych](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Po zastosowaniu <xref:System.CLSCompliantAttribute> elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` aby wskazać, zgodności ani niezgodności. Nie istnieje domyślny dla tego parametru. Ponadto należy podać wartość.  
  
 Jeśli nie zastosujesz <xref:System.CLSCompliantAttribute> elementu, jest uznawane za niezgodne.  
  
 Domyślnie ta wiadomość jest ostrzeżenie. Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40028  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Jeśli procedura musi przyjmować parametr tego określonego typu, Usuń <xref:System.CLSCompliantAttribute>. Procedura nie może być zgodne ze specyfikacją CLS.  
  
- Jeśli procedury muszą być zgodne ze specyfikacją CLS, należy zmienić typ tohoto parametru do najbliższego typu zgodny ze specyfikacją CLS. Na przykład, zamiast z `UInteger` można użyć `Integer` Jeśli nie potrzebujesz zakres wartości ponad 2 147 483 647. Jeśli potrzebujesz rozszerzonej zakresu, można zastąpić `UInteger` z `Long`.  
  
- Czy komunikowanie się z obiektami automatyzacji lub COM, pamiętać, że niektóre typy mają różnych szerokościach danych niż na platformie .NET Framework. Na przykład `int` często jest 16 bitów w innych środowiskach. Jeśli akceptujesz 16-bitową liczbę całkowitą z takiego składnika, Zadeklaruj go jako `Short` zamiast `Integer` w zarządzanym kodzie języka Visual Basic.
