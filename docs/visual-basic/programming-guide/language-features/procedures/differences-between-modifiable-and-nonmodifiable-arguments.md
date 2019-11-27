---
title: Różnice między argumentami modyfikowalnymi i niemodyfikowalnymi
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: 989795ee2cdd3a78b71bad4d95cf9b384c2719bd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341390"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a>Różnice pomiędzy argumentami modyfikowalnymi i niemodyfikowalnymi (Visual Basic)
Po wywołaniu procedury zwykle przekazywany jest jeden lub więcej argumentów. Każdy argument odpowiada bazowemu elementowi programistycznemu. Zarówno elementy bazowe, jak i same argumenty mogą być modyfikowalne lub niemodyfikowane.  
  
## <a name="modifiable-and-nonmodifiable-elements"></a>Modyfikowalne i niemodyfikowalne elementy  
 Elementem programistycznym może być *element modyfikowalny*, który może mieć zmienioną wartość, lub *niemodyfikowalny element*, który ma ustaloną wartość po utworzeniu.  
  
 W poniższej tabeli wymieniono elementy programistyczne modyfikowane i niemodyfikowane.  
  
|Modyfikowalne elementy|Elementy niemodyfikowalne|  
|-------------------------|----------------------------|  
|Zmienne lokalne (zadeklarowane wewnątrz procedur), w tym zmienne obiektów, z wyjątkiem tylko do odczytu|Zmienne tylko do odczytu, pola i właściwości|  
|Pola (zmienne składowe modułów, klas i struktur), z wyjątkiem tylko do odczytu|Stałe i literały|  
|Właściwości, z wyjątkiem tylko do odczytu|Elementy członkowskie wyliczenia|  
|Elementy tablicy|Wyrażenia (nawet jeśli ich elementy są modyfikowane)|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a>Modyfikowalne i niemodyfikowalne argumenty  
 *Modyfikowalny argument* to jeden z modyfikowalnym elementem bazowym. Kod wywołujący może przechowywać nową wartość w dowolnym momencie, a w przypadku przekazania argumentu [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)kod w procedurze może także zmodyfikować podstawowy element w kodzie wywołującym.  
  
 *Argument niemodyfikowalny* ma niemodyfikowalny element podstawowy lub został przekazaną wartość [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Procedura nie może zmodyfikować podstawowego elementu w kodzie wywołującym, nawet jeśli jest to element modyfikowalny. Jeśli jest to niemodyfikowalny element, sam kod wywołujący nie może go zmodyfikować.  
  
 Wywołana procedura może zmodyfikować swoją lokalną kopię niemodyfikowalnego argumentu, ale ta modyfikacja nie ma wpływu na element podstawowy w kodzie wywołującym.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Instrukcje: przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)
- [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)
- [Różnice między przekazywaniem argumentu według wartości i według odwołania](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Instrukcje: zmiana wartości argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)
- [Instrukcje: ochrona argumentu procedury przed zmianami wartości](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Instrukcje: wymuszanie przekazywania argumentu przez wartość](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md)
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
