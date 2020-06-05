---
title: Słowa kluczowe jako nazwy elementów w kodzie
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: a98f0b027700717b414d58e1284ddec655eb25f7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403229"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a>Słowa kluczowe jako nazwy elementów w Code (Visual Basic)
Każdy element programu, taki jak zmienna, Klasa lub element członkowski — może mieć taką samą nazwę jak słowo kluczowe z ograniczeniami. Na przykład można utworzyć zmienną o nazwie `Loop` . Jednak, aby odwołać się do używanej wersji programu, która ma taką samą nazwę jak `Loop` słowo kluczowe z ograniczeniami, należy poprzedzić ją ciągiem zawierającym pełną kwalifikację lub ująć ją w nawiasy kwadratowe ( `[ ]` ), jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 Jeśli nie wykonasz żadnej z tych czynności, Visual Basic zakłada użycie `Loop` słowa kluczowego wewnętrznego i tworzy błąd, jak w poniższym przykładzie:  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 Można użyć nawiasów kwadratowych podczas odwoływania się do formularzy i kontrolek, a w przypadku deklarowania zmiennej lub definiowania procedury o tej samej nazwie co słowo kluczowe z ograniczeniami. Można łatwo zapomnieć o kwalifikowaniu się nazw lub dołączeniu nawiasów kwadratowych, a tym samym wprowadzić błędy do kodu i utrudnić odczytanie. Z tego powodu zaleca się, aby nie używać słów kluczowych z ograniczeniami jako nazw elementów programu. Jeśli jednak przyszła wersja Visual Basic definiuje nowe słowo kluczowe, które powoduje konflikt z istniejącą nazwą formularza lub kontrolki, wówczas można użyć tej techniki podczas aktualizowania kodu do pracy z nową wersją.  
  
> [!NOTE]
> Program może również zawierać nazwy elementów udostępniane przez inne przywoływane zestawy. Jeśli te nazwy powodują konflikt z ograniczonymi słowami kluczowymi, umieszczenie nawiasów kwadratowych spowoduje, że Visual Basic interpretują je jako zdefiniowane elementy.  
  
## <a name="see-also"></a>Zobacz też

- [Visual Basic — Konwencje nazewnictwa](naming-conventions.md)
- [Struktura programu i konwencje związane z kodem](program-structure-and-code-conventions.md)
- [Słowa kluczowe](../../language-reference/keywords/index.md)
