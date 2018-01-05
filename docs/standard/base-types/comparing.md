---
title: "Porównywanie ciągów w .NET"
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
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a9c2597ed2321c7494eaf44c3c43c2edc4df1952
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="comparing-strings-in-net"></a>Porównywanie ciągów w .NET
.NET zapewnia kilka metod do porównania wartości ciągów. W poniższej tabeli wymieniono i opisano metody porównania wartości.  
  
|Nazwa metody|Zastosowanie|  
|-----------------|---------|  
|<xref:System.String.Compare%2A?displayProperty=nameWithType>|Porównuje dwa ciągi wartości. Zwraca liczbę całkowitą.|  
|<xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>|Porównuje dwa ciągi niezależnie lokalnego kultury. Zwraca liczbę całkowitą.|  
|<xref:System.String.CompareTo%2A?displayProperty=nameWithType>|Porównuje bieżący obiekt ciągu na inny ciąg. Zwraca liczbę całkowitą.|  
|<xref:System.String.StartsWith%2A?displayProperty=nameWithType>|Określa, czy ciąg rozpoczyna się od ciągu przekazany. Zwraca wartość logiczną.|  
|<xref:System.String.EndsWith%2A?displayProperty=nameWithType>|Określa, czy ciąg kończy się na ciąg znaków przekazany. Zwraca wartość logiczną.|  
|<xref:System.String.Equals%2A?displayProperty=nameWithType>|Określa, czy dwa ciągi są takie same. Zwraca wartość logiczną.|  
|<xref:System.String.IndexOf%2A?displayProperty=nameWithType>|Zwraca indeks znaku lub ciąg, od początku ciąg, do którego się. Zwraca liczbę całkowitą.|  
|<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>|Zwraca indeks znaku lub ciąg, począwszy od końca ciągu, który się. Zwraca liczbę całkowitą.|  
  
## <a name="compare"></a>Porównaj  
 Statycznych <xref:System.String.Compare%2A?displayProperty=nameWithType> metoda zapewnia możliwość dokładnego porównywania dwóch ciągów. Ta metoda jest kulturalnie uwagę. Ta funkcja służy do porównywania dwóch ciągów lub podciągów dwóch ciągów. Ponadto przeciążenia są podane w tym zakresie lub pominąć wielkość liter i odchylenie kultury. W poniższej tabeli przedstawiono trzy całkowitych wartości, że ta metoda może zwracać.  
  
|Wartość zwracana|Warunek|  
|------------------|---------------|  
|Ujemna liczba całkowita|Pierwszy ciąg poprzedza drugi ciąg w kolejności sortowania.<br /><br /> —lub—<br /><br /> Pierwszy ciąg jest `null`.|  
|0|Pierwszy ciąg, a drugi ciąg są takie same.<br /><br /> —lub—<br /><br /> Oba parametry są `null`.|  
|Dodatnia liczba całkowita<br /><br /> —lub—<br /><br /> 1|Pierwszy ciąg zgodny drugi ciąg w kolejności sortowania.<br /><br /> —lub—<br /><br /> Drugi ciąg jest `null`.|  
  
