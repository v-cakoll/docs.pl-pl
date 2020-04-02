---
title: 'Porady: Iteracja po katalogach plików z wykorzystaniem technologii PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
ms.openlocfilehash: de33561e2ef8e8fe62e8179272abe8adfffecd6f
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80587762"
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>Porady: Iteracja po katalogach plików z wykorzystaniem technologii PLINQ
W tym przykładzie przedstawiono dwa proste sposoby równoległości operacji w katalogach plików. Pierwsza kwerenda używa <xref:System.IO.Directory.GetFiles%2A> tej metody do wypełniania tablicy nazw plików w katalogu i wszystkich podkatalogach. Ta metoda nie zwraca, dopóki cała tablica jest wypełniona i dlatego może wprowadzić opóźnienie na początku operacji. Jednak po wypełnieniu tablicy PLINQ może przetwarzać ją równolegle bardzo szybko.  
  
 Druga kwerenda używa <xref:System.IO.Directory.EnumerateDirectories%2A> statyczne <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> i metody, które zaczynają zwracać wyniki natychmiast. Takie podejście może być szybsze, gdy iteracji przez drzewa dużych katalogów, chociaż czas przetwarzania w porównaniu do pierwszego przykładu może zależeć od wielu czynników.  
  
> [!WARNING]
> Te przykłady są przeznaczone do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do kwerendy obiektów. Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszania w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak iterować za pomocą katalogów plików w prostych scenariuszach, gdy masz dostęp do wszystkich katalogów w drzewie, rozmiary plików nie są bardzo duże, a czasy dostępu nie są znaczące. Takie podejście obejmuje okres opóźnienia na początku, podczas gdy tablica nazw plików jest konstruowany.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak iterować za pomocą katalogów plików w prostych scenariuszach, gdy masz dostęp do wszystkich katalogów w drzewie, rozmiary plików nie są bardzo duże, a czasy dostępu nie są znaczące. Takie podejście rozpoczyna tworzenie wyników szybciej niż w poprzednim przykładzie.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 Podczas <xref:System.IO.Directory.GetFiles%2A>korzystania z programu upewnij się, że masz wystarczające uprawnienia do wszystkich katalogów w drzewie. W przeciwnym razie zostanie zgłoszony wyjątek i nie zostaną zwrócone żadne wyniki. Podczas korzystania <xref:System.IO.Directory.EnumerateDirectories%2A> z kwerendy PLINQ, jest problematyczne do obsługi wyjątków we/wy w sposób pełen wdzięku, który umożliwia kontynuowanie iteracji. Jeśli kod musi obsługiwać wyjątki we/wy lub nieautoryzowany dostęp, należy rozważyć podejście opisane w [Jak: Iteracji katalogów plików z parallel klasy](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).  
  
 Jeśli opóźnienie we/wy jest problemem, na przykład z plik we/wy w sieci, należy rozważyć użycie jednej z asynchronicznych technik we/wy opisanych w [TPL i tradycyjnych programach asynchronicznych .NET Framework](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) i w tym [wpisie](https://devblogs.microsoft.com/pfxteam/parallel-extensions-and-io/)w blogu .  
  
## <a name="see-also"></a>Zobacz też

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
