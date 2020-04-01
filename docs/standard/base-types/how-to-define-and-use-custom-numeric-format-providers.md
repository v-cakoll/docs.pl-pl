---
title: 'Instrukcje: Definiowanie i używanie niestandardowych dostawców formatu liczbowego'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- custom numeric format strings
- numbers [.NET Framework], custom numeric format strings
- displaying date and time data
- format providers [.NET Framework]
- custom format strings
ms.assetid: a281bfbf-6596-45ed-a2d6-3782d535ada2
ms.openlocfilehash: 5345c90d966ea9ce0a0bbf6c884b8d8abc8b5fa7
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523936"
---
# <a name="how-to-define-and-use-custom-numeric-format-providers"></a>Instrukcje: Definiowanie i używanie niestandardowych dostawców formatu liczbowego
.NET Framework zapewnia rozległą kontrolę nad reprezentacją ciągów wartości liczbowych. Obsługuje następujące funkcje dostosowywania formatu wartości liczbowych:  
  
- Standardowe ciągi formatu numerycznego, które zapewniają wstępnie zdefiniowany zestaw formatów do konwertowania liczb na ich reprezentację ciągu. Można ich używać z dowolną metodą formatowania numerycznego, taką jak <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>, która ma `format` parametr. Aby uzyskać szczegółowe informacje, zobacz [Standardowe ciągi formatu numerycznego](../../../docs/standard/base-types/standard-numeric-format-strings.md).  
  
- Niestandardowe ciągi formatu numerycznego, które zapewniają zestaw symboli, które można łączyć w celu zdefiniowania niestandardowych specyfikatorów formatu liczbowego. Mogą być również używane z dowolną metodą <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>formatowania numerycznego, taką jak , która ma `format` parametr. Aby uzyskać szczegółowe informacje, zobacz [Niestandardowe ciągi formatu numerycznego](../../../docs/standard/base-types/custom-numeric-format-strings.md).  
  
- <xref:System.Globalization.CultureInfo> Niestandardowe <xref:System.Globalization.NumberFormatInfo> lub obiekty, które definiują symbole i wzorce formatowania używane do wyświetlania reprezentacji ciągów wartości liczbowych. Można ich używać z dowolną metodą formatowania numerycznego, taką jak <xref:System.Int32.ToString%2A>, która ma `provider` parametr. Zazwyczaj `provider` parametr jest używany do określania formatowania specyficznego dla kultury.  
  
 W niektórych przypadkach (na przykład gdy aplikacja musi wyświetlać sformatowany numer konta, numer identyfikacyjny lub kod pocztowy) te trzy techniki są niewłaściwe. .NET Framework umożliwia również zdefiniowanie obiektu formatowania, <xref:System.Globalization.CultureInfo> który <xref:System.Globalization.NumberFormatInfo> nie jest ani obiektem, ani obiektem w celu określenia sposobu formatowania wartości liczbowej. Ten temat zawiera instrukcje krok po kroku dotyczące implementowania takiego obiektu i zawiera przykład, który formatuje numery telefonów.  
  
### <a name="to-define-a-custom-format-provider"></a>Aby zdefiniować dostawcę formatu niestandardowego  
  
1. Zdefiniuj klasę, która implementuje <xref:System.IFormatProvider> i <xref:System.ICustomFormatter> interfejsy.  
  
2. Zaimplementuj <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metodę. <xref:System.IFormatProvider.GetFormat%2A>jest metodą wywołania zwrotnego, którą <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metoda formatowania (taka jak metoda) wywołuje w celu pobrania obiektu, który jest faktycznie odpowiedzialny za wykonywanie formatowania niestandardowego. Typowe wykonanie <xref:System.IFormatProvider.GetFormat%2A> wykonuje następujące czynności:  
  
    1. Określa, <xref:System.Type> czy obiekt przekazany jako parametr <xref:System.ICustomFormatter> metody reprezentuje interfejs.  
  
    2. Jeśli parametr reprezentuje <xref:System.ICustomFormatter> interfejs, <xref:System.IFormatProvider.GetFormat%2A> zwraca obiekt, który <xref:System.ICustomFormatter> implementuje interfejs, który jest odpowiedzialny za zapewnienie formatowania niestandardowego. Zazwyczaj obiekt formatowania niestandardowego zwraca się.  
  
    3. Jeśli parametr nie reprezentuje <xref:System.ICustomFormatter> <xref:System.IFormatProvider.GetFormat%2A> interfejsu, `null`zwraca program .  
  
