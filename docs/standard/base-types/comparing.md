---
title: Porównywanie ciągów w programie .NET
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df526c93c195275751c393299b0e0d80337eee44
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688899"
---
# <a name="comparing-strings-in-net"></a>Porównywanie ciągów w programie .NET
.NET zapewnia kilka metod, aby porównać wartości ciągów. Poniższej tabeli wymieniono i opisano metody porównania wartości.  
  
|Nazwa metody|Zastosowanie|  
|-----------------|---------|  
|<xref:System.String.Compare%2A?displayProperty=nameWithType>|Porównanie wartości dwóch ciągów. Zwraca wartość całkowitą.|  
|<xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>|Porównuje dwa ciągi bez względu na lokalne kultury. Zwraca wartość całkowitą.|  
|<xref:System.String.CompareTo%2A?displayProperty=nameWithType>|Porównuje bieżący obiekt ciągu do innego ciągu. Zwraca wartość całkowitą.|  
|<xref:System.String.StartsWith%2A?displayProperty=nameWithType>|Określa, czy ciąg zaczyna się od ciągu przekazany. Zwraca wartość typu Boolean.|  
|<xref:System.String.EndsWith%2A?displayProperty=nameWithType>|Określa, czy ciąg kończy się ciągiem przekazany. Zwraca wartość typu Boolean.|  
|<xref:System.String.Equals%2A?displayProperty=nameWithType>|Określa, czy dwa ciągi są takie same. Zwraca wartość typu Boolean.|  
|<xref:System.String.IndexOf%2A?displayProperty=nameWithType>|Zwraca indeks znaku lub ciąg, zaczynając od początku ciągu, który sprawdzasz. Zwraca wartość całkowitą.|  
|<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>|Zwraca indeks znaku lub ciąg, zaczynając od końca ciągu, który sprawdzasz. Zwraca wartość całkowitą.|  
  
## <a name="compare"></a>{1&gt;Compare&lt;1}  
 Statyczne <xref:System.String.Compare%2A?displayProperty=nameWithType> metoda zapewnia możliwość dokładnego porównywania dwóch ciągów. Ta metoda jest kulturalnie pamiętać. Ta funkcja służy do porównywania dwóch ciągów lub podciągów dwa ciągi. Ponadto przeciążenia są podane w tym zakresie lub zignorować wielkość liter i Wariancja kultury. W poniższej tabeli przedstawiono wartości całkowitych trzy, że ta metoda może zwrócić.  
  
|Wartość zwracana|Warunek|  
|------------------|---------------|  
|Ujemna liczba całkowita|Pierwszy ciąg poprzedza drugi ciąg w porządku sortowania.<br /><br /> —lub—<br /><br /> Pierwszy ciąg jest `null`.|  
|0|Pierwszy ciąg, a drugi ciąg są równe.<br /><br /> —lub—<br /><br /> Oba ciągi są `null`.|  
|Dodatnia liczba całkowita<br /><br /> —lub—<br /><br /> 1|Pierwszy ciąg jest zgodna drugi ciąg w porządku sortowania.<br /><br /> —lub—<br /><br /> Drugi ciąg jest `null`.|  
  
