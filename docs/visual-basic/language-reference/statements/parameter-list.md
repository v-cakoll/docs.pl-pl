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
ms.openlocfilehash: 147a2501219db9f1f1c10f9cf1a81aa395b5ec2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605059"
---
# <a name="parameter-list-visual-basic"></a>Lista parametrów (Visual Basic)
Określa parametry, które oczekuje procedury, gdy jest wywoływana. Wiele parametrów są oddzielone przecinkami. Poniżej przedstawiono składnię jeden parametr.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## <a name="parts"></a>Części  
 `attributelist`  
 Opcjonalna. Lista atrybutów, które są stosowane do tego parametru. Musisz ją ująć [lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasy ("`<`"i"`>`").  
  
 `Optional`  
 Opcjonalna. Określa, że ten parametr nie jest wymagany, gdy procedura jest wywoływana.  
  
 `ByVal`  
 Opcjonalna. Określa, że procedura nie można zastąpić lub ponownie przypisać zmiennej element bazowy odpowiadającego mu argumentu w wywoływanym kodzie.  
  
 `ByRef`  
 Opcjonalna. Określa, czy procedurę można zmodyfikować odpowiedniego elementu zmiennej w wywoływanym kodzie w taki sam sposób można kodu wywołującego.  
  
 `ParamArray`  
 Opcjonalna. Określa, że ostatnim parametrem na liście parametrów opcjonalną tablicę elementów określonego typu danych. Dzięki temu kod wywołujący przekazać dowolnej liczby argumentów do procedury.  
  
 `parametername`  
 Wymagana. Nazwa zmiennej lokalnej reprezentujące parametr.  
  
 `parametertype`  
 Jeśli wymagane `Option Strict` jest `On`. Typ danych zmiennej lokalnej reprezentujące parametr.  
  
 `defaultvalue`  
 Wymagany dla `Optional` parametrów. Dowolne wyrażenie stałej lub stała, którego wynikiem jest typ danych parametru. Jeśli typ jest `Object`, lub klasy, interfejsu, tablicy lub struktury, wartością domyślną można tylko `Nothing`.  
  
## <a name="remarks"></a>Uwagi  
 Parametry są ujęte w nawiasy i oddzielonych przecinkami. Parametr mogą być deklarowane w przypadku każdego typu danych. Jeśli nie określisz `parametertype`, domyślne `Object`.  
  
 Gdy kod wywołujący wywołuje procedurę, przekazuje *argument* do wszystkich wymaganych parametrów. Aby uzyskać więcej informacji, zobacz [różnice pomiędzy parametrami i argumentami](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).  
  
 Argument kod wywołujący przekazuje do każdego parametru jest wskaźnik do odpowiedniego elementu kodu wywołującego. Jeśli ten element jest *nonvariable* (stała, literal, wyliczenie lub wyrażenie), nie jest możliwe w dla żadnego kodu go zmienić. Jeśli jest *zmiennej* elementu (zadeklarowana zmienna, pola, właściwości, element tablicy lub element struktury), można go zmienić kod wywołujący. Aby uzyskać więcej informacji, zobacz [różnice między modyfikowalnymi i niemodyfikowalnymi argumenty](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).  
  
 Jeśli element zmienna jest przekazywana `ByRef`, procedury można go także zmienić. Aby uzyskać więcej informacji, zobacz [różnice pomiędzy przekazywaniem argumentu według wartości i według odwołania](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## <a name="rules"></a>Reguły  
  
-   **Nawiasy.** Jeśli określisz listę parametrów, należy ująć go w nawiasach. Jeśli nie ma żadnych parametrów, możesz nadal używać nawiasów pustej listy otaczającej. Zwiększa to czytelność kodu przez wyjaśnienia, że element jest procedurą.  
  
-   **Parametry opcjonalne.** Jeśli używasz `Optional` modyfikator w parametrze, wszystkie kolejne parametry na liście muszą być opcjonalne i można zadeklarować przy użyciu `Optional` modyfikator.  
  
     Należy podać co deklaracja opcjonalny parametr `defaultvalue` klauzuli.  
  
     Aby uzyskać więcej informacji, zobacz [następujące parametry opcjonalne](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).  
  
-   **Tablice parametrów.** Należy określić `ByVal` dla `ParamArray` parametru.  
  
     Nie można używać obu `Optional` i `ParamArray` w tej samej listy parametrów.  
  
     Aby uzyskać więcej informacji, zobacz [tablice parametrów](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).  
  
-   **Mechanizm przekazywania.** Domyślny mechanizm dla każdego argumentu jest `ByVal`, co oznacza procedury nie można zmienić odpowiedniego elementu zmiennej. Jednak jeśli element jest typem referencyjnym, procedury można zmodyfikować zawartość lub elementy członkowskie obiektu podstawowego, nawet jeśli nie można zastąpić, lub ponownie przypisać samego obiektu.  
  
-   **Nazwy parametrów.** Typ danych parametru jest tablicą, należy wykonać `parametername` natychmiast w nawiasach. Aby uzyskać więcej informacji na nazwy parametrów, zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `Function` procedury, który definiuje dwa parametry.  
  
 [!code-vb[VbVbalrStatements#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-list_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Atrybuty — omówienie](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [Instrukcje: przerywanie i łączenie instrukcji w kodzie](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
