---
title: Zmiana wielkości liter w programie .NET
description: Dowiedz się, jak zmienić w przypadku ciągów w programie .NET.
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
ms.openlocfilehash: 91fc0022eae3f036e0ec046ea12446871926ab27
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711470"
---
# <a name="changing-case-in-net"></a>Zmiana wielkości liter w programie .NET
Jeśli napiszesz aplikację, która akceptuje dane wejściowe od użytkownika, możesz nigdy nie mieć pewności, co ma być używane do wprowadzania danych. Często w przypadku ciągów ma być uwzględniana wielkość liter, szczególnie jeśli są one wyświetlane w interfejsie użytkownika. W poniższej tabeli opisano trzy metody zmiany wielkości liter. Dwie pierwsze metody zapewniają Przeciążenie, które akceptuje kulturę.  
  
|Nazwa metody|Zastosowanie|  
|-----------------|---------|  
|<xref:System.String.ToUpper%2A?displayProperty=nameWithType>|Konwertuje wszystkie znaki w ciągu na wielkie litery.|  
|<xref:System.String.ToLower%2A?displayProperty=nameWithType>|Konwertuje wszystkie znaki w ciągu na małe litery.|  
|<xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType>|Konwertuje ciąg na wielkość liter.|  
  
> [!WARNING]
> Należy zauważyć, że metody <xref:System.String.ToUpper%2A?displayProperty=nameWithType> i <xref:System.String.ToLower%2A?displayProperty=nameWithType> nie powinny być używane do konwertowania ciągów w celu ich porównania lub testowania pod kątem równości. Aby uzyskać więcej informacji, zobacz [Porównywanie ciągów w przypadku mieszanego przypadku](#Comparing) .  
  
<a name="Comparing"></a>   
## <a name="comparing-strings-of-mixed-case"></a>Porównywanie ciągów z przypadku mieszanego  
 Aby porównać ciągi o mieszanym przypadku w celu określenia ich kolejności, wywołaj jedno z przeciążeń metody <xref:System.String.CompareTo%2A?displayProperty=nameWithType> z parametrem `comparisonType` i podaj wartość <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>, <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> dla argumentu `comparisonType`. W celu porównania przy użyciu określonej kultury innej niż bieżąca kultura Wywołaj Przeciążenie metody <xref:System.String.CompareTo%2A?displayProperty=nameWithType> z parametrami `culture` i `options` i podaj wartość <xref:System.Globalization.CompareOptions.IgnoreCase?displayProperty=nameWithType> jako argument `options`.  
  
 Aby porównać ciągi o mieszanym przypadku, aby określić, czy są równe, wywołaj jedno z przeciążeń metody <xref:System.String.Equals%2A?displayProperty=nameWithType> z parametrem `comparisonType` i podaj wartość <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>, <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> dla argumentu `comparisonType`.  
  
 Aby uzyskać więcej informacji, zobacz [najlepsze rozwiązania dotyczące używania ciągów](../../../docs/standard/base-types/best-practices-strings.md).  
  
## <a name="toupper"></a>ToUpper  
 Metoda <xref:System.String.ToUpper%2A?displayProperty=nameWithType> zmienia wszystkie znaki w ciągu na wielkie litery. Poniższy przykład konwertuje ciąg "Hello world!" od mieszanego przypadku na wielkie litery.  
  
 [!code-csharp[Strings.ChangingCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#1)]
 [!code-vb[Strings.ChangingCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#1)]  
  
 Poprzedni przykład jest domyślnie uwzględniany w kulturze; stosuje konwencje wielkości liter bieżącej kultury. Aby wykonać niezależną od kultury zmianę wielkości liter lub zastosować konwencje wielkości liter w danej kulturze, Użyj przeciążenia metody <xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> i podaj wartość <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> lub <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> obiektu, który reprezentuje określoną kulturę do parametru *kultury* . Aby zapoznać się z przykładem, w którym pokazano, jak użyć metody <xref:System.String.ToUpper%2A>, aby wykonać niezależną od kultury zmianę wielkości liter, zobacz [wykonywanie zmian wielkości liter niewrażliwych na kulturę](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="tolower"></a>toLower  
 Metoda <xref:System.String.ToLower%2A?displayProperty=nameWithType> jest podobna do poprzedniej metody, ale zamiast tego konwertuje wszystkie znaki w ciągu na małe litery. Poniższy przykład konwertuje ciąg "Hello world!" na małe litery.  
  
 [!code-csharp[Strings.ChangingCase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#2)]
 [!code-vb[Strings.ChangingCase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#2)]  
  
 Poprzedni przykład jest domyślnie uwzględniany w kulturze; stosuje konwencje wielkości liter bieżącej kultury. Aby wykonać niezależną od kultury zmianę wielkości liter lub zastosować konwencje wielkości liter w danej kulturze, Użyj przeciążenia metody <xref:System.String.ToLower%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> i podaj wartość <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> lub <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> obiektu, który reprezentuje określoną kulturę do parametru *kultury* . Aby zapoznać się z przykładem, w którym pokazano, jak użyć metody <xref:System.String.ToLower%28System.Globalization.CultureInfo%29>, aby wykonać niezależną od kultury zmianę wielkości liter, zobacz [wykonywanie zmian wielkości liter niewrażliwych na kulturę](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="totitlecase"></a>ToTitleCase  
 <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> konwertuje pierwszy znak każdego wyrazu na wielkie litery i pozostałe znaki na małe litery. Jednak wyrazy, które są całkowicie pisane wielkimi literami, założono, że są akronimami i nie są konwertowane.  
  
 Metoda <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> jest wrażliwa na kulturę; oznacza to, że używa konwencji wielkości liter w określonej kulturze. Aby wywołać metodę, należy najpierw pobrać obiekt <xref:System.Globalization.TextInfo>, który reprezentuje konwencje wielkości liter danej kultury z właściwości <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> określonej kultury.  
  
 Poniższy przykład przekazuje każdy ciąg w tablicy do metody <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType>.  Ciągi zawierają odpowiednie ciągi tytułu, a także akronimy. Ciągi są konwertowane do wielkości liter przy użyciu konwencji wielkości liter w kulturze angielskiej (Stany Zjednoczone).  
  
 [!code-csharp[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/cs/totitlecase2.cs#1)]
 [!code-vb[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/vb/totitlecase2.vb#1)]  
  
 Należy pamiętać, że chociaż jest to zależne od kultury, Metoda <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> nie zapewnia odpowiednich do języka reguł dotyczących wielkości liter. Na przykład w poprzednim przykładzie metoda konwertuje "wskaźnik z dwóch miast" na "wskaźnik o dwóch miejscowości". Niemniej jednak w języku z tytułami dla kultury en-US jest to "wskaźnik dwóch miast".  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)
- [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
