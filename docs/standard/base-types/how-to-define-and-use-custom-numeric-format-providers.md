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
ms.openlocfilehash: d12899fff7d9e6cb63728ba0b160b70fa2a41a1a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290516"
---
# <a name="how-to-define-and-use-custom-numeric-format-providers"></a>Instrukcje: Definiowanie i używanie niestandardowych dostawców formatu liczbowego
.NET Framework zapewnia szeroką kontrolę nad reprezentacją ciągu wartości liczbowych. Program obsługuje następujące funkcje dostosowywania formatu wartości liczbowych:  
  
- Standardowe ciągi formatujące liczbę, które zapewniają wstępnie zdefiniowany zestaw formatów do konwertowania liczb na ich reprezentację w postaci ciągu. Można ich używać z dowolną metodą formatowania liczbowego, taką jak <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> , która ma `format` parametr. Aby uzyskać szczegółowe informacje, zobacz [Standardowe ciągi formatujące liczby](standard-numeric-format-strings.md).  
  
- Niestandardowe ciągi formatujące liczbę, które zawierają zestaw symboli, które można łączyć w celu zdefiniowania niestandardowych specyfikatorów formatu liczbowego. Mogą być również używane z dowolną metodą formatowania liczbowego, taką jak <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> , która ma `format` parametr. Aby uzyskać szczegółowe informacje, zobacz [Niestandardowe ciągi formatujące](custom-numeric-format-strings.md).  
  
- Niestandardowe <xref:System.Globalization.CultureInfo> lub <xref:System.Globalization.NumberFormatInfo> obiekty, które definiują symbole i wzorce formatu używane do wyświetlania reprezentacji ciągów wartości liczbowych. Można ich używać z dowolną metodą formatowania liczbowego, taką jak <xref:System.Int32.ToString%2A> , która ma `provider` parametr. Zazwyczaj `provider` parametr służy do określania formatowania specyficznego dla kultury.  
  
 W niektórych przypadkach (na przykład gdy aplikacja musi wyświetlić sformatowany numer konta, numer identyfikacyjny lub kod pocztowy) te trzy techniki są nieodpowiednie. .NET Framework umożliwia również zdefiniowanie obiektu formatowania, który nie jest <xref:System.Globalization.CultureInfo> ani <xref:System.Globalization.NumberFormatInfo> obiektem, aby określić, jak jest sformatowana wartość liczbowa. Ten temat zawiera instrukcje krok po kroku dotyczące implementowania takiego obiektu i zawiera przykład formatowania numerów telefonów.  
  
### <a name="to-define-a-custom-format-provider"></a>Aby zdefiniować niestandardowego dostawcę formatowania  
  
1. Zdefiniuj klasę implementującą <xref:System.IFormatProvider> <xref:System.ICustomFormatter> interfejsy i.  
  
2. Zaimplementuj <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metodę. <xref:System.IFormatProvider.GetFormat%2A>to metoda wywołania zwrotnego, która Metoda formatowania (taka jak <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> Metoda) wywołuje, aby pobrać obiekt, który jest odpowiedzialny za wykonywanie formatowania niestandardowego. Typowa implementacja programu <xref:System.IFormatProvider.GetFormat%2A> wykonuje następujące czynności:  
  
    1. Określa, czy <xref:System.Type> obiekt przesłany jako parametr metody reprezentuje <xref:System.ICustomFormatter> interfejs.  
  
    2. Jeśli parametr reprezentuje <xref:System.ICustomFormatter> interfejs, <xref:System.IFormatProvider.GetFormat%2A> zwraca obiekt, który implementuje <xref:System.ICustomFormatter> interfejs, który jest odpowiedzialny za dostarczanie formatowania niestandardowego. Zazwyczaj obiekt formatowania niestandardowego zwraca sam siebie.  
  
    3. Jeśli parametr nie reprezentuje <xref:System.ICustomFormatter> interfejsu, <xref:System.IFormatProvider.GetFormat%2A> zwraca `null` .  
  
