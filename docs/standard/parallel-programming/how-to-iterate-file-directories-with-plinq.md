---
title: 'Porady: Iteracja po katalogach plików z wykorzystaniem technologii PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
ms.openlocfilehash: 90afc767e422515c6122b8a6ef0e63ffc07caf3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091366"
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>Porady: Iteracja po katalogach plików z wykorzystaniem technologii PLINQ
W tym przykładzie przedstawiono dwa proste sposoby równoległości operacji w katalogach plików. Pierwsza kwerenda <xref:System.IO.Directory.GetFiles%2A> używa metody do wypełniania tablicy nazw plików w katalogu i wszystkich podkatalogów. Ta metoda nie zwraca, dopóki cała tablica jest wypełniona i dlatego może wprowadzić opóźnienie na początku operacji. Jednak po wypełnieniu tablicy funkcja PLINQ może bardzo szybko przetwarzać ją równolegle.  
  
 Druga kwerenda używa <xref:System.IO.Directory.EnumerateDirectories%2A> <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> statycznych i metod, które zaczynają zwracać wyniki natychmiast. Takie podejście może być szybsze, gdy iterujesz drzewa dużych katalogów, chociaż czas przetwarzania w porównaniu z pierwszym przykładem może zależeć od wielu czynników.  
  
> [!WARNING]
> Te przykłady są przeznaczone do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do obiektów kwerendy. Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszenia w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak iterate nad katalogami plików w prostych scenariuszach, gdy masz dostęp do wszystkich katalogów w drzewie, rozmiary plików nie są bardzo duże, a czasy dostępu nie są znaczące. Takie podejście obejmuje okres opóźnienia na początku, podczas gdy tablica nazw plików jest konstruowana.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak iterate nad katalogami plików w prostych scenariuszach, gdy masz dostęp do wszystkich katalogów w drzewie, rozmiary plików nie są bardzo duże, a czasy dostępu nie są znaczące. Takie podejście zaczyna przynosić wyniki szybciej niż w poprzednim przykładzie.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 Podczas <xref:System.IO.Directory.GetFiles%2A>korzystania , upewnij się, że masz wystarczające uprawnienia do wszystkich katalogów w drzewie. W przeciwnym razie zostanie zgłoszony wyjątek i nie zostaną zwrócone żadne wyniki. Podczas korzystania <xref:System.IO.Directory.EnumerateDirectories%2A> z zapytania PLINQ, jest problematyczne do obsługi wyjątków we/wy w sposób wdzięku, który umożliwia kontynuowanie iteracji. Jeśli kod musi obsługiwać wyjątki we/wy lub nieautoryzowanego dostępu, należy wziąć pod uwagę podejście opisane w [jak: Iterować katalogi plików z klasą równoległą](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).  
  
 Jeśli opóźnienie we/wy jest problemem, na przykład z we/wy pliku za pomocą sieci, należy rozważyć użycie jednej z asynchronicznych technik we/wy opisanych w [TPL i tradycyjne .NET Framework programowania asynchronicznego](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) i w tym [blogu](https://devblogs.microsoft.com/pfxteam/parallel-extensions-and-io/).  
  
## <a name="see-also"></a>Zobacz też

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
