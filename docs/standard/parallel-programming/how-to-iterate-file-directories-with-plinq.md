---
title: 'Instrukcje: Iteracja katalogów plików przy użyciu technologii PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f80f1903c4187a8da93d42ec6de363d097bcc37
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988173"
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>Instrukcje: Iteracja katalogów plików przy użyciu technologii PLINQ
Ten przykład przedstawia dwa proste sposoby zrównoleglanie operacji na katalogach plików. Pierwsze zapytanie używa metody, <xref:System.IO.Directory.GetFiles%2A> aby wypełnić tablicę nazw plików w katalogu i wszystkich podkatalogach. Ta metoda nie zwraca wartości, dopóki cała tablica nie zostanie wypełniona i w związku z tym może wprowadzić opóźnienie na początku operacji. Jednak po wypełnieniu tablicy PLINQ może szybko przetwarzać ją w sposób równoległy.  
  
 Drugie zapytanie używa metod statycznych <xref:System.IO.Directory.EnumerateDirectories%2A> i <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> , które zaczynają natychmiast zwracać wyniki. Takie podejście może być szybsze w przypadku iteracji nad dużymi drzewami katalogów, chociaż czas przetwarzania w porównaniu z pierwszym przykładem może zależeć od wielu czynników.  
  
> [!WARNING]
> Te przykłady są przeznaczone do zademonstrowania użycia i mogą nie działać szybciej niż równoważne LINQ to Objects sekwencyjne zapytanie. Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [Opis przyspieszenie w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wykonać iterację katalogów plików w prostych scenariuszach, gdy masz dostęp do wszystkich katalogów w drzewie, rozmiary plików nie są bardzo duże, a czasy dostępu nie są istotne. Takie podejście obejmuje okres opóźnienia na początku podczas konstruowania tablicy nazw plików.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wykonać iterację katalogów plików w prostych scenariuszach, gdy masz dostęp do wszystkich katalogów w drzewie, rozmiary plików nie są bardzo duże, a czasy dostępu nie są istotne. Takie podejście rozpoczyna generowanie wyników szybciej niż w poprzednim przykładzie.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 W przypadku <xref:System.IO.Directory.GetFiles%2A>korzystania z programu upewnij się, że masz wystarczające uprawnienia do wszystkich katalogów w drzewie. W przeciwnym razie wyjątek zostanie wygenerowany i żadne wyniki nie zostaną zwrócone. W przypadku korzystania <xref:System.IO.Directory.EnumerateDirectories%2A> z programu w zapytaniu PLINQ problemy są obsługiwane w sposób ciągły, który umożliwia kontynuowanie iteracji. Jeśli kod musi obsługiwać wyjątki we/wy lub dostęp nieautoryzowany, należy wziąć pod uwagę podejście opisane w [temacie How to: Wykonaj iterację katalogów plików z klasą](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md)równoległą.  
  
 Jeśli opóźnienie operacji we/wy jest problemem, na przykład w przypadku wejścia/wyjścia plików przez sieć, należy rozważyć użycie jednej z asynchronicznych technik we/wy opisanych w [TPL i tradycyjnym .NET Framework programowaniu asynchronicznym](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) oraz w tym wpisie w [blogu](https://blogs.msdn.microsoft.com/pfxteam/2009/08/04/parallel-extensions-and-io/).  
  
## <a name="see-also"></a>Zobacz także

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
