---
title: Porównywanie ciągów w .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- value comparisons of strings
- LastIndexOf method
- CompareTo method
- IndexOf method
- Compare method
- strings [.NET Framework], comparing
- CompareOrdinal method
- EndsWith method
- Equals method
- StartsWith method
ms.assetid: 977dc094-fe19-4955-98ec-d2294d04a4ba
ms.openlocfilehash: e63b2a8ac44d6171f9c48990882780ea420f8c76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73101668"
---
# <a name="comparing-strings-in-net"></a>Porównywanie ciągów w .NET
.NET udostępnia kilka metod porównywania wartości ciągów. W poniższej tabeli wymieniono i opisano metody porównywania wartości.  
  
|Nazwa metody|Użycie|  
|-----------------|---------|  
|<xref:System.String.Compare%2A?displayProperty=nameWithType>|Porównuje wartości dwóch ciągów. Zwraca wartość całkowitą.|  
|<xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>|Porównuje dwa ciągi bez względu na kulturę lokalną. Zwraca wartość całkowitą.|  
|<xref:System.String.CompareTo%2A?displayProperty=nameWithType>|Porównuje bieżący ciąg obiektu do innego ciągu. Zwraca wartość całkowitą.|  
|<xref:System.String.StartsWith%2A?displayProperty=nameWithType>|Określa, czy ciąg zaczyna się od przekazanego ciągu. Zwraca wartość logiczną.|  
|<xref:System.String.EndsWith%2A?displayProperty=nameWithType>|Określa, czy ciąg kończy się przekazanym ciągiem. Zwraca wartość logiczną.|  
|<xref:System.String.Equals%2A?displayProperty=nameWithType>|Określa, czy dwa ciągi są takie same. Zwraca wartość logiczną.|  
|<xref:System.String.IndexOf%2A?displayProperty=nameWithType>|Zwraca pozycję indeksu znaku lub ciągu, począwszy od początku ciągu, który badasz. Zwraca wartość całkowitą.|  
|<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>|Zwraca pozycję indeksu znaku lub ciągu, począwszy od końca ciągu, który badasz. Zwraca wartość całkowitą.|  
  
## <a name="compare"></a>Porównanie  
 Metoda <xref:System.String.Compare%2A?displayProperty=nameWithType> statyczna zapewnia dokładny sposób porównywania dwóch ciągów. Ta metoda jest kulturowo świadoma. Ta funkcja służy do porównywania dwóch ciągów lub podciągów dwóch ciągów. Ponadto przeciążenia są pod warunkiem, że w odniesieniu lub pomijanie przypadku i wariancji kulturowej. W poniższej tabeli przedstawiono trzy wartości całkowite, które ta metoda może zwrócić.  
  
|Wartość zwracana|Warunek|  
|------------------|---------------|  
|Ujemna liczba całkowita|Pierwszy ciąg poprzedza drugi ciąg w kolejności sortowania.<br /><br /> — lub —<br /><br /> Pierwszym ciągiem `null`jest .|  
|0|Pierwszy ciąg i drugi ciąg są równe.<br /><br /> — lub —<br /><br /> Oba ciągi `null`są .|  
|Dodatnia liczba całkowita<br /><br /> — lub —<br /><br /> 1|Pierwszy ciąg następuje drugi ciąg w kolejności sortowania.<br /><br /> — lub —<br /><br /> Drugi ciąg `null`jest .|  
  