3. Zaimplementuj <xref:System.ICustomFormatter.Format%2A> metodę. Ta metoda jest wywoływana przez <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metodę i jest odpowiedzialna za zwracanie ciągu reprezentującego liczbę. Implementacja metody zwykle obejmuje następujące elementy:  
  
    1. Opcjonalnie upewnij się, że metoda jest uzasadniona celem zapewnienia usług formatowania, sprawdzając `provider` parametr. W przypadku formatowania obiektów, które implementują oba <xref:System.IFormatProvider> i <xref:System.ICustomFormatter> , obejmuje to testowanie `provider` parametru pod kątem równości z bieżącym obiektem formatowania.  
  
    2. Ustal, czy obiekt formatowania powinien obsługiwać niestandardowe specyfikatory formatu. (Na przykład specyfikator formatu "N" może wskazywać, że numer telefonu w Stanach Zjednoczonych powinien być wyjściowy w formacie NANP, a "I" może wskazywać na dane wyjściowe w formacie E. 123 z zaleceniem ITU-T). Jeśli używane są specyfikatory formatu, metoda powinna obsługiwać określony specyfikator formatu. Jest ona przenoszona do metody w `format` parametrze. Jeśli żaden specyfikator nie jest obecny, wartość `format` parametru to <xref:System.String.Empty?displayProperty=nameWithType> .  
  
    3. Pobierz wartość liczbową przekazaną do metody jako `arg` parametr. Wykonaj wszelkie manipulacje wymagane do przekonwertowania go na jego reprezentację ciągu.  
  
    4. Zwraca reprezentację ciągu dla `arg` parametru.  
  
### <a name="to-use-a-custom-numeric-formatting-object"></a>Aby użyć niestandardowego obiektu formatowania liczbowego  
  
1. Utwórz nowe wystąpienie niestandardowej klasy formatowania.  
  
2. Wywołaj <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metodę formatowania, przekazując ją do niestandardowego obiektu formatowania, specyfikator formatowania (lub <xref:System.String.Empty?displayProperty=nameWithType> , jeśli taki nie jest używany) i wartość liczbową do sformatowania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano niestandardowego dostawcę formatu liczbowego `TelephoneFormatter` , który konwertuje liczbę reprezentującą numer telefonu w Stanach Zjednoczonych do formatu NANP lub E. 123. Metoda obsługuje dwa specyfikatory formatu: "N" (który wyprowadza format NANP) i "I" (który wyprowadza międzynarodowy format E. 123).  
  
 [!code-csharp[Formatting.HowTo.NumericValue#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#1)]
 [!code-vb[Formatting.HowTo.NumericValue#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#1)]  
  
 Niestandardowego dostawcy formatu liczbowego można używać tylko z <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metodą. Inne przeciążenia metod formatowania liczbowego (takich jak `ToString` ), które mają parametr typu all, <xref:System.IFormatProvider> przekazują <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementację <xref:System.Type> obiektu, który reprezentuje <xref:System.Globalization.NumberFormatInfo> Typ. W powrocie oczekuje, że metoda zwraca <xref:System.Globalization.NumberFormatInfo> obiekt. Jeśli tak nie jest, dostawca niestandardowego formatu liczbowego jest ignorowany, a <xref:System.Globalization.NumberFormatInfo> obiekt dla bieżącej kultury jest używany w jego miejscu. W przykładzie `TelephoneFormatter.GetFormat` Metoda obsługuje możliwość, że może być niewłaściwie przenoszona do metody formatowania liczbowego poprzez zbadanie parametru Method i zwrócenie, `null` Jeśli reprezentuje typ inny niż <xref:System.ICustomFormatter> .  
  
 Jeśli dostawca niestandardowego formatu liczb obsługuje zestaw specyfikatorów formatu, upewnij się, że zostało podane zachowanie domyślne, jeśli w elemencie formatu użytym w wywołaniu metody nie podano specyfikatora formatu <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> . W przykładzie "N" jest domyślnym specyfikatorem formatu. Pozwala to na konwersję liczby na sformatowany numer telefonu przez udostępnienie jawnego specyfikatora formatu. Poniższy przykład ilustruje takie wywołanie metody.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#2)]
 [!code-vb[Formatting.HowTo.NumericValue#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#2)]  
  
 Jednak umożliwia również konwersję, jeśli nie ma specyfikatora formatu. Poniższy przykład ilustruje takie wywołanie metody.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#3)]
 [!code-vb[Formatting.HowTo.NumericValue#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#3)]  
  
 Jeśli nie zdefiniowano domyślnego specyfikatora formatu, implementacja <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> metody powinna obejmować kod, taki jak następujące, aby program .NET mógł zapewnić formatowanie, którego kod nie obsługuje.  
  
 [!code-csharp[System.ICustomFormatter.Format#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.ICustomFormatter.Format/cs/format.cs#1)]
 [!code-vb[System.ICustomFormatter.Format#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.ICustomFormatter.Format/vb/Format.vb#1)]  
  
 W przypadku tego przykładu Metoda implementująca <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> ma służyć jako metoda wywołania zwrotnego dla <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metody. W związku z tym sprawdza `formatProvider` parametr, aby określić, czy zawiera odwołanie do bieżącego `TelephoneFormatter` obiektu. Jednak metodę można również wywołać bezpośrednio z kodu. W takim przypadku można użyć `formatProvider` parametru, aby dostarczyć <xref:System.Globalization.CultureInfo> <xref:System.Globalization.NumberFormatInfo> obiekt lub, który dostarcza informacje o formatowaniu specyficzne dla kultury.
