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
ms.openlocfilehash: f88020c7407fb9c91e06bc2ee177773171e344fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="optional-visual-basic"></a>Optional (Visual Basic)
Określa, że argument procedury można pominąć, gdy procedura jest wywoływana.  
  
## <a name="remarks"></a>Uwagi  
 Dla każdego parametru opcjonalnego wartością domyślną tego parametru należy określić wyrażenie stałe. Jeśli wyrażenie ma [nic](../../../visual-basic/language-reference/nothing.md), wartość domyślna typu danych wartość jest używana jako wartość domyślna parametru.  
  
 Jeśli lista parametrów zawiera parametr opcjonalny, każdy parametr następującym musi być opcjonalne.  
  
 `Optional` Modyfikatora można używać w tych sytuacjach:  
  
-   [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  Podczas wywoływania procedury z lub bez parametrów, można przekazywać argumenty, według położenia lub nazwy. Aby uzyskać więcej informacji, zobacz [przekazywanie argumentów według pozycji i według nazwy](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).  
  
> [!NOTE]
>  Można również definiować procedury z opcjonalnymi parametrami za pomocą przeciążenia. Jeśli masz jeden opcjonalny parametr można zdefiniować dwie wersje przeciążone procedurą, który akceptuje parametr i bez. Aby uzyskać więcej informacji, zobacz [przeciążanie procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
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
 W poniższym przykładzie pokazano sposób wywołania procedury z argumentów przekazywanych według pozycji i argumenty przekazane według nazwy. Procedura zawiera dwa parametry opcjonalne.  
  
 [!code-vb[VbVbalrKeywords#21](../../../visual-basic/language-reference/codesnippet/VisualBasic/optional_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Lista parametrów](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [Parametry opcjonalne](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