3. Zaimplementuj <xref:System.ICustomFormatter.Format%2A> metodę. Ta metoda jest <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> wywoływana przez metodę i jest odpowiedzialny za zwracanie reprezentacji ciągu liczby. Implementacja metody zazwyczaj obejmuje następujące czynności:  
  
    1. Opcjonalnie upewnij się, że metoda jest zgodnie z prawem przeznaczone `provider` do świadczenia usług formatowania przez sprawdzenie parametru. W przypadku formatowania <xref:System.IFormatProvider> obiektów, które implementują zarówno i <xref:System.ICustomFormatter>, obejmuje to testowanie parametru `provider` równości z bieżącym obiektem formatowania.  
  
    2. Określ, czy obiekt formatowania powinien obsługiwać specyfikatory formatów niestandardowych. (Na przykład specyfikator formatu "N" może wskazywać, że numer telefonu w USA powinien być wyprowadzany w formacie NANP, a "I" może wskazywać dane wyjściowe w formacie E.123 rekomendacji ITU-T). Jeśli używane są specyfikatory formatu, metoda powinna obsługiwać specyfikator określonego formatu. Jest przekazywana do `format` metody w parametrze. Jeśli nie ma specyfikatora, `format` wartość <xref:System.String.Empty?displayProperty=nameWithType>parametru jest .  
  
    3. Pobierz wartość liczbową przekazywana do `arg` metody jako parametr. Wykonaj niezależnie od manipulacji są wymagane do konwersji go do jego reprezentacji ciągów.  
  
    4. Zwraca reprezentację ciągu `arg` parametru.  
  
### <a name="to-use-a-custom-numeric-formatting-object"></a>Aby użyć niestandardowego obiektu formatowania liczbowego  
  
1. Utwórz nowe wystąpienie niestandardowej klasy formatowania.  
  
2. Wywołanie <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metody formatowania, przekazanie jej obiektu formatowania niestandardowego, <xref:System.String.Empty?displayProperty=nameWithType>specyfikatora formatowania (lub , jeśli nie jest używany) i wartości liczbowej, która ma zostać sformatowana.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład definiuje niestandardowego dostawcy `TelephoneFormatter` formatu liczbowego o nazwie, który konwertuje liczbę reprezentującą numer telefonu w USA na format NANP lub E.123. Metoda obsługuje dwa specyfikatory formatu, "N" (który wyprowadza format NANP) i "I" (który wyprowadza międzynarodowy format E.123).  
  
 [!code-csharp[Formatting.HowTo.NumericValue#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#1)]
 [!code-vb[Formatting.HowTo.NumericValue#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#1)]  
  
 Niestandardowy dostawca formatu numerycznego może <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> być używany tylko z metodą. Inne przeciążenia metod formatowania numerycznego `ToString`(takich jak ), <xref:System.IFormatProvider> które mają <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> parametr <xref:System.Type> typu wszystkie <xref:System.Globalization.NumberFormatInfo> przekazać implementacji obiektu, który reprezentuje typ. W zamian oczekują, że metoda <xref:System.Globalization.NumberFormatInfo> do zwrócenia obiektu. Jeśli tak nie jest, dostawca niestandardowego formatu <xref:System.Globalization.NumberFormatInfo> liczbowego jest ignorowany, a obiekt dla bieżącej kultury jest używany w jego miejsce. W przykładzie `TelephoneFormatter.GetFormat` metoda obsługuje możliwość, że może być niewłaściwie przekazywane do metody formatowania numerycznego, `null` badając parametr metody i <xref:System.ICustomFormatter>zwracając, jeśli reprezentuje typ inny niż .  
  
 Jeśli niestandardowy dostawca formatu numerycznego obsługuje zestaw specyfikatorów formatu, upewnij się, że podasz domyślne zachowanie, jeśli w elemencie formatu używanym w wywołaniu <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metody nie jest podany żaden specyfikator formatu. W przykładzie "N" jest domyślnym specyfikatorem formatu. Pozwala to na przekonwertowanie numeru na sformatowany numer telefonu przez podanie jawnego specyfikatora formatu. Poniższy przykład ilustruje takie wywołanie metody.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#2)]
 [!code-vb[Formatting.HowTo.NumericValue#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#2)]  
  
 Ale umożliwia również konwersji występuje, jeśli nie specyfikator formatu jest obecny. Poniższy przykład ilustruje takie wywołanie metody.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#3)]
 [!code-vb[Formatting.HowTo.NumericValue#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#3)]  
  
 Jeśli nie zdefiniowano domyślnego specyfikatora <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> formatu, implementacja metody powinna zawierać kod, taki jak poniższy, aby program .NET mógł zapewnić formatowanie, które nie obsługuje kodu.  
  
 [!code-csharp[System.ICustomFormatter.Format#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.ICustomFormatter.Format/cs/format.cs#1)]
 [!code-vb[System.ICustomFormatter.Format#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.ICustomFormatter.Format/vb/Format.vb#1)]  
  
 W tym przykładzie metoda, która <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> implementuje ma służyć jako metoda <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> wywołania zwrotnego dla metody. W związku z tym `formatProvider` bada parametr, aby ustalić, `TelephoneFormatter` czy zawiera odwołanie do bieżącego obiektu. Jednak metoda może być również wywoływana bezpośrednio z kodu. W takim przypadku można `formatProvider` użyć parametru, aby podać <xref:System.Globalization.CultureInfo> lub <xref:System.Globalization.NumberFormatInfo> obiekt, który dostarcza informacji formatowania specyficzne dla kultury.
