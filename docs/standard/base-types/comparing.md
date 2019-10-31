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
ms.openlocfilehash: e63b2a8ac44d6171f9c48990882780ea420f8c76
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101668"
---
# <a name="comparing-strings-in-net"></a>Porównywanie ciągów w programie .NET
Platforma .NET udostępnia kilka metod porównywania wartości ciągów. W poniższej tabeli wymieniono i opisano metody porównywania wartości.  
  
|Nazwa metody|Zastosowanie|  
|-----------------|---------|  
|<xref:System.String.Compare%2A?displayProperty=nameWithType>|Porównuje wartości dwóch ciągów. Zwraca wartość całkowitą.|  
|<xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>|Porównuje dwa ciągi bez względu na lokalną kulturę. Zwraca wartość całkowitą.|  
|<xref:System.String.CompareTo%2A?displayProperty=nameWithType>|Porównuje bieżący obiekt ciągu z innym ciągiem. Zwraca wartość całkowitą.|  
|<xref:System.String.StartsWith%2A?displayProperty=nameWithType>|Określa, czy ciąg rozpoczyna się ciągiem. Zwraca wartość logiczną.|  
|<xref:System.String.EndsWith%2A?displayProperty=nameWithType>|Określa, czy ciąg jest zakończony ciągiem zakończonym ciągiem. Zwraca wartość logiczną.|  
|<xref:System.String.Equals%2A?displayProperty=nameWithType>|Określa, czy dwa ciągi są takie same. Zwraca wartość logiczną.|  
|<xref:System.String.IndexOf%2A?displayProperty=nameWithType>|Zwraca pozycję indeksu znaku lub ciągu, rozpoczynając od początku badanego ciągu. Zwraca wartość całkowitą.|  
|<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>|Zwraca pozycję indeksu znaku lub ciągu, rozpoczynając od końca badanego ciągu. Zwraca wartość całkowitą.|  
  
## <a name="compare"></a>Porównaniu  
 Metoda static <xref:System.String.Compare%2A?displayProperty=nameWithType> zapewnia dokładny sposób porównywania dwóch ciągów. Ta metoda ma świadomość kulturową. Ta funkcja służy do porównywania dwóch ciągów lub podciągów dwóch ciągów. Ponadto przeciążenia są zapewnione w odniesieniu do wielkości liter i wariancji kulturowej. W poniższej tabeli przedstawiono trzy wartości całkowite, które ta metoda może zwrócić.  
  
|Wartość zwracana|Warunek|  
|------------------|---------------|  
|Ujemna liczba całkowita|Pierwszy ciąg poprzedza drugi ciąg w kolejności sortowania.<br /><br /> —lub—<br /><br /> Pierwszy ciąg jest `null`.|  
|0|Pierwszy ciąg i drugi ciąg są równe.<br /><br /> —lub—<br /><br /> Oba ciągi są `null`.|  
|Dodatnia liczba całkowita<br /><br /> —lub—<br /><br /> 1|Pierwszy ciąg jest zgodny z drugim ciągiem w kolejności sortowania.<br /><br /> —lub—<br /><br /> Drugi ciąg jest `null`.|  
  
