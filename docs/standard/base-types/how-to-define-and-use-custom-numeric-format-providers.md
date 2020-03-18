---
title: 'Porady: definiowanie i użycie niestandardowych dostawców formatu liczbowego'
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
ms.openlocfilehash: 151bf40cf042517b7441b89688122373259dc7dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140064"
---
# <a name="how-to-define-and-use-custom-numeric-format-providers"></a>Porady: definiowanie i użycie niestandardowych dostawców formatu liczbowego
.NET Framework zapewnia szeroką kontrolę nad reprezentacją ciągów wartości liczbowych. Obsługuje następujące funkcje dostosowywania formatu wartości liczbowych:  
  
- Standardowe ciągi formatu numerycznego, które zapewniają wstępnie zdefiniowany zestaw formatów do konwertowania liczb na ich reprezentację ciągów. Można ich używać z dowolną metodą formatowania <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>numerycznego, `format` taką jak , która ma parametr. Aby uzyskać szczegółowe informacje, zobacz [Standardowe ciągi formatu numerycznego](../../../docs/standard/base-types/standard-numeric-format-strings.md).  
  
- Niestandardowe ciągi formatu numerycznego, które zapewniają zestaw symboli, które można łączyć w celu zdefiniowania niestandardowych specyfikatorów formatu numerycznego. Mogą być również używane z dowolną metodą formatowania numerycznego, taką jak <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>, która ma `format` parametr. Aby uzyskać szczegółowe informacje, zobacz [Niestandardowe ciągi formatu numerycznego](../../../docs/standard/base-types/custom-numeric-format-strings.md).  
  
- Niestandardowe <xref:System.Globalization.CultureInfo> <xref:System.Globalization.NumberFormatInfo> lub obiekty, które definiują symbole i wzorce formatu używane do wyświetlania reprezentacji ciągów wartości liczbowych. Można ich używać z dowolną metodą formatowania <xref:System.Int32.ToString%2A>numerycznego, `provider` taką jak , która ma parametr. Zazwyczaj `provider` parametr jest używany do określania formatowania specyficznedla kultury.  
  
 W niektórych przypadkach (na przykład, gdy aplikacja musi wyświetlać sformatowany numer konta, numer identyfikacyjny lub kod pocztowy) te trzy techniki są nieodpowiednie. Program .NET Framework umożliwia również zdefiniowanie obiektu formatującego, <xref:System.Globalization.NumberFormatInfo> który nie jest ani obiektem, <xref:System.Globalization.CultureInfo> aby określić sposób formatowania wartości liczbowej. W tym temacie przedstawiono instrukcje krok po kroku dotyczące implementowania takiego obiektu i przedstawiono przykład formatowania numerów telefonów.  
  
### <a name="to-define-a-custom-format-provider"></a>Aby zdefiniować dostawcę formatu niestandardowego  
  
1. Zdefiniuj klasę, która implementuje <xref:System.IFormatProvider> interfejsy i. <xref:System.ICustomFormatter>  
  
2. Zaimplementuj <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metodę. <xref:System.IFormatProvider.GetFormat%2A>jest metodą wywołania zwrotu, którą wywołuje <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metoda formatowania (na przykład metoda), aby pobrać obiekt, który jest faktycznie odpowiedzialny za wykonywanie formatowania niestandardowego. Typowa implementacja <xref:System.IFormatProvider.GetFormat%2A> wykonuje następujące czynności:  
  
    1. Określa, <xref:System.Type> czy obiekt przekazany jako parametr <xref:System.ICustomFormatter> metody reprezentuje interfejs.  
  
    2. Jeśli parametr reprezentuje <xref:System.ICustomFormatter> interfejs, <xref:System.IFormatProvider.GetFormat%2A> zwraca obiekt, który <xref:System.ICustomFormatter> implementuje interfejs, który jest odpowiedzialny za zapewnienie formatowania niestandardowego. Zazwyczaj niestandardowy obiekt formatowania zwraca się.  
  
    3. Jeśli parametr nie reprezentuje <xref:System.ICustomFormatter> <xref:System.IFormatProvider.GetFormat%2A> interfejsu, `null`zwraca .  
  
