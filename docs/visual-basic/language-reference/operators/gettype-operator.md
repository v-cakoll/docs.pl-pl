---
title: GetType — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 581f576222eb149aede841a5da7a0e5f38c77b58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="gettype-operator-visual-basic"></a>GetType — Operator (Visual Basic)
Zwraca <xref:System.Type> obiektu określonego typu. <xref:System.Type> Obiektu zawiera informacje o typie, takie jak jego właściwości, metod i zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
GetType(typename)  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---|---|  
|`typename`|Nazwa typu, dla którego chcesz uzyskać informacje.|  
  
## <a name="remarks"></a>Uwagi  
 `GetType` Operator zwraca <xref:System.Type> obiektu dla określonego `typename`. Można przekazać nazwę typu zdefiniowanego w `typename`. Obejmuje to następujące elementy:  
  
-   Typ danych Visual Basic, takie jak `Boolean` lub `Date`.  
  
-   .NET Framework klasy, struktury, moduł lub interfejsu, takich jak <xref:System.ArgumentException?displayProperty=nameWithType> lub <xref:System.Double?displayProperty=nameWithType>.  
  
-   Wszystkie klasy, struktury, modułu lub interfejs zdefiniowany przez aplikację.  
  
-   Tablicy zdefiniowany przez aplikację.  
  
-   Delegat, wszelkie zdefiniowane przez aplikację.  
  
-   Wszystkie wyliczenia zdefiniowanych przez Visual Basic, .NET Framework lub aplikacji.  
  
 Aby uzyskać obiekt typu zmiennej obiektu, należy użyć <xref:System.Type.GetType%2A?displayProperty=nameWithType> metody.  
  
 `GetType` Operator może być przydatne w następujących okolicznościach:  
  
-   Należy uzyskać dostępu do metadanych dla typu w czasie wykonywania. <xref:System.Type> Obiektu udostępnia metadane, takie jak elementy członkowskie typu i informacje o wdrożeniu. To konieczne, na przykład do uwzględnienia w zestawie. Aby uzyskać więcej informacji, zobacz <xref:System.Reflection?displayProperty=nameWithType>.  
  
-   Chcesz porównać dwa odwołania do obiektów, aby sprawdzić, czy odnoszą się do wystąpień tego samego typu. Jeśli nie, `GetType` zwraca odwołania do tej samej <xref:System.Type> obiektu.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano `GetType` operatora w użyciu.  
  
 [!code-vb[VbVbalrOperators#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/gettype-operator_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
