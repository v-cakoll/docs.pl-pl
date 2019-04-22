---
title: Różnice pomiędzy argumentami modyfikowalnymi i niemodyfikowalnymi (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: a880ae8c13eebd5d9d325468098e058f58d3fa71
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826668"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a>Różnice pomiędzy argumentami modyfikowalnymi i niemodyfikowalnymi (Visual Basic)
Po wywołaniu procedury, zazwyczaj pass jeden lub więcej argumentów do niego. Każdy argument odnosi się do podstawowego elementu programowania. Zarówno w przypadku podstawowych elementów, jak i same argumenty, może być modyfikowalnymi i niemodyfikowalnymi.  
  
## <a name="modifiable-and-nonmodifiable-elements"></a>Elementy argumentami modyfikowalnymi i niemodyfikowalnymi  
 Elementu programowania może być *można modyfikować element*, która może zawierać swoją wartość, lub *niemodyfikowalnymi elementu*, mającego stałą wartość, po jego utworzeniu.  
  
 W poniższej tabeli wymieniono argumentami modyfikowalnymi i niemodyfikowalnymi elementów programowania.  
  
|Modyfikowalne elementy|Elementy niemodyfikowalnymi|  
|-------------------------|----------------------------|  
|Zmienne lokalne (zadeklarowana wewnątrz procedury), w tym zmienne obiektów, z wyjątkiem tylko do odczytu|Zmienne tylko do odczytu, pola i właściwości|  
|Pola (zmienne Członkowskie modułów, klasy i struktury), z wyjątkiem tylko do odczytu|Literały i stałe|  
|Właściwości, z wyjątkiem tylko do odczytu|Elementy członkowskie wyliczenia|  
|Elementy tablicy|Wyrażenia (nawet jeśli ich elementy są modyfikowane przez)|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a>Argumentami modyfikowalnymi i niemodyfikowalnymi  
 A *argument można modyfikować* jest jednym z elementem podstawowym można modyfikować. Kod wywołujący może przechowywać nową wartość w dowolnym momencie, a jeśli przekazać argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), kod w ramach procedury można także zmodyfikować element podstawowy w wywoływanym kodzie.  
  
 A *niemodyfikowalnymi argument* ma niemodyfikowalnymi elementu bazowego albo jest przekazywany [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Procedury nie można zmodyfikować element podstawowy w wywoływanym kodzie, nawet jeśli jest on elementem można modyfikować. Jeśli element niemodyfikowalnymi, nie można zmodyfikować kod wywołujący, sam.  
  
 Wywoływana procedura może zmodyfikować swojej lokalnej kopii niemodyfikowalnymi argumentu, ale ta zmiana nie ma wpływu na element podstawowy w wywoływanym kodzie.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Instrukcje: Przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)
- [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)
- [Różnice między przekazywaniem argumentu według wartości i według odwołania](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Instrukcje: Zmień wartość argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)
- [Instrukcje: Chronienie argumentu procedury przed zmianami wartości](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Instrukcje: Wymuszanie być przekazywany przez wartość argumentu](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md)
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