3. Zaimplementuj <xref:System.ICustomFormatter.Format%2A> metodę. Ta metoda jest <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> wywoływana przez metodę i jest odpowiedzialny za zwracanie reprezentacji ciągu liczby. Implementowanie metody zazwyczaj obejmuje następujące czynności:  
  
    1. Opcjonalnie upewnij się, że metoda jest zgodnie z prawem przeznaczone do `provider` świadczenia usług formatowania przez zbadanie parametru. W przypadku obiektów formatowania, które implementują oba <xref:System.IFormatProvider> i <xref:System.ICustomFormatter>, obejmuje to testowanie parametru `provider` równości z bieżącym obiektem formatowania.  
  
    2. Określ, czy obiekt formatowania powinien obsługiwać specyfikatory formatu niestandardowego. (Na przykład specyfikator formatu "N" może wskazywać, że numer telefonu w USA powinien być wyprowadzany w formacie NANP, a "I" może wskazywać dane wyjściowe w formacie ITU-T Recommendation E.123). Jeśli używane są specyfikatory formatu, metoda powinna obsługiwać specyfikator określonego formatu. Jest on przekazywany do `format` metody w parametrze. Jeśli nie ma specyfikatora, `format` wartość <xref:System.String.Empty?displayProperty=nameWithType>parametru jest .  
  
    3. Pobierz wartość liczbową przekazaną do `arg` metody jako parametr. Wykonaj wszelkie manipulacje są wymagane do konwersji go do jego reprezentacji ciągu.  
  
    4. Zwraca reprezentację ciągu `arg` parametru.  
  
### <a name="to-use-a-custom-numeric-formatting-object"></a>Aby użyć niestandardowego obiektu formatowania liczbowego  
  
1. Utwórz nowe wystąpienie niestandardowej klasy formatowania.  
  
2. Wywołaj <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metodę formatowania, przekazując jej niestandardowy obiekt formatowania, specyfikator formatowania (lub <xref:System.String.Empty?displayProperty=nameWithType>, jeśli nie jest używany) i wartość liczbową do sformatowania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano niestandardowego dostawcę formatu numerycznego o nazwie, `TelephoneFormatter` który konwertuje liczbę reprezentującą numer telefonu w STANACH USA na format NANP lub E.123. Metoda obsługuje dwa specyfikatory formatu, "N" (który wyprowadza format NANP) i "I" (który wyprowadza międzynarodowy format E.123).  
  
 [!code-csharp[Formatting.HowTo.NumericValue#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#1)]
 [!code-vb[Formatting.HowTo.NumericValue#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#1)]  
  
 Niestandardowego dostawcy formatu numerycznego można <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> używać tylko z tą metodą. Inne przeciążenia metod formatowania liczbowego (takich jak), `ToString`które <xref:System.IFormatProvider> mają parametr <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> typu <xref:System.Type> wszystkie przekazać <xref:System.Globalization.NumberFormatInfo> implementacji obiektu, który reprezentuje typ. W zamian oczekują metody do <xref:System.Globalization.NumberFormatInfo> zwrócenia obiektu. Jeśli tak nie jest, niestandardowy dostawca formatu <xref:System.Globalization.NumberFormatInfo> numerycznego jest ignorowany, a obiekt bieżącej kultury jest używany w jego miejsce. W tym przykładzie `TelephoneFormatter.GetFormat` metoda obsługuje możliwość, że może być niewłaściwie przekazywane do metody formatowania liczbowego, `null` sprawdzając parametr metody <xref:System.ICustomFormatter>i zwracając, jeśli reprezentuje typ inny niż .  
  
 Jeśli dostawca niestandardowego formatu numerycznego obsługuje zestaw specyfikatorów formatu, upewnij się, że podana jest <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> domyślna zachowanie, jeśli w elemencie formatu nie podano elementu formatu używanego w wywołaniu metody. W przykładzie "N" jest domyślnym specyfikatorem formatu. Dzięki temu numer ma zostać przekonwertowany na sformatowany numer telefonu, podając jawny specyfikator formatu. W poniższym przykładzie przedstawiono takie wywołanie metody.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#2)]
 [!code-vb[Formatting.HowTo.NumericValue#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#2)]  
  
 Ale pozwala również na konwersję występuje, jeśli nie specyfikator formatu jest obecny. W poniższym przykładzie przedstawiono takie wywołanie metody.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#3)]
 [!code-vb[Formatting.HowTo.NumericValue#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#3)]  
  
 Jeśli nie zdefiniowano domyślnego specyfikatora formatu, implementacja <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> metody powinna zawierać kod, taki jak poniższy, aby program .NET mógł zapewnić formatowanie, które nie obsługuje kodu.  
  
 [!code-csharp[System.ICustomFormatter.Format#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.ICustomFormatter.Format/cs/format.cs#1)]
 [!code-vb[System.ICustomFormatter.Format#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.ICustomFormatter.Format/vb/Format.vb#1)]  
  
 W tym przykładzie metoda, która implementuje <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> jest przeznaczony do służyć jako <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metoda wywołania wywołania dla metody. W związku z `formatProvider` tym sprawdza parametr, aby ustalić, `TelephoneFormatter` czy zawiera odwołanie do bieżącego obiektu. Jednak metoda może być również wywoływana bezpośrednio z kodu. W takim przypadku można `formatProvider` użyć parametru, aby podać <xref:System.Globalization.CultureInfo> lub <xref:System.Globalization.NumberFormatInfo> obiekt, który dostarcza informacji o formatowaniu specyficznych dla kultury.  
  
## <a name="see-also"></a>Zobacz też

- [Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)