> [!IMPORTANT]
> Metoda <xref:System.String.Compare%2A?displayProperty=nameWithType> jest przeznaczona głównie do użycia podczas porządkowania i sortowania ciągów. Nie należy używać metody <xref:System.String.Compare%2A?displayProperty=nameWithType> do testowania równości (oznacza to, że aby jawnie wyszukać wartość zwracaną przez 0 bez względu na to, czy jeden ciąg jest mniejszy od drugiego). Zamiast tego, aby określić, czy dwa ciągi są równe, użyj metody <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType>.  
  
 W poniższym przykładzie zastosowano metodę <xref:System.String.Compare%2A?displayProperty=nameWithType>, aby określić względne wartości dwóch ciągów.  
  
 [!code-cpp[Conceptual.String.BasicOps#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#6)]
 [!code-csharp[Conceptual.String.BasicOps#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#6)]
 [!code-vb[Conceptual.String.BasicOps#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#6)]  
  
 Ten przykład wyświetla `-1` konsoli programu.  
  
 Poprzedni przykład jest domyślnie uwzględniany w kulturze. Aby wykonać Porównywanie ciągów niewrażliwych na kulturę, Użyj przeciążenia metody <xref:System.String.Compare%2A?displayProperty=nameWithType>, która pozwala określić kulturę do użycia przez dostarczenie parametru *kultury* . Aby zapoznać się z przykładem, który ilustruje sposób użycia metody <xref:System.String.Compare%2A?displayProperty=nameWithType> do przeprowadzenia porównania niewrażliwego na kulturę, zobacz [wykonywanie porównania ciągów nieuwzględniających kulturowo](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="compareordinal"></a>CompareOrdinal  
 Metoda <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> porównuje dwa obiekty String bez rozważania lokalnej kultury. Wartości zwracane tej metody są identyczne z wartościami zwracanymi przez metodę **Compare** w poprzedniej tabeli.  
  
> [!IMPORTANT]
> Metoda <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> jest przeznaczona głównie do użycia podczas porządkowania i sortowania ciągów. Nie należy używać metody <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> do testowania równości (oznacza to, że aby jawnie wyszukać wartość zwracaną przez 0 bez względu na to, czy jeden ciąg jest mniejszy od drugiego). Zamiast tego, aby określić, czy dwa ciągi są równe, użyj metody <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType>.  
  
 W poniższym przykładzie zastosowano metodę **CompareOrdinal** w celu porównania wartości dwóch ciągów.  
  
 [!code-cpp[Conceptual.String.BasicOps#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#7)]
 [!code-csharp[Conceptual.String.BasicOps#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#7)]
 [!code-vb[Conceptual.String.BasicOps#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#7)]  
  
 Ten przykład wyświetla `-32` konsoli programu.  
  
## <a name="compareto"></a>CompareTo  
 Metoda <xref:System.String.CompareTo%2A?displayProperty=nameWithType> porównuje ciąg, który jest hermetyzowany przez bieżący obiekt ciągu do innego ciągu lub obiektu. Wartości zwracane tej metody są identyczne z wartościami zwracanymi przez metodę <xref:System.String.Compare%2A?displayProperty=nameWithType> w poprzedniej tabeli.  
  
> [!IMPORTANT]
> Metoda <xref:System.String.CompareTo%2A?displayProperty=nameWithType> jest przeznaczona głównie do użycia podczas porządkowania i sortowania ciągów. Nie należy używać metody <xref:System.String.CompareTo%2A?displayProperty=nameWithType> do testowania równości (oznacza to, że aby jawnie wyszukać wartość zwracaną przez 0 bez względu na to, czy jeden ciąg jest mniejszy od drugiego). Zamiast tego, aby określić, czy dwa ciągi są równe, użyj metody <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType>.  
  
 W poniższym przykładzie zastosowano metodę <xref:System.String.CompareTo%2A?displayProperty=nameWithType>, aby porównać obiekt `string1` z obiektem `string2`.  
  
 [!code-cpp[Conceptual.String.BasicOps#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#8)]
 [!code-csharp[Conceptual.String.BasicOps#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#8)]
 [!code-vb[Conceptual.String.BasicOps#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#8)]  
  
 Ten przykład wyświetla `-1` konsoli programu.  
  
 Wszystkie przeciążenia metody <xref:System.String.CompareTo%2A?displayProperty=nameWithType> domyślnie wykonują porównania z uwzględnieniem kultur i uwzględniania wielkości liter. Nie są dostarczane żadne przeciążenia tej metody, które umożliwiają wykonanie porównania niewrażliwego na kulturę. W przypadku przejrzystości kodu zalecamy użycie metody **String. Compare** , określając <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> dla operacji zależnych od kultury lub <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> dla operacji niewrażliwych na kulturę. Przykłady pokazujące, jak używać metody **String. Compare** do wykonywania porównań zarówno z uwzględnieniem kulturowym, jak i niewrażliwym na kulturę, można znaleźć w temacie [wykonywanie porównania ciągów bez uwzględniania kultury](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="equals"></a>Ubiegł  
 Metoda **String. Equals** może łatwo określić, czy dwa ciągi są takie same. Ta metoda uwzględniania wielkości liter zwraca wartość logiczną **true** lub **false** . Można go użyć z istniejącej klasy, jak pokazano w następnym przykładzie. W poniższym przykładzie zastosowano metodę **Equals** , aby określić, czy obiekt String zawiera frazę "Hello World".  
  
 [!code-cpp[Conceptual.String.BasicOps#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#9)]
 [!code-csharp[Conceptual.String.BasicOps#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#9)]
 [!code-vb[Conceptual.String.BasicOps#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#9)]  
  
 Ten przykład wyświetla `True` konsoli programu.  
  
 Tej metody można również użyć jako metody statycznej. Poniższy przykład porównuje dwa obiekty String przy użyciu metody statycznej.  
  
 [!code-cpp[Conceptual.String.BasicOps#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#10)]
 [!code-csharp[Conceptual.String.BasicOps#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#10)]
 [!code-vb[Conceptual.String.BasicOps#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#10)]  
  
 Ten przykład wyświetla `True` konsoli programu.  
  
## <a name="startswith-and-endswith"></a>StartsWith i EndsWith  
 Można użyć metody **String. StartsWith** , aby określić, czy obiekt String zaczyna się od tych samych znaków, które obejmują inny ciąg. Ta metoda uwzględniania wielkości liter zwraca **wartość true** , jeśli bieżący obiekt String zaczyna się od przekazaną ciągiem i **zwraca wartość false** , jeśli nie. Poniższy przykład używa tej metody w celu ustalenia, czy obiekt String zaczyna się od "Hello".  
  
 [!code-cpp[Conceptual.String.BasicOps#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#11)]
 [!code-csharp[Conceptual.String.BasicOps#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#11)]
 [!code-vb[Conceptual.String.BasicOps#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#11)]  
  
 Ten przykład wyświetla `True` konsoli programu.  
  
 Metoda **String. EndsWith** porównuje przekazaną ciąg z znakami, które istnieją na końcu bieżącego obiektu ciągu. Zwraca również wartość logiczną. Poniższy przykład sprawdza koniec ciągu przy użyciu metody **EndsWith** .  
  
 [!code-cpp[Conceptual.String.BasicOps#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#12)]
 [!code-csharp[Conceptual.String.BasicOps#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#12)]
 [!code-vb[Conceptual.String.BasicOps#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#12)]  
  
 Ten przykład wyświetla `False` konsoli programu.  
  
## <a name="indexof-and-lastindexof"></a>IndexOf i LastIndexOf  
 Można użyć metody **String. IndexOf** , aby określić pozycję pierwszego wystąpienia określonego znaku w ciągu. Ta metoda uwzględniająca wielkość liter rozpoczyna zliczanie od początku ciągu i zwraca pozycję podanego znaku przy użyciu indeksu rozpoczynającego się od zera. Jeśli nie można znaleźć znaku, zwracana jest wartość-1.  
  
 Poniższy przykład używa metody **IndexOf** w celu wyszukania pierwszego wystąpienia znaku "`l`" w ciągu.  
  
 [!code-cpp[Conceptual.String.BasicOps#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#13)]
 [!code-csharp[Conceptual.String.BasicOps#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#13)]
 [!code-vb[Conceptual.String.BasicOps#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#13)]  
  
 Ten przykład wyświetla `2` konsoli programu.  
  
 Metoda **String. LastIndexOf** jest podobna do metody **String. IndexOf** , z tą różnicą, że zwraca pozycję ostatniego wystąpienia określonego znaku w ciągu. Jest uwzględniana wielkość liter i używa indeksu od zera.  
  
 Poniższy przykład używa metody **LastIndexOf** w celu wyszukania ostatniego wystąpienia znaku "`l`" w ciągu.  
  
 [!code-cpp[Conceptual.String.BasicOps#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#14)]
 [!code-csharp[Conceptual.String.BasicOps#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#14)]
 [!code-vb[Conceptual.String.BasicOps#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#14)]  
  
 Ten przykład wyświetla `9` konsoli programu.  
  
 Obie metody są przydatne, gdy są używane w połączeniu z metodą **String. Remove** . Można użyć metody **IndexOf** lub **LastIndexOf** , aby pobrać pozycję znaku, a następnie podać tę pozycję do metody **Remove** , aby usunąć znak lub wyraz zaczynający się od tego znaku.  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)
- [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- [Sortowanie tabel wag (dla platformy .NET w systemie Windows)](https://www.microsoft.com/download/details.aspx?id=10921)
- [Domyślna tabela elementów sortowania Unicode (dla platformy .NET Core w systemie Linux i macOS)](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