> [!IMPORTANT]
> Metoda <xref:System.String.Compare%2A?displayProperty=nameWithType> jest przeznaczona głównie do użycia podczas zamawiania lub sortowania ciągów. Nie należy używać <xref:System.String.Compare%2A?displayProperty=nameWithType> metody do testowania równości (oznacza to jawnie szukać wartości zwracanej 0 bez względu na to, czy jeden ciąg jest mniejsza lub większa niż inny). Zamiast tego, aby ustalić, czy dwa <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> ciągi są równe, należy użyć metody.  
  
 W poniższym <xref:System.String.Compare%2A?displayProperty=nameWithType> przykładzie użyto metody do określenia względnych wartości dwóch ciągów.  
  
 [!code-cpp[Conceptual.String.BasicOps#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#6)]
 [!code-csharp[Conceptual.String.BasicOps#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#6)]
 [!code-vb[Conceptual.String.BasicOps#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#6)]  
  
 W tym `-1` przykładzie jest wyświetlany na konsoli.  
  
 W poprzednim przykładzie jest domyślnie zależne od kultury. Aby wykonać porównanie ciągów nieczułych na kulturę, należy użyć przeciążenia <xref:System.String.Compare%2A?displayProperty=nameWithType> metody, która umożliwia określenie kultury do użycia przez podanie parametru *kultury.* Na przykład, który pokazuje, <xref:System.String.Compare%2A?displayProperty=nameWithType> jak używać metody do wykonywania porównania niewrażliwe kultury, zobacz [Wykonywanie kultury niewrażliwe porównania ciągów](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="compareordinal"></a>CompareOrdinal (CompareOrdinal)  
 Metoda <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> porównuje dwa obiekty ciąg bez uwzględnienia kultury lokalnej. Wartości zwracane tej metody są identyczne z wartościami zwracanymi przez **Compare** metody w poprzedniej tabeli.  
  
> [!IMPORTANT]
> Metoda <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> jest przeznaczona głównie do użycia podczas zamawiania lub sortowania ciągów. Nie należy używać <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> metody do testowania równości (oznacza to jawnie szukać wartości zwracanej 0 bez względu na to, czy jeden ciąg jest mniejsza lub większa niż inny). Zamiast tego, aby ustalić, czy dwa <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> ciągi są równe, należy użyć metody.  
  
 W poniższym przykładzie **użyto CompareOrdinal** metody do porównywania wartości dwóch ciągów.  
  
 [!code-cpp[Conceptual.String.BasicOps#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#7)]
 [!code-csharp[Conceptual.String.BasicOps#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#7)]
 [!code-vb[Conceptual.String.BasicOps#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#7)]  
  
 W tym `-32` przykładzie jest wyświetlany na konsoli.  
  
## <a name="compareto"></a>Compareto  
 Metoda <xref:System.String.CompareTo%2A?displayProperty=nameWithType> porównuje ciąg, który bieżący obiekt ciągu hermetyzuje do innego ciągu lub obiektu. Wartości zwracane tej metody są identyczne z <xref:System.String.Compare%2A?displayProperty=nameWithType> wartościami zwracanymi przez metodę w poprzedniej tabeli.  
  
> [!IMPORTANT]
> Metoda <xref:System.String.CompareTo%2A?displayProperty=nameWithType> jest przeznaczona głównie do użycia podczas zamawiania lub sortowania ciągów. Nie należy używać <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody do testowania równości (oznacza to jawnie szukać wartości zwracanej 0 bez względu na to, czy jeden ciąg jest mniejsza lub większa niż inny). Zamiast tego, aby ustalić, czy dwa <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> ciągi są równe, należy użyć metody.  
  
 W poniższym <xref:System.String.CompareTo%2A?displayProperty=nameWithType> przykładzie użyto `string1` metody `string2` do porównania obiektu z obiektem.  
  
 [!code-cpp[Conceptual.String.BasicOps#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#8)]
 [!code-csharp[Conceptual.String.BasicOps#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#8)]
 [!code-vb[Conceptual.String.BasicOps#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#8)]  
  
 W tym `-1` przykładzie jest wyświetlany na konsoli.  
  
 Wszystkie przeciążenia <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody domyślnie wykonują porównania uwzględniające kulturę i wielkość liter. Nie przeciążenia tej metody są dostarczane, które umożliwiają wykonywanie porównania niewrażliwe kultury. Dla jasności kodu zaleca się użycie **String.Compare** metody <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> zamiast, określając dla <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> operacji zależnych od kultury lub dla operacji niewrażliwych na kulturę. Przykłady, które pokazują, jak używać **String.Compare** metody do wykonywania porównań zarówno zależne od kultury i kultury niewrażliwe, zobacz [Wykonywanie kultury niewrażliwe porównania ciągów](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="equals"></a>Równa się  
 **String.Equals** Metoda można łatwo określić, czy dwa ciągi są takie same. Ta metoda z uwzględnieniem wielkości liter zwraca wartość logiczną **true** lub **false.** Może być używany z istniejącej klasy, jak pokazano w następnym przykładzie. W poniższym przykładzie użyto **Equals** metody, aby ustalić, czy obiekt ciąg zawiera frazę "Hello World".  
  
 [!code-cpp[Conceptual.String.BasicOps#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#9)]
 [!code-csharp[Conceptual.String.BasicOps#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#9)]
 [!code-vb[Conceptual.String.BasicOps#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#9)]  
  
 W tym `True` przykładzie jest wyświetlany na konsoli.  
  
 Ta metoda może być również używana jako metoda statyczna. W poniższym przykładzie porównano dwa obiekty ciągów przy użyciu metody statycznej.  
  
 [!code-cpp[Conceptual.String.BasicOps#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#10)]
 [!code-csharp[Conceptual.String.BasicOps#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#10)]
 [!code-vb[Conceptual.String.BasicOps#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#10)]  
  
 W tym `True` przykładzie jest wyświetlany na konsoli.  
  
## <a name="startswith-and-endswith"></a>StartsWith i endswith  
 Można użyć **String.StartsWith** metody, aby ustalić, czy obiekt ciągu zaczyna się od tych samych znaków, które obejmują inny ciąg. Ta metoda z uwzględnieniem wielkości liter zwraca **wartość true,** jeśli bieżący obiekt ciągu rozpoczyna się od przekazanego ciągu i **false,** jeśli nie. W poniższym przykładzie użyto tej metody, aby ustalić, czy obiekt ciągu zaczyna się od "Hello".  
  
 [!code-cpp[Conceptual.String.BasicOps#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#11)]
 [!code-csharp[Conceptual.String.BasicOps#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#11)]
 [!code-vb[Conceptual.String.BasicOps#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#11)]  
  
 W tym `True` przykładzie jest wyświetlany na konsoli.  
  
 **String.EndsWith** Metoda porównuje przekazany ciąg do znaków, które istnieją na końcu bieżącego obiektu ciągu. Zwraca również wartość logiczną. Poniższy przykład sprawdza koniec ciągu przy użyciu **EndsWith** metody.  
  
 [!code-cpp[Conceptual.String.BasicOps#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#12)]
 [!code-csharp[Conceptual.String.BasicOps#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#12)]
 [!code-vb[Conceptual.String.BasicOps#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#12)]  
  
 W tym `False` przykładzie jest wyświetlany na konsoli.  
  
## <a name="indexof-and-lastindexof"></a>IndexOf i LastIndexOf  
 Za pomocą **String.IndexOf** metody, aby określić położenie pierwszego wystąpienia określonego znaku w ciągu. Ta metoda z uwzględnieniem wielkości liter rozpoczyna liczenie od początku ciągu i zwraca pozycję przekazanego znaku przy użyciu indeksu od zera. Jeśli nie można odnaleźć znaku, zwracana jest wartość –1.  
  
 W poniższym przykładzie użyto **IndexOf** metody do`l`wyszukiwania pierwszego wystąpienia ' znak w ciągu.  
  
 [!code-cpp[Conceptual.String.BasicOps#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#13)]
 [!code-csharp[Conceptual.String.BasicOps#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#13)]
 [!code-vb[Conceptual.String.BasicOps#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#13)]  
  
 W tym `2` przykładzie jest wyświetlany na konsoli.  
  
 **String.LastIndexOf** Metoda jest podobna do **String.IndexOf** metody z tą różnicą, że zwraca pozycję ostatniego wystąpienia określonego znaku w ciągu. Jest rozróżniana wielkość liter i używa indeksu od zera.  
  
 W poniższym przykładzie użyto **LastIndexOf** metody do`l`wyszukiwania ostatniego wystąpienia ' znak w ciągu.  
  
 [!code-cpp[Conceptual.String.BasicOps#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#14)]
 [!code-csharp[Conceptual.String.BasicOps#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#14)]
 [!code-vb[Conceptual.String.BasicOps#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#14)]  
  
 W tym `9` przykładzie jest wyświetlany na konsoli.  
  
 Obie metody są przydatne w połączeniu z **String.Remove** metody. Można użyć **Metody IndexOf** lub **LastIndexOf,** aby pobrać pozycję znaku, a następnie podać tę pozycję do **Remove** metody w celu usunięcia znaku lub wyrazu, który zaczyna się od tego znaku.  
  
## <a name="see-also"></a>Zobacz też

- [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)
- [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- [Sortowanie tabel wagowych (dla .NET w systemie Windows)](https://www.microsoft.com/download/details.aspx?id=10921)
- [Domyślna tabela elementów sortowania Unicode (dla .NET Core w systemach Linux i macOS)](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
