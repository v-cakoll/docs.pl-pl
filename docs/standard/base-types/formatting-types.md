---
title: Formatowanie typów w programie .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data formatting [.NET Framework]
- dates [.NET Framework], formatting
- date formatting [.NET Framework]
- number formatting [.NET Framework]
- ToString method
- custom cultural settings [.NET Framework]
- numbers [.NET Framework], formatting
- formatting strings [.NET Framework]
- time [.NET Framework], formatting
- currency [.NET Framework], formatting
- types [.NET Framework], formatting
- format specifiers [.NET Framework]
- times [.NET Framework], formatting
- culture [.NET Framework], formatting
- formatting [.NET Framework], types supported
- base types [.NET Framework], formatting
- custom formatting [.NET Framework]
- strings [.NET Framework], formatting
ms.assetid: 0d1364da-5b30-4d42-8e6b-03378343343f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82dc1e36ae5a0eede7099c8e13ac9a2393bbb904
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253980"
---
# <a name="formatting-types-in-net"></a>Formatowanie typów w programie .NET

Formatowanie to proces konwersji wystąpienia klasy, struktury lub wartości wyliczenia na reprezentację ciągu, często tak, aby otrzymany ciąg można było wyświetlić użytkownikom lub deserializacji w celu przywrócenia oryginalnego typu danych. Ta konwersja może stanowić wiele wyzwań:

