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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3898caa90c695ae681c2d9b20abbba57a2a9f61
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590470"
---
# <a name="how-to-define-and-use-custom-numeric-format-providers"></a>Instrukcje: Definiowanie i używanie niestandardowych dostawców formatu liczbowego
.NET Framework zapewnia szeroką kontrolę nad reprezentację ciągu wartości liczbowych. Obsługuje następujące funkcje dostosowywania format wartości liczbowe:  
  
- Ciągi standardowego formatu liczb, które zawierają zestaw wstępnie zdefiniowanych formatów do konwertowania liczb na jego reprezentację ciągu. Mogą być używane z wszelkie wartości numeryczne, formatowanie, metody, takie jak <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>, która ma `format` parametru. Aby uzyskać więcej informacji, zobacz [Standard Numeric Format Strings](../../../docs/standard/base-types/standard-numeric-format-strings.md).  
  
- Ciągi niestandardowego formatu liczb, które zawierają zestaw symboli, które można łączyć, aby zdefiniować specyfikatory niestandardowego formatu liczb. One można również za pomocą wszelkie wartości numeryczne, formatowanie, metody, takie jak <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>, która ma `format` parametru. Aby uzyskać więcej informacji, zobacz [Custom Numeric Format Strings](../../../docs/standard/base-types/custom-numeric-format-strings.md).  
  
- Niestandardowe <xref:System.Globalization.CultureInfo> lub <xref:System.Globalization.NumberFormatInfo> obiektów, które zdefiniować symbole i formatowanie wzorców służącego do wyświetlania ciągów reprezentujących wartości numeryczne. Mogą być używane z wszelkie wartości numeryczne, formatowanie, metody, takie jak <xref:System.Int32.ToString%2A>, która ma `provider` parametru. Zazwyczaj `provider` parametr jest używany do określenia formatowanie specyficzne dla kultury.  
  
 W niektórych przypadkach (na przykład gdy aplikacji musi wyświetlić numer konta sformatowane, numer identyfikacyjny lub kod pocztowy) tych trzech metod nie mają zastosowania. .NET Framework oferuje również możliwość definiowania formatowania obiektu, który nie jest ani <xref:System.Globalization.CultureInfo> ani <xref:System.Globalization.NumberFormatInfo> obiektu, aby określić sposób formatowania wartości liczbowej. Ten temat zawiera szczegółowe instrukcje dotyczące wdrażania takiego obiektu i przedstawiono przykład formatowania numerów telefonów.  
  
### <a name="to-define-a-custom-format-provider"></a>Aby zdefiniować dostawcę formatu niestandardowego  
  
1. Definiowanie klasy, która implementuje <xref:System.IFormatProvider> i <xref:System.ICustomFormatter> interfejsów.  
  
2. Implementowanie <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metody. <xref:System.IFormatProvider.GetFormat%2A> jest metodą wywołania zwrotnego, metoda formatowania (takie jak <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metoda) wywołuje w celu pobrania obiektu, który jest faktycznie odpowiedzialny za wykonanie, niestandardowe formatowanie. Typowa implementacja metody <xref:System.IFormatProvider.GetFormat%2A> wykonuje następujące czynności:  
  
    1. Określa, czy <xref:System.Type> przekazano obiekt jako metoda parametr reprezentuje <xref:System.ICustomFormatter> interfejsu.  
  
    2. Jeśli parametr reprezentują <xref:System.ICustomFormatter> interfejsu <xref:System.IFormatProvider.GetFormat%2A> zwraca obiekt, który implementuje <xref:System.ICustomFormatter> interfejs, który jest odpowiedzialny za zapewnienie niestandardowe formatowanie. Zazwyczaj obiektów formatowania niestandardowych zwraca samą siebie.  
  
    3. Jeśli parametr nie reprezentuje <xref:System.ICustomFormatter> interfejsu <xref:System.IFormatProvider.GetFormat%2A> zwraca `null`.  
  
3. Implementowanie <xref:System.ICustomFormatter.Format%2A> metody. Ta metoda jest wywoływana <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metody i jest odpowiedzialna za zwrócenie ciąg reprezentujący liczbę. Implementacja metody zwykle obejmuje następujące czynności:  
  
    1. Opcjonalnie, upewnij się, że metoda rzeczywiście jest przeznaczona do świadczenia usług formatowania, sprawdzając `provider` parametru. Obiekty, które implementują zarówno formatowania <xref:System.IFormatProvider> i <xref:System.ICustomFormatter>, wiąże się to testowanie `provider` parametr dla porównania z bieżącym obiektem formatowania.  
  
    2. Ustal, czy obiekt formatowania powinien obsługiwać specyfikatorów formatu niestandardowego. (Na przykład, specyfikator formatu "N" może wskazywać, że numer telefonu w Stanach Zjednoczonych, powinien być danych wyjściowych w formacie NANP, i "I" może wskazywać dane wyjściowe w formacie ITU-T E.123 zalecenia.) Jeśli używane są specyfikatorów formatu, metoda powinna obsługiwać specyfikator formatu określone. Jest przekazywany do metody w `format` parametru. Jeśli specyfikator nie jest obecna, wartość `format` parametr <xref:System.String.Empty?displayProperty=nameWithType>.  
  
    3. Pobierz wartość liczbową przekazywany do metody jako `arg` parametru. Wykonywać dowolne operacje są wymagane, aby przekonwertować go na jego reprezentację ciągu.  
  
    4. Zwraca reprezentację ciągu `arg` parametru.  
  
