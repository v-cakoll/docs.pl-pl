---
title: "Porady: użycie globalnych aliasów przestrzeni nazw (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f2a854d2f963578cb8b89da445af660f3c029fae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a>Porady: użycie globalnych aliasów przestrzeni nazw (Przewodnik programowania w języku C#)
Umożliwia uzyskiwanie dostępu do członka w globalnej [przestrzeni nazw](../../../csharp/language-reference/keywords/namespace.md) jest przydatne, gdy element członkowski może być ukryty przez inną jednostkę o takiej samej nazwie.  
  
 Na przykład w poniższym kodzie `Console` jest rozpoznawana jako `TestApp.Console` zamiast do `Console` wpisz <xref:System> przestrzeni nazw.  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-use-the-global-namespace-alias_1.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#1](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_2.cs)]  
  
 Przy użyciu `System.Console` nadal powoduje błąd, ponieważ `System` przestrzeni nazw jest ukryty przez klasę `TestApp.System`:  
  
 [!code-csharp[csProgGuideNamespaces#2](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_3.cs)]  
  
 Jednak można obejść ten błąd przy użyciu `global::System.Console`, podobnie do następującej:  
  
 [!code-csharp[csProgGuideNamespaces#3](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_4.cs)]  
  
 Po lewej identyfikator `global`, wyszukaj identyfikator prawo rozpoczyna się w globalnej przestrzeni nazw. Na przykład następujące oświadczenie odwołuje się do `TestApp` jako członek globalnej przestrzeni.  
  
 [!code-csharp[csProgGuideNamespaces#4](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_5.cs)]  
  
 Oczywiście, tworzenie własnych przestrzeni nazw o nazwie `System` nie jest zalecane, i jest mało prawdopodobne, wystąpi żadnego kodu, w którym miało to miejsce. Jednak w większych projektów jest bardzo prawdziwy możliwość, że duplikatów nazw może wystąpić w czy innej formie. W takich przypadkach kwalifikator globalnej przestrzeni nazw jest Twoje gwarancji, że można określić głównej przestrzeni nazw.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie obszar nazw `System` jest używana do włączenia klasy `TestClass` w związku z tym `global::System.Console` musi być używany do odwołania `System.Console` klasy, która jest ukryty przez `System` przestrzeni nazw. Ponadto alias `colAlias` służy do odwoływania się do przestrzeni nazw `System.Collections`; w związku z tym wystąpienie <xref:System.Collections.Hashtable?displayProperty=nameWithType> został utworzony za pomocą tego aliasu zamiast przestrzeni nazw.  
  
 [!code-csharp[csProgGuideNamespaces#5](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_6.cs)]  
  
 **1**  
**B 2**  
**C 3**   
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Przestrzenie nazw](../../../csharp/programming-guide/namespaces/index.md)  
 [. Operator](../../../csharp/language-reference/operators/member-access-operator.md)  
 [:: — Operator](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [extern](../../../csharp/language-reference/keywords/extern.md)
