---
title: "Porady: Iteracja po katalogach plików z wykorzystaniem technologii PLINQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 40fd9f64b5702f5205b7817f3de1e0a8709c5a63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>Porady: Iteracja po katalogach plików z wykorzystaniem technologii PLINQ
W tym przykładzie przedstawiono dwie metody proste parallelize operacje na katalogi plików. Pierwsze zapytanie używa <xref:System.IO.Directory.GetFiles%2A> metodę, aby wypełnić tablicę nazw plików w katalogu i jego podkatalogach. Ta metoda nie zwraca dopóki cała tablica jest wypełniana i w związku z tym może powodować opóźnienia na początku operacji. Jednak po zapełnieniu tablicy, PLINQ można go przetworzyć równolegle bardzo szybko.  
  
 Drugi zapytanie używa statycznych <xref:System.IO.Directory.EnumerateDirectories%2A> i <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metody, które rozpocząć od razu zwracania wyników. Ta metoda może być szybsza podczas są Iterowanie po drzewa dużych katalogów, mimo że czas przetwarzania w porównaniu do w pierwszym przykładzie może zależeć od wielu czynników.  
  
> [!WARNING]
>  Te przykłady służą jedynie do zademonstrowania użycia i mogą nie działać szybciej niż równoważne sekwencyjnych zapytań LINQ do obiektów zapytania. Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób iteracja katalogi plików w scenariuszach proste, gdy masz dostęp do wszystkich katalogów w drzewie, nie są bardzo duże rozmiary plików i godziny dostępu nie są istotne. Takie podejście obejmuje okres czas oczekiwania na początku, gdy jest tworzona tablica nazw plików.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób iteracja katalogi plików w scenariuszach proste, gdy masz dostęp do wszystkich katalogów w drzewie, nie są bardzo duże rozmiary plików i godziny dostępu nie są istotne. Takie podejście rozpoczyna szybciej niż w poprzednim przykładzie przedstawiania wyników.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 Korzystając z <xref:System.IO.Directory.GetFiles%2A>, pamiętaj, że masz wystarczające uprawnienia we wszystkich katalogach w drzewie. W przeciwnym razie zostanie wygenerowany wyjątek i nie będzie można zwrócić wyników. Korzystając z <xref:System.IO.Directory.EnumerateDirectories%2A> w zapytaniu PLINQ jest problematyczne do obsługi wyjątków we/wy w sposób bezpieczne, który umożliwia kontynuowanie iteracja. Jeśli kod musi obsługiwać operacje We/Wy lub wyjątki nieautoryzowanego dostępu, a następnie należy rozważyć podejścia opisanego w [porady: iterowanie katalogi plików z wykorzystaniem klas równoległych](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).  
  
 Jeśli czas oczekiwania operacji We/Wy problem, na przykład plik we/wy przez sieć, należy wziąć pod uwagę przy użyciu jednej z asynchroniczne We/Wy metod opisanych w [TPL i tradycyjnych .NET Framework asynchronicznego programowania](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) i w tym [wpis w blogu ](http://go.microsoft.com/fwlink/?LinkID=186458).  
  
## <a name="see-also"></a>Zobacz też  
 [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
