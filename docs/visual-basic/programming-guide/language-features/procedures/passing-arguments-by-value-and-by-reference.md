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
ms.openlocfilehash: 2d333bc873ba055d7a7b53c50fcfeec4cc0f9491
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>Przekazywanie argumentów według wartości i według odwołania (Visual Basic)
W języku Visual Basic, argument można przekazać do procedury *przez wartość* lub *przez odwołanie*. Jest to nazywane *przekazywanie mechanizm*, i określa, czy procedurę można zmodyfikować elementu programistycznego bazowy argumentu w wywoływanym kodzie. Deklaracja procedury określa mechanizm przekazywania dla każdego parametru, określając [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) — słowo kluczowe.  
  
## <a name="distinctions"></a>Różnice  
 Podczas przekazywania argumentów do procedury, należy pamiętać o kilka różnych różnice, które współdziałają ze sobą:  
  
-   Określa, czy odpowiedniego elementu programowania jest modyfikowalnymi i niemodyfikowalnymi  
  
-   Określa, czy z samym argumentem jest modyfikowalnymi i niemodyfikowalnymi  
  
-   Określa, czy argument jest przekazywany przez wartość lub według odwołania  
  
-   Określa, czy typ danych argumentu jest typem wartości lub typ referencyjny  
  
 Aby uzyskać więcej informacji, zobacz [różnice między modyfikowalnymi i niemodyfikowalnymi argumenty](./differences-between-modifiable-and-nonmodifiable-arguments.md) i [różnice pomiędzy przekazywaniem argumentu według wartości i według odwołania](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## <a name="choice-of-passing-mechanism"></a>Wybór mechanizm przekazywania  
 Należy wybrać uważnie każdy argument mechanizm przekazywania.  
  
-   **Ochrona**. Wybierając między mechanizmy dwóch przekazywania, najważniejszych kryterium jest narażenia wywoływania zmienne można zmienić. Zaletą przekazywaniem argumentu `ByRef` jest procedura może zwracać wartości do wywołującego kodu za pomocą tego argumentu. Zaletą przekazywaniem argumentu `ByVal` jest chroni zmienną, zmianie przez procedurę.  
  
-   **Wydajność**. Mimo że mechanizm przekazywania może wpływać na wydajność kodu, różnica polega na tym zazwyczaj nieistotne. Jedynym wyjątkiem jest to typ wartości przekazane `ByVal`. W takim przypadku Visual Basic kopiuje zawartość danych argumentu. W związku z tym dla typu duża wartość przykład struktury, może być skuteczniejsza przekazywany `ByRef`.  
  
     Dla typów odwołań tylko wskaźnik do danych jest skopiowany (cztery bajtów na 32-bitowych platform ośmiu bajtów na platformach 64-bitowe). W związku z tym można przekazywać argumenty typu `String` lub `Object` przez wartość bez szkody wydajności.  
  
## <a name="determination-of-the-passing-mechanism"></a>Oznaczanie mechanizm przekazywania  
 Deklaracja procedury określa mechanizm przekazywania dla każdego parametru. Nie można zastąpić kod wywołujący `ByVal` mechanizmu.  
  
 Jeśli parametr jest zadeklarowany za pomocą `ByRef`, kod wywołujący może wymusić mechanizm `ByVal` umieszczając Nazwa argumentu w nawiasach w wywołaniu. Aby uzyskać więcej informacji, zobacz [porady: Wymuszanie przekazywania argumentu przez wartość](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
 Domyślnie w języku Visual Basic nie jest przekazywanie argumentów według wartości.  
  
## <a name="when-to-pass-an-argument-by-value"></a>Kiedy do przekazywania argumentu przez wartość  
  
-   Wywołanie elementu kodu źródłowego argument jest elementem niemodyfikowalnymi, zadeklarować odpowiadającego mu parametru [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Żaden kod nie można zmienić wartości elementu niemodyfikowalnymi.  
  
-   Jeśli odpowiedniego elementu można modyfikować, ale nie chcesz, aby procedury, aby można było zmienić jego wartość, należy zadeklarować parametru `ByVal`. Kod wywołujący można zmienić wartości można modyfikować elementu przekazany przez wartość.  
  
## <a name="when-to-pass-an-argument-by-reference"></a>Kiedy do przekazywania argumentu przez odwołanie  
  
-   Jeśli procedura ma oryginalny trzeba zmienić odpowiedniego elementu kodu wywołującego, należy zadeklarować odpowiadającego mu parametru [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).  
  
-   Jeśli prawidłowe wykonanie kodu zależy od procedury zmiana odpowiedniego elementu kodu wywołującego, Zadeklaruj parametr `ByRef`. Jeśli zostanie przekazany przez wartość lub kod wywołujący zastępuje `ByRef` przekazywanie mechanizmu umieszczając argument w nawiasach, wywołanie procedury mogą powodować nieoczekiwane rezultaty.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład pokazuje, kiedy przekazywanie argumentów według wartości i kiedy należy przekazać je przez odwołanie. Procedura `Calculate` ma zarówno atrybut `ByVal` i `ByRef` parametru. Podane stopie procentowej `rate`i gotówki, `debt`, zadanie procedury to obliczyć nową wartość dla `debt` będący wynikiem zastosowania stopę procentową w oryginalnej wartości `debt`. Ponieważ `debt` jest `ByRef` parametru nowa suma jest widoczny w wartości argumentu w wywoływanym kodzie, który odpowiada `debt`. Parametr `rate` jest `ByVal` parametru ponieważ `Calculate` nie należy zmieniać jego wartość.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbcnProcedures#74](./codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Instrukcje: przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)  
 [Instrukcje: zmiana wartości argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Instrukcje: ochrona argumentu procedury przed zmianami wartości](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Instrukcje: wymuszanie przekazywania argumentu przez wartość](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md)  
 [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
