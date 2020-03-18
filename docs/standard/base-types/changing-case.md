---
title: Zmiana sprawy w .NET
description: Dowiedz się, jak zmienić w przypadku ciągów w .NET.
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
ms.openlocfilehash: 19795cbed27ca979af813b6060163e76fc5b3780
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187213"
---
# <a name="change-case-in-net"></a>Zmiana przypadku w .NET

Jeśli napiszesz aplikację, która akceptuje dane wejściowe od użytkownika, nigdy nie możesz być pewien, w jakiej sprawie (górnej lub dolnej) będą używać do wprowadzania danych. Często chcesz, aby ciągi były ustalane konsekwentnie, szczególnie jeśli wyświetlasz je w interfejsie użytkownika. W poniższej tabeli opisano trzy metody zmiany wielkości liter. Pierwsze dwie metody zapewniają przeciążenie, które akceptuje kultury.  
  
|Nazwa metody|Użycie|  
|-----------------|---------|  
|<xref:System.String.ToUpper%2A?displayProperty=nameWithType>|Konwertuje wszystkie znaki w ciągu na wielkie litery.|  
|<xref:System.String.ToLower%2A?displayProperty=nameWithType>|Konwertuje wszystkie znaki w ciągu na małe litery.|  
|<xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType>|Konwertuje ciąg na przypadek tytułu.|  
  
> [!WARNING]
> Należy zauważyć, że <xref:System.String.ToUpper%2A?displayProperty=nameWithType> i <xref:System.String.ToLower%2A?displayProperty=nameWithType> metody nie powinny być używane do konwertowania ciągów w celu porównania ich lub przetestować je pod kątem równości. Aby uzyskać więcej informacji, zobacz [porównywanie ciągów mieszanych case](#Comparing) sekcji.  
  
<a name="Comparing"></a>
## <a name="compare-strings-of-mixed-case"></a>Porównanie ciągów mieszanych  

 Aby porównać ciągi mieszanych przypadków w celu określenia ich kolejności, należy `comparisonType` wywołać jeden z <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>przeciążeń <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody `comparisonType` z parametrem i podać wartość jednego , <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>lub dla argumentu. Dla porównania przy użyciu określonej kultury innych niż bieżącej <xref:System.String.CompareTo%2A?displayProperty=nameWithType> kultury, wywołać `options` przeciążenie metody <xref:System.Globalization.CompareOptions.IgnoreCase?displayProperty=nameWithType> z `options` obu `culture` i parametru i podać wartość jako argument.  
  
 Aby porównać ciągi mieszanych przypadków, aby ustalić, czy są równe, <xref:System.String.Equals%2A?displayProperty=nameWithType> ich, `comparisonType` wywołać jeden z <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>przeciążeń metody z parametrem i podać wartość albo , <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>, lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> dla argumentu. `comparisonType`  
  
 Aby uzyskać więcej informacji, zobacz [Najważniejsze wskazówki dotyczące używania ciągów](../../../docs/standard/base-types/best-practices-strings.md).  
  
## <a name="toupper"></a>Toupper  
 Metoda <xref:System.String.ToUpper%2A?displayProperty=nameWithType> zmienia wszystkie znaki w ciągu na wielkie litery. Poniższy przykład konwertuje ciąg "Hello World!" od mieszanych liter do wielkich liter.  
  
 [!code-csharp[Strings.ChangingCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#1)]
 [!code-vb[Strings.ChangingCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#1)]  
  
 W poprzednim przykładzie jest domyślnie zależne od kultury; stosuje konwencje obudowy obecnej kultury. Aby wykonać zmiany wielkości liter bez uwzględniania kultury lub zastosować konwencje <xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> wielkości liter określonej kultury, <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> należy <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> użyć przeciążenia metody i podać wartość lub obiekt, który reprezentuje określoną kulturę do parametru *culture.* Na przykład, który pokazuje, <xref:System.String.ToUpper%2A> jak używać metody do wykonywania zmiany wielkości liter niewrażliwe na kulturę, zobacz [Wykonywanie kultury niewrażliwe zmiany wielkości liter](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="tolower"></a>Tolower  
 Metoda <xref:System.String.ToLower%2A?displayProperty=nameWithType> jest podobna do poprzedniej metody, ale zamiast tego konwertuje wszystkie znaki w ciągu na małe litery. Poniższy przykład konwertuje ciąg "Hello World!" małych liter.  
  
 [!code-csharp[Strings.ChangingCase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#2)]
 [!code-vb[Strings.ChangingCase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#2)]  
  
 W poprzednim przykładzie jest domyślnie zależne od kultury; stosuje konwencje obudowy obecnej kultury. Aby wykonać zmiany wielkości liter bez uwzględniania kultury lub zastosować konwencje <xref:System.String.ToLower%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> wielkości liter określonej kultury, <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> należy <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> użyć przeciążenia metody i podać wartość lub obiekt, który reprezentuje określoną kulturę do parametru *culture.* Na przykład, który pokazuje, <xref:System.String.ToLower%28System.Globalization.CultureInfo%29> jak używać metody do wykonywania zmiany wielkości liter niewrażliwe na kulturę, zobacz [Wykonywanie kultury niewrażliwe zmiany wielkości liter](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="totitlecase"></a>ToTitleCase (ToTitleCase)  
 Pierwszy <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> znak każdego wyrazu jest konwertowany na wielkie litery, a pozostałe na małe. Jednak wyrazy, które są całkowicie wielkie litery są uważane za akronimy i nie są konwertowane.  
  
 Metoda <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> jest kulturowa; oznacza to, że używa konwencji wielkości liter danej kultury. Aby wywołać metodę, należy najpierw <xref:System.Globalization.TextInfo> pobrać obiekt, który reprezentuje konwencje wielkości <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> liter określonej kultury z właściwości określonej kultury.  
  
 Poniższy przykład przekazuje każdy ciąg w <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> tablicy do metody.  Ciągi zawierają odpowiednie ciągi tytułu, a także akronimy. Ciągi są konwertowane na przypadek tytułu przy użyciu konwencji wielkości liter kultury angielskiej (Stany Zjednoczone).  
  
 [!code-csharp[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/cs/totitlecase2.cs#1)]
 [!code-vb[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/vb/totitlecase2.vb#1)]  
  
 Należy zauważyć, że chociaż jest <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> zależne od kultury, metoda nie zapewnia reguły wielkości liter poprawnych językowo. Na przykład w poprzednim przykładzie metoda konwertuje "opowieść o dwóch miastach" na "Opowieść o dwóch miastach". Jednak językowo poprawne obudowy tytuł dla kultury en-USA jest "Opowieść o dwóch miastach."  
  
## <a name="see-also"></a>Zobacz też

- [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)
- [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
