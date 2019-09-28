---
title: GetType — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 2e3e05973f2ef72fef5e429bc98cc58b4b21f2c2
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592152"
---
# <a name="gettype-operator-visual-basic"></a>GetType — Operator (Visual Basic)
Zwraca obiekt <xref:System.Type> dla określonego typu. Obiekt <xref:System.Type> zawiera informacje o typie, takich jak jego właściwości, metody i zdarzenia.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---|---|  
|`typename`|Nazwa typu, dla którego chcesz uzyskać informacje.|  
  
## <a name="remarks"></a>Uwagi  
 Operator `GetType` zwraca obiekt <xref:System.Type> dla określonego `typename`. Można przekazać nazwę dowolnego zdefiniowanego typu w `typename`. Uwzględnione są następujące elementy:  
  
- Dowolny Visual Basic typ danych, taki jak `Boolean` lub `Date`.  
  
- Wszystkie .NET Framework klasy, struktury, modułu lub interfejsu, takie jak <xref:System.ArgumentException?displayProperty=nameWithType> lub <xref:System.Double?displayProperty=nameWithType>.  
  
- Wszystkie klasy, struktury, moduły lub interfejsy zdefiniowane przez aplikację.  
  
- Dowolna tablica zdefiniowana przez aplikację.  
  
- Każdy delegat zdefiniowany przez aplikację.  
  
- Każde Wyliczenie zdefiniowane przez Visual Basic, .NET Framework lub aplikację.  
  
 Jeśli chcesz uzyskać obiekt typu zmiennej obiektu, użyj metody <xref:System.Type.GetType%2A?displayProperty=nameWithType>.  
  
 Operator `GetType` może być przydatny w następujących sytuacjach:  
  
- Należy uzyskać dostęp do metadanych dla typu w czasie wykonywania. Obiekt <xref:System.Type> dostarcza metadane, takie jak elementy członkowskie typu i informacje o wdrożeniu. Jest to konieczne, na przykład w celu odzwierciedlenia zestawu. Aby uzyskać więcej informacji, zobacz <xref:System.Reflection?displayProperty=nameWithType>.  
  
- Chcesz porównać dwa odwołania do obiektów, aby sprawdzić, czy odwołują się do wystąpień tego samego typu. Jeśli tak, `GetType` zwraca odwołania do tego samego obiektu <xref:System.Type>.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano operator `GetType` w użyciu.  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a>Zobacz także

- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
