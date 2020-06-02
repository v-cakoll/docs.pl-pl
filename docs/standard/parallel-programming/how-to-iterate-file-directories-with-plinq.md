---
title: 'Instrukcje: Iteracja katalogów plików przy użyciu technologii PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
ms.openlocfilehash: abf31ea69af6a85140efb783959a9a586ef6a59e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278002"
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>Instrukcje: Iteracja katalogów plików przy użyciu technologii PLINQ

W tym artykule przedstawiono dwa sposoby zrównoleglanie operacji na katalogach plików. Pierwsze zapytanie używa metody, <xref:System.IO.Directory.GetFiles%2A> Aby wypełnić tablicę nazw plików w katalogu i wszystkich podkatalogach. Ta metoda może wprowadzić opóźnienie na początku operacji, ponieważ nie jest zwracana do momentu wypełnienia całej tablicy. Jednak po wypełnieniu tablicy PLINQ może szybko przetwarzać ją w sposób równoległy.  
  
Drugie zapytanie używa <xref:System.IO.Directory.EnumerateDirectories%2A> metod static i <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> , które natychmiast zaczynają zwracać wyniki. Takie podejście może być szybsze w przypadku iteracji nad dużymi drzewami katalogów, ale czas przetwarzania w porównaniu do pierwszego przykładu zależy od wielu czynników.  
  
> [!NOTE]
> Te przykłady są przeznaczone do zademonstrowania użycia i mogą nie działać szybciej niż równoważne LINQ to Objects sekwencyjne zapytanie. Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [Opis przyspieszenie w PLINQ](understanding-speedup-in-plinq.md).  
  
## <a name="getfiles-example"></a>Przykład GetFiles

 Ten przykład pokazuje, jak wykonać iterację katalogów plików w prostych scenariuszach, gdy masz dostęp do wszystkich katalogów w drzewie, rozmiary plików nie są duże i czasy dostępu nie są istotne. Takie podejście obejmuje okres opóźnienia na początku podczas konstruowania tablicy nazw plików.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="enumeratefiles-example"></a>Przykład EnumerateFiles

 Ten przykład pokazuje, jak wykonać iterację katalogów plików w prostych scenariuszach, gdy masz dostęp do wszystkich katalogów w drzewie, rozmiary plików nie są duże i czasy dostępu nie są istotne. Takie podejście rozpoczyna generowanie wyników szybciej niż w poprzednim przykładzie.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 W przypadku korzystania z programu <xref:System.IO.Directory.GetFiles%2A> upewnij się, że masz wystarczające uprawnienia do wszystkich katalogów w drzewie. W przeciwnym razie zostanie zgłoszony wyjątek i nie zostaną zwrócone żadne wyniki. W przypadku korzystania z programu <xref:System.IO.Directory.EnumerateDirectories%2A> w zapytaniu PLINQ problemy są obsługiwane w sposób ciągły, który umożliwia kontynuowanie iteracji. Jeśli kod musi obsługiwać wyjątki we/wy lub dostęp nieautoryzowany, należy wziąć pod uwagę podejście opisane w temacie [How to: Iterowanie katalogów plików z klasą równoległą](how-to-iterate-file-directories-with-the-parallel-class.md).  
  
 Jeśli opóźnienie operacji we/wy jest problemem, na przykład w przypadku wejścia/wyjścia plików przez sieć, należy rozważyć użycie jednej z asynchronicznych technik we/wy opisanych w [TPL i tradycyjnym .NET Framework programowaniu asynchronicznym](tpl-and-traditional-async-programming.md) oraz w tym [wpisie w blogu](https://devblogs.microsoft.com/pfxteam/parallel-extensions-and-io/).  
  
## <a name="see-also"></a>Zobacz także

- [Równoległe LINQ (PLINQ)](introduction-to-plinq.md)
