---
title: 'Porady: Iteracja po katalogach plików z wykorzystaniem technologii PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
ms.openlocfilehash: 90afc767e422515c6122b8a6ef0e63ffc07caf3a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091366"
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>Porady: Iteracja po katalogach plików z wykorzystaniem technologii PLINQ
Ten przykład przedstawia dwa proste sposoby zrównoleglanie operacji na katalogach plików. Pierwsze zapytanie używa metody <xref:System.IO.Directory.GetFiles%2A>, aby wypełnić tablicę nazw plików w katalogu i wszystkich podkatalogach. Ta metoda nie zwraca wartości, dopóki cała tablica nie zostanie wypełniona i w związku z tym może wprowadzić opóźnienie na początku operacji. Jednak po wypełnieniu tablicy PLINQ może szybko przetwarzać ją w sposób równoległy.  
  
 Drugie zapytanie używa metod statycznych <xref:System.IO.Directory.EnumerateDirectories%2A> i <xref:System.IO.DirectoryInfo.EnumerateFiles%2A>, które natychmiast zwracają wyniki. Takie podejście może być szybsze w przypadku iteracji nad dużymi drzewami katalogów, chociaż czas przetwarzania w porównaniu z pierwszym przykładem może zależeć od wielu czynników.  
  
> [!WARNING]
> Te przykłady są przeznaczone do zademonstrowania użycia i mogą nie działać szybciej niż równoważne LINQ to Objects sekwencyjne zapytanie. Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [Opis przyspieszenie w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wykonać iterację katalogów plików w prostych scenariuszach, gdy masz dostęp do wszystkich katalogów w drzewie, rozmiary plików nie są bardzo duże, a czasy dostępu nie są istotne. Takie podejście obejmuje okres opóźnienia na początku podczas konstruowania tablicy nazw plików.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wykonać iterację katalogów plików w prostych scenariuszach, gdy masz dostęp do wszystkich katalogów w drzewie, rozmiary plików nie są bardzo duże, a czasy dostępu nie są istotne. Takie podejście rozpoczyna generowanie wyników szybciej niż w poprzednim przykładzie.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 W przypadku korzystania z <xref:System.IO.Directory.GetFiles%2A>upewnij się, że masz wystarczające uprawnienia do wszystkich katalogów w drzewie. W przeciwnym razie wyjątek zostanie wygenerowany i żadne wyniki nie zostaną zwrócone. W przypadku korzystania z <xref:System.IO.Directory.EnumerateDirectories%2A> w kwerendzie PLINQ problemy z obsługą we/wy mogą być obsługiwane w sposób płynny, który umożliwia kontynuowanie iteracji. Jeśli kod musi obsługiwać wyjątki we/wy lub dostęp nieautoryzowany, należy wziąć pod uwagę podejście opisane w temacie [How to: Iterowanie katalogów plików z klasą równoległą](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).  
  
 Jeśli opóźnienie operacji we/wy jest problemem, na przykład w przypadku wejścia/wyjścia plików przez sieć, należy rozważyć użycie jednej z asynchronicznych technik we/wy opisanych w [TPL i tradycyjnym .NET Framework programowaniu asynchronicznym](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) oraz w tym [wpisie w blogu](https://devblogs.microsoft.com/pfxteam/parallel-extensions-and-io/).  
  
## <a name="see-also"></a>Zobacz także

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