- Sposób, w jaki są przechowywane wartości wewnętrznie, niekoniecznie odzwierciedla sposób, w jaki użytkownicy chcą je wyświetlić. Na przykład numer telefonu może być przechowywany w postaci 8009999999, który nie jest przyjazny dla użytkownika. Zamiast tego powinna być wyświetlana jako 800-999-9999. Zapoznaj się z sekcją [ciągów formatów niestandardowych](#customStrings) , aby zapoznać się z przykładem, który formatuje liczbę w ten sposób.

- Czasami Konwersja obiektu na jego reprezentację w postaci ciągu nie jest intuicyjna. Na przykład nie jest jasne, jak powinna zostać wyświetlona Reprezentacja ciągu obiektu temperatury lub osoby. Aby zapoznać się z przykładem, który formatuje obiekt temperatury na różne sposoby, zobacz sekcję [ciągi formatu standardowego](#standardStrings) .

- Wartości często wymagają formatowania z uwzględnieniem kultury. Na przykład w aplikacji, która używa liczb do odzwierciedlenia wartości pieniężnych, ciągi numeryczne powinny zawierać symbol waluty bieżącej kultury, separator grupy (który w większości kultur jest separatorem tysięcy) i symbol dziesiętny. Aby zapoznać się z przykładem, zobacz [Formatowanie z uwzględnieniem kultury przy użyciu dostawców formatów i sekcji interfejsu IFormatProvider](#FormatProviders) .

- Aplikacja może mieć taką samą wartość na różne sposoby. Na przykład aplikacja może reprezentować element członkowski wyliczenia, wyświetlając ciąg reprezentujący jego nazwę lub wyświetlając jego wartość podstawową. Aby zapoznać się z przykładem formatowania elementu członkowskiego <xref:System.DayOfWeek> wyliczenia na różne sposoby, zobacz sekcję [ciągi formatu standardowego](#standardStrings) .

> [!NOTE]
> Formatowanie konwertuje wartość typu na reprezentację w postaci ciągu. Analizowanie jest odwrotnością formatowania. Operacja analizowania tworzy wystąpienie typu danych z jego reprezentacji w postaci ciągu. Aby uzyskać informacje o konwertowaniu ciągów na inne typy danych, zobacz [Analizowanie ciągów](../../../docs/standard/base-types/parsing-strings.md).

Platforma .NET zapewnia obsługę formatowania zaawansowanego, która umożliwia deweloperom rozwiązywanie tych wymagań.

To omówienie zawiera następujące sekcje:

- [Formatowanie w programie .NET](#NetFormatting)

- [Formatowanie domyślne przy użyciu metody ToString](#DefaultToString)

- [Zastępowanie metody ToString](#OverrideToString)

- [Metody ToString i ciągi formatujące](#FormatStrings)

  - [Ciągi formatu standardowego](#standardStrings)

  - [Niestandardowe ciągi formatujące](#customStrings)

  - [Ciągi formatujące i typy bibliotek klas .NET](#stringRef)

- [Uwzględnianie kulturowe formatowania przy użyciu dostawców formatów i interfejsu IFormatProvider](#FormatProviders)

  - [Czułe na kulturę formatowanie wartości liczbowych](#numericCulture)

  - [Czułe na kulturowe formatowanie wartości daty i godziny](#dateCulture)

- [Interfejs IFormattable](#IFormattable)

- [Złożone formatowanie](#CompositeFormatting)

- [Niestandardowe formatowanie za pomocą ICustomFormatter](#Custom)

- [Tematy pokrewne](#RelatedTopics)

- [Dokumentacja](#Reference)

<a name="NetFormatting"></a>

## <a name="formatting-in-net"></a>Formatowanie w programie .NET

Podstawowym mechanizmem formatowania jest domyślna implementacja <xref:System.Object.ToString%2A?displayProperty=nameWithType> metody, która została omówiona w [domyślnym formatowaniu przy użyciu metody ToString](#DefaultToString) w dalszej części tego tematu. Jednak platforma .NET oferuje kilka sposobów modyfikowania i zwiększania obsługi formatowania domyślnego. Należą do nich między innymi:

- Zastępowanie <xref:System.Object.ToString%2A?displayProperty=nameWithType> metody, aby zdefiniować niestandardową reprezentację obiektu w postaci ciągu. Aby uzyskać więcej informacji, zobacz sekcję [Zastępowanie metody ToString](#OverrideToString) w dalszej części tego tematu.

- Definiowanie specyfikatorów formatu, które umożliwiają reprezentację ciągu obiektu w celu przejęcia wielu formularzy. Na przykład, specyfikator formatu "X" w poniższej instrukcji konwertuje liczbę całkowitą na ciąg reprezentujący wartość szesnastkową.

     [!code-csharp[Conceptual.Formatting.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#3)]
     [!code-vb[Conceptual.Formatting.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#3)]

     Aby uzyskać więcej informacji na temat specyfikatorów formatu, zobacz sekcję [metody ToString i ciągi formatu](#FormatStrings) .

- Korzystanie z dostawców formatu w celu wykorzystania Konwencji formatowania określonej kultury. Na przykład poniższa instrukcja wyświetla wartość waluty przy użyciu Konwencji formatowania kultury en-US.

     [!code-csharp[Conceptual.Formatting.Overview#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#10)]
     [!code-vb[Conceptual.Formatting.Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#10)]

     Aby uzyskać więcej informacji o formatowaniu z dostawcami formatu, zobacz sekcję about [providers and the IFormatProvider Interface (interfejs](#FormatProviders) ).

- Implementacja interfejsu do obsługi obydwu konwersji ciągów <xref:System.Convert> z klasą i formatowaniem złożonym. <xref:System.IFormattable> Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [interfejsu IFormattable](#IFormattable) .

- Użycie formatowania złożonego do osadzenia ciągu reprezentującego wartość w większym ciągu. Aby uzyskać więcej informacji, zobacz sekcję [formatowanie złożone](#CompositeFormatting) .

- <xref:System.ICustomFormatter> Implementowanie <xref:System.IFormatProvider> i zapewnianie kompletnego rozwiązania do formatowania niestandardowego. Aby uzyskać więcej informacji, zobacz sekcję [formatowanie niestandardowe z ICustomFormatter](#Custom) .

Poniższe sekcje przedstawiają te metody konwertowania obiektu na jego reprezentację w postaci ciągu.

<a name="DefaultToString"></a>

## <a name="default-formatting-using-the-tostring-method"></a>Domyślne formatowania przy użyciu metody ToString

Każdy typ pochodzący od <xref:System.Object?displayProperty=nameWithType> automatycznie dziedziczy `ToString` metodę bez parametrów, która domyślnie zwraca nazwę typu. Poniższy przykład ilustruje metodę domyślną `ToString` . Definiuje klasę o nazwie `Automobile` , która nie ma implementacji. Po utworzeniu wystąpienia klasy i `ToString` wywołaniu metody jest wyświetlana nazwa typu. Należy zauważyć, `ToString` że metoda nie jest jawnie wywoływana w przykładzie. Metoda niejawnie wywołuje metodę obiektu, do którego jest przenoszona jako argument. `ToString` <xref:System.Console.WriteLine%28System.Object%29?displayProperty=nameWithType>

[!code-csharp[Conceptual.Formatting.Overview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/default1.cs#1)]
[!code-vb[Conceptual.Formatting.Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/default1.vb#1)]

> [!WARNING]
> Począwszy od <xref:Windows.Foundation.IStringable> , środowisko wykonawcze systemu Windows zawiera interfejs o pojedynczej metodzie [IStringable. ToString](xref:Windows.Foundation.IStringable.ToString%2A), która zapewnia obsługę formatowania domyślnego. [!INCLUDE[win81](../../../includes/win81-md.md)] Jednak zaleca się, aby typy zarządzane nie implementują `IStringable` interfejsu. Aby uzyskać więcej informacji, zobacz sekcję "środowisko wykonawcze systemu Windows i `IStringable` interfejs" <xref:System.Object.ToString%2A?displayProperty=nameWithType> na stronie odniesienia.

Ponieważ wszystkie typy inne niż interfejsy są wyprowadzane <xref:System.Object>z, ta funkcja jest automatycznie dostarczana do niestandardowych klas lub struktur. Jednak funkcje oferowane przez metodę domyślną `ToString` są ograniczone: Chociaż identyfikuje typ, nie zawiera on informacji o wystąpieniu typu. Aby podać ciąg reprezentujący obiekt, który zawiera informacje o tym obiekcie, należy zastąpić `ToString` metodę.

> [!NOTE]
> Struktury dziedziczą <xref:System.ValueType>z, które z kolei są wyprowadzane z. <xref:System.Object> Chociaż <xref:System.ValueType> zastąpienia<xref:System.Object.ToString%2A?displayProperty=nameWithType>, jego implementacja jest taka sama.

<a name="OverrideToString"></a>

## <a name="overriding-the-tostring-method"></a>Zastąpienie metody ToString

Wyświetlanie nazwy typu jest często ograniczonym zastosowaniem i nie pozwala na odbiorców typów odróżnienia jednego wystąpienia od drugiego. Można jednak zastąpić `ToString` metodę, aby zapewnić bardziej przydatną reprezentację wartości obiektu. Poniższy przykład definiuje `Temperature` obiekt i zastępuje jego `ToString` metodę, aby wyświetlić temperaturę w stopniach Celsjusza.

[!code-csharp[Conceptual.Formatting.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/overrides1.cs#2)]
[!code-vb[Conceptual.Formatting.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/overrides1.vb#2)]

W programie .NET `ToString` Metoda każdego typu wartości pierwotnej została zastąpiona, aby wyświetlić wartość obiektu zamiast jego nazwy. W poniższej tabeli przedstawiono przesłonięcie dla każdego typu pierwotnego. Należy zauważyć, że większość zastąpionych metod wywołuje inne Przeciążenie `ToString` metody i przekazuje ją specyfikator formatu "G", który definiuje format ogólny dla jego typu, <xref:System.IFormatProvider> a obiekt, który reprezentuje bieżącą kulturę.

|Typ|Zastąpienie metody ToString|
|----------|-----------------------|
|<xref:System.Boolean>|Zwraca albo <xref:System.Boolean.TrueString?displayProperty=nameWithType>. <xref:System.Boolean.FalseString?displayProperty=nameWithType>|
|<xref:System.Byte>|Wywołuje `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` metodę<xref:System.Byte> formatowania wartości dla bieżącej kultury.|
|<xref:System.Char>|Zwraca znak jako ciąg.|
|<xref:System.DateTime>|Wywołuje `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` metodę formatowania wartości daty i godziny dla bieżącej kultury.|
|<xref:System.Decimal>|Wywołuje `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` metodę<xref:System.Decimal> formatowania wartości dla bieżącej kultury.|
|<xref:System.Double>|Wywołuje `Double.ToString("G", NumberFormatInfo.CurrentInfo)` metodę<xref:System.Double> formatowania wartości dla bieżącej kultury.|
|<xref:System.Int16>|Wywołuje `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` metodę<xref:System.Int16> formatowania wartości dla bieżącej kultury.|
|<xref:System.Int32>|Wywołuje `Int32.ToString("G", NumberFormatInfo.CurrentInfo)` metodę<xref:System.Int32> formatowania wartości dla bieżącej kultury.|
|<xref:System.Int64>|Wywołuje `Int64.ToString("G", NumberFormatInfo.CurrentInfo)` metodę<xref:System.Int64> formatowania wartości dla bieżącej kultury.|
|<xref:System.SByte>|Wywołuje `SByte.ToString("G", NumberFormatInfo.CurrentInfo)` metodę<xref:System.SByte> formatowania wartości dla bieżącej kultury.|
|<xref:System.Single>|Wywołuje `Single.ToString("G", NumberFormatInfo.CurrentInfo)` metodę<xref:System.Single> formatowania wartości dla bieżącej kultury.|
|<xref:System.UInt16>|Wywołuje `UInt16.ToString("G", NumberFormatInfo.CurrentInfo)` metodę<xref:System.UInt16> formatowania wartości dla bieżącej kultury.|
|<xref:System.UInt32>|Wywołuje `UInt32.ToString("G", NumberFormatInfo.CurrentInfo)` metodę<xref:System.UInt32> formatowania wartości dla bieżącej kultury.|
|<xref:System.UInt64>|Wywołuje `UInt64.ToString("G", NumberFormatInfo.CurrentInfo)` metodę<xref:System.UInt64> formatowania wartości dla bieżącej kultury.|

<a name="FormatStrings"></a>

## <a name="the-tostring-method-and-format-strings"></a>Metoda ToString i ciągi formatujące

Opieranie się na domyślnej `ToString` metodzie lub `ToString` zastępowaniu jest odpowiednie, gdy obiekt ma pojedynczą reprezentację ciągu. Jednak wartość obiektu często ma wiele reprezentacji. Na przykład temperatura może być wyrażona w stopniach Fahrenheita, stopniach Celsjusza i kelwinach. Podobnie wartość całkowita 10 może być reprezentowana na wiele sposobów, w tym 10, 10,0, 1.0 E01 lub $10,00.

Aby włączyć pojedynczą wartość, aby zawierała wiele reprezentacji ciągów, platforma .NET używa ciągów formatu. Ciąg formatu jest ciągiem zawierającym co najmniej jeden wstępnie zdefiniowany specyfikator formatu, które są pojedynczymi znakami lub grupami znaków, które definiują `ToString` sposób formatowania danych wyjściowych przez metodę. Ciąg formatu jest następnie przenoszona jako parametr do `ToString` metody obiektu i określa, jak będzie wyglądać ciąg reprezentujący wartość tego obiektu.

Wszystkie typy liczbowe, typy daty i godziny oraz typy wyliczeniowe w programie .NET obsługują wstępnie zdefiniowany zestaw specyfikatorów formatu. Można również użyć ciągów formatowania do zdefiniowania wielu reprezentacji ciągów dla typów danych zdefiniowanych przez aplikację.

<a name="standardStrings"></a>

### <a name="standard-format-strings"></a>Standardowe ciągi formatujące

Ciąg formatu standardowego zawiera pojedynczy specyfikator formatu, który jest znakiem alfabetycznym, który definiuje ciąg reprezentujący obiekt, do którego jest stosowany, wraz z opcjonalnym specyfikatorem dokładności, który ma wpływ na liczbę cyfr wyświetlanych w Ciąg wynikowy. Jeśli specyfikator dokładności zostanie pominięty lub nie jest obsługiwany, specyfikator formatu standardowego jest równoznaczny z ciągiem formatu standardowego.

Platforma .NET definiuje zestaw specyfikatorów formatu standardowego dla wszystkich typów liczbowych, wszystkich typów daty i godziny oraz wszystkich typów wyliczeniowych. Na przykład każda z tych kategorii obsługuje specyfikator formatu standardowego "G", który definiuje ogólną reprezentację ciągu wartości tego typu.

Ciągi formatu standardowego dla typów wyliczeniowych bezpośrednio kontrolują reprezentację ciągu wartości. Ciągi formatu przesłane do `ToString` metody wartości wyliczenia określają, czy wartość jest wyświetlana przy użyciu nazwy ciągu (specyfikatory formatu "G" i "F"), jej podstawowej wartości całkowitej (specyfikator formatu "D") lub jej wartości szesnastkowej ("X" "specyfikator formatu). Poniższy przykład ilustruje użycie ciągów formatu standardowego do formatowania <xref:System.DayOfWeek> wartości wyliczenia.

[!code-csharp[Conceptual.Formatting.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/standard1.cs#4)]
[!code-vb[Conceptual.Formatting.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/standard1.vb#4)]

Aby uzyskać informacje na temat ciągów formatu wyliczenia, zobacz [ciągi formatujące Wyliczenie](../../../docs/standard/base-types/enumeration-format-strings.md).

Ciągi formatu standardowego dla typów liczbowych zwykle definiują ciąg wynikowy, którego dokładny wygląd jest kontrolowany przez jedną lub więcej wartości właściwości. Na przykład specyfikator formatu "C" formatuje liczbę jako wartość walutową. Po wywołaniu `ToString` metody ze specyfikatorem formatu "C" jako jedynego parametru, następujące wartości właściwości z <xref:System.Globalization.NumberFormatInfo> obiektu bieżącej kultury są używane do definiowania ciągu reprezentującego wartość liczbową:

- <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A> Właściwość, która określa symbol waluty bieżącej kultury.

- Właściwość <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> lub<xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A> , która zwraca liczbę całkowitą, która określa następujące elementy:

  - Położenie symbolu waluty.

  - Czy wartości ujemne są wskazywane przez wiodący znak ujemny, końcowy znak minus lub nawiasy.

  - Określa, czy spacja jest wyświetlana między wartością liczbową, a symbolem waluty.

- <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A> Właściwość, która definiuje liczbę cyfr dziesiętnych w ciągu wynikowym.

- <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A> Właściwość, która definiuje symbol separatora dziesiętnego w ciągu wynikowym.

- <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A> Właściwość, która definiuje symbol separatora grupy.

- <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A> Właściwość, która definiuje liczbę cyfr w każdej grupie po lewej stronie wartości dziesiętnej.

- <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> Właściwość, która określa znak ujemny używany w ciągu wynikowym, jeśli nawiasy nie są używane do wskazania wartości ujemnych.

Ponadto ciągi formatu liczbowego mogą zawierać specyfikator dokładności. Znaczenie tego specyfikatora zależy od ciągu formatu, z którym jest używany, ale zazwyczaj wskazuje całkowitą liczbę cyfr lub liczbę cyfr, które powinny być wyświetlane w ciągu wynikowym. Na przykład w poniższym przykładzie użyto standardowego ciągu numerycznego "X4" i specyfikatora dokładności, aby utworzyć wartość ciągu, która ma cztery cyfry szesnastkowe.

[!code-csharp[Conceptual.Formatting.Overview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/precisionspecifier1.cs#6)]
[!code-vb[Conceptual.Formatting.Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/precisionspecifier1.vb#6)]

Aby uzyskać więcej informacji na temat standardowych ciągów formatowania liczbowego, zobacz [Standardowe ciągi formatujące](../../../docs/standard/base-types/standard-numeric-format-strings.md).

Ciągi formatu standardowego dla wartości daty i godziny to aliasy dla ciągów formatów niestandardowych przechowywanych przez określoną <xref:System.Globalization.DateTimeFormatInfo> właściwość. Na przykład wywołanie `ToString` metody wartości daty i godziny z specyfikatorem formatu "D" powoduje wyświetlenie daty i godziny przy użyciu niestandardowego ciągu formatu przechowywanego we <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> właściwości bieżącej kultury. (Aby uzyskać więcej informacji na temat ciągów formatu niestandardowego, zobacz [następną sekcję](#customStrings)). Poniższy przykład ilustruje tę relację.

[!code-csharp[Conceptual.Formatting.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/alias1.cs#5)]
[!code-vb[Conceptual.Formatting.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/alias1.vb#5)]

Aby uzyskać więcej informacji na temat standardowych ciągów formatu daty i godziny, zobacz [ciągi standardowych formatów daty i godziny](../../../docs/standard/base-types/standard-date-and-time-format-strings.md).

Za pomocą ciągów formatu standardowego można także zdefiniować ciąg reprezentujący obiekt zdefiniowany przez aplikację, który jest generowany przez `ToString(String)` metodę obiektu. Można zdefiniować określone specyfikatory formatu standardowego, które obsługuje dany obiekt, i można określić, czy są one rozróżniane wielkości liter czy nie są rozróżniane wielkości liter. Implementacja `ToString(String)` metody powinna obsługiwać następujące elementy:

- Specyfikator formatu "G", który reprezentuje niestandardowy lub typowy format obiektu. Przeciążenie bez parametrów `ToString` metody obiektu powinno wywołać jego `ToString(String)` Przeciążenie i przekazać do niego ciąg formatu standardowego "G".

- Obsługa specyfikatora formatu, który jest równy odwołaniu o wartości null (`Nothing` w Visual Basic). Specyfikator formatu, który jest równy odwołaniu o wartości null, powinien być uważany za równoważny specyfikatorowi formatu "G".

Na przykład `Temperature` Klasa może wewnętrznie przechowywać temperaturę w stopniach Celsjusza i używać specyfikatorów formatu do reprezentowania wartości `Temperature` obiektu w stopniach Celsjusza, stopniach Fahrenheita i kelwinach. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.Formatting.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/appstandard1.cs#7)]
[!code-vb[Conceptual.Formatting.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/appstandard1.vb#7)]

<a name="customStrings"></a>

### <a name="custom-format-strings"></a>Niestandardowe ciągi formatujące

Oprócz standardowych ciągów formatu, .NET definiuje niestandardowe ciągi formatu dla wartości liczbowych i wartości daty i godziny. Niestandardowy ciąg formatu składa się z co najmniej jednego specyfikatora formatu niestandardowego, który definiuje reprezentację ciągu wartości. Na przykład niestandardowy ciąg formatu daty i godziny "rrrr/mm/dd hh: mm: SS. FFFF t ZZZ" konwertuje datę na reprezentację ciągu w postaci "2008/11/15 07:45:00.0000 P-08:00" dla kultury en-US. Podobnie ciąg formatu niestandardowego "0000" konwertuje wartość całkowitą 12 na "0012". Aby zapoznać się z pełną listą niestandardowych ciągów formatujących, zobacz [Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) oraz [Niestandardowe ciągi formatujące liczbowe](../../../docs/standard/base-types/custom-numeric-format-strings.md).

Jeśli ciąg formatu składa się z pojedynczego specyfikatora formatu niestandardowego, specyfikator formatu powinien być poprzedzony wartością procentową (%) symbol, aby uniknąć nieporozumień ze specyfikatorem formatu standardowego. Poniższy przykład używa specyfikatora formatu niestandardowego "M", aby wyświetlić jedną cyfrę lub dwucyfrową liczbę miesięcy w danym dniu.

[!code-csharp[Conceptual.Formatting.Overview#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/singlecustom1.cs#8)]
[!code-vb[Conceptual.Formatting.Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/singlecustom1.vb#8)]

Wiele ciągów formatu standardowego dla wartości daty i godziny to aliasy dla ciągów formatów niestandardowych, które są zdefiniowane przez właściwości <xref:System.Globalization.DateTimeFormatInfo> obiektu. Niestandardowe ciągi formatujące oferują również znaczną elastyczność w dostarczaniu formatowania zdefiniowanego przez aplikację dla wartości numerycznych lub wartości daty i godziny. Można zdefiniować własne niestandardowe ciągi wynikowe dla wartości liczbowych i wartości daty i godziny, łącząc wiele niestandardowych specyfikatorów formatu w jeden ciąg formatu niestandardowego. W poniższym przykładzie zdefiniowano ciąg formatu niestandardowego, który wyświetla dzień tygodnia w nawiasach po nazwie miesiąca, dzień i roku.

[!code-csharp[Conceptual.Formatting.Overview#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/custom1.cs#9)]
[!code-vb[Conceptual.Formatting.Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/custom1.vb#9)]

W poniższym przykładzie zdefiniowano ciąg formatu niestandardowego, który wyświetla <xref:System.Int64> wartość jako standardowy, 7-cyfrowy numer telefonu amerykańskiego wraz z numerem kierunkowym.

[!code-csharp[Conceptual.Formatting.Overview#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/telnumber1.cs#21)]
[!code-vb[Conceptual.Formatting.Overview#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/telnumber1.vb#21)]

Chociaż ciągi formatu standardowego mogą ogólnie obsłużyć większość potrzeb formatowania dla typów zdefiniowanych przez aplikację, można także zdefiniować specyfikatory formatu niestandardowego, aby sformatować typy.

<a name="stringRef"></a>

### <a name="format-strings-and-net-types"></a>Ciągi formatujące i typy .NET

Wszystkie typy liczbowe <xref:System.Byte>(czyli <xref:System.Single> ,,<xref:System.UInt64>,,,, ,<xref:System.UInt32>,, ,,i<xref:System.UInt16> <xref:System.Decimal> <xref:System.Double> <xref:System.Int16> <xref:System.Int32> <xref:System.Int64> <xref:System.SByte> <xref:System.Numerics.BigInteger>typy <xref:System.DateTime>), a także <xref:System.DateTimeOffset> <xref:System.Guid>typy wyliczeniowe,, ,iwszystkie,obsługująformatowanieciągówformatowania.<xref:System.TimeSpan> Informacje o określonych ciągach formatu obsługiwanych przez poszczególne typy można znaleźć w następujących tematach:

|Tytuł|Definicja|
|-----------|----------------|
|[Standardowe ciągi formatujące liczby](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Opisuje ciągi formatu standardowego, które tworzą często używane reprezentacje ciągów wartości liczbowych.|
|[Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Opisuje niestandardowe ciągi formatujące, które tworzą formaty specyficzne dla aplikacji dla wartości liczbowych.|
|[Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Opisuje ciągi formatu standardowego, które tworzą często używane reprezentacje <xref:System.DateTime> ciągu <xref:System.DateTimeOffset> i wartości.|
|[Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Opisuje niestandardowe ciągi formatujące, które tworzą formaty dla i <xref:System.DateTime> <xref:System.DateTimeOffset> wartości specyficzne dla aplikacji.|
|[Standardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Opisuje ciągi formatu standardowego, które tworzą często używane reprezentacje ciągów przedziałów czasu.|
|[Niestandardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Opisuje niestandardowe ciągi formatujące, które tworzą formaty specyficzne dla aplikacji dla przedziałów czasu.|
|[Ciągi formatujące wyliczenia](../../../docs/standard/base-types/enumeration-format-strings.md)|Opisuje ciągi formatu standardowego, które są używane do tworzenia reprezentacji ciągów wartości wyliczenia.|
|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|Opisuje ciągi formatu standardowego dla <xref:System.Guid> wartości.|

<a name="FormatProviders"></a>

## <a name="culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface"></a>Wrażliwość na ustawienia kulturowe — mechanizm formatowania i interfejs IFormatProvider

Chociaż specyfikatory formatu pozwalają dostosować formatowanie obiektów, generowanie znaczących reprezentacji obiektów często wymaga dodatkowych informacji o formatowaniu. Na przykład formatowanie liczby jako wartości walutowej przy użyciu standardowego ciągu formatu "C" lub niestandardowego ciągu formatu, takiego jak "$ #, #. 00" wymaga co najmniej informacji o poprawnym symbolu waluty, separatorze grup i separatorze dziesiętnym do dostępne do uwzględnienia w sformatowanym ciągu. W programie .NET te dodatkowe informacje o formatowaniu są udostępniane za <xref:System.IFormatProvider> pomocą interfejsu, który jest dostarczany jako parametr do jednego lub większej liczby przeciążeń `ToString` metody typów liczbowych i typów dat i godzin. <xref:System.IFormatProvider>implementacje są używane w programie .NET do obsługi formatowania specyficznego dla kultury. Poniższy przykład ilustruje sposób, w jaki ciąg reprezentujący obiekt ulega zmianie, gdy jest sformatowany przy <xref:System.IFormatProvider> użyciu trzech obiektów, które reprezentują różne kultury.

[!code-csharp[Conceptual.Formatting.Overview#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformatprovider1.cs#11)]
[!code-vb[Conceptual.Formatting.Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformatprovider1.vb#11)]

Interfejs zawiera jedną metodę, <xref:System.IFormatProvider.GetFormat%28System.Type%29>, która ma jeden parametr, który określa typ obiektu, który zawiera informacje o formatowaniu. <xref:System.IFormatProvider> Jeśli metoda może dostarczyć obiekt tego typu, zwraca go. W przeciwnym razie zwraca odwołanie o wartości null`Nothing` (w Visual Basic).

<xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType>jest metodą wywołania zwrotnego. Po wywołaniu `ToString` przeciążenia metody, która <xref:System.IFormatProvider> zawiera <xref:System.IFormatProvider.GetFormat%2A> parametr, <xref:System.IFormatProvider> wywołuje metodę tego obiektu. Metoda jest odpowiedzialna za zwracanie obiektu, który dostarcza niezbędne informacje o formatowaniu, jak określono przez `formatType` jego parametr, do `ToString` metody. <xref:System.IFormatProvider.GetFormat%2A>

Wiele metod formatowania lub konwersji ciągów zawiera parametr typu <xref:System.IFormatProvider>, ale w wielu przypadkach wartość parametru jest ignorowana, gdy wywoływana jest metoda. W poniższej tabeli wymieniono niektóre metody formatowania, które używają parametru i typu <xref:System.Type> obiektu, który przekazuje <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> do metody.

|Metoda|`formatType` Typ parametru|
|------------|------------------------------------|
|`ToString`Metoda typów liczbowych|<xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>|
|`ToString`Metoda typów daty i godziny|<xref:System.Globalization.DateTimeFormatInfo?displayProperty=nameWithType>|
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|

> [!NOTE]
> Metody typów liczbowych i daty i godziny są przeciążone, a tylko niektóre przeciążenia <xref:System.IFormatProvider> zawierają parametr. `ToString` Jeśli metoda nie ma parametru typu <xref:System.IFormatProvider>, zamiast niego zostanie przekazana obiekt, który jest zwracany <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> przez właściwość. Na przykład wywołanie metody domyślnej <xref:System.Int32.ToString?displayProperty=nameWithType> ostatecznie powoduje wywołanie metody, takie jak:. `Int32.ToString("G", System.Globalization.CultureInfo.CurrentCulture)`

Platforma .NET udostępnia trzy klasy, <xref:System.IFormatProvider>które implementują:

- <xref:System.Globalization.DateTimeFormatInfo>, Klasa, która zawiera informacje o formatowaniu dla wartości daty i godziny dla określonej kultury. Jego <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementacja zwraca wystąpienie samego siebie.

- <xref:System.Globalization.NumberFormatInfo>, Klasa, która zawiera informacje o formatowaniu liczb dla określonej kultury. Jego <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementacja zwraca wystąpienie samego siebie.

- <xref:System.Globalization.CultureInfo>. Jego <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementacja może zwrócić <xref:System.Globalization.NumberFormatInfo> obiekt, aby zapewnić informacje o formatowaniu <xref:System.Globalization.DateTimeFormatInfo> liczb lub obiekt, aby zapewnić informacje o formatowaniu dla wartości daty i godziny.

Możesz również zaimplementować własnego dostawcę formatu, aby zastąpić każdą z tych klas. Jednak <xref:System.IFormatProvider.GetFormat%2A> Metoda implementacji musi zwrócić obiekt typu wymienionego w poprzedniej tabeli, jeśli musi dostarczyć informacje o formatowaniu `ToString` do metody.

<a name="numericCulture"></a>

### <a name="culture-sensitive-formatting-of-numeric-values"></a>Wrażliwość na ustawienia kulturowe — formatowania wartości numerycznych

Domyślnie formatowanie wartości liczbowych jest zależne od kultury. Jeśli nie określisz kultury podczas wywoływania metody formatowania, używane są konwencje formatowania bieżącej kultury wątku. Jest to zilustrowane w poniższym przykładzie, który zmienia bieżącą kulturę wątku czterokrotnie, a następnie wywołuje <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> metodę. W każdym przypadku ciąg wynikowy odzwierciedla konwencje formatowania bieżącej kultury. Wynika to z faktu `ToString(String)` , że `ToString` metody i zawijają wywołania `ToString(String, IFormatProvider)` do poszczególnych metod typu liczbowego.

[!code-csharp[Conceptual.Formatting.Overview#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific3.cs#19)]
[!code-vb[Conceptual.Formatting.Overview#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific3.vb#19)]

Możesz również sformatować wartość numeryczną dla określonej kultury, wywołując `ToString` Przeciążenie, które `provider` ma parametr i przekazując go jedną z następujących czynności:

- <xref:System.Globalization.CultureInfo> Obiekt, który reprezentuje kulturę, której konwencje formatowania mają być używane. Jego <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> Metoda zwraca <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> wartość<xref:System.Globalization.NumberFormatInfo> właściwości, która jest obiektem, który zawiera informacje o formatowaniu specyficzne dla kultury dla wartości numerycznych.

- <xref:System.Globalization.NumberFormatInfo> Obiekt, który definiuje konwencje formatowania specyficzne dla kultury, które mają być używane. Jego <xref:System.Globalization.NumberFormatInfo.GetFormat%2A> Metoda zwraca wystąpienie samego siebie.

Poniższy przykład używa <xref:System.Globalization.NumberFormatInfo> obiektów, które reprezentują kultury angielskie (Stany Zjednoczone) i angielskie (Wielka Brytania) oraz kulturę neutralną w języku francuskim i rosyjskim do formatowania liczby zmiennoprzecinkowej.

[!code-csharp[Conceptual.Formatting.Overview#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific4.cs#20)]
[!code-vb[Conceptual.Formatting.Overview#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific4.vb#20)]

<a name="dateCulture"></a>

### <a name="culture-sensitive-formatting-of-date-and-time-values"></a>Wrażliwość na ustawienia kulturowe — formatowanie wartości daty i godziny

Domyślnie formatowanie wartości daty i godziny jest zależne od kultury. Jeśli nie określisz kultury podczas wywoływania metody formatowania, używane są konwencje formatowania bieżącej kultury wątku. Jest to zilustrowane w poniższym przykładzie, który zmienia bieżącą kulturę wątku czterokrotnie, a następnie wywołuje <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> metodę. W każdym przypadku ciąg wynikowy odzwierciedla konwencje formatowania bieżącej kultury. <xref:System.DateTime.ToString?displayProperty=nameWithType>Jest to spowodowane tym, że <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType>metody, <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>, i zawijają wywołania <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metod <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> i.

[!code-csharp[Conceptual.Formatting.Overview#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific1.cs#17)]
[!code-vb[Conceptual.Formatting.Overview#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific1.vb#17)]

Możesz również sformatować wartość daty i godziny dla określonej kultury poprzez wywołanie metody <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> przeciążenia, która ma `provider` parametr i przekazanie do niego jednego z następujących elementów:

- <xref:System.Globalization.CultureInfo> Obiekt, który reprezentuje kulturę, której konwencje formatowania mają być używane. Jego <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> Metoda zwraca <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> wartość<xref:System.Globalization.DateTimeFormatInfo> właściwości, która jest obiektem, który zawiera informacje o formatowaniu specyficzne dla kultury dla wartości daty i godziny.

- <xref:System.Globalization.DateTimeFormatInfo> Obiekt, który definiuje konwencje formatowania specyficzne dla kultury, które mają być używane. Jego <xref:System.Globalization.DateTimeFormatInfo.GetFormat%2A> Metoda zwraca wystąpienie samego siebie.

Poniższy przykład używa <xref:System.Globalization.DateTimeFormatInfo> obiektów, które reprezentują kultury angielskie (Stany Zjednoczone) i angielskie (Wielka Brytania) oraz kulturę neutralną w języku francuskim i rosyjskim do formatowania daty.

[!code-csharp[Conceptual.Formatting.Overview#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific2.cs#18)]
[!code-vb[Conceptual.Formatting.Overview#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific2.vb#18)]

<a name="IFormattable"></a>

## <a name="the-iformattable-interface"></a>Interfejs IFormattable

Zazwyczaj typy, które przeciążą `ToString` metodę z ciągiem formatu <xref:System.IFormatProvider> i parametrem również implementują <xref:System.IFormattable> interfejs. Ten interfejs ma pojedynczy element członkowski <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, który zawiera ciąg formatu i dostawcę formatowania jako parametry.

<xref:System.IFormattable> Implementacja interfejsu dla klasy zdefiniowanej przez aplikację oferuje dwie zalety:

- Obsługa konwersji ciągów przez <xref:System.Convert> klasę. Wywołania metod <xref:System.Convert.ToString%28System.Object%2CSystem.IFormatProvider%29?displayProperty=nameWithType> <xref:System.IFormattable> i powodują automatyczne wywoływanie implementacji. <xref:System.Convert.ToString%28System.Object%29?displayProperty=nameWithType>

- Obsługa formatowania złożonego. Jeśli element formatu, który zawiera ciąg formatu, jest używany do formatowania typu niestandardowego, środowisko uruchomieniowe języka wspólnego automatycznie wywoła <xref:System.IFormattable> implementację i przekaże ciąg formatu. Aby uzyskać więcej informacji na temat formatowania złożonego przy <xref:System.String.Format%2A?displayProperty=nameWithType> użyciu <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>metod takich jak lub, zobacz sekcję [formatowanie złożone](#CompositeFormatting) .

W poniższym przykładzie zdefiniowano `Temperature` klasę, która <xref:System.IFormattable> implementuje interfejs. Obsługuje specyfikatory formatu "C" lub "G", aby wyświetlić temperaturę w c, specyfikator formatu "F", aby wyświetlić temperaturę w stopniach Fahrenheita i specyfikator formatu "K", aby wyświetlić temperaturę w Kelvin.

[!code-csharp[Conceptual.Formatting.Overview#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#12)]
[!code-vb[Conceptual.Formatting.Overview#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#12)]

Poniższy przykład tworzy wystąpienie `Temperature` obiektu. Następnie wywołuje <xref:System.Convert.ToString%2A> metodę i używa kilku ciągów formatu złożonego, aby uzyskać różne reprezentacje `Temperature` ciągu obiektu. Z kolei każda z tych wywołań metod wywołuje <xref:System.IFormattable> implementację `Temperature` klasy.

[!code-csharp[Conceptual.Formatting.Overview#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#13)]
[!code-vb[Conceptual.Formatting.Overview#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#13)]

<a name="CompositeFormatting"></a>

## <a name="composite-formatting"></a>Złożone formatowanie

Niektóre metody, takie jak <xref:System.String.Format%2A?displayProperty=nameWithType> i <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, obsługują formatowanie złożone. Ciąg formatu złożonego jest rodzajem szablonu, który zwraca pojedynczy ciąg, który zawiera ciąg reprezentujący zero, jeden lub więcej obiektów. Każdy obiekt jest reprezentowany w ciągu formatu złożonego przez element formatu indeksowanego. Indeks elementu formatu odnosi się do położenia obiektu reprezentowanego na liście parametrów metody. Indeksy są oparte na zero. Na przykład <xref:System.String.Format%2A?displayProperty=nameWithType> w poniższym wywołaniu metody pierwszy `{0:D}`element formatu,, jest zastępowany ciągiem reprezentującym `thatDate`; drugi element `{1}`formatu,, jest zastępowany ciągiem reprezentującym `item1`; i trzeci element `{2:C2}`formatu,,, jest zamieniany na ciąg `item1.Value`reprezentujący.

[!code-csharp[Conceptual.Formatting.Overview#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite1.cs#14)]
[!code-vb[Conceptual.Formatting.Overview#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite1.vb#14)]

Oprócz zamiany elementu formatu na ciąg reprezentujący odpowiadający mu obiekt, elementy formatu umożliwiają również kontrolę następujących elementów:

- Określony sposób, w którym obiekt jest reprezentowany jako ciąg, jeśli obiekt implementuje <xref:System.IFormattable> interfejs i obsługuje ciągi formatu. Można to zrobić, wykonując indeks elementu formatowania z `:` dwukropkiem, po którym następuje prawidłowy ciąg formatu. W poprzednim przykładzie pokazano, jak sformatować wartość daty za pomocą ciągu formatu "d" (krótkiej daty) (np. `{0:d}`) oraz przez formatowanie wartości liczbowej przy użyciu ciągu formatu "C2" (np `{2:C2}` . do reprezentowania liczby jako wartości walutowej z dwoma ułamkowe cyfry dziesiętne.

- Szerokość pola zawierającego reprezentację ciągu obiektu oraz wyrównanie ciągu reprezentującego w tym polu. W tym celu należy postępować według szerokości pola `,` (indeks elementu formatu z przecinkiem). Ciąg jest wyrównany do prawej w polu, jeśli szerokość pola jest wartością dodatnią i jest wyrównany do lewej, jeśli szerokość pola jest wartością ujemną. Poniższy przykład wyrównuje wartości dat w polu 20-znakowym i wyrównuje wartości dziesiętne z jedną cyfrą ułamkową w polu 11-znakowym.

     [!code-csharp[Conceptual.Formatting.Overview#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite2.cs#22)]
     [!code-vb[Conceptual.Formatting.Overview#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite2.vb#22)]

     Należy zauważyć, że jeśli zarówno składnik ciągu wyrównania, jak i składnik ciągu formatu są obecne, dawniej poprzedza ostatni (na przykład `{0,-20:g}`.

Aby uzyskać więcej informacji na temat formatowania złożonego, zobacz [formatowanie złożone](../../../docs/standard/base-types/composite-formatting.md).

<a name="Custom"></a>

## <a name="custom-formatting-with-icustomformatter"></a>Niestandardowe formatowanie z ICustomFormatter

Dwie metody <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> formatowania złożonego i <xref:System.Text.StringBuilder.AppendFormat%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>zawierają parametr dostawcy formatu obsługujący niestandardowe formatowanie. Gdy każda z tych metod formatowania jest wywoływana, przekazuje <xref:System.Type> obiekt, który <xref:System.ICustomFormatter> reprezentuje interfejs <xref:System.IFormatProvider.GetFormat%2A> do metody dostawcy formatowania. Metoda jest następnie odpowiedzialna za <xref:System.ICustomFormatter> zwrócenie implementacji, która zapewnia niestandardowe formatowanie. <xref:System.IFormatProvider.GetFormat%2A>

Interfejs ma pojedynczą <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29>metodę, która jest wywoływana automatycznie przez metodę formatowania złożonego, jednokrotnie dla każdego elementu formatu w ciągu formatu złożonego. <xref:System.ICustomFormatter> Metoda ma trzy parametry: ciąg formatu, który `formatString` reprezentuje argument w elemencie formatu, obiekt <xref:System.IFormatProvider> do sformatowania i obiekt, który zapewnia usługi formatowania. <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29> Zazwyczaj Klasa <xref:System.ICustomFormatter> implementująca również implementuje <xref:System.IFormatProvider>, dlatego ostatni parametr jest odwołaniem do samej klasy formatowania niestandardowego. Metoda zwraca niestandardową reprezentację ciągu obiektu do sformatowania. Jeśli metoda nie może sformatować obiektu, powinna zwrócić odwołanie o wartości null (`Nothing` w Visual Basic).

W poniższym przykładzie przedstawiono <xref:System.ICustomFormatter> implementację o nazwie `ByteByByteFormatter` , która wyświetla wartości całkowite jako sekwencję dwucyfrowych wartości szesnastkowych, po których występuje spacja.

[!code-csharp[Conceptual.Formatting.Overview#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#15)]
[!code-vb[Conceptual.Formatting.Overview#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#15)]

Poniższy przykład używa `ByteByByteFormatter` klasy do formatowania wartości całkowitych. Należy zauważyć, <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> że metoda jest wywoływana więcej niż raz w drugim <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> wywołaniu metody i że dostawca domyślny <xref:System.Globalization.NumberFormatInfo> jest używany w trzecim wywołaniu metody, ponieważ.`ByteByByteFormatter.Format` Metoda nie rozpoznaje ciągu formatu "N0" i zwraca odwołanie o wartości null (`Nothing` w Visual Basic).

[!code-csharp[Conceptual.Formatting.Overview#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#16)]
[!code-vb[Conceptual.Formatting.Overview#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#16)]

<a name="RelatedTopics"></a>

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Definicja|
|-----------|----------------|
|[Standardowe ciągi formatujące liczby](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Opisuje ciągi formatu standardowego, które tworzą często używane reprezentacje ciągów wartości liczbowych.|
|[Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Opisuje niestandardowe ciągi formatujące, które tworzą formaty specyficzne dla aplikacji dla wartości liczbowych.|
|[Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Opisuje ciągi formatu standardowego, które tworzą często używane reprezentacje <xref:System.DateTime> ciągów wartości.|
|[Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Opisuje niestandardowe ciągi formatujące, które tworzą formaty charakterystyczne <xref:System.DateTime> dla aplikacji dla wartości.|
|[Standardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Opisuje ciągi formatu standardowego, które tworzą często używane reprezentacje ciągów przedziałów czasu.|
|[Niestandardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Opisuje niestandardowe ciągi formatujące, które tworzą formaty specyficzne dla aplikacji dla przedziałów czasu.|
|[Ciągi formatujące wyliczenia](../../../docs/standard/base-types/enumeration-format-strings.md)|Opisuje ciągi formatu standardowego, które są używane do tworzenia reprezentacji ciągów wartości wyliczenia.|
|[Złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md)|Opisuje sposób osadzenia jednej lub więcej sformatowanych wartości w ciągu. Ciąg można następnie wyświetlić w konsoli lub zapisać w strumieniu.|
|[Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)|Wyświetla listę tematów, które zawierają instrukcje krok po kroku dotyczące wykonywania określonych operacji formatowania.|
|[Analizowanie ciągów](../../../docs/standard/base-types/parsing-strings.md)|Opisuje sposób inicjowania obiektów do wartości opisanych przez ciąg reprezentujący te obiekty. Analizowanie jest operacją odwrotną formatowania.|

<a name="Reference"></a>

## <a name="reference"></a>Tematy pomocy

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- <xref:System.ICustomFormatter?displayProperty=nameWithType>
