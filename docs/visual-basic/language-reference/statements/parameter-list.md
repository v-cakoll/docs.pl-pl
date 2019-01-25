---
title: Lista parametrów (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
ms.openlocfilehash: 7c5f6fa4015c90802cdd48d3a70f06f56c926c7a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662286"
---
# <a name="parameter-list-visual-basic"></a>Lista parametrów (Visual Basic)
Określa parametry, których oczekuje procedury, gdy jest wywoływana. Wiele parametrów są oddzielone przecinkami. Poniżej przedstawiono składnię jeden parametr.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## <a name="parts"></a>Części  
 `attributelist`  
 Opcjonalna. Lista atrybutów, które są stosowane do tego parametru. Należy ująć [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasy ("`<`"i"`>`").  
  
 `Optional`  
 Opcjonalna. Określa, że ten parametr nie jest wymagany, gdy procedura jest wywoływana.  
  
 `ByVal`  
 Opcjonalna. Określa, że procedura nie można zastąpić, lub ponowne przypisanie zmiennej elementu bazowego odnośnego argumentu w wywoływanym kodzie.  
  
 `ByRef`  
 Opcjonalna. Określa, czy procedurę można zmodyfikować element podstawowy zmiennej w wywoływanym kodzie taki sam sposób, który sam kod wywołujący może.  
  
 `ParamArray`  
 Opcjonalna. Określa, że ostatnim parametrem na liście parametrów jest opcjonalną tablicę elementów określonego typu danych. Dzięki temu kod wywołujący przekazać dowolną liczbę argumentów do procedury.  
  
 `parametername`  
 Wymagana. Nazwa zmiennej lokalnej, reprezentujący parametr.  
  
 `parametertype`  
 Jeśli wymagane `Option Strict` jest `On`. Typ danych zmiennej lokalnej, reprezentujący parametr.  
  
 `defaultvalue`  
 Wymagane dla `Optional` parametrów. Dowolne wyrażenie stałe lub stałą, którego wynikiem jest typ danych parametru. Jeśli typ jest `Object`, lub klasy, interfejsu, tablicy lub struktury, wartość domyślna może składać się `Nothing`.  
  
## <a name="remarks"></a>Uwagi  
 Parametry są ujęte w nawiasy i rozdzielone przecinkami. Parametr może być zadeklarowana z dowolnego typu danych. Jeśli nie określisz `parametertype`, jego wartość domyślna to `Object`.  
  
 Gdy kod wywołujący wywołuje procedurę, przekazuje on *argument* do wszystkich wymaganych parametrów. Aby uzyskać więcej informacji, zobacz [różnice pomiędzy parametrami i argumentami](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).  
  
 Argument, którego kod wywołujący przekazuje do każdego z parametrów jest wskaźnik do podstawowego elementu w wywoływanym kodzie. Jeśli ten element jest *nonvariable* (stałą, literał, wyliczenie lub wyrażenia), nie jest możliwe dla jakiegokolwiek kodu ją zmienić. Jeśli jest *zmiennej* — element (zadeklarowanej zmiennej, pola, właściwości, elementu tablicy lub element struktury), kod wywołujący można go zmienić. Aby uzyskać więcej informacji, zobacz [różnice między modyfikowalnymi i niemodyfikowalnymi argumenty](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).  
  
 Jeśli element zmienna jest przekazywana `ByRef`, procedury można go także zmienić. Aby uzyskać więcej informacji, zobacz [różnice pomiędzy przekazywaniem argumentu według wartości i według odwołania](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## <a name="rules"></a>reguły  
  
-   **Nawiasy.** Jeśli określisz listę parametrów, należy ująć go w nawiasach. Jeśli nie ma żadnych parametrów, ale nadal używać nawiasów obejmujących pustej listy. Zwiększa to czytelność kodu przez wyjaśnienie, że element jest procedurą.  
  
-   **Parametry opcjonalne.** Jeśli używasz `Optional` modyfikator parametru, wszystkie kolejne parametry na liście musi być również opcjonalne i można zadeklarować za pomocą `Optional` modyfikator.  
  
     Należy podać co deklaracja parametru opcjonalnego `defaultvalue` klauzuli.  
  
     Aby uzyskać więcej informacji, zobacz [następujące parametry opcjonalne](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).  
  
-   **Tablice parametrów.** Należy określić `ByVal` dla `ParamArray` parametru.  
  
     Nie można używać obu `Optional` i `ParamArray` liście parametrów.  
  
     Aby uzyskać więcej informacji, zobacz [Parameter — tablice](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).  
  
-   **Mechanizm przekazywania.** Domyślny mechanizm dla każdego argumentu jest `ByVal`, co oznacza procedury nie można zmienić podstawowego elementu zmiennej. Jednak jeśli element jest typem referencyjnym, procedury można zmodyfikować zawartość lub elementy członkowskie obiektu bazowego, mimo że nie można zastąpić, lub ponownie przypisać samego obiektu.  
  
-   **Nazwy parametrów.** Jeśli typ danych parametru jest tablicą, postępuj zgodnie z `parametername` bezpośrednio przez nawiasy. Aby uzyskać więcej informacji na temat nazw parametrów, zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `Function` procedury, która definiuje dwa parametry.  
  
 [!code-vb[VbVbalrStatements#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-list_1.vb)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Omówienie atrybuty](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Instrukcje: przerywanie i łączenie instrukcji w kodzie](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
