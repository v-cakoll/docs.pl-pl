---
title: GetType — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: e3b4ee9a1bfcc2132d3e9e1239ff2c8f7158e513
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966768"
---
# <a name="gettype-operator-visual-basic"></a>GetType — Operator (Visual Basic)
Zwraca <xref:System.Type> obiektu określonego typu. <xref:System.Type> Obiekt zawiera informacje o typie, takie jak jego właściwości, metody i zdarzenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
GetType(typename)  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---|---|  
|`typename`|Nazwa typu, dla którego chcesz uzyskać informacje.|  
  
## <a name="remarks"></a>Uwagi  
 `GetType` Operator zwraca <xref:System.Type> obiektu dla określonego `typename`. Można przekazać nazwę typu zdefiniowanego w `typename`. Uwzględnione są następujące elementy:  
  
-   Typ danych dowolnego języka Visual Basic, takie jak `Boolean` lub `Date`.  
  
-   Wszelkie .NET Framework klasy, struktury, moduł lub interfejsu, takich jak <xref:System.ArgumentException?displayProperty=nameWithType> lub <xref:System.Double?displayProperty=nameWithType>.  
  
-   Wszystkie klasy, struktury, modułu lub interfejsem zdefiniowanym przez aplikację.  
  
-   Tablica, wszelkie zdefiniowane przez aplikację.  
  
-   Dowolnym delegatem, który zdefiniowano w aplikacji.  
  
-   Wyliczenie, wszelkie zdefiniowane przez Visual Basic, .NET Framework lub aplikacji.  
  
 Aby uzyskać obiekt typu zmiennej obiektu, należy użyć <xref:System.Type.GetType%2A?displayProperty=nameWithType> metody.  
  
 `GetType` Operator może być przydatne w następujących okolicznościach:  
  
-   Należy uzyskać dostęp do metadanych dla typu w czasie wykonywania. <xref:System.Type> Obiektu dostarcza metadane, takie jak elementy członkowskie typu i informacje o wdrożeniu. Jest to potrzebne, na przykład, aby odzwierciedlić za pośrednictwem zestawu. Aby uzyskać więcej informacji, zobacz <xref:System.Reflection?displayProperty=nameWithType>.  
  
-   Chcesz porównać dwa odwołania do obiektu, aby sprawdzić, czy odnoszą się do wystąpienia tego samego typu. Jeśli tak, `GetType` zwraca odwołania do tej samej <xref:System.Type> obiektu.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano `GetType` operatora w użyciu.  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a>Zobacz także
- [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