> [!IMPORTANT]
>  <xref:System.String.Compare%2A?displayProperty=nameWithType> Metoda jest przeznaczona głównie do użytku podczas zamawiania lub sortowanie ciągów. Nie należy używać <xref:System.String.Compare%2A?displayProperty=nameWithType> metody do testowania pod kątem równości (oznacza to, aby jawnie szukać zwracana wartość wynosząca 0 przy użyciu nie ma znaczenia, czy jeden ciąg jest mniejsze lub większe niż ten drugi). Aby ustalić, czy dwa ciągi są równe, użyj <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metody.  
  
 W poniższym przykładzie użyto <xref:System.String.Compare%2A?displayProperty=nameWithType> metodę pozwala ustalić wartości względne dwa ciągi.  
  
 [!code-cpp[Conceptual.String.BasicOps#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#6)]
 [!code-csharp[Conceptual.String.BasicOps#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#6)]
 [!code-vb[Conceptual.String.BasicOps#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#6)]  
  
 Ten przykład wyświetla `-1` do konsoli.  
  
 Powyższy przykład dotyczy wrażliwość na ustawienia kulturowe domyślnie. Aby wykonać porównania ciągów niewrażliwość na ustawienia kulturowe, użyj przeciążenia <xref:System.String.Compare%2A?displayProperty=nameWithType> metodę, która pozwala na określenie kultura używana przez dostarczenie *kultury* parametru. Aby uzyskać przykład, który demonstruje sposób używania <xref:System.String.Compare%2A?displayProperty=nameWithType> metodę w celu porównania niewrażliwość na ustawienia kulturowe, zobacz [wykonywanie niezależnych od kultury porównań ciągów](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="compareordinal"></a>Compareordinal —  
 <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> Metoda porównuje dwa obiekty ciągów bez uwzględniania lokalnego kultury. Wartości zwracane przez tę metodę są identyczne do wartości zwracanych przez **porównania** metoda w poprzedniej tabeli.  
  
> [!IMPORTANT]
>  <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> Metoda jest przeznaczona głównie do użytku podczas zamawiania lub sortowanie ciągów. Nie należy używać <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> metody do testowania pod kątem równości (oznacza to, aby jawnie szukać zwracana wartość wynosząca 0 przy użyciu nie ma znaczenia, czy jeden ciąg jest mniejsze lub większe niż ten drugi). Aby ustalić, czy dwa ciągi są równe, użyj <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metody.  
  
 W poniższym przykładzie użyto **compareordinal —** metodę, aby porównać wartości dwóch ciągów.  
  
 [!code-cpp[Conceptual.String.BasicOps#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#7)]
 [!code-csharp[Conceptual.String.BasicOps#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#7)]
 [!code-vb[Conceptual.String.BasicOps#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#7)]  
  
 Ten przykład wyświetla `-32` do konsoli.  
  
## <a name="compareto"></a>Element compareTo  
 <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Metoda porównuje ciąg, który hermetyzuje bieżący obiekt ciągu, do innego ciągu lub obiektu. Wartości zwracane przez tę metodę są identyczne do wartości zwracanych przez <xref:System.String.Compare%2A?displayProperty=nameWithType> metoda w poprzedniej tabeli.  
  
> [!IMPORTANT]
>  <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Metoda jest przeznaczona głównie do użytku podczas zamawiania lub sortowanie ciągów. Nie należy używać <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody do testowania pod kątem równości (oznacza to, aby jawnie szukać zwracana wartość wynosząca 0 przy użyciu nie ma znaczenia, czy jeden ciąg jest mniejsze lub większe niż ten drugi). Aby ustalić, czy dwa ciągi są równe, użyj <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metody.  
  
 W poniższym przykładzie użyto <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metodę, aby porównać `string1` obiekt `string2` obiektu.  
  
 [!code-cpp[Conceptual.String.BasicOps#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#8)]
 [!code-csharp[Conceptual.String.BasicOps#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#8)]
 [!code-vb[Conceptual.String.BasicOps#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#8)]  
  
 Ten przykład wyświetla `-1` do konsoli.  
  
 Wszystkie przeciążenia <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody wykonywania uwzględniana kultura i wielkość liter, domyślnie. Nie przeciążenia tej metody są dostarczane, umożliwiają wykonywanie niezależnych od kultury porównanie. Czystości kodu zaleca się, że używasz **String.COMPARE —** metody zamiast tego określenia <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> dla operacji wrażliwych na kulturę lub <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> niezależnych od kultury operacji. Przykłady pokazujące, jak używać **String.COMPARE —** metodę w celu porównania wrażliwość na ustawienia kulturowe i niewrażliwość na ustawienia kulturowe, zobacz [wykonywanie niezależnych od kultury porównań ciągów](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="equals"></a>Równa się  
 **String.Equals** metody można łatwo określić, czy dwa ciągi są takie same. Wielkość liter metoda zwraca **true** lub **false** wartość logiczną. Może służyć z istniejącej klasy, jak pokazano w następnym przykładzie. W poniższym przykładzie użyto **jest równa** metodę, aby określić, czy obiekt ciągu zawiera frazę "Hello World".  
  
 [!code-cpp[Conceptual.String.BasicOps#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#9)]
 [!code-csharp[Conceptual.String.BasicOps#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#9)]
 [!code-vb[Conceptual.String.BasicOps#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#9)]  
  
 Ten przykład wyświetla `True` do konsoli.  
  
 Ta metoda również może służyć jako metoda statyczna. Poniższy przykład porównuje dwa obiekty ciągu przy użyciu metody statycznej.  
  
 [!code-cpp[Conceptual.String.BasicOps#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#10)]
 [!code-csharp[Conceptual.String.BasicOps#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#10)]
 [!code-vb[Conceptual.String.BasicOps#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#10)]  
  
 Ten przykład wyświetla `True` do konsoli.  
  
## <a name="startswith-and-endswith"></a>StartsWith i EndsWith  
 Możesz użyć **String.StartsWith** metodę pozwala ustalić, czy obiekt ciągu rozpoczyna się od te same znaki, odnoszący się do innego ciągu. Wielkość liter metoda zwraca **true** Jeżeli bieżący obiekt ciąg rozpoczyna się od przekazany ciąg i **false** Jeśli tak nie jest. W poniższym przykładzie użyto tej metody, aby określić, jeśli obiekt ciągu rozpoczyna się ciągiem "Hello".  
  
 [!code-cpp[Conceptual.String.BasicOps#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#11)]
 [!code-csharp[Conceptual.String.BasicOps#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#11)]
 [!code-vb[Conceptual.String.BasicOps#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#11)]  
  
 Ten przykład wyświetla `True` do konsoli.  
  
 **String.EndsWith** metoda porównuje przekazany ciąg znaków, znajdujące się na końcu bieżącego obiektu ciągu. Zwraca wartość logiczną. Poniższy przykład sprawdza koniec ciągu przy użyciu **EndsWith** metody.  
  
 [!code-cpp[Conceptual.String.BasicOps#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#12)]
 [!code-csharp[Conceptual.String.BasicOps#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#12)]
 [!code-vb[Conceptual.String.BasicOps#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#12)]  
  
 Ten przykład wyświetla `False` do konsoli.  
  
## <a name="indexof-and-lastindexof"></a>IndexOf i LastIndexOf  
 Możesz użyć **String.IndexOf** metodę, aby określały położenie pierwszego wystąpienia określonego znaku w ciągu. Ta metoda jest wielkość liter rozpoczyna zliczanie od początku ciągu i zwraca pozycję znaku przekazany przy użyciu indeksu zaczynającego się od zera. Jeśli znak nie zostanie znaleziony, jest zwracana wartość -1.  
  
 W poniższym przykładzie użyto **IndexOf** metodę wyszukiwania dla pierwszego wystąpienia "`l`" znak w ciągu.  
  
 [!code-cpp[Conceptual.String.BasicOps#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#13)]
 [!code-csharp[Conceptual.String.BasicOps#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#13)]
 [!code-vb[Conceptual.String.BasicOps#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#13)]  
  
 Ten przykład wyświetla `2` do konsoli.  
  
 **String.LastIndexOf** metoda jest podobna do **String.IndexOf** metody, ale zwraca pozycję ostatniego wystąpienia określonego znaku w ciągu. Jest rozróżniana wielkość liter i korzysta z indeksu.  
  
 W poniższym przykładzie użyto **LastIndexOf** metodę wyszukiwania dla ostatniego wystąpienia "`l`" znak w ciągu.  
  
 [!code-cpp[Conceptual.String.BasicOps#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#14)]
 [!code-csharp[Conceptual.String.BasicOps#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#14)]
 [!code-vb[Conceptual.String.BasicOps#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#14)]  
  
 Ten przykład wyświetla `9` do konsoli.  
  
 Obie metody są przydatne, gdy jest używana w połączeniu z **String.Remove** metody. Można użyć dowolnego **IndexOf** lub **LastIndexOf** metody w celu pobrania położenie znaku, a następnie podaj tej pozycji, aby **Usuń** metody, aby usunąć znak lub słowo, które zaczyna się od znaku.  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)
- [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- [Sortowanie wagi tabel (w przypadku platformy .NET, Windows)](https://www.microsoft.com/en-us/download/details.aspx?id=10921)
- [Tabela elementów sortowanie domyślne Unicode (dla platformy .NET Core w systemie Linux i macOS)](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
