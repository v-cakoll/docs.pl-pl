---
title: "GetType — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 38a984dce44133936f7f163e6afb20f0f336377c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
