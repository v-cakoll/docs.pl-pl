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
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: 68bce927c6426fc32cd2fe26dcc488432199612d
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987205"
---
# <a name="changing-case-in-net"></a>Zmiana wielkości liter w programie .NET
Jeśli napiszesz aplikację, która akceptuje dane wejściowe od użytkownika, możesz nigdy nie mieć pewności, co ma być używane do wprowadzania danych. Często w przypadku ciągów ma być uwzględniana wielkość liter, szczególnie jeśli są one wyświetlane w interfejsie użytkownika. W poniższej tabeli opisano trzy metody zmiany wielkości liter. Dwie pierwsze metody zapewniają Przeciążenie, które akceptuje kulturę.  
  
|Nazwa metody|Zastosowanie|  
|-----------------|---------|  
|<xref:System.String.ToUpper%2A?displayProperty=nameWithType>|Konwertuje wszystkie znaki w ciągu na wielkie litery.|  
|<xref:System.String.ToLower%2A?displayProperty=nameWithType>|Konwertuje wszystkie znaki w ciągu na małe litery.|  
|<xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType>|Konwertuje ciąg na wielkość liter.|  
  
> [!WARNING]
> Należy zauważyć, <xref:System.String.ToUpper%2A?displayProperty=nameWithType> że <xref:System.String.ToLower%2A?displayProperty=nameWithType> metody i nie powinny być używane do konwersji ciągów w celu ich porównania lub przetestowania pod kątem równości. Aby uzyskać więcej informacji, zobacz [Porównywanie ciągów w przypadku mieszanego przypadku](#Comparing) .  
  
<a name="Comparing"></a>   
## <a name="comparing-strings-of-mixed-case"></a>Porównywanie ciągów z przypadku mieszanego  
 Aby porównać ciągi <xref:System.String.CompareTo%2A?displayProperty=nameWithType> o mieszanym przypadku w celu określenia ich kolejności, wywołaj jedno z przeciążeń metody `comparisonType` z parametrem i podaj wartość albo <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>, lub dla `comparisonType` <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> argument. W celu porównania przy użyciu określonej kultury innej niż bieżąca <xref:System.String.CompareTo%2A?displayProperty=nameWithType> kultura należy wywołać Przeciążenie metody z `culture` parametrem i i `options` podać wartość <xref:System.Globalization.CompareOptions.IgnoreCase?displayProperty=nameWithType> jako `options` argument.  
  
 Aby porównać ciągi o mieszanym przypadku, aby określić, czy są one równe, <xref:System.String.Equals%2A?displayProperty=nameWithType> Wywołaj jedno z przeciążeń metody `comparisonType` z parametrem i podaj wartość albo <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>, lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> dla `comparisonType` argument.  
  
 Aby uzyskać więcej informacji, zobacz [najlepsze rozwiązania dotyczące używania ciągów](../../../docs/standard/base-types/best-practices-strings.md).  
  
## <a name="toupper"></a>ToUpper  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType> Metoda zmienia wszystkie znaki w ciągu na wielkie litery. Poniższy przykład konwertuje ciąg "Hello world!" od mieszanego przypadku na wielkie litery.  
  
 [!code-csharp[Strings.ChangingCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#1)]
 [!code-vb[Strings.ChangingCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#1)]  
  
 Poprzedni przykład jest domyślnie uwzględniany w kulturze; stosuje konwencje wielkości liter bieżącej kultury. Aby wykonać niezależną od kultury zmianę wielkości liter lub zastosować konwencje wielkości liter w danej kulturze, użyj <xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> przeciążenia metody i podaj <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> wartość lub <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> obiekt, który reprezentuje określoną kulturę do  *parametr kultury* . Aby zapoznać się z przykładem, który ilustruje <xref:System.String.ToUpper%2A> sposób użycia metody w celu przeprowadzenia zmiany wielkości liter niewrażliwych na kulturę, zobacz [wykonywanie zmian wielkości liter](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)niewrażliwych na kulturę.  
  
## <a name="tolower"></a>ToLower  
 <xref:System.String.ToLower%2A?displayProperty=nameWithType> Metoda jest podobna do poprzedniej metody, ale zamiast tego konwertuje wszystkie znaki w ciągu na małe litery. Poniższy przykład konwertuje ciąg "Hello world!" na małe litery.  
  
 [!code-csharp[Strings.ChangingCase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#2)]
 [!code-vb[Strings.ChangingCase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#2)]  
  
 Poprzedni przykład jest domyślnie uwzględniany w kulturze; stosuje konwencje wielkości liter bieżącej kultury. Aby wykonać niezależną od kultury zmianę wielkości liter lub zastosować konwencje wielkości liter w danej kulturze, użyj <xref:System.String.ToLower%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> przeciążenia metody i podaj <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> wartość lub <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> obiekt, który reprezentuje określoną kulturę do  *parametr kultury* . Aby zapoznać się z przykładem, który ilustruje <xref:System.String.ToLower%28System.Globalization.CultureInfo%29> sposób użycia metody w celu przeprowadzenia zmiany wielkości liter niewrażliwych na kulturę, zobacz [wykonywanie zmian wielkości liter](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)niewrażliwych na kulturę.  
  
## <a name="totitlecase"></a>ToTitleCase  
 <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> Konwertuje pierwszy znak każdego wyrazu na wielkie litery i pozostałe znaki na małe litery. Jednak wyrazy, które są całkowicie pisane wielkimi literami, założono, że są akronimami i nie są konwertowane.  
  
 <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> Metoda jest wrażliwa na kulturę, czyli używa konwencji wielkości liter w określonej kulturze. Aby wywołać metodę, należy najpierw pobrać <xref:System.Globalization.TextInfo> obiekt, który reprezentuje konwencje wielkości liter danej kultury <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> z właściwości określonej kultury.  
  
 Poniższy przykład przekazuje każdy ciąg w tablicy do <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> metody.  Ciągi zawierają odpowiednie ciągi tytułu, a także akronimy. Ciągi są konwertowane do wielkości liter przy użyciu konwencji wielkości liter w kulturze angielskiej (Stany Zjednoczone).  
  
 [!code-csharp[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/cs/totitlecase2.cs#1)]
 [!code-vb[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/vb/totitlecase2.vb#1)]  
  
 Należy pamiętać, że chociaż jest to zależne od <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> kultury, metoda nie zapewnia odpowiedniej do języka reguł dotyczących wielkości liter. Na przykład w poprzednim przykładzie metoda konwertuje "wskaźnik z dwóch miast" na "wskaźnik o dwóch miejscowości". Niemniej jednak w języku z tytułami dla kultury en-US jest to "wskaźnik dwóch miast".  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)
- [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
