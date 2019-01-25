---
title: Przekazywanie argumentów według wartości i według odwołania (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- passing arguments [Visual Basic], by value or by reference
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing [Visual Basic], by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
ms.openlocfilehash: 86dc813c264f45e4f9c2cdf8d2dc7e7e6603c4d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725366"
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>Przekazywanie argumentów według wartości i według odwołania (Visual Basic)
W języku Visual Basic można przekazać argument do procedury *według wartości* lub *przez odwołanie*. Jest to nazywane *mechanizm przekazywania*, i określa, czy procedurę można zmodyfikować elementu programistycznego, bazowy argumentu w wywoływanym kodzie. Deklaracja procedury określa mechanizm przekazywania dla każdego parametru, określając [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) — słowo kluczowe.  
  
## <a name="distinctions"></a>Różnice  
 Podczas przekazywania argumentów do procedury, należy pamiętać o kilku różnych różnice, które współdziałają ze sobą:  
  
-   Czy jest podstawowym elementem programowania, modyfikowalnymi i niemodyfikowalnymi  
  
-   Czy z samym argumentem jest modyfikowalnymi i niemodyfikowalnymi  
  
-   Czy argument jest przekazywany przez wartość lub przez odwołanie  
  
-   Czy typ danych argumentu, który jest typem wartości lub typem referencyjnym  
  
 Aby uzyskać więcej informacji, zobacz [różnice między modyfikowalnymi i niemodyfikowalnymi argumenty](./differences-between-modifiable-and-nonmodifiable-arguments.md) i [różnice pomiędzy przekazywaniem argumentu według wartości i według odwołania](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## <a name="choice-of-passing-mechanism"></a>Wybór mechanizm przekazywania  
 Wybierz mechanizm przekazywania dokładnie dla każdego argumentu.  
  
-   **Ochrona**. Wybierając między mechanizmy dwóch przekazywania, najbardziej istotna jest narażenie wywołaniem zmienne, aby zmienić. Zaletą przekazywaniem argumentu `ByRef` jest procedura może zwracać wartość do wywołującego kodu za pomocą tego argumentu. Zaletą przekazywaniem argumentu `ByVal` jest chroni zmienną, przed zmianami przez procedurę.  
  
-   **Wydajność**. Mimo że mechanizm przekazywania może mieć wpływ na wydajność kodu, różnica polega na zwykle nieistotne. Jedynym wyjątkiem jest typ wartości przekazane `ByVal`. W tym przypadku języka Visual Basic kopiuje zawartość danych całej argumentu. W związku z tym, dla typu duża wartość, takie jak struktury, może być bardziej efektywne w celu przekazania jej `ByRef`.  
  
     Dla typów referencyjnych tylko wskaźnik do danych jest skopiowany (cztery bajty na platformach 32-bitowych, 8 bajtów na platformach 64-bitowych). W związku z tym, można przekazać argumenty typu `String` lub `Object` według wartości bez szkody wydajności.  
  
## <a name="determination-of-the-passing-mechanism"></a>Oznaczanie mechanizm przekazywania  
 Deklaracja procedury określa mechanizm przekazywania dla każdego parametru. Nie można przesłonić, kod wywołujący `ByVal` mechanizm.  
  
 Jeśli parametr jest zadeklarowana za pomocą `ByRef`, kod wywołujący może wymusić mechanizm `ByVal` , umieszczając nazwę argumentu w nawiasach w wywołaniu. Aby uzyskać więcej informacji, zobacz [jak: Wymuszanie być przekazywany przez wartość argumentu](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
 Domyślnie w języku Visual Basic nie jest przekazywanie argumentów według wartości.  
  
## <a name="when-to-pass-an-argument-by-value"></a>Gdy do przekazywania argumentu przez wartość  
  
-   W przypadku wywoływania elementu kodu bazowego argument jest elementem niemodyfikowalnymi, Zadeklaruj odpowiadającego mu parametru [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Brak kodu można zmienić wartości elementu niemodyfikowalnymi.  
  
-   Jeśli element podstawowy jest modyfikowalny, ale nie chcesz, aby procedury, aby można było zmienić jego wartość, Zadeklaruj parametr `ByVal`. Kod wywołujący można zmienić wartość elementu można modyfikować, przekazać przez wartość.  
  
## <a name="when-to-pass-an-argument-by-reference"></a>Kiedy należy przekazywać argumentów przez odwołanie  
  
-   Jeśli procedura ma oryginalnych trzeba zmieniać element podstawowy w wywoływanym kodzie, należy zadeklarować odpowiadającego mu parametru [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).  
  
-   Jeśli prawidłowe wykonanie kodu jest zależna od procedury, zmieniając element podstawowy w wywoływanym kodzie, Zadeklaruj parametr `ByRef`. W przypadku przekazania według wartości lub kod wywołujący zastępuje `ByRef` przekazywanie mechanizm umieszczając argument w nawiasach, po wywołaniu procedury może dawać nieoczekiwane wyniki.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład ilustruje, kiedy należy przekazywać argumentów przez wartość i kiedy do przekazywania ich przez odwołanie. Procedura `Calculate` znajdują się oba `ByVal` i `ByRef` parametru. Biorąc pod uwagę stopy procentowej `rate`i sumę pieniądze, `debt`, zadaniem procedura jest obliczyć nową wartość dla `debt` oznacza to wynik zastosowania stopę do oryginalnej wartości elementu `debt`. Ponieważ `debt` jest `ByRef` parametrów, nowa suma znajduje odzwierciedlenie w wartości argumentu w wywoływanym kodzie, który odpowiada `debt`. Parametr `rate` jest `ByVal` parametru ponieważ `Calculate` nie należy zmieniać jego wartość.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbcnProcedures#74](./codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Instrukcje: Przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)
- [Instrukcje: Zmień wartość argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)
- [Instrukcje: Chronienie argumentu procedury przed zmianami wartości](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Instrukcje: Wymuszanie być przekazywany przez wartość argumentu](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md)
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
