---
title: Optional (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: 40605d4843bfccf9d2819b3ec6f2ef65f9e9cf9a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64661329"
---
# <a name="optional-visual-basic"></a>Optional (Visual Basic)
Określa, czy argumentu procedury, można pominąć, jeśli procedura jest wywoływana.  
  
## <a name="remarks"></a>Uwagi  
 Dla każdego opcjonalnego parametru należy określić wyrażenie stałe, wartością domyślną tego parametru. Jeśli wyrażenie ma [nic](../../../visual-basic/language-reference/nothing.md), wartością domyślną typu danych wartość jest używana jako wartość domyślna parametru.  
  
 Jeśli lista parametrów zawiera parametr opcjonalny, każdy parametr, który po nim następuje również musi być opcjonalny.  
  
 `Optional` Modyfikator mogą być używane w tych kontekstach:  
  
- [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
- [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  Podczas wywoływania procedury z lub bez parametrów opcjonalnych, istnieje możliwość przekazywania argumentów według pozycji i według nazwy. Aby uzyskać więcej informacji, zobacz [przekazywanie argumentów według pozycji i według nazwy](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).  
  
> [!NOTE]
>  Aby zdefiniować procedury z opcjonalnymi parametrami, można również za pomocą przeciążenia. Jeśli masz jeden parametr opcjonalny, można zdefiniować dwie przeciążone wersje procedury, taki, który akceptuje parametr i jedną, która nie. Aby uzyskać więcej informacji, zobacz [przeciążanie procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano procedury, która ma parametr opcjonalny.  
  
```  
Public Function FindMatches(ByRef values As List(Of String),  
                            ByVal searchString As String,  
                            Optional ByVal matchCase As Boolean = False) As List(Of String)  
  
    Dim results As IEnumerable(Of String)  
  
    If matchCase Then  
        results = From v In values  
                  Where v.Contains(searchString)  
    Else  
        results = From v In values  
                  Where UCase(v).Contains(UCase(searchString))  
    End If  
  
    Return results.ToList()  
End Function  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wywołać procedurę z argumenty przekazywane według pozycji i argumenty przekazywane według nazwy. Procedura nie zawiera dwa parametry opcjonalne.  
  
 [!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]  
  
## <a name="see-also"></a>Zobacz także

- [Lista parametrów](../../../visual-basic/language-reference/statements/parameter-list.md)
- [Parametry opcjonalne](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
