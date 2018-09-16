---
title: 'Porady: Iteracja po katalogach plików z wykorzystaniem technologii PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d48f6df1e0e7680d2706c73c33dc817e1feaf1d5
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45689330"
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>Porady: Iteracja po katalogach plików z wykorzystaniem technologii PLINQ
Ten przykład przedstawia dwa upraszczają równoległe przetwarzanie operacji na katalogach plików. Pierwsze zapytanie używa <xref:System.IO.Directory.GetFiles%2A> metodę, aby wypełnić tablicę nazw plików w katalogu i wszystkich podkatalogach. Ta metoda nie zwraca dopiero po zapełnieniu macierz w całości i w związku z tym może wprowadzić opóźnienie na początku operacji. Jednak po wypełnieniu tablicy PLINQ może przetwarzać je w sposób równoległy bardzo szybko.  
  
 Drugie zapytanie używa statycznego <xref:System.IO.Directory.EnumerateDirectories%2A> i <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metod, których nazwy rozpoczynają się od razu zwracania wyników. Takie podejście może być szybsze, gdy są Iterowanie drzewa katalogów dużych, mimo że czas przetwarzania, w porównaniu z pierwszego przykładu może zależeć od wielu czynników.  
  
> [!WARNING]
>  Przykłady te służą do zademonstrowania użycia i może nie działać szybciej niż równoważna sekwencyjnego LINQ do kwerendy obiekty. Aby uzyskać więcej informacji na temat przyspieszenie zobacz [ogólne informacje o przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak iteracja katalogów plików w prostych scenariuszy po użytkownik ma dostęp do wszystkich katalogów w drzewie, nie są bardzo duże rozmiary plików i godziny dostępu nie są istotne. To podejście obejmuje okres opóźnienia na początku, gdy tablica nazwy pliku jest generowana.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak iteracja katalogów plików w prostych scenariuszy po użytkownik ma dostęp do wszystkich katalogów w drzewie, nie są bardzo duże rozmiary plików i godziny dostępu nie są istotne. To podejście zaczyna szybciej niż w poprzednim przykładzie przedstawiania wyników.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 Korzystając z <xref:System.IO.Directory.GetFiles%2A>, pamiętaj, że masz wystarczające uprawnienia na wszystkich katalogów w drzewie. W przeciwnym razie zostanie zgłoszony wyjątek i żadne wyniki nie zostaną zwrócone. Korzystając z <xref:System.IO.Directory.EnumerateDirectories%2A> w zapytaniu PLINQ jest problematyczne do obsługi wyjątków we/wy w sposób płynnego, który umożliwia kontynuowanie iteracja. Jeśli Twój kod musi obsługiwać operacje We/Wy lub wyjątki przed nieautoryzowanym dostępem, a następnie należy wziąć pod uwagę podejście opisane w [porady: iterowanie katalogów plików przy użyciu klas równoległych](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).  
  
 Jeśli czas oczekiwania operacji We/Wy jest problemem, na przykład z plikiem operacji We/Wy przez sieć, należy wziąć pod uwagę przy użyciu jednej z asynchronicznych operacji We/Wy metod opisanych w [TPL i tradycyjnym .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) i w tym [wpis w blogu ](https://blogs.msdn.microsoft.com/pfxteam/2009/08/04/parallel-extensions-and-io/).  
  
## <a name="see-also"></a>Zobacz także

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
