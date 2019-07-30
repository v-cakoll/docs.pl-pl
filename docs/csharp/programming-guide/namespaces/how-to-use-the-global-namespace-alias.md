---
title: 'Instrukcje: Użyj globalnego aliasu przestrzeni nazw C# — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
ms.openlocfilehash: f44bb1f010f154973fc6982882c9b5a09528da76
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629442"
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a>Instrukcje: Użyj globalnego aliasu przestrzeni nazwC# (Przewodnik programowania)
Możliwość uzyskania dostępu do elementu członkowskiego w globalnej [przestrzeni nazw](../../../csharp/language-reference/keywords/namespace.md) jest przydatna, gdy członek może być ukryty przez inną jednostkę o tej samej nazwie.  
  
 Na przykład, `Console` w poniższym kodzie, jest rozpoznawana jako `TestApp.Console` zamiast <xref:System> do `Console` typu w przestrzeni nazw.  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuideNamespaces#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#1)]  
  
 Użycie `System.Console` nadal powoduje błąd, `System` ponieważ przestrzeń nazw jest ukryta przez klasę `TestApp.System`:  
  
 [!code-csharp[csProgGuideNamespaces#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#2)]  
  
 Można jednak obejść ten błąd przy użyciu `global::System.Console`, jak to:  
  
 [!code-csharp[csProgGuideNamespaces#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#3)]  
  
 Gdy lewy identyfikator to `global`, wyszukiwanie właściwego identyfikatora zaczyna się od globalnej przestrzeni nazw. Na przykład następująca deklaracja jest odwołująca `TestApp` się jako składowa obszaru globalnego.  
  
 [!code-csharp[csProgGuideNamespaces#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#4)]  
  
 Oczywiście utworzenie własnych nazw o nazwie `System` nie jest zalecane i jest mało prawdopodobne, że zostanie napotkany kod, w którym wystąpił ten plik. Jednak w większych projektach jest to bardzo prawdziwa możliwość duplikowania przestrzeni nazw może wystąpić w jednej postaci lub w innym. W takich sytuacjach kwalifikator globalnej przestrzeni nazw jest gwarancją, że można określić główną przestrzeń nazw.  
  
## <a name="example"></a>Przykład  
 W `System` tym przykładzie przestrzeń nazw jest używana do uwzględnienia klasy `TestClass` , `global::System.Console` dlatego musi być używana do odwoływania `System.Console` się do klasy, która jest ukryta przez `System` przestrzeń nazw. Alias `colAlias` jest również używany do odwoływania się do przestrzeni nazw `System.Collections`, dlatego wystąpienie elementu <xref:System.Collections.Hashtable?displayProperty=nameWithType> zostało utworzone przy użyciu tego aliasu zamiast przestrzeni nazw.  
  
 [!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]  
  
**A 1**
**B 2**
**C 3**

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Przestrzenie nazw](../../../csharp/programming-guide/namespaces/index.md)
- [:: operator](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [extern](../../../csharp/language-reference/keywords/extern.md)
