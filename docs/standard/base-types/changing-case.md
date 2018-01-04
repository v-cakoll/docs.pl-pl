---
title: "Zmienianie wielkości liter w programie .NET Framework"
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
helpviewer_keywords:
- strings [.NET Framework], case
- case sensitivity
- ToUpper method
- ToLower method
- uppercase
- lowercase
ms.assetid: 6805f81b-e9ad-4387-9f4c-b9bdb21b87c0
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a3d845f53238f3b5b1744c13de9800e0d8f65dbc
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="changing-case-in-net"></a>Zmienianie wielkości liter w .NET
Jeśli piszesz aplikację, która akceptuje dane wejściowe użytkownika, nigdy nie można się przypadek, jakie użytkownik będzie służy do wprowadzania danych. Często mają ciągi, aby mieć prawidłową wielkość spójnie, zwłaszcza w przypadku, gdy są ich wyświetlanie interfejsu użytkownika. W poniższej tabeli opisano trzy metody zmiana case. Pierwsze dwie metody Udostępnij przeciążenie akceptującego kultury.  
  
|Nazwa metody|Zastosowanie|  
|-----------------|---------|  
|<xref:System.String.ToUpper%2A?displayProperty=nameWithType>|Konwertuje wszystkie znaki w ciągu na wielkie litery.|  
|<xref:System.String.ToLower%2A?displayProperty=nameWithType>|Konwertuje wszystkie znaki w ciągu na małe litery.|  
|<xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType>|Konwertuje ciąg na wielkość liter.|  
  
> [!WARNING]
>  Należy pamiętać, że <xref:System.String.ToUpper%2A?displayProperty=nameWithType> i <xref:System.String.ToLower%2A?displayProperty=nameWithType> metody nie powinna być używana do konwertowania ciągów, aby porównać je lub testowane pod kątem równości. Aby uzyskać więcej informacji, zobacz [porównywanie ciągów wielkich i małych liter](#Comparing) sekcji.  
  
<a name="Comparing"></a>   
## <a name="comparing-strings-of-mixed-case"></a>Porównywanie ciągów wielkich i małych liter  
 Należy porównywać ciągi wielkich i małych liter, aby określić ich kolejność, wywoływanie jednego z przeciążeń <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody z `comparisonType` parametru i podaj wartości <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>, <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>, lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> dla `comparisonType` argument. Porównanie przy użyciu określonej kultury innej niż bieżąca kultura wywoływać przeciążenia <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody zarówno `culture` i `options` parametru i podaj wartość <xref:System.Globalization.CompareOptions.IgnoreCase?displayProperty=nameWithType> jako `options` argumentu.  
  
 Należy porównywać ciągi wielkich i małych liter w celu ustalenia, czy są równe, ich, wywoływanie jednego z przeciążeń <xref:System.String.Equals%2A?displayProperty=nameWithType> metody z `comparisonType` parametru i podaj wartości <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>, <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>, lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> dla `comparisonType` argumentu.  
  
 Aby uzyskać więcej informacji, zobacz [najlepsze rozwiązania dotyczące ciągów za pomocą](../../../docs/standard/base-types/best-practices-strings.md).  
  
## <a name="toupper"></a>toUpper  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType> Metoda zmienia wszystkie znaki w ciągu na wielkie litery. Poniższy przykład konwertuje ciąg "Hello World!" z wielkich i małych liter na wielkie litery.  
  
 [!code-csharp[Strings.ChangingCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#1)]
 [!code-vb[Strings.ChangingCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#1)]  
  
 Powyższy przykład jest zależne od kultury domyślnie; ma to zastosowanie Konwencji wielkość liter w bieżącej kultury. Do wykonania niezależnych od kultury zmian wielkości lub zastosować konwencje wielkość liter w określonej kultury, użyj <xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> metoda przeciążenia i podaj wartość <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> lub <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> obiektu, który reprezentuje określonej kultury *kultury* parametru. Na przykład, który demonstruje sposób użycia <xref:System.String.ToUpper%2A> metodę w celu niezależnych od kultury zmian wielkości, zobacz [wykonywanie niezależnych od kultury zmian przypadku](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="tolower"></a>toLower  
 <xref:System.String.ToLower%2A?displayProperty=nameWithType> Metody jest podobny do poprzedniego metody, ale zamiast tego konwertuje wszystkie znaki w ciągu na małe litery. Poniższy przykład konwertuje ciąg "Hello World!" na małe litery.  
  
 [!code-csharp[Strings.ChangingCase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#2)]
 [!code-vb[Strings.ChangingCase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#2)]  
  
 Powyższy przykład jest zależne od kultury domyślnie; ma to zastosowanie Konwencji wielkość liter w bieżącej kultury. Do wykonania niezależnych od kultury zmian wielkości lub zastosować konwencje wielkość liter w określonej kultury, użyj <xref:System.String.ToLower%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> metoda przeciążenia i podaj wartość <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> lub <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> obiektu, który reprezentuje określonej kultury *kultury* parametru. Na przykład, który demonstruje sposób użycia <xref:System.String.ToLower%28System.Globalization.CultureInfo%29> metodę w celu niezależnych od kultury zmian wielkości, zobacz [wykonywanie niezależnych od kultury zmian przypadku](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="totitlecase"></a>ToTitleCase  
 <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> Konwertuje pierwszy znak każdego wyrazu na wielkie litery i pozostałych znaków na małe litery. Jednak słowa, które są całkowicie wielkie są rozpatrywane akronimów i nie są konwertowane.  
  
 <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> Metoda jest zależne od kultury; oznacza to, używa konwencji wielkość liter w określonej kultury. Aby można było wywołać metodę, należy najpierw pobrać <xref:System.Globalization.TextInfo> obiekt, który reprezentuje konwencje wielkość liter w określonej kultury z <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> właściwości określonej kultury.  
  
 Poniższy przykład przekazuje każdy ciąg w macierzy <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> metody.  Ciągi obejmują tytuł odpowiednie parametry, a także akronimów. Ciągi są konwertowane na wielkość liter przy użyciu konwencji wielkości liter kultury angielski (Stany Zjednoczone).  
  
 [!code-csharp[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/cs/totitlecase2.cs#1)]
 [!code-vb[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/vb/totitlecase2.vb#1)]  
  
 Należy pamiętać, że chociaż jest zależne od kultury, <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> — metoda nie ma reguł zależnej poprawną wielkość liter. Na przykład w poprzednim przykładzie metoda konwertuje "wskaźnik dwóch miast" do "Jak A wskaźnik dwóch miast". Jednak wielkość liter tytułu zależnej dla kultury en US jest "Wskaźnik dwóch miast."  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)  
 [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
