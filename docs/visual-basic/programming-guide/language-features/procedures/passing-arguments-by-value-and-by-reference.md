---
title: Przekazywanie argumentów według wartości i według odwołania
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- passing arguments [Visual Basic], by value or by reference
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing [Visual Basic], by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
ms.openlocfilehash: 28e59753a35ab67b15fbc549df5bb8a3489aba5a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352603"
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>Przekazywanie argumentów według wartości i według odwołania (Visual Basic)
W Visual Basic można przekazać argument do procedury *przez wartość* lub *przez odwołanie*. Jest to nazywane *mechanizmem przekazywania*i określa, czy procedura może zmodyfikować element programowania, który jest powiązany z argumentem w kodzie wywołującym. Deklaracja procedury określa mechanizm przekazywania dla każdego parametru przez określenie słowa kluczowego [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) .  
  
## <a name="distinctions"></a>Różnice  
 Podczas przekazywania argumentu do procedury należy pamiętać o kilku różnych rozróżnieniu, które współpracują ze sobą:  
  
- Czy bazowy element programistyczny jest modyfikowalny, czy niemodyfikowalny  
  
- Czy sam argument jest modyfikowalny, czy niemodyfikowalny  
  
- Określa, czy argument jest przesyłany przez wartość, czy przez odwołanie  
  
- Czy typ danych argumentu jest typem wartości czy typem referencyjnym  
  
 Aby uzyskać więcej informacji, zobacz [różnice między modyfikowalnymi i niemodyfikowalnymi argumentami](./differences-between-modifiable-and-nonmodifiable-arguments.md) i [różnicami między przekazywaniem argumentu według wartości i przez odwołanie](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## <a name="choice-of-passing-mechanism"></a>Wybór mechanizmu przechodzenia  
 Dla każdego argumentu należy uważnie wybrać mechanizm przekazywania.  
  
- **Ochrona**. W wyborze między dwoma mechanizmami przekazywania najważniejszym kryterium jest narażenie zmiennych wywołujących na zmianę. Zalety przekazywania argumentu `ByRef` polega na tym, że procedura może zwrócić wartość do kodu wywołującego za pomocą tego argumentu. Zalety przekazywania argumentu `ByVal` polega na tym, że chroni zmienną przed zmianą przez procedurę.  
  
- **Wydajność**. Chociaż mechanizm przekazywania może mieć wpływ na wydajność kodu, różnica jest zwykle nieistotna. Jedynym wyjątkiem jest typ wartości przekazaną `ByVal`. W takim przypadku Visual Basic Kopiuje całą zawartość danych argumentu. W związku z tym w przypadku typu dużej wartości, takiego jak struktura, może być bardziej wydajna, aby przekazać go `ByRef`.  
  
     W przypadku typów referencyjnych kopiowany jest tylko wskaźnik do danych (cztery bajty na 32-bitowych platformach, osiem bajtów na platformach 64-bitowych). W związku z tym można przekazywać argumenty typu `String` lub `Object` przez wartość bez zakłócania wydajności.  
  
## <a name="determination-of-the-passing-mechanism"></a>Określanie mechanizmu przekazywania  
 Deklaracja procedury określa mechanizm przekazywania dla każdego parametru. Kod wywołujący nie może przesłonić mechanizmu `ByVal`.  
  
 Jeśli parametr jest zadeklarowany za pomocą `ByRef`, kod wywołujący może wymusić `ByVal`, umieszczając nazwę argumentu w nawiasach w wywołaniu. Aby uzyskać więcej informacji, zobacz [jak: Wymuś przekazywanie argumentu przez wartość](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
 Wartością domyślną w Visual Basic jest przekazanie argumentów według wartości.  
  
## <a name="when-to-pass-an-argument-by-value"></a>Kiedy przekazać argument według wartości  
  
- Jeśli element kodu wywołującego, który jest powiązany z argumentem jest niemodyfikowalny element, zadeklaruj odpowiedni parametr [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Żaden kod nie może zmienić wartości elementu, którego nie można modyfikować.  
  
- Jeśli element źródłowy jest modyfikowalny, ale nie chcesz, aby procedura mogła zmienić jego wartość, zadeklaruj `ByVal`parametru. Tylko kod wywołujący może zmienić wartość modyfikowalnego elementu przekazaną przez wartość.  
  
## <a name="when-to-pass-an-argument-by-reference"></a>Kiedy przekazać argument przez odwołanie  
  
- Jeśli procedura ma oryginalną potrzebę zmiany podstawowego elementu w kodzie wywołującym, zadeklaruj odpowiedni parametr [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).  
  
- Jeśli prawidłowe wykonanie kodu zależy od procedury zmiany bazowego elementu w kodzie wywołującym, należy zadeklarować parametr `ByRef`. Jeśli przekazujesz ją przez wartość lub Jeśli wywołujący kod przesłania `ByRef` mechanizm przekazywania przez załączanie argumentu w nawiasach, wywołanie procedury może dawać nieoczekiwane wyniki.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład ilustruje czas przekazywania argumentów według wartości i czas przekazywania ich przez odwołanie. Procedura `Calculate` ma zarówno parametr `ByVal`, jak i `ByRef`. Uwzględniając stawkę odsetek, `rate`i sumę pieniędzy, `debt`, zadanie procedury polega na obliczeniu nowej wartości dla `debt`, która jest wynikiem zastosowania stopy oprocentowania do oryginalnej wartości `debt`. Ponieważ `debt` jest parametrem `ByRef`, Nowa suma jest odzwierciedlona w wartości argumentu w kodzie wywołującym, który odnosi się do `debt`. Parametr `rate` jest parametrem `ByVal`, ponieważ `Calculate` nie powinien zmieniać jego wartości.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbcnProcedures#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class2.vb#74)]  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Instrukcje: przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)
- [Instrukcje: zmiana wartości argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)
- [Instrukcje: ochrona argumentu procedury przed zmianami wartości](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Instrukcje: wymuszanie przekazywania argumentu przez wartość](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md)
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
