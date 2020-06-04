---
title: Niejawna konwersja z „<typename1>” na „<typename2>” podczas kopiowania wartości parametru „ByRef” „<parametername>” z powrotem do pasującego argumentu.
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: 4d0f9aac795f683cf58210ea38b3783e451ccfc3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402865"
---
# <a name="implicit-conversion-from-typename1-to-typename2-in-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument"></a>Niejawna konwersja z „\<typename1>” na „\<typename2>” podczas kopiowania wartości parametru „ByRef” „\<parametername>” z powrotem do pasującego argumentu.
Procedura jest wywoływana z argumentem [ByRef](../modifiers/byref.md) innego typu niż odpowiedni parametr.  
  
 W przypadku przekazania argumentu `ByRef` Visual Basic czasami kopiuje wartość argumentu do zmiennej lokalnej w procedurze, zamiast przekazywać odwołanie. W takim przypadku, gdy procedura zwraca, Visual Basic należy skopiować wartość zmiennej lokalnej z powrotem do argumentu w kodzie wywołującym.  
  
 Jeśli `ByRef` wartość argumentu jest kopiowana do procedury, a argument i parametr są tego samego typu, konwersja nie jest konieczna. Ale jeśli typy są różne, Visual Basic muszą być konwertowane w obu kierunkach. Ponieważ nie można używać `CType` ani żadnych innych słów kluczowych konwersji dla argumentu lub parametru procedury, taka konwersja jest zawsze niejawna.  
  
 Domyślnie ten komunikat jest ostrzeżeniem. Aby uzyskać informacje na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC41999  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Jeśli to możliwe, użyj argumentu wywołującego tego samego typu co parametr procedury, więc Visual Basic nie musi wykonywać żadnej konwersji.  
  
- Jeśli musisz wywołać procedurę z typem argumentu innym niż typ parametru, ale nie musisz zwracać wartości do argumentu wywołującego, zdefiniuj parametr jako [ByVal](../modifiers/byval.md) zamiast `ByRef` .  
  
## <a name="see-also"></a>Zobacz też

- [Procedury](../../programming-guide/language-features/procedures/index.md)
- [Parametry i argumenty procedur](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [Przekazywanie argumentów według wartości i według odwołania](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [Konwersje jawne i niejawne](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
