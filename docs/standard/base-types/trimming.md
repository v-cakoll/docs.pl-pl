---
title: Przycinanie i usuwanie znaków z ciągów w .NET
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
ms.openlocfilehash: bdbe267bb178e90c0008422e6543a23178c2c4d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159991"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a>Przycinanie i usuwanie znaków z ciągów w .NET
W przypadku analizowania zdania na poszczególne wyrazy może skończyć się słowami, które mają puste spacje (nazywane również białymi spacjami) na obu końcach wyrazu. W tej sytuacji można użyć jednej z metod przycinania w **System.String** klasy, aby usunąć dowolną liczbę spacji lub innych znaków z określonej pozycji w ciągu. W poniższej tabeli opisano dostępne metody przycinania.  
  
|Nazwa metody|Użycie|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|Usuwa białe spacje lub znaki określone w tablicy znaków od początku i końca ciągu.|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|Usuwa znaki określone w tablicy znaków z końca ciągu.|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|Usuwa znaki określone w tablicy znaków od początku ciągu.|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|Usuwa określoną liczbę znaków z określonej pozycji indeksu w ciągu.|  
  
## <a name="trim"></a>Trim

 Za pomocą <xref:System.String.Trim%2A?displayProperty=nameWithType> metody można łatwo usunąć białe spacje z obu końców ciągu, jak pokazano w poniższym przykładzie.  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 Można również usunąć znaki określone w tablicy znaków od początku i końca ciągu. Poniższy przykład usuwa znaki odstępu, kropki i gwiazdki.  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a>Metoda TrimEnd

 **Metoda String.TrimEnd** usuwa znaki z końca ciągu, tworząc nowy obiekt ciągu. Tablica znaków jest przekazywana do tej metody, aby określić znaki, które mają zostać usunięte. Kolejność elementów w tablicy znaków nie ma wpływu na operację przycinania. Przycięcie zatrzymuje się po znalezieniu znaku nieokreślonego w tablicy.  
  
 Poniższy przykład usuwa ostatnie litery ciągu przy użyciu **TrimEnd** metody. W tym przykładzie położenie `'r'` znaku i `'W'` znak są odwrócone, aby zilustrować, że kolejność znaków w tablicy nie ma znaczenia. Należy zauważyć, że ten kod `MyString` usuwa ostatnie słowo plus część pierwszego.  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 Ten kod `He` jest wyświetlany na konsoli.  
  
 Poniższy przykład usuwa ostatnie słowo ciągu przy użyciu **TrimEnd** metody. W tym kodzie przecinek `Hello` następuje po słowie, a ponieważ przecinek nie jest określony w tablicy znaków do przycięcia, przycięcie kończy się przecinkiem.  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 Ten kod `Hello,` jest wyświetlany na konsoli.  
  
## <a name="trimstart"></a>Metoda TrimStart

 **String.TrimStart** Metoda jest podobna do **String.TrimEnd** metody, z tą różnicą, że tworzy nowy ciąg przez usunięcie znaków od początku istniejącego obiektu ciągu. Tablica znaków jest przekazywana do **TrimStart** metody, aby określić znaki, które mają zostać usunięte. Podobnie jak w przypadku **TrimEnd** metody kolejność elementów w tablicy znaków nie ma wpływu na operację przycinania. Przycięcie zatrzymuje się po znalezieniu znaku nieokreślonego w tablicy.  
  
 Poniższy przykład usuwa pierwsze słowo ciągu. W tym przykładzie położenie `'l'` znaku i `'H'` znak są odwrócone, aby zilustrować, że kolejność znaków w tablicy nie ma znaczenia.  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 Ten kod `World!` jest wyświetlany na konsoli.  
  
## <a name="remove"></a>Remove

 Metoda <xref:System.String.Remove%2A?displayProperty=nameWithType> usuwa określoną liczbę znaków, które rozpoczynają się w określonej pozycji w istniejącym ciągu. Ta metoda zakłada indeks od zera.  
  
 Poniższy przykład usuwa dziesięć znaków z ciągu rozpoczynającego się w pozycji piątej indeksu od zera ciągu.  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
## <a name="replace"></a>Replace

 Można również usunąć określony znak lub podciąg z <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> ciągu, wywołując metodę i<xref:System.String.Empty?displayProperty=nameWithType>określając pusty ciąg ( ) jako zamiennik. Poniższy przykład usuwa wszystkie przecinki z ciągu.  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a>Zobacz też

- [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)
