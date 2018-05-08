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
ms.openlocfilehash: 2b60d732b260ad0477946e41ece4cd182de541ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a>Różnice pomiędzy argumentami modyfikowalnymi i niemodyfikowalnymi (Visual Basic)
Po wywołaniu procedury, zwykle przekazywania jednego lub więcej argumentów do niej. Każdy argument odnosi się do odpowiedniego elementu programowania. Zarówno elementy źródłowe, jak i argumentów, same może być modyfikowalnymi i niemodyfikowalnymi.  
  
## <a name="modifiable-and-nonmodifiable-elements"></a>Elementy modyfikowalnymi i niemodyfikowalnymi  
 Elementu programistycznego mogą być *można modyfikować elementu*, która może zawierać wartość zmienione, lub *niemodyfikowalnymi elementu*, mającego stałą wartość, po jego utworzeniu.  
  
 W poniższej tabeli wymieniono modyfikowalnymi i niemodyfikowalnymi elementów programowania.  
  
|Można modyfikować elementów|Elementy niemodyfikowalnymi|  
|-------------------------|----------------------------|  
|Zmienne lokalne (zadeklarowana wewnątrz procedury), w tym zmiennych obiektu, z wyjątkiem tylko do odczytu|Zmienne tylko do odczytu, pól i właściwości|  
|Pola (zmienne Członkowskie modułów, klasy i struktury), z wyjątkiem tylko do odczytu|Literały i stałe|  
|Właściwości, z wyjątkiem tylko do odczytu|Elementy członkowskie wyliczenia|  
|Elementy tablicy|Wyrażenia (nawet jeśli ich elementy są modyfikowane przez)|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a>Modyfikowalnymi i niemodyfikowalnymi  
 A *można modyfikować argumentu* jest jednym z elementem podstawowej można modyfikować. Kod wywołujący może przechowywać nową wartość w dowolnym momencie i jeśli zostanie przekazany argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), kod w procedurze można modyfikować również odpowiedniego elementu kodu wywołującego.  
  
 A *niemodyfikowalnymi argument* ma niemodyfikowalnymi odpowiedniego elementu albo jest przekazywany [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Procedury nie można zmodyfikować odpowiedniego elementu kodu wywołującego, nawet jeśli jest on elementem można modyfikować. Jeśli element niemodyfikowalnymi, nie można zmodyfikować kodu wywołującego.  
  
 Wywoływana procedura może zmodyfikować swojej lokalnej kopii niemodyfikowalnymi argumentu, ale modyfikacji nie ma wpływu na odpowiedniego elementu kodu wywołującego.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Instrukcje: przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)  
 [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)  
 [Różnice między przekazywaniem argumentu według wartości i według odwołania](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Instrukcje: zmiana wartości argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Instrukcje: ochrona argumentu procedury przed zmianami wartości](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Instrukcje: wymuszanie przekazywania argumentu przez wartość](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md)  
 [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
