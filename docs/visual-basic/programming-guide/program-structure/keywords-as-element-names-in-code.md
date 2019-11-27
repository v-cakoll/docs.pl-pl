---
title: Słowa kluczowe jako nazwy elementów w Code
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: 4cdcda7c5c78481af1633bf29d75070c521ab393
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347395"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a>Słowa kluczowe jako nazwy elementów w Code (Visual Basic)
Każdy element programu, taki jak zmienna, Klasa lub element członkowski — może mieć taką samą nazwę jak słowo kluczowe z ograniczeniami. Na przykład można utworzyć zmienną o nazwie `Loop`. Jednak, aby odwołać się do używanej wersji programu, która ma taką samą nazwę jak słowo kluczowe `Loop` z ograniczeniami, należy poprzedzić ją ciągiem z pełną kwalifikacją lub ująć ją w nawiasy kwadratowe (`[ ]`), jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 Jeśli nie wykonasz żadnej z tych czynności, Visual Basic zakłada użycie słowa kluczowego `Loop` wewnętrznego i wygeneruje błąd, jak w poniższym przykładzie:  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 Można użyć nawiasów kwadratowych podczas odwoływania się do formularzy i kontrolek, a w przypadku deklarowania zmiennej lub definiowania procedury o tej samej nazwie co słowo kluczowe z ograniczeniami. Można łatwo zapomnieć o kwalifikowaniu się nazw lub dołączeniu nawiasów kwadratowych, a tym samym wprowadzić błędy do kodu i utrudnić odczytanie. Z tego powodu zaleca się, aby nie używać słów kluczowych z ograniczeniami jako nazw elementów programu. Jeśli jednak przyszła wersja Visual Basic definiuje nowe słowo kluczowe, które powoduje konflikt z istniejącą nazwą formularza lub kontrolki, wówczas można użyć tej techniki podczas aktualizowania kodu do pracy z nową wersją.  
  
> [!NOTE]
> Program może również zawierać nazwy elementów udostępniane przez inne przywoływane zestawy. Jeśli te nazwy powodują konflikt z ograniczonymi słowami kluczowymi, umieszczenie nawiasów kwadratowych spowoduje, że Visual Basic interpretują je jako zdefiniowane elementy.  
  
## <a name="see-also"></a>Zobacz także

- [Konwencje nazewnictwa Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [Struktura programu i konwencje związane z kodami](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
