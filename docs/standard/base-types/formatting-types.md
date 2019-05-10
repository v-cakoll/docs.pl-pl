---
title: Typy formatowania na platformie .NET
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
ms.openlocfilehash: ac253e5ff294360fff89e9746ca3038b4e1ee75c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751102"
---
# <a name="formatting-types-in-net"></a>Typy formatowania na platformie .NET

Formatowanie jest procesem konwertowania instancji klasy, struktury lub wartości wyliczenia na jego reprezentację ciągu często tak, aby wynikowy ciąg znaków, które mogą być wyświetlane użytkownikom lub deserializowany w celu przywrócenia oryginalnego typu danych. Ta konwersja może stwarzać wiele wyzwań:

- Sposób, że wartości są przechowywane wewnętrznie, niekoniecznie odzwierciedla sposób, w jaki użytkownicy chcą je wyświetlić. Na przykład numer telefonu mogą być przechowywane w formacie 8009999999, który nie jest. Zamiast tego jego powinna być wyświetlana jako 800-999-9999. Zobacz [niestandardowe ciągi formatujące](#customStrings) sekcji, aby uzyskać przykład formatujący liczbę w ten sposób.

- Czasami Konwersja obiektu na jego reprezentację ciągu nie jest intuicyjna. Na przykład nie jest jasne wygląd ciąg reprezentujący obiekt temperatury lub osoby. Aby uzyskać przykład formatowania obiektu temperatury na różne sposoby, zobacz [standardowe ciągi formatujące](#standardStrings) sekcji.

- Wartości zwykle wymagają formatowania kultury. Na przykład w aplikacji, która używa numerów do odzwierciedlenia wartości pieniężnych, ciągi numeryczne powinny obejmować symbol waluty bieżącej kultury, separator grupy (, w większości kultur, czyli tysięcy separator) oraz symbol dziesiętny. Aby uzyskać przykład, zobacz [wrażliwość na ustawienia kulturowe — mechanizm formatowania i interfejs IFormatProvider](#FormatProviders) sekcji.

- Aplikacja może być zmuszona wyświetlić tę samą wartość na różne sposoby. Na przykład aplikacja może reprezentować członka wyliczenia, wyświetlając ciąg reprezentujący jego nazwę lub wyświetlając jego podstawową wartość. Aby uzyskać przykład formatowania członka <xref:System.DayOfWeek> wyliczenia na różne sposoby, zobacz [standardowe ciągi formatujące](#standardStrings) sekcji.

> [!NOTE]
> Formatowanie konwertuje wartość typu na reprezentację ciągu znaków. Analizowania jest przeciwieństwem formatowania. Operacja analizy składni tworzy wystąpienie typu danych, z jego reprezentację ciągu. Aby uzyskać informacje na temat konwersji ciągów na inne typy danych, zobacz [analizowania ciągów](../../../docs/standard/base-types/parsing-strings.md).

.NET zapewnia szeroką obsługę formatowania, który pozwala deweloperom spełniać te wymagania.

Ten przegląd zawiera następujące sekcje:

- [Formatowanie w .NET](#NetFormatting)

- [Domyślne formatowania przy użyciu metody ToString](#DefaultToString)

- [Zastąpienie metody ToString](#OverrideToString)

- [Metoda ToString i ciągi formatujące](#FormatStrings)

  - [Standardowe ciągi formatujące](#standardStrings)

  - [Niestandardowe ciągi formatujące](#customStrings)

  - [Ciągi formatów i typy biblioteki klas .NET](#stringRef)

- [Wrażliwość na ustawienia kulturowe — mechanizm formatowania i interfejs IFormatProvider](#FormatProviders)

  - [Wrażliwość na ustawienia kulturowe formatowania wartości numerycznych](#numericCulture)

  - [Wrażliwość na ustawienia kulturowe formatowanie wartości daty i godziny](#dateCulture)

- [Interfejs IFormattable](#IFormattable)

- [Złożone formatowanie](#CompositeFormatting)

- [Niestandardowe formatowanie z ICustomFormatter](#Custom)

- [Tematy pokrewne](#RelatedTopics)

- [Dokumentacja](#Reference)

<a name="NetFormatting"></a>

## <a name="formatting-in-net"></a>Formatowanie w .NET

Podstawowy mechanizm formatowania jest implementacją domyślną <xref:System.Object.ToString%2A?displayProperty=nameWithType> metody, która została omówiona w [domyślne formatowania przy użyciu metody ToString](#DefaultToString) w dalszej części tego tematu. Jednak .NET oferuje kilka sposobów modyfikowania i rozszerzania jej obsługi domyślnego formatowania. Należą do nich między innymi:

- Zastępowanie <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodę, aby zdefiniować niestandardowy ciąg reprezentujący wartość obiektu. Aby uzyskać więcej informacji, zobacz [zastąpienie metody ToString](#OverrideToString) w dalszej części tego tematu.

- Definiowanie specyfikatorów formatu, które umożliwiają ciągowi reprezentującemu wartość obiektu Przybieranie wielu Form. Na przykład specyfikator formatu "X" w następującej instrukcji Konwertuje liczbę całkowitą na ciąg reprezentujący wartość szesnastkową.

     [!code-csharp[Conceptual.Formatting.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#3)]
     [!code-vb[Conceptual.Formatting.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#3)]

     Aby uzyskać więcej informacji na temat specyfikatorów formatu, zobacz [metoda ToString i ciągi formatu](#FormatStrings) sekcji.

- Korzystanie z dostawców formatu, aby móc korzystać z Konwencji formatowania określonej kultury. Na przykład poniższa instrukcja wyświetla wartość waluty przy użyciu konwencji formatowania kultury en US.

     [!code-csharp[Conceptual.Formatting.Overview#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#10)]
     [!code-vb[Conceptual.Formatting.Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#10)]

     Aby uzyskać więcej informacji na temat formatowania z dostawcami formatu, zobacz [dostawców formatu i interfejs IFormatProvider](#FormatProviders) sekcji.

- Implementowanie <xref:System.IFormattable> interfejsu do obsługi zarówno konwersji ciągów z <xref:System.Convert> klasy i formatowania złożonego. Aby uzyskać więcej informacji, zobacz [interfejs IFormattable](#IFormattable) sekcji.

- Używanie opcji formatowania złożonego, aby osadzić ciąg reprezentujący wartość w dłuższym ciągu. Aby uzyskać więcej informacji, zobacz [formatowania złożonego](#CompositeFormatting) sekcji.

- Implementowanie <xref:System.ICustomFormatter> i <xref:System.IFormatProvider> zapewnienie kompletnego rozwiązania formatowania niestandardowego. Aby uzyskać więcej informacji, zobacz [niestandardowe formatowanie z ICustomFormatter](#Custom) sekcji.

Poniższe sekcje opisują te metody konwersji obiektu na jego reprezentację ciągu.

<a name="DefaultToString"></a>

## <a name="default-formatting-using-the-tostring-method"></a>Domyślne formatowania przy użyciu metody ToString

Każdy typ, który jest tworzony na podstawie <xref:System.Object?displayProperty=nameWithType> automatycznie dziedziczy bez parametrów `ToString` metody, która domyślnie zwraca nazwę typu. Poniższy przykład ilustruje domyślną `ToString` metody. Definiuje klasę o nazwie `Automobile` , nie ma implementacji. Podczas tworzenia wystąpienia klasy i jego `ToString` metoda jest wywoływana, wyświetla się nazwa jej typu. Należy pamiętać, że `ToString` metoda nie jest jawnie wywoływana w przykładzie. <xref:System.Console.WriteLine%28System.Object%29?displayProperty=nameWithType> Wywołuje niejawnie metodę `ToString` metody obiektu przekazanego do niej jako argument.

[!code-csharp[Conceptual.Formatting.Overview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/default1.cs#1)]
[!code-vb[Conceptual.Formatting.Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/default1.vb#1)]

> [!WARNING]
> Zaczynając od [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[wrt](../../../includes/wrt-md.md)] obejmuje <xref:Windows.Foundation.IStringable> interfejsu z jednej metody [IStringable.ToString](xref:Windows.Foundation.IStringable.ToString%2A), który zapewnia domyślną obsługę formatowania. Jednak zaleca się że typy zarządzane nie implementowały `IStringable` interfejsu. Aby uzyskać więcej informacji, zobacz " [!INCLUDE[wrt](../../../includes/wrt-md.md)] i `IStringable` interfejsu" sekcji na <xref:System.Object.ToString%2A?displayProperty=nameWithType> odwołania do stron.

Ponieważ wszystkie typy inne niż interfejsy są pochodną <xref:System.Object>, ta funkcjonalność jest dostarczana automatycznie do niestandardowych klas lub struktur. Jednak funkcjonalność oferowana przez domyślną `ToString` metoda, jest ograniczona: Mimo że identyfikuje typ, nie podaje żadnych informacji o instancji tego typu. Aby zapewnić reprezentację ciągu obiektu, który zawiera informacje dotyczące tego obiektu, konieczne jest przesłonięcie `ToString` metody.

> [!NOTE]
> Struktury dziedziczą z <xref:System.ValueType>, który z kolei pochodzi od <xref:System.Object>. Mimo że <xref:System.ValueType> zastępuje <xref:System.Object.ToString%2A?displayProperty=nameWithType>, jego implementacja jest identyczna.

<a name="OverrideToString"></a>

## <a name="overriding-the-tostring-method"></a>Zastąpienie metody ToString

Zastosowanie wyświetlania nazwy typu jest zwykle ograniczone i nie pozwala użytkownikom typów na odróżnianie jednej instancji od drugiej. Jednak możesz zastąpić `ToString` metody w celu zapewnienia bardziej użytecznej reprezentacji wartości obiektu. W poniższym przykładzie zdefiniowano `Temperature` obiektu i zastąpienia jej `ToString` metoda wyświetlający temperaturę w stopniach Celsjusza.

[!code-csharp[Conceptual.Formatting.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/overrides1.cs#2)]
[!code-vb[Conceptual.Formatting.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/overrides1.vb#2)]

Na platformie .NET `ToString` metoda każdego typu wartości pierwotnej została zastąpiona, aby wyświetlić wartość obiektu zamiast jego nazwy. W poniższej tabeli przedstawiono zastąpienie dla każdego podstawowego typu. Należy pamiętać, że większość zastąpionych metod wywołuje inne przeciążenie `ToString` metody i przekazać go specyfikator formatu "G", który definiuje format ogólny dla jego typu, i <xref:System.IFormatProvider> obiekt, który reprezentuje bieżącą kulturę.

|Typ|Zastępowanie ToString|
|----------|-----------------------|
|<xref:System.Boolean>|Zwraca albo <xref:System.Boolean.TrueString?displayProperty=nameWithType> lub <xref:System.Boolean.FalseString?displayProperty=nameWithType>.|
|<xref:System.Byte>|Wywołania `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` do sformatowania <xref:System.Byte> wartość dla bieżącej kultury.|
|<xref:System.Char>|Zwraca znak jako ciąg.|
|<xref:System.DateTime>|Wywołania `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` do sformatowania wartości daty i godziny dla bieżącej kultury.|
|<xref:System.Decimal>|Wywołania `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` do sformatowania <xref:System.Decimal> wartość dla bieżącej kultury.|
|<xref:System.Double>|Wywołania `Double.ToString("G", NumberFormatInfo.CurrentInfo)` do sformatowania <xref:System.Double> wartość dla bieżącej kultury.|
|<xref:System.Int16>|Wywołania `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` do sformatowania <xref:System.Int16> wartość dla bieżącej kultury.|
|<xref:System.Int32>|Wywołania `Int32.ToString("G", NumberFormatInfo.CurrentInfo)` do sformatowania <xref:System.Int32> wartość dla bieżącej kultury.|
|<xref:System.Int64>|Wywołania `Int64.ToString("G", NumberFormatInfo.CurrentInfo)` do sformatowania <xref:System.Int64> wartość dla bieżącej kultury.|
|<xref:System.SByte>|Wywołania `SByte.ToString("G", NumberFormatInfo.CurrentInfo)` do sformatowania <xref:System.SByte> wartość dla bieżącej kultury.|
|<xref:System.Single>|Wywołania `Single.ToString("G", NumberFormatInfo.CurrentInfo)` do sformatowania <xref:System.Single> wartość dla bieżącej kultury.|
|<xref:System.UInt16>|Wywołania `UInt16.ToString("G", NumberFormatInfo.CurrentInfo)` do sformatowania <xref:System.UInt16> wartość dla bieżącej kultury.|
|<xref:System.UInt32>|Wywołania `UInt32.ToString("G", NumberFormatInfo.CurrentInfo)` do sformatowania <xref:System.UInt32> wartość dla bieżącej kultury.|
|<xref:System.UInt64>|Wywołania `UInt64.ToString("G", NumberFormatInfo.CurrentInfo)` do sformatowania <xref:System.UInt64> wartość dla bieżącej kultury.|

<a name="FormatStrings"></a>

## <a name="the-tostring-method-and-format-strings"></a>Metoda ToString i ciągi formatujące

Opieranie się na domyślnej `ToString` metody lub zastępowanie `ToString` jest odpowiednie, jeśli obiekt ma jedną reprezentację ciągu. Jednak wartość obiektu często ma wiele reprezentacji. Na przykład temperatury mogą wyrażone w stopniach Fahrenheita, stopniach Celsjusza lub kelwinach. Podobnie, wartość całkowita 10 może być reprezentowany na wiele sposobów, w tym 10, 10,0, 1.0e01 lub 10,00 zł.

Aby włączyć pojedynczą wartość na wiele reprezentacji ciągów, .NET używa ciągów formatowania. Ciąg formatu to ciąg, który zawiera jeden lub więcej wstępnie zdefiniowanych specyfikatorów formatu, które są pojedyncze znaki lub grupy znaków, które definiują sposób, w jaki `ToString` metoda powinna formatować swoje dane wyjściowe. Ciąg formatu, który jest następnie przekazywany jako parametr do obiektu `ToString` metody i określa wygląd ciągu reprezentującego wartość tego obiektu.

Wszystkie typy liczbowe, daty i czasu typów oraz typy wyliczeniowe na platformie .NET obsługują predefiniowany zestaw specyfikatorów formatu. Ciągi formatu służy także do definiowania wielu ciągów znaków reprezentujących typów danych zdefiniowanych przez aplikację.

<a name="standardStrings"></a>

### <a name="standard-format-strings"></a>Standardowe ciągi formatujące

Ciąg formatu standardowego zawiera pojedynczy specyfikator formatu, który jest znakiem alfabetycznym, który definiuje ciąg reprezentujący obiekt, do którego ma zastosowanie, wraz z opcjonalnym specyfikatorem dokładności, który wpływa na liczbę cyfr wyświetlanych w ciąg wynikowy. Jeśli Specyfikator dokładności zostanie pominięty lub nie jest obsługiwany, specyfikator formatu standardowego jest równoważny ciągowi formatu standardowego.

.NET definiuje zestaw specyfikatorów formatu standardowego dla wszystkich typów liczbowych, wszystkie daty i czasu typów oraz wszystkich typów wyliczeń. Na przykład każdy z tych kategorii obsługuje specyfikator formatu standardowego "G", który definiuje ogólny ciąg reprezentujący wartość tego typu.

Ciągi formatu standardowego dla typów wyliczeń bezpośrednio kontrolują reprezentację ciągu wartości. Ciągi formatu przekazane do metody wartości wyliczenia `ToString` ustalają, czy wartość jest wyświetlana przy użyciu nazwy ciągu ("G" i specyfikatory formatu "F"), jego podstawowej wartości całkowitej (specyfikator formatu "D") lub jego wartości szesnastkowej ("X "specyfikator formatu). Poniższy przykład ilustruje użycie ciągów formatu standardowego do sformatowania <xref:System.DayOfWeek> wartość wyliczenia.

[!code-csharp[Conceptual.Formatting.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/standard1.cs#4)]
[!code-vb[Conceptual.Formatting.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/standard1.vb#4)]

Aby uzyskać informacje na temat ciągów formatów wyliczeń, zobacz [wyliczanie ciągów formatujących](../../../docs/standard/base-types/enumeration-format-strings.md).

Ciągi formatu standardowego dla typów numerycznych zazwyczaj definiują ciąg wynikowy, którego dokładny wygląd jest kontrolowany przez jedną lub więcej wartości właściwości. Na przykład specyfikator formatu "C" formatuje liczbę jako wartość walutową. Gdy wywołujesz `ToString` metody za pomocą specyfikatora formatu "C" jako jedynym parametrem, następujące wartości właściwości z bieżącej kultury <xref:System.Globalization.NumberFormatInfo> są używane do definiowania ciągu reprezentującego wartość liczbową:

- <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A> Właściwość, która określa symbol waluty bieżącej kultury.

- <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> Lub <xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A> właściwość, która zwraca liczbę całkowitą, która określa następujące:

  - Położenie symbolu waluty.

  - Czy wartości ujemne są wskazywane przez wiodący znak ujemny, końcowy znak ujemny lub nawiasy.

  - Czy spacja pojawia się między wartością numeryczną i symbolem waluty.

- <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A> Właściwość, która definiuje liczbę cyfr dziesiętnych w ciągu wynikowym.

- <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A> Właściwość, która określa symbol separatora dziesiętnego w ciągu wynikowym.

- <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A> Właściwość, która określa symbol separatora grupy.

- <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A> Właściwość, która definiuje liczbę cyfr w każdej grupie na lewo od separatora dziesiętnego.

- <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> Właściwość, która określa znak ujemny używany w ciągu wynikowym, jeśli nawiasy nie są używane do wskazywania wartości ujemnych.

Dodatkowo ciągi formatujące liczby mogą zawierać Specyfikator dokładności. Znaczenie tego specyfikatora zależy od ciągu formatu, z którym jest używany, ale zazwyczaj wskazuje albo całkowitą liczbę znaków lub liczbę cyfr dziesiętnych, które powinny być wyświetlane w ciągu wynikowym. Na przykład w poniższym przykładzie użyto "X 4" standardowego ciągu numerycznego i specyfikatora dokładności utworzyć wartość ciągu, która ma cztery cyfry szesnastkowe.

[!code-csharp[Conceptual.Formatting.Overview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/precisionspecifier1.cs#6)]
[!code-vb[Conceptual.Formatting.Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/precisionspecifier1.vb#6)]

Aby uzyskać więcej informacji na temat standardowych ciągów formatu liczbowego, zobacz [Standard Numeric Format Strings](../../../docs/standard/base-types/standard-numeric-format-strings.md).

Ciągi formatu standardowego dla wartości daty i godziny to aliasy dla ciągów formatów niestandardowych, zapisanych przez określoną <xref:System.Globalization.DateTimeFormatInfo> właściwości. Na przykład, wywołanie `ToString` metoda wartości daty i godziny, przy użyciu specyfikatora formatu "D" Wyświetla datę i godzinę przy użyciu ciągu formatu niestandardowego, przechowywane w bieżącej kultury <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> właściwości. (Aby uzyskać więcej informacji na temat ciągów formatów niestandardowych, zobacz [następnej sekcji](#customStrings).) Poniższy przykład ilustruje tę relację.

[!code-csharp[Conceptual.Formatting.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/alias1.cs#5)]
[!code-vb[Conceptual.Formatting.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/alias1.vb#5)]

Aby uzyskać więcej informacji na temat standardowych ciągów daty i godziny formatu, zobacz [standardowych ciągów daty i godziny Format](../../../docs/standard/base-types/standard-date-and-time-format-strings.md).

Można również użyć ciągów formatu standardowego do definiowania ciągu reprezentującego obiekt zdefiniowany przez aplikację, który jest generowany przez obiekt `ToString(String)` metody. Możesz zdefiniować określone specyfikatory formatu standardowego, które obsługuje Twój obiekt i określić, czy są one uwzględniających wielkość liter lub bez uwzględniania wielkości liter. Implementacja `ToString(String)` metoda powinna obsługiwać następujące:

- Specyfikator formatu "G" reprezentujący zwyczajowy lub wspólny format obiektu. Przeciążenie bez parametrów obiektu `ToString` powinny wywoływać metodę jego `ToString(String)` przeciążenia i przekazywać je ciąg formatu standardowego "G".

- Obsługa specyfikatora formatu, który jest taki sam, jak odwołanie o wartości null (`Nothing` w języku Visual Basic). Specyfikator formatu, który jest taki sam, jak odwołanie o wartości null należy rozważyć równoważny specyfikatorowi formatu "G".

Na przykład `Temperature` klasy może wewnętrznie przechowywać temperaturę w stopniach Celsjusza i używać specyfikatorów formatu do reprezentowania wartości obiektu `Temperature` obiektu w stopniach Celsjusza, stopniach Fahrenheita i kelwinach. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.Formatting.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/appstandard1.cs#7)]
[!code-vb[Conceptual.Formatting.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/appstandard1.vb#7)]

<a name="customStrings"></a>

### <a name="custom-format-strings"></a>Niestandardowe ciągi formatujące

Oprócz ciągów standardowego formatu .NET definiuje ciągi formatów niestandardowych dla zarówno wartości liczbowych, jak i wartości daty i godziny. Ciąg formatu niestandardowego składa się z jednego lub więcej specyfikatorów formatu niestandardowego, które definiują ciąg reprezentujący wartość. Na przykład niestandardowa data i godzina, o których formatu ciągu "rrrr/mm/dd hh:mm:ss.ffff t zzz" Konwertuje datę na jego reprezentację ciągu w postaci "2008/11/15 07:45:00.0000 P -08:00" dla kultury en US. Podobnie ciąg formatu niestandardowego "0000" konwertuje wartość całkowitą 12 na "0012". Aby uzyskać pełną listę ciągów formatów niestandardowych, zobacz [niestandardowych ciągów daty i godziny Format](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) i [liczbowe — niestandardowe ciągi formatujące](../../../docs/standard/base-types/custom-numeric-format-strings.md).

Jeżeli ciąg formatu zawiera pojedynczy specyfikator formatu niestandardowego, specyfikator formatu powinien być poprzedzony procentu (%) symbol, aby uniknąć mylenia go przy użyciu specyfikatora formatu standardowego. Poniższy przykład używa specyfikator formatu niestandardowego "M" do wyświetlania jedno- lub dwucyfrową liczbę miesiąca z określonej daty.

[!code-csharp[Conceptual.Formatting.Overview#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/singlecustom1.cs#8)]
[!code-vb[Conceptual.Formatting.Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/singlecustom1.vb#8)]

Wiele ciągów formatu standardowego dla wartości daty i godziny to aliasy dla ciągów formatów niestandardowych, które są definiowane przez właściwości <xref:System.Globalization.DateTimeFormatInfo> obiektu. Ciągi formatów niestandardowych oferują również znaczną elastyczność w dostarczaniu formatowania zdefiniowanego przez aplikację dla wartości numerycznych lub wartości daty i godziny. Można zdefiniować własne niestandardowe ciągi wyników dla wartości numerycznych oraz wartości daty i godziny, łącząc wiele specyfikatorów formatu niestandardowego w jeden ciąg formatu niestandardowego. W poniższym przykładzie zdefiniowano ciąg formatu niestandardowego, który wyświetla dzień tygodnia w nawiasie po nazwie miesiąca, dzień i rok.

[!code-csharp[Conceptual.Formatting.Overview#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/custom1.cs#9)]
[!code-vb[Conceptual.Formatting.Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/custom1.vb#9)]

W poniższym przykładzie zdefiniowano ciąg formatu niestandardowego, który wyświetla <xref:System.Int64> wartość jako standardowy, 7 cyfr USA numer telefonu wraz z jego numer kierunkowy.

[!code-csharp[Conceptual.Formatting.Overview#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/telnumber1.cs#21)]
[!code-vb[Conceptual.Formatting.Overview#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/telnumber1.vb#21)]

Chociaż ciągi formatów standardowych zazwyczaj mogą obsługiwać większość potrzeb formatowania dla typów zdefiniowanych przez aplikację, mogą również definiować specyfikatorów formatu niestandardowego, aby sformatować swoje typy.

<a name="stringRef"></a>

### <a name="format-strings-and-net-types"></a>Ciągi formatów i typów .NET

Wszystkie typy liczbowe (czyli <xref:System.Byte>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>i <xref:System.Numerics.BigInteger>typów), a także <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, <xref:System.Guid>, i wszystkich typów wyliczeń, obsługują formatowanie z ciągami formatu. Instrukcje dotyczące ciągów określonego formatu obsługiwanych przez każdy typ zobacz następujące tematy:

|Tytuł|Definicja|
|-----------|----------------|
|[Standardowe ciągi formatujące liczby](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Opisuje ciągi w standardowym formacie, które tworzenia często stosowanych ciągów reprezentujących wartości numeryczne.|
|[Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Opisuje tworzenie niestandardowych formatów ciągów, które tworzą formaty specyficzna dla wartości liczbowych.|
|[Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Opisuje ciągi w standardowym formacie, które do tworzenia często stosowanych ciągów reprezentujących <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości.|
|[Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Opisuje tworzenie niestandardowych formatów ciągów, które tworzą formaty specyficzna dla <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości.|
|[Standardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Opisuje ciągi w standardowym formacie, które tworzenia często stosowanych ciągów reprezentujących odstępy czasu.|
|[Niestandardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Opisuje tworzenie niestandardowych formatów ciągów, które tworzą formaty specyficzne dla aplikacji dla przedziałów czasowych.|
|[Ciągi formatujące wyliczenia](../../../docs/standard/base-types/enumeration-format-strings.md)|Opisuje ciągi w standardowym formacie, które są używane do tworzenia ciągów reprezentujących wartości wyliczenia.|
|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|Opisuje ciągi formatu standardowego dla <xref:System.Guid> wartości.|

<a name="FormatProviders"></a>

## <a name="culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface"></a>Wrażliwość na ustawienia kulturowe — mechanizm formatowania i interfejs IFormatProvider

Chociaż specyfikatory formatu pozwalają dostosować formatowanie obiektów, tworzenie reprezentacji ciągów mających znaczenie obiektów często wymaga dodatkowych informacji o formatowaniu. Na przykład, formatowanie liczby jako wartość waluty przy użyciu ciągu formatu standardowego "C" lub ciąg formatu niestandardowego, takiego jak "$ #, #. 00", wymaga co najmniej informacji o poprawnym symbolu waluty, separatorze grupy i separator dziesiętny jako dostępne do dołączenia w sformatowanym ciągu. Na platformie .NET, to dodatkowe informacje o formatowaniu są udostępniane za pośrednictwem <xref:System.IFormatProvider> interfejsu, która jest podawana jako parametr do jednego lub więcej przeciążenia `ToString` metody typów numerycznych oraz typów daty i godziny. <xref:System.IFormatProvider> implementacje są używane na platformie .NET do obsługi formatowania specyficznego dla kultury. W poniższym przykładzie pokazano, jak ciąg reprezentujący obiekt zmienia, gdy jest on formatowany z trzema <xref:System.IFormatProvider> obiektów, które reprezentują różne kultury.

[!code-csharp[Conceptual.Formatting.Overview#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformatprovider1.cs#11)]
[!code-vb[Conceptual.Formatting.Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformatprovider1.vb#11)]

<xref:System.IFormatProvider> Interfejs zawiera jedną metodę <xref:System.IFormatProvider.GetFormat%28System.Type%29>, który ma jeden parametr, który określa typ obiektu, który dostarcza informacje o formatowaniu. Jeśli metoda może dostarczyć obiekt tego typu, zwraca go. W przeciwnym razie zwraca odwołanie o wartości null (`Nothing` w języku Visual Basic).

<xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> jest metodą wywołania zwrotnego. Gdy wywołujesz `ToString` przeciążenia metody, która obejmuje <xref:System.IFormatProvider> parametru, wywołuje <xref:System.IFormatProvider.GetFormat%2A> metodę, która <xref:System.IFormatProvider> obiektu. <xref:System.IFormatProvider.GetFormat%2A> Metoda jest odpowiedzialna za zwrócenie obiektu, który dostarcza niezbędne informacje formatowania, określony przez jego `formatType` parametr, `ToString` metody.

Numeru formatowania lub ciąg metody konwersji zawierają parametr typu <xref:System.IFormatProvider>, ale w wielu przypadkach wartość parametru jest ignorowana, gdy jest wywoływana metoda. W poniższej tabeli wymieniono niektóre metody formatowania, które używają parametru i typu <xref:System.Type> obiektu, który przekazują do <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metody.

|Metoda|Typ `formatType` parametru|
|------------|------------------------------------|
|`ToString` Metoda typy liczbowe|<xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>|
|`ToString` Metoda typów daty i godziny|<xref:System.Globalization.DateTimeFormatInfo?displayProperty=nameWithType>|
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|

> [!NOTE]
> `ToString` Metody typów numerycznych oraz typów daty i godziny są przeciążone, a niektóre przeciążenia zawierają <xref:System.IFormatProvider> parametru. Jeśli metoda nie ma parametru typu <xref:System.IFormatProvider>, obiekt, który jest zwracany przez <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwość jest przekazywany zamiast tego. Na przykład, wywołanie domyślnej <xref:System.Int32.ToString?displayProperty=nameWithType> metoda ostatecznie powoduje wywołanie metody podobny do następującego: `Int32.ToString("G", System.Globalization.CultureInfo.CurrentCulture)`.

.NET zawiera trzy klasy, które implementują <xref:System.IFormatProvider>:

- <xref:System.Globalization.DateTimeFormatInfo>, klasa, która dostarcza informacje o formatowaniu dla wartości daty i godziny dla określonej kultury. Jego <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementacja zwraca instancję samego siebie.

- <xref:System.Globalization.NumberFormatInfo>, klasa, która dostarcza informacje o formatowaniu liczb dla określonej kultury. Jego <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementacja zwraca instancję samego siebie.

- <xref:System.Globalization.CultureInfo>. Jego <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementacji może zwracać albo <xref:System.Globalization.NumberFormatInfo> obiektu, aby zapewnić informacje o formatowaniu liczb lub <xref:System.Globalization.DateTimeFormatInfo> obiektu, aby zapewnić informacje o formatowaniu dla wartości daty i godziny.

Można także zaimplementować własnego dostawcę formatu, aby zastąpić dowolną z tych klas. Jednak Twoja implementacja <xref:System.IFormatProvider.GetFormat%2A> metoda musi zwracać obiekt typu wymienionych w powyższej tabeli, jeśli musi zapewnić informacje o formatowaniu `ToString` metody.

<a name="numericCulture"></a>

### <a name="culture-sensitive-formatting-of-numeric-values"></a>Wrażliwość na ustawienia kulturowe — formatowania wartości numerycznych

Domyślnie formatowanie wartości liczbowych uwzględnia kulturę. Jeśli nie określisz kultury przy wywołaniu metody formatowania, są używane konwencje formatowania bieżącej kultury wątku. Jest to zilustrowane w poniższym przykładzie, który zmienia bieżącą kulturę wątku cztery razy, a następnie wywołuje <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> metody. W każdym przypadku ciąg wynikowy odzwierciedla konwencje formatowania bieżącej kultury. Jest to spowodowane `ToString` i `ToString(String)` owijają wywołania do każdego liczbowego typu `ToString(String, IFormatProvider)` metody.

[!code-csharp[Conceptual.Formatting.Overview#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific3.cs#19)]
[!code-vb[Conceptual.Formatting.Overview#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific3.vb#19)]

Możesz również sformatować wartość numeryczną dla określonej kultury poprzez wywołanie `ToString` przeciążenie `provider` parametru i podając mu jedno z następujących czynności:

- Element <xref:System.Globalization.CultureInfo> obiektu, który reprezentuje kulturę, której konwencje formatowania mają zostać użyte. Jego <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> metoda zwraca wartość <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> właściwość, która jest <xref:System.Globalization.NumberFormatInfo> obiektu, który dostarcza specyficzne dla kultury informacje o formatowaniu dla wartości liczbowych.

- A <xref:System.Globalization.NumberFormatInfo> obiekt, który definiuje konwencje formatowania specyficzne dla kultury, ma być używany. Jego <xref:System.Globalization.NumberFormatInfo.GetFormat%2A> metoda zwraca instancję samego siebie.

W poniższym przykładzie użyto <xref:System.Globalization.NumberFormatInfo> obiekty reprezentujące angielski (Stany Zjednoczone) i angielska (Wielka Brytania) oraz kultury neutralne francuska i Rosyjska w celu sformatowania liczby zmiennopozycyjnej.

[!code-csharp[Conceptual.Formatting.Overview#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific4.cs#20)]
[!code-vb[Conceptual.Formatting.Overview#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific4.vb#20)]

<a name="dateCulture"></a>

### <a name="culture-sensitive-formatting-of-date-and-time-values"></a>Wrażliwość na ustawienia kulturowe — formatowanie wartości daty i godziny

Domyślnie formatowanie wartości daty i godziny jest uwzględniana kultura. Jeśli nie określisz kultury przy wywołaniu metody formatowania, są używane konwencje formatowania bieżącej kultury wątku. Jest to zilustrowane w poniższym przykładzie, który zmienia bieżącą kulturę wątku cztery razy, a następnie wywołuje <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> metody. W każdym przypadku ciąg wynikowy odzwierciedla konwencje formatowania bieżącej kultury. Jest to spowodowane <xref:System.DateTime.ToString?displayProperty=nameWithType>, <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType>, i <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> owijają wywołania do <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> i <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody.

[!code-csharp[Conceptual.Formatting.Overview#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific1.cs#17)]
[!code-vb[Conceptual.Formatting.Overview#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific1.vb#17)]

Możesz również sformatować wartość daty i godziny dla określonej kultury poprzez wywołanie <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> przeciążenie `provider` parametru i podając mu jedno z następujących czynności:

- Element <xref:System.Globalization.CultureInfo> obiektu, który reprezentuje kulturę, której konwencje formatowania mają zostać użyte. Jego <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> metoda zwraca wartość <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> właściwość, która jest <xref:System.Globalization.DateTimeFormatInfo> obiektu, który dostarcza specyficzne dla kultury informacje o formatowaniu dla wartości daty i godziny.

- A <xref:System.Globalization.DateTimeFormatInfo> obiekt, który definiuje konwencje formatowania specyficzne dla kultury, ma być używany. Jego <xref:System.Globalization.DateTimeFormatInfo.GetFormat%2A> metoda zwraca instancję samego siebie.

W poniższym przykładzie użyto <xref:System.Globalization.DateTimeFormatInfo> obiekty reprezentujące angielski (Stany Zjednoczone) i angielska (Wielka Brytania) oraz kultury neutralne francuska i Rosyjska w celu sformatowania daty.

[!code-csharp[Conceptual.Formatting.Overview#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific2.cs#18)]
[!code-vb[Conceptual.Formatting.Overview#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific2.vb#18)]

<a name="IFormattable"></a>

## <a name="the-iformattable-interface"></a>Interfejs IFormattable

Zwykle typy, które przeciążają `ToString` metody za pomocą ciągu formatu i <xref:System.IFormatProvider> parametru także implementować <xref:System.IFormattable> interfejsu. Ten interfejs ma jeden element członkowski <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, które zawiera zarówno ciąg formatu, jak i dostawcę formatu jako parametry.

Implementowanie <xref:System.IFormattable> interfejsu klasy zdefiniowane przez aplikację ma dwie zalety:

- Obsługa konwersji ciągów przez <xref:System.Convert> klasy. Wywołania <xref:System.Convert.ToString%28System.Object%29?displayProperty=nameWithType> i <xref:System.Convert.ToString%28System.Object%2CSystem.IFormatProvider%29?displayProperty=nameWithType> wywołania metody usługi <xref:System.IFormattable> implementacji automatycznie.

- Obsługa formatowania złożonego. Jeśli element formatu, który zawiera ciąg formatu jest używany do formatowania niestandardowego typu, środowisko uruchomieniowe języka wspólnego automatycznie wywołuje swoje <xref:System.IFormattable> implementacji i przekazuje jej ciąg formatu. Aby uzyskać więcej informacji na temat formatowania złożonego za pomocą metod takich jak <xref:System.String.Format%2A?displayProperty=nameWithType> lub <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, zobacz [formatowania złożonego](#CompositeFormatting) sekcji.

W poniższym przykładzie zdefiniowano `Temperature` klasę, która implementuje <xref:System.IFormattable> interfejsu. Obsługuje ona "C" lub "G" specyfikatorów formatu wyświetlający temperaturę w stopniach Celsjusza, specyfikator formatu "F" wyświetlający temperaturę w Fahrenheita i specyfikator formatu "K" wyświetlający temperaturę w kelwinach.

[!code-csharp[Conceptual.Formatting.Overview#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#12)]
[!code-vb[Conceptual.Formatting.Overview#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#12)]

Poniższy przykład tworzy wystąpienie `Temperature` obiektu. Następnie wywołuje <xref:System.Convert.ToString%2A> metody i wykorzystuje kilka ciągów formatowania złożonego w celu uzyskania różnych reprezentacji ciągów obiektu `Temperature` obiektu. Każda z tych wywołań metody wywołuje z kolei wywołuje <xref:System.IFormattable> implementacji `Temperature` klasy.

[!code-csharp[Conceptual.Formatting.Overview#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#13)]
[!code-vb[Conceptual.Formatting.Overview#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#13)]

<a name="CompositeFormatting"></a>

## <a name="composite-formatting"></a>Złożone formatowanie

Niektóre metody, takie jak <xref:System.String.Format%2A?displayProperty=nameWithType> i <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, obsługują formatowanie złożone. Ciąg formatu złożonego jest to rodzaj szablonu, który zwraca jeden ciąg, który zawiera ciąg reprezentujący zero, jeden lub więcej obiektów. Każdy obiekt jest reprezentowany w ciągu formatu złożonego przez indeksowany element formatu. Indeks elementu formatu odnosi się do położenia obiektu, który reprezentuje on na liście parametrów metody. Indeksy są od zera. Na przykład, w następującym wywołaniu do <xref:System.String.Format%2A?displayProperty=nameWithType> metody, pierwszy element formatu, `{0:D}`, jest zastępowany przez ciąg reprezentujący `thatDate`; drugi element formatu `{1}`, jest zastępowany przez ciąg reprezentujący `item1`; i trzeci element formatu `{2:C2}`, jest zastępowany przez ciąg reprezentujący `item1.Value`.

[!code-csharp[Conceptual.Formatting.Overview#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite1.cs#14)]
[!code-vb[Conceptual.Formatting.Overview#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite1.vb#14)]

Oprócz zastępując ciąg reprezentujący jego odpowiedni obiekt element formatu, elementami formatu pozwalają również kontrolują następujące elementy:

- Konkretny sposób, który obiekt jest reprezentowany jako ciąg, jeśli obiekt implementuje <xref:System.IFormattable> interfejs i obsługuje ciągi formatu. Można to zrobić, po indeks elementu formatu z `:` (dwukropek), a następnie poprawny ciąg formatujący. W poprzednim przykładzie zostało to już zrobione, formatowanie wartości daty przy użyciu ciągu formatu "d" (wzorzec daty krótkiej) (np. `{0:d}`) i formatując wartość liczbową z "C2" w ciągu formatu (np. `{2:C2}` do reprezentowania liczby jako wartość waluty przy użyciu dwóch cyfry ułamkowe.

- Szerokość pola, które zawiera reprezentację ciągu obiektu i wyrównanie reprezentacji w postaci ciągu w danym polu. Można to zrobić, po indeks elementu formatu z `,` (przecinek), a następnie szerokości pola. Ten ciąg jest wyrównany do prawej w polu Jeśli szerokość pola jest wartość dodatnią, a jego jest wyrównany do lewej, jeśli szerokość pola jest liczbą ujemną. Poniższy przykład powoduje wyrównanie po lewej stronie wartości daty w polu 20 znaków, a następnie go po prawej stronie Wyrównuje wartości dziesiętne z jednej cyfry ułamkowe w polu 11 znaków.

     [!code-csharp[Conceptual.Formatting.Overview#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite2.cs#22)]
     [!code-vb[Conceptual.Formatting.Overview#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite2.vb#22)]

     Należy pamiętać, że jeśli istnieją zarówno składnik parametrów wyrównanie, jak i element ciągu formatującego poprzedniego poprzedza one (na przykład `{0,-20:g}`.

Aby uzyskać więcej informacji na temat formatowania złożonego, zobacz [formatowania złożonego](../../../docs/standard/base-types/composite-formatting.md).

<a name="Custom"></a>

## <a name="custom-formatting-with-icustomformatter"></a>Niestandardowe formatowanie z ICustomFormatter

Dwie metody formatowania złożonego, <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> i <xref:System.Text.StringBuilder.AppendFormat%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, obejmują parametr dostawcy formatowania, który obsługuje formatowanie niestandardowe. Gdy wywoływana jest któraś z tych metod formatowania, przekazuje on <xref:System.Type> obiekt, który reprezentuje <xref:System.ICustomFormatter> interfejsu dostawcę formatu <xref:System.IFormatProvider.GetFormat%2A> metody. <xref:System.IFormatProvider.GetFormat%2A> Metoda jest odpowiedzialna za zwrócenie <xref:System.ICustomFormatter> implementację, która zawiera niestandardowe formatowanie.

<xref:System.ICustomFormatter> Interfejs zawiera tylko jedną metodę <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29>, która jest wywoływana automatycznie przez metodę formatowania złożonego, jeden raz dla każdego elementu formatu w ciąg formatu złożonego. <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29> Metoda ma trzy parametry: ciąg formatu, który reprezentuje `formatString` argumentów w elemencie formatu, formatowany obiekt, a <xref:System.IFormatProvider> usług obiektu, który dostarcza formatowania. Zazwyczaj klasa, która implementuje <xref:System.ICustomFormatter> implementuje również <xref:System.IFormatProvider>, więc ten ostatni parametr jest odwołaniem do formatowania niestandardowego samej klasy. Metoda zwraca reprezentację ciągu formatu niestandardowego obiektu, który ma być sformatowane. Jeśli metoda nie może sformatować obiektu, powinna zwrócić odwołanie o wartości null (`Nothing` w języku Visual Basic).

W poniższym przykładzie przedstawiono <xref:System.ICustomFormatter> wdrożenia o nazwie `ByteByByteFormatter` która wyświetla wartości całkowite jako sekwencję dwucyfrowych wartości szesnastkowych, następuje spacja.

[!code-csharp[Conceptual.Formatting.Overview#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#15)]
[!code-vb[Conceptual.Formatting.Overview#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#15)]

W poniższym przykładzie użyto `ByteByByteFormatter` klasy w celu formatowania wartości całkowitych. Należy pamiętać, że <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> metoda jest wywoływana więcej niż jeden raz w ciągu sekundy <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> wywołania metody, a wartość domyślna <xref:System.Globalization.NumberFormatInfo> dostawcy jest używany w trzecim wywołaniu metody, ponieważ.`ByteByByteFormatter.Format` Metoda nie rozpoznaje formatu ciągu "N0" i zwraca odwołanie o wartości null (`Nothing` w języku Visual Basic).

[!code-csharp[Conceptual.Formatting.Overview#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#16)]
[!code-vb[Conceptual.Formatting.Overview#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#16)]

<a name="RelatedTopics"></a>

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Definicja|
|-----------|----------------|
|[Standardowe ciągi formatujące liczby](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Opisuje ciągi w standardowym formacie, które tworzenia często stosowanych ciągów reprezentujących wartości numeryczne.|
|[Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Opisuje tworzenie niestandardowych formatów ciągów, które tworzą formaty specyficzna dla wartości liczbowych.|
|[Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Opisuje ciągi w standardowym formacie, które do tworzenia często stosowanych ciągów reprezentujących <xref:System.DateTime> wartości.|
|[Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Opisuje tworzenie niestandardowych formatów ciągów, które tworzą formaty specyficzna dla <xref:System.DateTime> wartości.|
|[Standardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Opisuje ciągi w standardowym formacie, które tworzenia często stosowanych ciągów reprezentujących odstępy czasu.|
|[Niestandardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Opisuje tworzenie niestandardowych formatów ciągów, które tworzą formaty specyficzne dla aplikacji dla przedziałów czasowych.|
|[Ciągi formatujące wyliczenia](../../../docs/standard/base-types/enumeration-format-strings.md)|Opisuje ciągi w standardowym formacie, które są używane do tworzenia ciągów reprezentujących wartości wyliczenia.|
|[Złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md)|W tym artykule opisano, jak osadzić jedną lub więcej sformatowanych wartości w ciągu. Ciąg można następnie wyświetlany w konsoli lub zapisywany do strumienia.|
|[Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)|Wyświetla listę tematów, które oferują instrukcje krok po kroku do wykonywania określonych operacji formatowania.|
|[Analizowanie ciągów](../../../docs/standard/base-types/parsing-strings.md)|W tym artykule opisano sposób inicjowania obiektów do wartości opisanych przez ciąg reprezentujący te obiekty. Analizowanie jest odwróconą operacją formatowania.|

<a name="Reference"></a>

## <a name="reference"></a>Tematy pomocy

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- <xref:System.ICustomFormatter?displayProperty=nameWithType>
