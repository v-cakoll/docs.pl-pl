---
title: Różnice pomiędzy przekazywaniem argumentu według wartości i według odwołania
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- procedures [Visual Basic], passing arguments
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
ms.openlocfilehash: bd316ae2239ad85e4ef6dadbb8a634d5fe7ecf02
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403333"
---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a>Różnice pomiędzy przekazywaniem argumentu według wartości i według odwołania (Visual Basic)
Gdy przekazujesz jeden lub więcej argumentów do procedury, każdy argument odpowiada bazowemu elementowi programowania w kodzie wywołującym. Można przekazać wartość tego podstawowego elementu lub odwołanie do niego. Jest to tzw. *mechanizm przekazywania*.  
  
## <a name="passing-by-value"></a>Przekazywanie przez wartość  
 Argument jest przekazywany *przez wartość* poprzez określenie słowa kluczowego [ByVal](../../../language-reference/modifiers/byval.md) dla odpowiadającego parametru w definicji procedury. Korzystając z tego mechanizmu przekazującego, Visual Basic kopiuje wartość bazowego elementu programowania do zmiennej lokalnej w procedurze. Kod procedury nie ma dostępu do podstawowego elementu w kodzie wywołującym.  
  
## <a name="passing-by-reference"></a>Przekazywanie przez odwołanie  
 Argument jest przekazywany *przez odwołanie* poprzez określenie słowa kluczowego [ByRef](../../../language-reference/modifiers/byref.md) dla odpowiadającego parametru w definicji procedury. W przypadku korzystania z tego mechanizmu przekazującego, Visual Basic daje procedurę bezpośrednio odniesienia do bazowego elementu programowania w kodzie wywołującym.  
  
## <a name="passing-mechanism-and-element-type"></a>Mechanizm przekazywania i typ elementu  
 Wybór mechanizmu przekazywania nie jest taki sam jak Klasyfikacja podstawowego typu elementu. Przekazywanie przez wartość lub przez odwołanie dotyczy tego, co Visual Basic dostarcza do kodu procedury. Typ wartości lub typ referencyjny odnosi się do sposobu przechowywania elementu programowania w pamięci.  
  
 Jednak mechanizm przekazywania i typ elementu są wzajemnie powiązane. Wartość typu referencyjnego to wskaźnik do danych znajdujących się w innym miejscu w pamięci. Oznacza to, że w przypadku przekazania typu odwołania przez wartość kod procedury ma wskaźnik do danych elementu podstawowego, nawet jeśli nie może uzyskać dostępu do samego elementu bazowego. Na przykład jeśli element jest zmienną tablicową, kod procedury nie ma dostępu do samej zmiennej, ale może uzyskać dostęp do elementów członkowskich tablicy.  
  
## <a name="ability-to-modify"></a>Możliwość modyfikowania  
 W przypadku przekazania niemodyfikowalnego elementu jako argumentu procedura może nigdy nie modyfikować w kodzie wywołującym, niezależnie od tego, czy została przekazana, czy `ByVal` `ByRef` .  
  
 W przypadku elementu, który można modyfikować, Poniższa tabela zawiera podsumowanie interakcji między typem elementu a mechanizmem przekazywania.  
  
|Typ elementu|Przeniesione`ByVal`|Przeniesione`ByRef`|  
|------------------|--------------------|--------------------|  
|Typ wartości (zawiera tylko wartość)|Procedura nie może zmienić zmiennej ani żadnego z jej elementów członkowskich.|Procedura może zmienić zmienną i jej członków.|  
|Typ odwołania (zawiera wskaźnik do klasy lub wystąpienia struktury)|Procedura nie może zmienić zmiennej, ale może zmienić elementy członkowskie wystąpienia, do którego się odwołuje.|Procedura może zmienić zmienną i członków wystąpienia, do którego wskazuje.|  
  
## <a name="see-also"></a>Zobacz też

- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Instrukcje: przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)
- [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)
- [Różnice między argumentami modyfikowalnymi i niemodyfikowalnymi](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Instrukcje: zmiana wartości argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)
- [Instrukcje: ochrona argumentu procedury przed zmianami wartości](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Instrukcje: wymuszanie przekazywania argumentu przez wartość](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md)
- [Typy wartości i odwołań](../data-types/value-types-and-reference-types.md)
