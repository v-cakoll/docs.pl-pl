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
ms.openlocfilehash: 1d13d4e115caa636e5d760b65bc98e195490f911
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45508099"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a>Przycinanie i usuwanie znaków z ciągów w programie .NET
Jeśli zdania są analizy do poszczególnych wyrazów, może być na końcu słowa, które mają puste miejsca (nazywane również białych znaków) na jednym z końców słowa. W takiej sytuacji można użyć jednej z metod przycinania w **System.String** klasy, aby usunąć dowolną liczbę spacji lub inne znaki od określonej pozycji w ciągu. W poniższej tabeli opisano dostępne metody przycinania.  
  
|Nazwa metody|Zastosowanie|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|Usuwa spacje lub znaki określone w tablicy znaków od początku i końca ciągu.|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|Usuwa określone w tablicy znaków od końca ciągu znaków.|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|Usuwa określone w tablicy znaków od początku ciągu znaków.|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|Usuwa określoną liczbę znaków od pozycji określonym indeksie w ciągu.|  
  
## <a name="trim"></a>TRIM  
 Można łatwo usunąć spacji z obydwu końców ciąg, przy użyciu <xref:System.String.Trim%2A?displayProperty=nameWithType> metodzie, jak pokazano w poniższym przykładzie.  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 Można również usunąć znaki, które są określone w tablicy znaków od początku i końca ciągu. Poniższy przykład usuwa białe znaki, kropki i gwiazdki.  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a>Metoda TrimEnd  
 **String.TrimEnd** metoda usuwa znaków od końca ciągu, utworzenie nowego obiektu ciągu. Tablica znaków jest przekazywany do tej metody, aby określić znaków, który ma zostać usunięty. Kolejność elementów w tablicy znaków nie ma wpływu na operację przycinania. Trim zatrzymuje, gdy znajduje się znak nie jest określone w tablicy.  
  
 Poniższy przykład umożliwia usunięcie ostatniej litery w ciągu przy użyciu **trimend —** metody. W tym przykładzie położenie `'r'` znak i `'W'` znak zostały cofnięte, aby zilustrować, że kolejność znaków w tablicy nie ma znaczenia. Należy zauważyć, że ten kod usuwa ostatni wyraz z `MyString` plus część pierwsza.  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 Ten kod wyświetla `He` do konsoli.  
  
 Poniższy przykład usuwa ostatni wyraz w ciągu przy użyciu **trimend —** metody. W tym kodzie przecinek następuje wyraz `Hello` i ponieważ przecinek nie została określona w tablicy znaków można przycięcia, trim kończy się przecinkiem.  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 Ten kod wyświetla `Hello,` do konsoli.  
  
## <a name="trimstart"></a>Metoda TrimStart  
 **String.TrimStart** metoda jest podobna do **String.TrimEnd** metody, z wyjątkiem że utworzy nowy ciąg przez usunięcie znaków od początku istniejący obiekt ciągu. Tablica znaków jest przekazywany do **trimstart —** metodę, aby określić znaków, który ma zostać usunięty. Podobnie jak w przypadku **trimend —** metody, kolejność elementów w tablicy znaków nie ma wpływu na operację przycinania. Trim zatrzymuje, gdy znajduje się znak nie jest określone w tablicy.  
  
 Poniższy przykład usuwa pierwszy wyraz w ciągu. W tym przykładzie położenie `'l'` znak i `'H'` znak zostały cofnięte, aby zilustrować, że kolejność znaków w tablicy nie ma znaczenia.  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 Ten kod wyświetla `World!` do konsoli.  
  
## <a name="remove"></a>Usuń  
 <xref:System.String.Remove%2A?displayProperty=nameWithType> Metoda usuwa określoną liczbę znaków, które zaczynają się na określonej pozycji w istniejących parametrów. Ta metoda przyjmuje liczony od zera indeks.  
  
 Poniższy przykład usuwa dziesięć znaków od początku ciągu w położeniu pięciu liczony od zera indeks w ciągu.  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
 Można również usunąć określony znak lub podciągów z ciągu, wywołując <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> metody i określając ciąg pusty (<xref:System.String.Empty?displayProperty=nameWithType>) do zamiany. Poniższy przykład usuwa wszystkie przecinkami z ciągu.  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)
