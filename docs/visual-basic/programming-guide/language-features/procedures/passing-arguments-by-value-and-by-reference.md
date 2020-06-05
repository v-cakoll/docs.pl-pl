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
ms.openlocfilehash: 3dd4be6ea6de9dfe8eb165e5d4ba9a990fc40585
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363957"
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>Przekazywanie argumentów według wartości i według odwołania (Visual Basic)
W Visual Basic można przekazać argument do procedury *przez wartość* lub *przez odwołanie*. Jest to nazywane *mechanizmem przekazywania*i określa, czy procedura może zmodyfikować element programowania, który jest powiązany z argumentem w kodzie wywołującym. Deklaracja procedury określa mechanizm przekazywania dla każdego parametru przez określenie słowa kluczowego [ByVal](../../../language-reference/modifiers/byval.md) lub [ByRef](../../../language-reference/modifiers/byref.md) .  
  
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
  
- **Wydajność**. Chociaż mechanizm przekazywania może mieć wpływ na wydajność kodu, różnica jest zwykle nieistotna. Jedynym wyjątkiem jest przekazanie typu wartości `ByVal` . W takim przypadku Visual Basic Kopiuje całą zawartość danych argumentu. W związku z tym, w przypadku typu dużej wartości, takiego jak struktura, może być bardziej wydajny `ByRef` .  
  
     W przypadku typów referencyjnych kopiowany jest tylko wskaźnik do danych (cztery bajty na 32-bitowych platformach, osiem bajtów na platformach 64-bitowych). W związku z tym można przekazać argumenty typu `String` lub `Object` według wartości bez zakłócania wydajności.  
  
## <a name="determination-of-the-passing-mechanism"></a>Określanie mechanizmu przekazywania  
 Deklaracja procedury określa mechanizm przekazywania dla każdego parametru. Kod wywołujący nie może przesłonić `ByVal` mechanizmu.  
  
 Jeśli parametr jest zadeklarowany za pomocą `ByRef` , wywoływany kod może wymusić, `ByVal` umieszczając nazwę argumentu w nawiasach w wywołaniu. Aby uzyskać więcej informacji, zobacz [jak: Wymuś przekazywanie argumentu przez wartość](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
 Wartością domyślną w Visual Basic jest przekazanie argumentów według wartości.  
  
## <a name="when-to-pass-an-argument-by-value"></a>Kiedy przekazać argument według wartości  
  
- Jeśli element kodu wywołującego, który jest powiązany z argumentem jest niemodyfikowalny element, zadeklaruj odpowiedni parametr [ByVal](../../../language-reference/modifiers/byval.md). Żaden kod nie może zmienić wartości elementu, którego nie można modyfikować.  
  
- Jeśli element źródłowy jest modyfikowalny, ale nie chcesz, aby procedura mogła zmienić jego wartość, zadeklaruj parametr `ByVal` . Tylko kod wywołujący może zmienić wartość modyfikowalnego elementu przekazaną przez wartość.  
  
## <a name="when-to-pass-an-argument-by-reference"></a>Kiedy przekazać argument przez odwołanie  
  
- Jeśli procedura ma oryginalną potrzebę zmiany podstawowego elementu w kodzie wywołującym, zadeklaruj odpowiedni parametr [ByRef](../../../language-reference/modifiers/byref.md).  
  
- Jeśli prawidłowe wykonanie kodu zależy od procedury zmiany bazowego elementu w kodzie wywołującym, zadeklaruj parametr `ByRef` . Jeśli przekazujesz go przez wartość lub, Jeśli wywołujący kod zastępuje `ByRef` mechanizm przekazywania przez ujęcie argumentu w nawiasach, wywołanie procedury może generować nieoczekiwane wyniki.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład ilustruje czas przekazywania argumentów według wartości i czas przekazywania ich przez odwołanie. Procedura `Calculate` ma zarówno `ByVal` parametr, jak i `ByRef` . Mając na względzie stawkę odsetek, `rate` i sumę pieniędzy, `debt` zadanie procedury polega na obliczeniu nowej wartości, `debt` która jest wynikiem zastosowania stopy oprocentowania do oryginalnej wartości `debt` . Ponieważ `debt` jest `ByRef` parametrem, Nowa suma jest odzwierciedlona w wartości argumentu kodu wywołującego, który odnosi się do `debt` . Parametr `rate` jest `ByVal` parametrem, ponieważ `Calculate` nie należy zmieniać jego wartości.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbcnProcedures#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class2.vb#74)]  
  
## <a name="see-also"></a>Zobacz też

- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Instrukcje: przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)
- [Instrukcje: zmiana wartości argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)
- [Instrukcje: ochrona argumentu procedury przed zmianami wartości](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Instrukcje: wymuszanie przekazywania argumentu przez wartość](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md)
- [Typy wartości i odwołań](../data-types/value-types-and-reference-types.md)
