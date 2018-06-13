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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9800f1b1ec8fbb0eaf91611895aaf9d45629fae0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575827"
---
# <a name="how-to-define-and-use-custom-numeric-format-providers"></a>Porady: definiowanie i użycie niestandardowych dostawców formatu liczbowego
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Zapewnia szeroką gamę kontrolę nad reprezentację ciągu wartości liczbowych. Format wartości liczbowych dostosowywania obsługuje następujące funkcje:  
  
-   Standardowe ciągi formatujące liczb, które zapewniają zestaw wstępnie zdefiniowanych formatów Konwertowanie liczb ich reprezentacji ciągu. Mogą być używane z dowolnego liczbowe formatowania metody, takie jak <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>, która ma `format` parametru. Aby uzyskać więcej informacji, zobacz [standardowe ciągi formatu liczbowego](../../../docs/standard/base-types/standard-numeric-format-strings.md).  
  
-   Niestandardowe ciągi formatujące liczb, które udostępniają zestaw symboli, które można łączyć, aby zdefiniować specyfikatory niestandardowego formatu liczbowego. Można można również używać razem żadnych formatowanie metody, takie jak liczbowe <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>, która ma `format` parametru. Aby uzyskać więcej informacji, zobacz [niestandardowe ciągi formatów liczbowych](../../../docs/standard/base-types/custom-numeric-format-strings.md).  
  
-   Niestandardowe <xref:System.Globalization.CultureInfo> lub <xref:System.Globalization.NumberFormatInfo> obiektów, które zdefiniować symbole i sformatować wzorce służącego do wyświetlania reprezentacji ciągu wartości liczbowych. Mogą być używane z dowolnego liczbowe formatowania metody, takie jak <xref:System.Int32.ToString%2A>, która ma `provider` parametru. Zazwyczaj `provider` parametr jest używany do określenia, formatowanie specyficzne dla kultury.  
  
 W niektórych przypadkach (na przykład kiedy aplikacja musi zawierać numer konta sformatowane, numer identyfikacyjny lub kod pocztowy) tych trzech metod nie mają zastosowania. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Również umożliwia zdefiniowanie formatowania obiekt, który nie jest ani <xref:System.Globalization.CultureInfo> ani <xref:System.Globalization.NumberFormatInfo> obiektem, aby określić sposób formatowania wartości numerycznej. Ten temat zawiera instrukcje krok po kroku dotyczące implementowania takiego obiektu i zawiera przykładowy formatów numerów telefonów.  
  
### <a name="to-define-a-custom-format-provider"></a>Aby zdefiniować dostawcy formatu niestandardowego  
  
1.  Definiowanie klasy, która implementuje <xref:System.IFormatProvider> i <xref:System.ICustomFormatter> interfejsów.  
  
2.  Implementowanie <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metody. <xref:System.IFormatProvider.GetFormat%2A> jest to metoda wywołania zwrotnego który formatowania — metoda (takich jak <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> — metoda) wywołuje można pobrać obiektu, który są odpowiedzialne za wykonywanie formatowania niestandardowego. Typowa implementacja <xref:System.IFormatProvider.GetFormat%2A> wykonuje następujące czynności:  
  
    1.  Określa, czy <xref:System.Type> przekazano obiekt jako metoda reprezentuje parametr <xref:System.ICustomFormatter> interfejsu.  
  
    2.  Jeśli parametr reprezentują <xref:System.ICustomFormatter> interfejsu <xref:System.IFormatProvider.GetFormat%2A> zwraca obiekt, który implementuje <xref:System.ICustomFormatter> interfejs, który jest odpowiedzialny za zapewnienie formatowania niestandardowego. Zazwyczaj niestandardowego obiektu formatowania zwraca siebie.  
  
    3.  Jeśli parametr nie reprezentuje <xref:System.ICustomFormatter> interfejsu <xref:System.IFormatProvider.GetFormat%2A> zwraca `null`.  
  
3.  Implementowanie <xref:System.ICustomFormatter.Format%2A> metody. Ta metoda jest wywoływana przez <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> — metoda i jest odpowiedzialny za zwrócenie reprezentację liczby. Implementacja metody zwykle obejmuje następujące czynności:  
  
    1.  Opcjonalnie, upewnij się, że metoda legalnie mają na celu dostarczenie usług formatowania, sprawdzając `provider` parametru. Dla obiektów implementujących zarówno formatowania <xref:System.IFormatProvider> i <xref:System.ICustomFormatter>, proces ten obejmuje testowanie `provider` parametru do porównania z bieżącym obiektem formatowania.  
  
    2.  Ustal, czy obiekt formatowania powinna obsługiwać specyfikatorów formatu niestandardowego. (Na przykład specyfikator formatu "N" może wskazywać, że numer telefonu USA powinny być danymi wyjściowymi w formacie NANP, i "I" może wskazywać danych wyjściowych w formacie ITU-T E.123 zalecenie.) Jeśli używane są specyfikatory formatu, metoda powinna obsługiwać specyfikator formatu określonego. Jest przekazywany do metody w `format` parametru. Jeśli nie specyfikator jest obecna, wartość `format` parametr jest <xref:System.String.Empty?displayProperty=nameWithType>.  
  
    3.  Pobierz wartość liczbową przekazywany do metody jako `arg` parametru. Wykonaj, niezależnie od manipulacje są wymagane do konwertowania do reprezentacji ciągu.  
  
    4.  Zwraca reprezentację ciągu `arg` parametru.  
  
