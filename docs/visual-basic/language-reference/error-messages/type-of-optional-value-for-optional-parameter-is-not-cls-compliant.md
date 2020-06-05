---
title: Typ wartości opcjonalnej dla parametru opcjonalnego <parametername> jest niezgodny ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords:
- BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
ms.openlocfilehash: 8e53d036ead114d828d9035cef76cee72bf6b1db
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400295"
---
# <a name="type-of-optional-value-for-optional-parameter-parametername-is-not-cls-compliant"></a>Typ wartości opcjonalnej dla parametru opcjonalnego \<parametername> jest niezgodny ze specyfikacją CLS
Procedura jest oznaczona jako, `<CLSCompliant(True)>` ale deklaruje [opcjonalny](../modifiers/optional.md) parametr z wartością domyślną niezgodnego typu.  
  
 Aby procedura była zgodna z [niezależnością od języka i składnikami niezależnymi od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS), musi używać tylko typów zgodnych ze specyfikacją CLS. Dotyczy to typów parametrów, typu zwracanego i typów wszystkich zmiennych lokalnych. Ma również zastosowanie do domyślnych wartości parametrów opcjonalnych.  
  
 Następujące Visual Basic typy danych nie są zgodne ze specyfikacją CLS:  
  
- [SByte, typ danych](../data-types/sbyte-data-type.md)  
  
- [UInteger, typ danych](../data-types/uinteger-data-type.md)  
  
- [ULong, typ danych](../data-types/ulong-data-type.md)  
  
- [UShort, typ danych](../data-types/ushort-data-type.md)  
  
 Po zastosowaniu <xref:System.CLSCompliantAttribute> atrybutu do elementu programistycznego, należy ustawić `isCompliant` parametr atrybutu na wartość `True` lub, `False` Aby wskazać zgodność lub niezgodność. Dla tego parametru nie ma wartości domyślnej i należy podać wartość.  
  
 Jeśli nie ma zastosowania <xref:System.CLSCompliantAttribute> do elementu, jest on uznawany za niezgodny.  
  
 Domyślnie ten komunikat jest ostrzeżeniem. Aby uzyskać informacje na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40042  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Jeśli opcjonalny parametr musi mieć wartość domyślną tego konkretnego typu, Usuń <xref:System.CLSCompliantAttribute> . Procedura nie może być zgodna ze specyfikacją CLS.  
  
- Jeśli procedura musi być zgodna ze specyfikacją CLS, Zmień typ tej wartości domyślnej na najbliższy typ zgodny ze specyfikacją CLS. Na przykład, zamiast `UInteger` można użyć, `Integer` Jeśli nie potrzebujesz zakresu wartości powyżej 2 147 483 647. Jeśli potrzebujesz rozszerzonego zakresu, możesz zamienić `UInteger` na `Long` .  
  
- Jeśli masz połączenie z obiektami automatyzacji lub COM, pamiętaj, że niektóre typy mają różne szerokości danych niż w .NET Framework. Na przykład `int` często jest 16 bitów w innych środowiskach. Jeśli zaakceptujesz 16-bitową liczbę całkowitą z tego składnika, zadeklaruj ją jako `Short` zamiast `Integer` w kodzie zarządzanym Visual Basic.
