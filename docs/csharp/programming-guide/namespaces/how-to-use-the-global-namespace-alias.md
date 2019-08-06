---
title: 'Instrukcje: Użyj globalnego aliasu przestrzeni nazw C# — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
ms.openlocfilehash: b163981d3cf6d56ab953757931b0b386a47263ff
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796287"
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
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Przestrzenie nazw](../../../csharp/programming-guide/namespaces/index.md)
- [:: operator](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [extern](../../../csharp/language-reference/keywords/extern.md)
