---
title: "Przycinanie i usuwanie znaków z ciągów w .NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: dac047c7efefcacb959401aedcb96080810f2278
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a>Przycinanie i usuwanie znaków z ciągów w .NET
Jeśli analizy zdanie w poszczególnych wyrazów może być na końcu wyrazy, które mają puste miejsca (nazywane również spacji) na dowolnym jej końcu słowo. W takiej sytuacji można użyć jednej z metod przycinania w **System.String** klasę, aby usunąć dowolną liczbę spacji ani innych znaków od określonej pozycji w ciągu. W poniższej tabeli opisano dostępne metody przycinania.  
  
|Nazwa metody|Zastosowanie|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|Usuwa spacji ani znaków określone w tablicy znaków od początku i końca ciągu.|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|Usuwa określone w tablicy znaków od końca ciągu znaków.|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|Usuwa określone w tablicy znaków od początku ciągu znaków.|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|Usuwa określoną liczbę znaków od pozycji określony indeks, w ciągu.|  
  
## <a name="trim"></a>TRIM  
 Można łatwo usunąć spacji z obydwu końców ciąg, przy użyciu <xref:System.String.Trim%2A?displayProperty=nameWithType> metody, jak pokazano w poniższym przykładzie.  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 Można również usunąć znaki określone w tablicy znaków od początku i końca ciągu. Poniższy przykład usuwa białe znaki, kropek i gwiazdki.  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a>Metoda TrimEnd  
 **String.TrimEnd** metoda usuwa znaków od końca ciągu, utworzenie nowego obiektu ciąg. Tablicy znaków jest przekazywany do tej metody, aby określić znaków ma zostać usunięty. Kolejność elementów w tablicy znaków nie ma wpływu na operację przycinania. Przycinanie zatrzymywana, gdy znajduje się znak nie jest określone w tablicy.  
  
 Poniższy przykład umożliwia usunięcie ostatniego litery przy użyciu ciągu **TrimEnd** metody. W tym przykładzie, pozycja `'r'` znaków i `'W'` znak są wycofywane w celu zilustrowania kolejność znaków w tablicy nie ma znaczenia. Zwróć uwagę, że ten kod usuwa wyrazu ostatnich `MyString` plus część pierwszy.  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 Ten kod wyświetla `He` do konsoli.  
  
 Poniższy przykład umożliwia usunięcie ostatniego wyrazu przy użyciu ciągu **TrimEnd** metody. W tym kodzie przecinek następuje wyraz `Hello` i ponieważ przecinek nie jest określone w tablicy znaków, aby przyciąć, przycinanie kończy się po przecinku.  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 Ten kod wyświetla `Hello,` do konsoli.  
  
## <a name="trimstart"></a>Metoda TrimStart  
 **String.TrimStart** metoda jest podobna do **String.TrimEnd** metody, ale tworzy nowy ciąg przez usunięcie znaków od początku z istniejącym obiektem ciągu. Tablicy znaków jest przekazywana do **TrimStart** metodę, aby określić znaków ma zostać usunięty. Jak **TrimEnd** metody, kolejność elementów w tablicy znaków nie ma wpływu na operację przycinania. Przycinanie zatrzymywana, gdy znajduje się znak nie jest określone w tablicy.  
  
 Poniższy przykład umożliwia usunięcie pierwsze słowo ciągu. W tym przykładzie, pozycja `'l'` znaków i `'H'` znak są wycofywane w celu zilustrowania kolejność znaków w tablicy nie ma znaczenia.  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 Ten kod wyświetla `World!` do konsoli.  
  
## <a name="remove"></a>Usuń  
 <xref:System.String.Remove%2A?displayProperty=nameWithType> Metoda usuwa określoną liczbę znaków, zaczynające się od określonej pozycji w ciągu istniejących. Ta metoda przyjmuje liczony od zera indeks.  
  
 Poniższy przykład umożliwia usunięcie 10 znaków od początku ciągu, w pozycji pięciu liczony od zera indeksu ciągu.  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
 Można również usunąć określony znak lub podciąg z ciągu wywołując <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> — metoda i określając pustego ciągu (<xref:System.String.Empty?displayProperty=nameWithType>) do zamiany. Poniższy przykład umożliwia usunięcie wszystkich przecinkami z ciągu.  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)