> [!IMPORTANT]
>  <xref:System.String.Compare%2A?displayProperty=nameWithType> Metody jest przeznaczony głównie do użytku podczas zamawiania lub sortowanie ciągów. Nie należy używać <xref:System.String.Compare%2A?displayProperty=nameWithType> metody do testowania pod kątem równości (szukać jawnie zwracana wartość 0, z uwzględnieniem nie czy jednego ciągu jest mniejszy lub większy niż drugi). Aby ustalić, czy dwa ciągi są takie same, użyj <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metody.  
  
 W poniższym przykładzie użyto <xref:System.String.Compare%2A?displayProperty=nameWithType> metodę, aby określić wartości dwa ciągi.  
  
 [!code-cpp[Conceptual.String.BasicOps#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#6)]
 [!code-csharp[Conceptual.String.BasicOps#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#6)]
 [!code-vb[Conceptual.String.BasicOps#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#6)]  
  
 W tym przykładzie wyświetlono `-1` do konsoli.  
  
 Powyższy przykład jest zależne od kultury domyślnie. Aby przeprowadzić porównania ciągów niezależnych od kultury, należy użyć przeciążenia <xref:System.String.Compare%2A?displayProperty=nameWithType> metodę, która umożliwia określenie kultury do użycia, podając *kultury* parametru. Na przykład, który demonstruje sposób użycia <xref:System.String.Compare%2A?displayProperty=nameWithType> metodę w celu porównania niezależnych od kultury, zobacz [wykonywanie niezależnych od kultury porównań ciągów](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="compareordinal"></a>CompareOrdinal  
 <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> Metoda porównuje dwa obiekty ciąg bez uwzględniania lokalnego kultury. Zwracane wartości tej metody są takie same jak wartości zwracanych przez **porównania** metody w poprzedniej tabeli.  
  
> [!IMPORTANT]
>  <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> Metody jest przeznaczony głównie do użytku podczas zamawiania lub sortowanie ciągów. Nie należy używać <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> metody do testowania pod kątem równości (szukać jawnie zwracana wartość 0, z uwzględnieniem nie czy jednego ciągu jest mniejszy lub większy niż drugi). Aby ustalić, czy dwa ciągi są takie same, użyj <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metody.  
  
 W poniższym przykładzie użyto **CompareOrdinal** metoda porównuje wartości z dwóch ciągów.  
  
 [!code-cpp[Conceptual.String.BasicOps#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#7)]
 [!code-csharp[Conceptual.String.BasicOps#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#7)]
 [!code-vb[Conceptual.String.BasicOps#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#7)]  
  
 W tym przykładzie wyświetlono `-32` do konsoli.  
  
## <a name="compareto"></a>Wykonanie funkcji CompareTo  
 <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Metoda porównuje ciąg, który hermetyzuje bieżący obiekt ciągu na inny ciąg lub obiekt. Zwracane wartości tej metody są takie same jak wartości zwracanych przez <xref:System.String.Compare%2A?displayProperty=nameWithType> metody w poprzedniej tabeli.  
  
> [!IMPORTANT]
>  <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Metody jest przeznaczony głównie do użytku podczas zamawiania lub sortowanie ciągów. Nie należy używać <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody do testowania pod kątem równości (szukać jawnie zwracana wartość 0, z uwzględnieniem nie czy jednego ciągu jest mniejszy lub większy niż drugi). Aby ustalić, czy dwa ciągi są takie same, użyj <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metody.  
  
 W poniższym przykładzie użyto <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody do porównania `string1` do obiektu `string2` obiektu.  
  
 [!code-cpp[Conceptual.String.BasicOps#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#8)]
 [!code-csharp[Conceptual.String.BasicOps#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#8)]
 [!code-vb[Conceptual.String.BasicOps#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#8)]  
  
 W tym przykładzie wyświetlono `-1` do konsoli.  
  
 Skompilowanie wszystkich przeciążeń <xref:System.String.CompareTo%2A?displayProperty=nameWithType> — metoda wykonywać porównania z uwzględnieniem kultury i z uwzględnieniem wielkości liter domyślnie. Nie przeciążenie tej metody są dostarczane umożliwiające przeprowadzenia porównania niezależnych od kultury. Dla jasności kodu, firma Microsoft zaleca się używanie **String.Compare** — metoda, określając <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> zależne od kultury operacji lub <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> niezależnych od kultury operacji. Aby uzyskać przykłady pokazujące, które prezentują sposób użycia **String.Compare** metodę w celu zarówno zależne od kultury i niezależnych od kultury porównań, zobacz [wykonywanie niezależnych od kultury porównywania ciągów](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="equals"></a>równa się  
 **String.Equals** metody może łatwo ustalić, czy dwa ciągi są takie same. Zwraca tę metodę z uwzględnieniem wielkości liter **true** lub **false** wartość logiczna. Może służyć z istniejącej klasy, jak pokazano w następnym przykładzie. W poniższym przykładzie użyto **jest równe** metodę, aby określić, czy obiekt ciągu zawiera wyrazy "Hello World".  
  
 [!code-cpp[Conceptual.String.BasicOps#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#9)]
 [!code-csharp[Conceptual.String.BasicOps#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#9)]
 [!code-vb[Conceptual.String.BasicOps#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#9)]  
  
 W tym przykładzie wyświetlono `True` do konsoli.  
  
 Ta metoda mogą służyć jako metoda statyczna. Poniższy przykład porównuje dwa obiekty ciągu przy użyciu metody statycznej.  
  
 [!code-cpp[Conceptual.String.BasicOps#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#10)]
 [!code-csharp[Conceptual.String.BasicOps#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#10)]
 [!code-vb[Conceptual.String.BasicOps#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#10)]  
  
 W tym przykładzie wyświetlono `True` do konsoli.  
  
## <a name="startswith-and-endswith"></a>StartsWith i EndsWith  
 Można użyć **String.StartsWith** metodę, aby określić, czy obiekt ciągu rozpoczyna się od znaków odnoszący się do innego ciągu. Zwraca tę metodę z uwzględnieniem wielkości liter **true** Jeśli bieżący obiekt ciąg rozpoczyna się od ciągu przekazany i **false** jeśli jej nie ma. W poniższym przykładzie użyto tej metody, aby określić, czy obiekt ciągu rozpoczyna się od "Hello".  
  
 [!code-cpp[Conceptual.String.BasicOps#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#11)]
 [!code-csharp[Conceptual.String.BasicOps#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#11)]
 [!code-vb[Conceptual.String.BasicOps#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#11)]  
  
 W tym przykładzie wyświetlono `True` do konsoli.  
  
 **String.EndsWith** metoda porównuje przekazany ciąg znaków, które istnieją na końcu ciągu bieżącego obiektu. Zwraca wartość logiczną. Poniższy przykład sprawdza końca ciągu przy użyciu **EndsWith** metody.  
  
 [!code-cpp[Conceptual.String.BasicOps#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#12)]
 [!code-csharp[Conceptual.String.BasicOps#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#12)]
 [!code-vb[Conceptual.String.BasicOps#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#12)]  
  
 W tym przykładzie wyświetlono `False` do konsoli.  
  
## <a name="indexof-and-lastindexof"></a>IndexOf i LastIndexOf  
 Można użyć **String.IndexOf** metodę, aby określić położenie pierwszego wystąpienia danego znaku w ciągu. Ta metoda z uwzględnieniem wielkości liter rozpoczyna zliczanie od początku ciągu i zwraca położenie znaku przekazany za pomocą liczony od zera indeks. Jeśli nie można odnaleźć znaku, jest zwracana wartość -1.  
  
 W poniższym przykładzie użyto **IndexOf** metodę wyszukiwania dla pierwszego wystąpienia "`l`" znak w ciągu.  
  
 [!code-cpp[Conceptual.String.BasicOps#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#13)]
 [!code-csharp[Conceptual.String.BasicOps#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#13)]
 [!code-vb[Conceptual.String.BasicOps#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#13)]  
  
 W tym przykładzie wyświetlono `2` do konsoli.  
  
 **String.LastIndexOf** metoda jest podobna do **String.IndexOf** metody, ale zwraca pozycję ostatniego wystąpienia danego znaku w ciągu. Jest rozróżniana wielkość liter i korzysta z indeksu.  
  
 W poniższym przykładzie użyto **LastIndexOf** metodę wyszukiwania ostatniego wystąpienia "`l`" znak w ciągu.  
  
 [!code-cpp[Conceptual.String.BasicOps#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#14)]
 [!code-csharp[Conceptual.String.BasicOps#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#14)]
 [!code-vb[Conceptual.String.BasicOps#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#14)]  
  
 W tym przykładzie wyświetlono `9` do konsoli.  
  
 Obie metody są przydatne, gdy jest używany w połączeniu z **String.Remove** metody. Możesz użyć dowolnej **IndexOf** lub **LastIndexOf** metod do pobrania położenie znaku, a następnie podaj tej pozycji do **Usuń** metody, aby można było usunąć znak lub słowo, który zaczyna się od znaku.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)  
 [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