### <a name="to-use-a-custom-numeric-formatting-object"></a>Aby użyć niestandardowego obiektu formatowanie liczbowe  
  
1.  Utwórz nowe wystąpienie klasy niestandardowej formatowania.  
  
2.  Wywołanie <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> formatowanie metody, niestandardowy obiekt formatowania formatowania specyfikator przekazywania (lub <xref:System.String.Empty?displayProperty=nameWithType>, jeśli nie jest on używany) i być sformatowana wartość liczbowa.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano dostawcy niestandardowego formatu liczbowego o nazwie `TelephoneFormatter` Konwertuje liczbę reprezentującą Amerykański numer telefonu do formatu NANP lub E.123. Metoda obsługuje dwóch specyfikatorów formatu "N" (która danych wyjściowych w formacie NANP) i "I" (która generuje format międzynarodowy E.123).  
  
 [!code-csharp[Formatting.HowTo.NumericValue#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#1)]
 [!code-vb[Formatting.HowTo.NumericValue#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#1)]  
  
 Dostawcy niestandardowego formatu liczbowego można używać tylko z <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metody. Przeciążeń metody formatowanie liczbowe (takich jak `ToString`) zawierających parametr typu <xref:System.IFormatProvider> wszystkie przekazać <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementacji <xref:System.Type> obiekt, który reprezentuje <xref:System.Globalization.NumberFormatInfo> typu. W zamian oczekiwane metodę, aby zwrócić <xref:System.Globalization.NumberFormatInfo> obiektu. Jeśli nie, dostawcy niestandardowego formatu liczbowego jest ignorowana i <xref:System.Globalization.NumberFormatInfo> obiektu dla bieżącej kultury jest używany w jego miejscu. W tym przykładzie `TelephoneFormatter.GetFormat` metoda obsługuje możliwości, który może być niewłaściwie przekazany do liczbową formatowania metody, sprawdzając parametru metody i zwracanie `null` Jeśli reprezentuje typ innych niż <xref:System.ICustomFormatter>.  
  
 Jeśli dostawcy niestandardowego formatu liczbowego obsługuje zestaw specyfikatory formatu, upewnij się, podaj zachowanie domyślne, jeśli nie specyfikator formatu nie jest dostarczony w elemencie format używany w <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> wywołania metody. W tym przykładzie "N" jest domyślna specyfikator formatu. Dzięki temu numer ma zostać przekonwertowane na numer telefonu sformatowany zapewniając specyfikator formatu jawnego. Poniższy przykład przedstawia wywołania metody.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#2)]
 [!code-vb[Formatting.HowTo.NumericValue#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#2)]  
  
 Ale pozwala także konwersja wystąpić, jeśli nie specyfikator formatu jest obecny. Poniższy przykład przedstawia wywołania metody.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#3)]
 [!code-vb[Formatting.HowTo.NumericValue#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#3)]  
  
 Jeśli zdefiniowano specyfikator formatu nie domyślnej, implementacji <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> — metoda powinna zawierać kodu podobne do poniższych, tak że .NET zapewniają formatowania kodu nie obsługuje.  
  
 [!code-csharp[System.ICustomFormatter.Format#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.ICustomFormatter.Format/cs/format.cs#1)]
 [!code-vb[System.ICustomFormatter.Format#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.ICustomFormatter.Format/vb/Format.vb#1)]  
  
 W tym przykładzie metoda, która implementuje <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> ma służyć jako metoda wywołania zwrotnego dla <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metody. W związku z tym sprawdza `formatProvider` parametr, aby określić, czy zawiera on odwołanie do bieżącego `TelephoneFormatter` obiektu. Jednak metoda również można wywołać bezpośrednio z kodu. W takim przypadku można użyć `formatProvider` parametr, aby zapewnić <xref:System.Globalization.CultureInfo> lub <xref:System.Globalization.NumberFormatInfo> obiektu, który dostarcza informacje dotyczące formatowania specyficzne dla kultury.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skompiluj kod w wierszu polecenia za pomocą csc.exe lub vb.exe. Aby skompilować kod w programie Visual Studio, umieść ją w szablonu projektu aplikacji konsoli.  
  
## <a name="see-also"></a>Zobacz też  
 [Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)
