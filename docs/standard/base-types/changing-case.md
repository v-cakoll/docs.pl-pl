---
title: Zmienianie wielkości liter w programie .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework], case
- case sensitivity
- ToUpper method
- ToLower method
- uppercase
- lowercase
ms.assetid: 6805f81b-e9ad-4387-9f4c-b9bdb21b87c0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd20db7fcc16f7781e093d59514c4be75705080a
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44076771"
---
# <a name="changing-case-in-net"></a>Zmienianie wielkości liter na platformie .NET
Jeśli piszesz aplikację, która akceptuje dane wejściowe od użytkownika, nigdy nie można się, że przypadek, jakie użytkownik użyje do wprowadzania danych. Często mają ciągi, aby mieć prawidłową wielkość spójne, szczególnie w przypadku, gdy są ich wyświetlania w interfejsie użytkownika. W poniższej tabeli opisano trzy metody zmiany sprawy. Pierwsze dwie metody dostarczać przeciążenia, które akceptuje kultury.  
  
|Nazwa metody|Zastosowanie|  
|-----------------|---------|  
|<xref:System.String.ToUpper%2A?displayProperty=nameWithType>|Konwertuje wszystkie znaki w ciągu na wielkie litery.|  
|<xref:System.String.ToLower%2A?displayProperty=nameWithType>|Konwertuje wszystkie znaki w ciągu na małe litery.|  
|<xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType>|Konwertuje ciąg na wielkimi literami.|  
  
> [!WARNING]
>  Należy pamiętać, że <xref:System.String.ToUpper%2A?displayProperty=nameWithType> i <xref:System.String.ToLower%2A?displayProperty=nameWithType> nie należy używać metod do konwersji ciągów znaków w celu porównania ich lub przetestuj je pod kątem równości. Aby uzyskać więcej informacji, zobacz [porównywanie ciągów wielkich i małych liter](#Comparing) sekcji.  
  
<a name="Comparing"></a>   
## <a name="comparing-strings-of-mixed-case"></a>Porównywanie ciągów wielkich i małych liter  
 Aby porównać ciągi wielkich i małych liter, aby określić ich kolejność, należy wywołać jedną z przeciążeń <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody z `comparisonType` parametru i podaj wartości <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>, <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>, lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> dla `comparisonType` argument. Porównanie przy użyciu określonej kultury innej niż bieżąca kultura wywołania przeciążenia <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metoda zarówno `culture` i `options` parametru i podaj wartość <xref:System.Globalization.CompareOptions.IgnoreCase?displayProperty=nameWithType> jako `options` argumentu.  
  
 Do porównywania ciągów znaków wielkich i małych liter w celu ustalenia, czy są równe, ich, wywoływanie jednego z przeciążeń <xref:System.String.Equals%2A?displayProperty=nameWithType> metody z `comparisonType` parametru i podaj wartości <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>, <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>, lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> dla `comparisonType` argumentu.  
  
 Aby uzyskać więcej informacji, zobacz [najlepsze rozwiązania dotyczące Using Strings](../../../docs/standard/base-types/best-practices-strings.md).  
  
## <a name="toupper"></a>toUpper  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType> Metoda zmienia wszystkie znaki w ciągu na wielkie litery. Poniższy przykład konwertuje ciąg "Hello World!" z wielkich i małych liter na wielkie litery.  
  
 [!code-csharp[Strings.ChangingCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#1)]
 [!code-vb[Strings.ChangingCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#1)]  
  
 Powyższy przykład dotyczy wrażliwość na ustawienia kulturowe domyślnie; ma to zastosowanie Konwencji obudowy bieżącej kultury. Do wykonania niezależnych od kultury zmian wielkości liter lub zastosowania, konwencje obudowy danej kultury, należy użyć <xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> metoda przeciążenia i podaj wartość <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> lub <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> obiektu, który reprezentuje określoną kulturę *kultury* parametru. Aby uzyskać przykład, który demonstruje sposób używania <xref:System.String.ToUpper%2A> metodę w celu niezależnych od kultury zmian wielkości liter, zobacz [wykonywanie niezależnych od kultury zmian przypadek](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="tolower"></a>toLower  
 <xref:System.String.ToLower%2A?displayProperty=nameWithType> Metody jest podobny do poprzedniego metody, ale zamiast tego konwertuje wszystkie znaki w ciągu na małe litery. Poniższy przykład konwertuje ciąg "Hello World!" na małe litery.  
  
 [!code-csharp[Strings.ChangingCase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#2)]
 [!code-vb[Strings.ChangingCase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#2)]  
  
 Powyższy przykład dotyczy wrażliwość na ustawienia kulturowe domyślnie; ma to zastosowanie Konwencji obudowy bieżącej kultury. Do wykonania niezależnych od kultury zmian wielkości liter lub zastosowania, konwencje obudowy danej kultury, należy użyć <xref:System.String.ToLower%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> metoda przeciążenia i podaj wartość <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> lub <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> obiektu, który reprezentuje określoną kulturę *kultury* parametru. Aby uzyskać przykład, który demonstruje sposób używania <xref:System.String.ToLower%28System.Globalization.CultureInfo%29> metodę w celu niezależnych od kultury zmian wielkości liter, zobacz [wykonywanie niezależnych od kultury zmian przypadek](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="totitlecase"></a>ToTitleCase  
 <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> Konwertuje pierwszym znakiem każdego wyrazu na wielką, a pozostałe znaki na małe litery. Jednak słów pisanych w całości wielkimi literami są zakłada się, że akronimów i nie są przekształcane.  
  
 <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> Metodą jest wrażliwe na ustawienia kulturowe; oznacza to, używa konwencji obudowy określonej kultury. Aby można było wywołać metodę, należy najpierw pobrać <xref:System.Globalization.TextInfo> obiekt, który reprezentuje konwencje obudowy określonej kultury z <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> właściwości określonej kultury.  
  
 Poniższy przykład przekazuje każdego ciągu w tablicy <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> metody.  Ciągi obejmują tytuł odpowiednie parametry, a także akronimów. Ciągi są konwertowane na wielkimi literami przy użyciu konwencji wielkości liter kultury angielski (Stany Zjednoczone).  
  
 [!code-csharp[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/cs/totitlecase2.cs#1)]
 [!code-vb[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/vb/totitlecase2.vb#1)]  
  
 Należy pamiętać, że chociaż jest uwzględniana kultura, <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> metoda nie dostarcza reguły językowo odpowiedniej wielkości liter. Na przykład w poprzednim przykładzie, Metoda ta konwertuje "wskaźnik dwóch miast" do "Jak wskaźnik dwóch miast". Jednak językowo odpowiedni tytuł wielkość liter w wyrazie dla kultury en US jest "Wskaźnik dwóch miast."  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)  
- [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
