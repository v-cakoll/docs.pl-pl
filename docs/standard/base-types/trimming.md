---
title: Przycinanie i usuwanie znaków z ciągów w programie .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET Framework], removing characters
- Remove method
- TrimEnd method
- Trim method
- trimming characters
- TrimStart method
- removing characters
ms.assetid: ab248dab-70d4-4413-81c6-542d153fd195
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c694a6792168f37e1f134cf965658e8a058e240a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037870"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a>Przycinanie i usuwanie znaków z ciągów w programie .NET
Jeśli analizujesz zdanie w poszczególnych słowach, możesz kończyć się wyrazami z pustymi spacjami (nazywanymi również białymi spacjami) na dowolnym końcu słowa. W takiej sytuacji można użyć jednej z metod przycinania w klasie **System. String** , aby usunąć dowolną liczbę spacji lub innych znaków z określonej pozycji w ciągu. W poniższej tabeli opisano dostępne metody przycinania.  
  
|Nazwa metody|Zastosowanie|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|Usuwa spacje lub znaki określone w tablicy znaków od początku i końca ciągu.|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|Usuwa znaki określone w tablicy znaków od końca ciągu.|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|Usuwa znaki określone w tablicy znaków od początku ciągu.|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|Usuwa określoną liczbę znaków z podanej pozycji indeksu w ciągu.|  
  
## <a name="trim"></a>Trim

 Można łatwo usunąć białe znaki z obu punktów końcowych ciągu za pomocą metody <xref:System.String.Trim%2A?displayProperty=nameWithType>, jak pokazano w poniższym przykładzie.  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 Można również usunąć znaki określone w tablicy znaków od początku i końca ciągu. Poniższy przykład usuwa znaki odstępu, kropki i gwiazdki.  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a>Metoda TrimEnd

 Metoda **String. TrimEnd** usuwa znaki z końca ciągu, tworząc nowy obiekt ciągu. Tablica znaków jest przenoszona do tej metody w celu określenia znaków do usunięcia. Kolejność elementów w tablicy znaków nie ma wpływu na operację przycinania. Przycinanie zostaje zatrzymane, gdy zostanie znaleziony znak nieokreślony w tablicy.  
  
 Poniższy przykład usuwa ostatnie litery ciągu przy użyciu metody **TrimEnd** . W tym przykładzie pozycja znaku `'r'` i znaku `'W'` są odwracane w celu zilustrowania, że kolejność znaków w tablicy nie ma znaczenia. Zauważ, że ten kod usuwa ostatni wyraz `MyString` i część pierwszej.  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 Ten kod wyświetla `He` konsoli programu.  
  
 Poniższy przykład usuwa ostatni wyraz ciągu przy użyciu metody **TrimEnd** . W tym kodzie przecinek następuje po słowie `Hello` i, ponieważ przecinek nie jest określony w tablicy znaków do przycinania, przycinanie następuje w przecinek.  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 Ten kod wyświetla `Hello,` konsoli programu.  
  
## <a name="trimstart"></a>Metoda TrimStart

 Metoda **String. TrimStart** jest podobna do metody **String. TrimEnd** , z tą różnicą, że tworzy nowy ciąg przez usunięcie znaków z początku istniejącego obiektu ciągu. Tablica znaków jest przenoszona do metody **TrimStart** w celu określenia znaków do usunięcia. Podobnie jak w przypadku metody **TrimEnd** , kolejność elementów w tablicy znaków nie ma wpływu na operację przycinania. Przycinanie zostaje zatrzymane, gdy zostanie znaleziony znak nieokreślony w tablicy.  
  
 Poniższy przykład usuwa pierwsze słowo ciągu. W tym przykładzie pozycja znaku `'l'` i znaku `'H'` są odwracane w celu zilustrowania, że kolejność znaków w tablicy nie ma znaczenia.  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 Ten kod wyświetla `World!` konsoli programu.  
  
## <a name="remove"></a>Usuń 

 Metoda <xref:System.String.Remove%2A?displayProperty=nameWithType> usuwa określoną liczbę znaków, zaczynając od określonej pozycji w istniejącym ciągu. Ta metoda przyjmuje indeks oparty na wartości zero.  
  
 Poniższy przykład usuwa dziesięć znaków z ciągu, zaczynając od pozycji piątej indeksu ciągu od zera.  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
## <a name="replace"></a>stępować

 Można również usunąć określony znak lub podciąg z ciągu, wywołując metodę <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> i określając pusty ciąg (<xref:System.String.Empty?displayProperty=nameWithType>) jako zamiennik. Poniższy przykład usuwa wszystkie przecinki z ciągu.  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)
