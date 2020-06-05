---
title: Parameter — Tablice
ms.date: 07/20/2015
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
ms.openlocfilehash: dac0575d73ffd4159e89bff344915a33b9d0e5d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364282"
---
# <a name="parameter-arrays-visual-basic"></a>Parameter — Tablice (Visual Basic)
Zazwyczaj nie można wywołać procedury z więcej argumentów niż Deklaracja procedury. Jeśli potrzebujesz nieograniczonej liczby argumentów, możesz zadeklarować *tablicę parametrów*, która umożliwia procedurę akceptowania tablicy wartości dla parametru. Podczas definiowania procedury nie trzeba znać liczby elementów w tablicy parametrów. Rozmiar tablicy jest określany indywidualnie przez każde wywołanie procedury.  
  
## <a name="declaring-a-paramarray"></a>Deklarowanie ParamArray  
 Za pomocą słowa kluczowego [ParamArray](../../../language-reference/modifiers/paramarray.md) można zauważyć tablicę parametrów na liście parametrów. Mają zastosowanie następujące zasady:  
  
- Procedura może definiować tylko jedną tablicę parametrów i musi być ostatnim parametrem w definicji procedury.  
  
- Tablica parametrów musi być przenoszona przez wartość. Dobrym sposobem programowania jest jawne dołączenie słowa kluczowego [ByVal](../../../language-reference/modifiers/byval.md) w definicji procedury.  
  
- Tablica parametrów jest automatycznie opcjonalna. Jego wartość domyślna to pusta Jednowymiarowa tablica typu elementu tablicy parametrów.  
  
- Wszystkie parametry poprzedzające tablicę parametrów muszą być wymagane. Tablica parametrów musi być jedynym opcjonalnym parametrem.  
  
## <a name="calling-a-paramarray"></a>Wywoływanie ParamArray  
 Po wywołaniu procedury, która definiuje tablicę parametrów, można podać argument w jednym z następujących sposobów:  
  
- Nic — to znaczy, że można pominąć argument [ParamArray](../../../language-reference/modifiers/paramarray.md) . W takim przypadku pusta tablica jest przenoszona do procedury. Jeśli jawnie przekażesz słowo kluczowe [Nothing](../../../language-reference/nothing.md) , tablica o wartości null zostanie przekazana do procedury i może skutkować NullReferenceException, jeśli wywołana procedura nie sprawdza tego warunku.
  
- Lista dowolnej liczby argumentów oddzielonych przecinkami. Typ danych każdego argumentu musi być niejawnie konwertowany na `ParamArray` Typ elementu.  
  
- Tablica z tym samym typem elementu co typ elementu tablicy parametrów.  
  
 We wszystkich przypadkach kod w procedurze traktuje tablicę parametrów jako tablicę jednowymiarową z elementami tego samego typu danych co `ParamArray` Typ danych.  
  
> [!IMPORTANT]
> Za każdym razem, gdy zajmujesz się tablicą, która może być nienieskończona, istnieje ryzyko, że zachodzi taka Wewnętrzna pojemność aplikacji. Jeśli zaakceptujesz tablicę parametrów, należy sprawdzić rozmiar tablicy, do której przeszedł kod wywołujący. Wykonaj odpowiednie kroki, jeśli są zbyt duże dla aplikacji. Aby uzyskać więcej informacji, zobacz [tablice](../arrays/index.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład definiuje i wywołuje funkcję `calcSum` . `ParamArray`Modyfikator dla parametru `args` umożliwia funkcji akceptującej zmienną liczbę argumentów.  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 Poniższy przykład definiuje procedurę z tablicą parametrów i wyprowadza wartości wszystkich elementów tablicy przekazaną do tablicy parametrów.  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)
- [Przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md)
- [Parametry opcjonalne](./optional-parameters.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Tablice](../arrays/index.md)
- [Opcjonalne](../../../language-reference/modifiers/optional.md)