### <a name="to-use-a-custom-numeric-formatting-object"></a>Aby użyć obiektów niestandardowych formatowania liczbowego  
  
1. Utwórz nowe wystąpienie klasy formatowania niestandardowego.  
  
2. Wywołaj <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metoda formatowania, niestandardowy obiekt formatowania formatowania specyfikator przekazywania (lub <xref:System.String.Empty?displayProperty=nameWithType>, jeśli nie jest on używany) oraz wartości numerycznych do sformatowania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano dostawcy niestandardowego formatu liczb, o nazwie `TelephoneFormatter` Konwertuje liczbę, która reprezentuje numer telefonu w Stanach Zjednoczonych, jego format NANP lub E.123. Metoda obsługuje dwa specyfikatorów formatu "N" (której dane wyjściowe są w formacie NANP) i "I" (która generuje formacie międzynarodowym E.123).  
  
 [!code-csharp[Formatting.HowTo.NumericValue#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#1)]
 [!code-vb[Formatting.HowTo.NumericValue#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#1)]  
  
 Dostawcy niestandardowego formatu liczb, mogą być używane tylko z <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metody. Przeciążenia metody formatowanie liczb (takie jak `ToString`), ma parametr typu <xref:System.IFormatProvider> wszystkie przekazać <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementacji <xref:System.Type> obiekt, który reprezentuje <xref:System.Globalization.NumberFormatInfo> typu. W zamian spełniają oczekiwane metody, aby zwrócić <xref:System.Globalization.NumberFormatInfo> obiektu. Jeśli nie, dostawcy niestandardowego formatu liczb jest ignorowana, a <xref:System.Globalization.NumberFormatInfo> obiekt bieżącej kultury jest używane w tym miejscu. W tym przykładzie `TelephoneFormatter.GetFormat` obsługiwała możliwość, że może być niewłaściwie przekazywane na liczbowy, metoda formatowania, sprawdzając parametru metody i zwracanie `null` Jeśli termin reprezentuje typ inny niż <xref:System.ICustomFormatter>.  
  
 Jeśli dostawcy niestandardowego formatu liczb obsługuje zestaw specyfikatorów formatu, upewnij się, zapewniasz zachowanie domyślne, jeśli nie dostarczono żadnych specyfikatora formatu w elemencie formatu, używane w <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> wywołania metody. W tym przykładzie "N" to domyślny specyfikator formatu. Dzięki temu liczby są konwertowane na numer telefonu sformatowane, zapewniając specyfikator formatu jawnego. W poniższym przykładzie pokazano wywołanie metody.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#2)]
 [!code-vb[Formatting.HowTo.NumericValue#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#2)]  
  
 Ale mogą również wystąpić, jeśli występuje nie specyfikatora formatu konwersji. W poniższym przykładzie pokazano wywołanie metody.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#3)]
 [!code-vb[Formatting.HowTo.NumericValue#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#3)]  
  
 Jeśli specyfikator formatu nie domyślny jest zdefiniowany, implementacja <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> metoda powinna zawierać następujący kod, tak że .NET umożliwia formatowanie kodu nie obsługuje.  
  
 [!code-csharp[System.ICustomFormatter.Format#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.ICustomFormatter.Format/cs/format.cs#1)]
 [!code-vb[System.ICustomFormatter.Format#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.ICustomFormatter.Format/vb/Format.vb#1)]  
  
 W tym przykładzie metoda, która implementuje <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> ma służyć jako metoda wywołania zwrotnego dla <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metody. W związku z tym, sprawdza, czy `formatProvider` parametru do określenia, czy zawiera on odwołanie do bieżącego `TelephoneFormatter` obiektu. Jednak metoda może być wywoływana bezpośrednio z kodu. W takim przypadku można użyć `formatProvider` parametru do podania <xref:System.Globalization.CultureInfo> lub <xref:System.Globalization.NumberFormatInfo> obiekt, który dostarcza informacje o formatowaniu specyficzne dla kultury.  
  
## <a name="see-also"></a>Zobacz także

- [Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)
