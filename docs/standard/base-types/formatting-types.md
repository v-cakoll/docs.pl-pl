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
ms.openlocfilehash: 20aa7ecd354ef1a8982ae75eda87275c80cdaaf6
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802469"
---
# <a name="format-types-in-net"></a>Typy formatów w programie .NET

Formatowanie jest procesem konwertowania instancji klasy, struktury lub wartości wyliczenia na jej reprezentację w postaci ciągu, zwykle po to, aby wynikowy ciąg mógł być wyświetlany użytkownikom lub deserializowany w celu przywrócenia oryginalnego typu danych. Ta konwersja może stwarzać wiele wyzwań:

- Sposób, w jaki wartości są przechowywane wewnętrznie, niekoniecznie odzwierciedla sposób, w jaki użytkownicy chcą je wyświetlić. Na przykład, numer telefonu może być przechowywany w formacie 8009999999, który nie jest zbyt czytelny. Zamiast tego, powinien być wyświetlany jako 800-999-9999. Zapoznaj się z sekcją [ciągów formatów niestandardowych](#custom-format-strings) , aby zapoznać się z przykładem, który formatuje liczbę w ten sposób.

- Czasami konwersja obiektu na jego reprezentację ciągu nie jest intuicyjna. Na przykład, nie wiadomo, jak powinien wyglądać ciąg reprezentujący obiekt temperatury lub osoby. Aby zapoznać się z przykładem, który formatuje obiekt temperatury na różne sposoby, zobacz sekcję [ciągi formatu standardowego](#standard-format-strings) .

- Wartości zwykle wymagają formatowania zależnego od kultury. Na przykład, w aplikacji, która używa numerów do odzwierciedlenia wartości pieniężnych, ciągi numeryczne powinny obejmować symbol waluty bieżącej kultury, separator grupy (w większości kultur jest to separator tysięcy) oraz symbol dziesiętny. Aby zapoznać się z przykładem, zobacz [Formatowanie wrażliwe na kulturę z sekcją dostawcy formatu](#culture-sensitive-formatting-with-format-providers) .

- Aplikacja może być zmuszona wyświetlić tę samą wartość na różne sposoby. Na przykład, aplikacja może reprezentować członka wyliczenia, wyświetlając ciąg reprezentujący jego nazwę lub wyświetlając jego podstawową wartość. Aby zapoznać się z przykładem, który formatuje element członkowski wyliczenia <xref:System.DayOfWeek> na różne sposoby, zobacz sekcję [ciągi formatu standardowego](#standard-format-strings) .

> [!NOTE]
> Formatowanie konwertuje wartość typu na reprezentację ciągu znaków. Analizowania składni jest przeciwieństwem formatowania. Operacja analizy składni tworzy wystąpienie typu danych z jego reprezentacji w postaci ciągu. Aby uzyskać informacje o konwertowaniu ciągów na inne typy danych, zobacz [Analizowanie ciągów](../../../docs/standard/base-types/parsing-strings.md).

Platforma .NET zapewnia obsługę formatowania zaawansowanego, która umożliwia deweloperom rozwiązywanie tych wymagań.

## <a name="formatting-in-net"></a>Formatowanie w programie .NET

Podstawowym mechanizmem formatowania jest domyślna implementacja metody <xref:System.Object.ToString%2A?displayProperty=nameWithType>, która została omówiona w [domyślnym formatowaniu przy użyciu metody ToString](#default-formatting-using-the-tostring-method) w dalszej części tego tematu. Jednak platforma .NET oferuje kilka sposobów modyfikowania i zwiększania obsługi formatowania domyślnego. Należą do nich między innymi:

- Zastępowanie metody <xref:System.Object.ToString%2A?displayProperty=nameWithType>, aby zdefiniować niestandardowy ciąg reprezentujący wartość obiektu. Aby uzyskać więcej informacji, zobacz sekcję [Zastępowanie metody ToString](#override-the-tostring-method) w dalszej części tego tematu.

- Definiowanie specyfikatorów formatu, które umożliwiają ciągowi reprezentującemu wartość obiektu przybieranie wielu form. Na przykład, specyfikator formatu "X" w następującej instrukcji konwertuje liczbę całkowitą na ciąg reprezentujący wartość szesnastkową.

     [!code-csharp[Conceptual.Formatting.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#3)]
     [!code-vb[Conceptual.Formatting.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#3)]

     Aby uzyskać więcej informacji na temat specyfikatorów formatu, zobacz sekcję [metody ToString i ciągi formatu](#the-tostring-method-and-format-strings) .

- Korzystanie z dostawców formatu, aby skorzystać z konwencji formatowania określonej kultury. Na przykład, poniższa instrukcja wyświetla wartość waluty przy użyciu konwencji formatowania kultury en-US.

     [!code-csharp[Conceptual.Formatting.Overview#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#10)]
     [!code-vb[Conceptual.Formatting.Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#10)]

     Aby uzyskać więcej informacji o formatowaniu z dostawcami formatu, zobacz sekcję about [Providers (dostawcy formatu](#culture-sensitive-formatting-with-format-providers) ).

- Implementacja interfejsu <xref:System.IFormattable> w celu obsługi zarówno konwersji ciągów z klasą <xref:System.Convert>, jak i formatowania złożonego. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [interfejsu IFormattable](#the-iformattable-interface) .

- Używanie formatowania złożonego, aby osadzić ciąg reprezentujący wartość w dłuższym ciągu. Aby uzyskać więcej informacji, zobacz sekcję [formatowanie złożone](#composite-formatting) .

- Implementacja <xref:System.ICustomFormatter> i <xref:System.IFormatProvider> w celu dostarczenia kompletnego rozwiązania formatowania niestandardowego. Aby uzyskać więcej informacji, zobacz sekcję [formatowanie niestandardowe z ICustomFormatter](#custom-formatting-with-icustomformatter) .

Poniższe sekcje opisują te metody konwersji obiektu na jego reprezentację ciągu.

## <a name="default-formatting-using-the-tostring-method"></a>Formatowanie domyślne przy użyciu metody ToString

Każdy typ, który pochodzi od <xref:System.Object?displayProperty=nameWithType>, automatycznie dziedziczy metodę `ToString` bez parametrów, która domyślnie zwraca nazwę typu. Poniższy przykład ilustruje domyślną metodę `ToString`. Definiuje klasę o nazwie `Automobile`, która nie ma implementacji. Kiedy utworzona zostanie instancja tej klasy i zostanie wywołana jej metoda `ToString`, wyświetla się nazwa jej typu. Zwróć uwagę, że metoda `ToString` nie jest w przykładzie wywoływana jawnie. Metoda <xref:System.Console.WriteLine%28System.Object%29?displayProperty=nameWithType> niejawnie wywołuje metodę `ToString` obiektu przekazanego do niej jako argument.

[!code-csharp[Conceptual.Formatting.Overview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/default1.cs#1)]
[!code-vb[Conceptual.Formatting.Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/default1.vb#1)]

> [!WARNING]
> Począwszy od Windows 8.1, środowisko wykonawcze systemu Windows zawiera interfejs <xref:Windows.Foundation.IStringable> z pojedynczą metodą [IStringable. ToString](xref:Windows.Foundation.IStringable.ToString%2A), która zapewnia obsługę formatowania domyślnego. Jednak zalecamy, aby typy zarządzane nie implementowały interfejsu `IStringable`. Aby uzyskać więcej informacji, zobacz sekcję "środowisko wykonawcze systemu Windows i interfejs `IStringable`" na stronie odwołania <xref:System.Object.ToString%2A?displayProperty=nameWithType>.

Ponieważ wszystkie typy inne niż interfejsy są pochodną obiektu <xref:System.Object>, ta funkcjonalność jest dostarczana automatycznie do niestandardowych klas lub struktur. Jednak funkcjonalność oferowana przez domyślną metodę `ToString` jest ograniczona: mimo że identyfikuje typ, nie podaje żadnych informacji o instancji tego typu. Aby zapewnić reprezentację ciągu obiektu, który zawiera informacje dotyczące tego obiektu, musisz zastąpić metodę `ToString`.

> [!NOTE]
> Struktury dziedziczą z <xref:System.ValueType>, który z kolei pochodzi od <xref:System.Object>. Chociaż obiekt <xref:System.ValueType> zastępuje obiekt <xref:System.Object.ToString%2A?displayProperty=nameWithType>, jego implementacja jest identyczna.

## <a name="override-the-tostring-method"></a>Zastąp metodę ToString

Zastosowanie wyświetlania nazwy typu jest zwykle ograniczone i nie pozwala użytkownikom typów na odróżnianie jednej instancji od drugiej. Możesz jednak zmienić metodę `ToString` w celu zapewnienia bardziej użytecznej reprezentacji wartości obiektu. W poniższym przykładzie zdefiniowano obiekt `Temperature` i zastąpiono jego metodę `ToString`, aby temperatura była wyświetlana w stopniach Celsjusza.

[!code-csharp[Conceptual.Formatting.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/overrides1.cs#2)]
[!code-vb[Conceptual.Formatting.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/overrides1.vb#2)]

W programie .NET Metoda `ToString` każdego typu wartości pierwotnej została zastąpiona, aby wyświetlić wartość obiektu zamiast jego nazwy. W poniższej tabeli przedstawiono zastąpienie dla każdego podstawowego typu. Zwróć uwagę, że większość zastąpionych metod wywołuje inne przeciążenie metody `ToString` i przekazuje mu specyfikator formatu "G", który definiuje format ogólny dla jego typu, oraz obiekt <xref:System.IFormatProvider>, który reprezentuje bieżącą kulturę.

|Typ|Zastępowanie ToString|
|----------|-----------------------|
|<xref:System.Boolean>|Zwraca albo <xref:System.Boolean.TrueString?displayProperty=nameWithType>, albo <xref:System.Boolean.FalseString?displayProperty=nameWithType>.|
|<xref:System.Byte>|Wywołuje metodę `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` do sformatowania wartości <xref:System.Byte> dla bieżącej kultury.|
|<xref:System.Char>|Zwraca znak jako ciąg znaków.|
|<xref:System.DateTime>|Wywołuje metodę `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` do sformatowania wartości daty i godziny dla bieżącej kultury.|
|<xref:System.Decimal>|Wywołuje metodę `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` do sformatowania wartości <xref:System.Decimal> dla bieżącej kultury.|
|<xref:System.Double>|Wywołuje metodę `Double.ToString("G", NumberFormatInfo.CurrentInfo)` do sformatowania wartości <xref:System.Double> dla bieżącej kultury.|
|<xref:System.Int16>|Wywołuje metodę `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` do sformatowania wartości <xref:System.Int16> dla bieżącej kultury.|
|<xref:System.Int32>|Wywołuje metodę `Int32.ToString("G", NumberFormatInfo.CurrentInfo)` do sformatowania wartości <xref:System.Int32> dla bieżącej kultury.|
|<xref:System.Int64>|Wywołuje metodę `Int64.ToString("G", NumberFormatInfo.CurrentInfo)` do sformatowania wartości <xref:System.Int64> dla bieżącej kultury.|
|<xref:System.SByte>|Wywołuje metodę `SByte.ToString("G", NumberFormatInfo.CurrentInfo)` do sformatowania wartości <xref:System.SByte> dla bieżącej kultury.|
|<xref:System.Single>|Wywołuje metodę `Single.ToString("G", NumberFormatInfo.CurrentInfo)` do sformatowania wartości <xref:System.Single> dla bieżącej kultury.|
|<xref:System.UInt16>|Wywołuje metodę `UInt16.ToString("G", NumberFormatInfo.CurrentInfo)` do sformatowania wartości <xref:System.UInt16> dla bieżącej kultury.|
|<xref:System.UInt32>|Wywołuje metodę `UInt32.ToString("G", NumberFormatInfo.CurrentInfo)` do sformatowania wartości <xref:System.UInt32> dla bieżącej kultury.|
|<xref:System.UInt64>|Wywołuje metodę `UInt64.ToString("G", NumberFormatInfo.CurrentInfo)` do sformatowania wartości <xref:System.UInt64> dla bieżącej kultury.|

## <a name="the-tostring-method-and-format-strings"></a>Metody ToString i ciągi formatujące

Opieranie się na domyślnej metodzie `ToString` lub zastępowanie `ToString` jest odpowiednie, jeśli obiekt ma jedną reprezentację ciągu. Jednak wartość obiektu często ma wiele reprezentacji. Na przykład, temperatury mogą być wyrażone w stopniach Fahrenheita, stopniach Celsjusza lub kelwinach. Podobnie, wartość całkowita 10 może być reprezentowana na wiele sposobów, w tym 10, 10,0, 1.0e01 lub 10,00 zł.

Aby włączyć pojedynczą wartość, aby zawierała wiele reprezentacji ciągów, platforma .NET używa ciągów formatu. Ciąg formatu to ciąg, który zawiera jeden lub więcej wstępnie zdefiniowanych specyfikatorów formatu, którymi są pojedyncze znaki lub grupy znaków, które definiują sposób, w jaki metoda `ToString` powinna formatować swoje dane wyjściowe. Ciąg formatu, który jest następnie przekazywany jako parametr do metody obiektu `ToString` i określa wygląd ciągu reprezentującego wartość tego obiektu.

Wszystkie typy liczbowe, typy daty i godziny oraz typy wyliczeniowe w programie .NET obsługują wstępnie zdefiniowany zestaw specyfikatorów formatu. Możesz również używać ciągów formatów w celu definiowania wielu ciągów znaków reprezentujących typy danych zdefiniowane przez aplikację.

### <a name="standard-format-strings"></a>Ciągi formatu standardowego

Ciąg formatu standardowego zawiera jeden specyfikator formatu, który jest znakiem alfabetycznym, który definiuje ciąg reprezentujący obiekt, do którego ma zastosowanie, wraz z opcjonalnym specyfikatorem dokładności, który wpływa na liczbę cyfr wyświetlanych w ciągu wyniku. Jeśli specyfikator dokładności zostanie pominięty lub nie jest obsługiwany, specyfikator formatu standardowego jest równoważny ciągowi formatu standardowego.

Platforma .NET definiuje zestaw specyfikatorów formatu standardowego dla wszystkich typów liczbowych, wszystkich typów daty i godziny oraz wszystkich typów wyliczeniowych. Na przykład, każda z tych kategorii obsługuje specyfikator formatu standardowego "G", który definiuje ogólny ciąg reprezentujący wartość tego typu.

Ciągi formatu standardowego dla typów wyliczeń bezpośrednio kontrolują reprezentację ciągu wartości. Ciągi formatu przekazane do metody wartości wyliczenia `ToString` ustalają, czy wartość jest wyświetlana przy użyciu nazwy ciągu (specyfikatory formatu "G" i "F"), jego podstawowej wartości całkowitej (specyfikator formatu "D"), czy jego wartości szesnastkowej (specyfikator formatu "X"). Poniższy przykład ilustruje użycie ciągów formatu standardowego w celu formatowania wartości wyliczenia <xref:System.DayOfWeek>.

[!code-csharp[Conceptual.Formatting.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/standard1.cs#4)]
[!code-vb[Conceptual.Formatting.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/standard1.vb#4)]

Aby uzyskać informacje na temat ciągów formatu wyliczenia, zobacz [ciągi formatujące Wyliczenie](../../../docs/standard/base-types/enumeration-format-strings.md).

Ciągi formatu standardowego dla typów numerycznych zazwyczaj definiują ciąg wynikowy, którego dokładny wygląd jest kontrolowany przez jedną lub więcej wartości właściwości. Na przykład, specyfikator formatu "C" formatuje liczbę jako wartość walutową. Gdy wywołujesz metodę `ToString` ze specyfikatorem formartu "C" jako jedynym parametrem, następujące wartości właściwości z obiektu bieżącej kultury <xref:System.Globalization.NumberFormatInfo> są używane do definiowania ciągu reprezentującego wartość liczbową:

- Właściwość <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A>, która określa symbol waluty bieżącej kultury.

- Właściwość <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> lub <xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A>, która zwraca liczbę całkowitą, która określa następujące:

  - Położenie symbolu waluty.

  - Czy wartości ujemne są wskazywane przez wiodący znak ujemny, końcowy znak ujemny lub nawiasy.

  - Czy spacja pojawia się między wartością numeryczną i symbolem waluty.

- Właściwość <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A>, która określa liczbę cyfr dziesiętnych w ciągu wyniku.

- Właściwość <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A>, która określa symbol separatora dziesiętnego w ciągu wyniku.

- Właściwość <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A>, która określa symbol separatora grupy.

- Właściwość <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A>, która określa liczbę cyfr w każdej grupie na lewo od separatora dziesiętnego.

- Właściwość <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>, która określa znak ujemny używany w ciągu wyniku, jeśli do wskazywania wartości ujemnych nie stosuje się nawiasów.

Dodatkowo ciągi formatów liczbowych mogą zawierać specyfikator dokładności. Znaczenie tego specyfikatora zależy od ciągu formatu, z którym jest używany, ale zazwyczaj wskazuje albo całkowitą liczbę znaków, albo liczbę cyfr dziesiętnych, które powinny być wyświetlane w wynikowym ciągu znaków. Na przykład, w poniższym przykładzie użyto standardowego ciągu numerycznego "X4" i specyfikatora dokładności, aby utworzyć wartość ciągu, która ma cztery cyfry szesnastkowe.

[!code-csharp[Conceptual.Formatting.Overview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/precisionspecifier1.cs#6)]
[!code-vb[Conceptual.Formatting.Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/precisionspecifier1.vb#6)]

Aby uzyskać więcej informacji na temat standardowych ciągów formatowania liczbowego, zobacz [Standardowe ciągi formatujące](../../../docs/standard/base-types/standard-numeric-format-strings.md).

Ciągi formatu standardowego dla wartości daty i godziny to aliasy dla ciągów formatów niestandardowych, zapisanych przez określoną właściwość <xref:System.Globalization.DateTimeFormatInfo>. Na przykład, wywołanie metody `ToString` wartości daty i godziny ze specyfikatorem formatu "D" wyświetla datę i godzinę przy użyciu ciągu w formacie niestandardowym zapisanego we właściwości bieżącej kultury <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType>. (Aby uzyskać więcej informacji na temat ciągów formatu niestandardowego, zobacz [następną sekcję](#custom-format-strings)). Poniższy przykład ilustruje tę relację.

[!code-csharp[Conceptual.Formatting.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/alias1.cs#5)]
[!code-vb[Conceptual.Formatting.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/alias1.vb#5)]

Aby uzyskać więcej informacji na temat standardowych ciągów formatu daty i godziny, zobacz [ciągi standardowych formatów daty i godziny](../../../docs/standard/base-types/standard-date-and-time-format-strings.md).

Możesz również użyć ciągów formatu standardowego do definiowania ciągu reprezentującego obiekt zdefiniowany przez aplikację, który jest produkowany przez metodę obiektu `ToString(String)`. Możesz zdefiniować określone specyfikatory formatu standardowego, które obsługuje twój obiekt, i możesz określić, czy rozróżniają wielkie i małe litery, czy nie. Twoja implementacja metody `ToString(String)` powinna obsługiwać następujące:

- Specyfikator formatu „G” reprezentujący zwyczajowy lub wspólny format obiektu. Przeciążenie bez parametrów metody obiektu `ToString` powinno wywołać jej przeciążenie `ToString(String)` i przekazać mu ciąg formatu standardowego "G".

- Obsługa specyfikatora formatu, który jest równy odwołaniu o wartości null (`Nothing` w języku Visual Basic). Specyfikator formatu, który jest równy odwołaniu o wartości null, powinien być uznany za równoważny specyfikatorowi formatu „G”.

Na przykład, klasa `Temperature` może wewnętrznie przechowywać temperaturę w stopniach Celsjusza i używać specyfikatorów formatu do reprezentowania wartości obiektu `Temperature` w stopniach Celsjusza, stopniach Fahrenheita i kelwinach. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.Formatting.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/appstandard1.cs#7)]
[!code-vb[Conceptual.Formatting.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/appstandard1.vb#7)]

### <a name="custom-format-strings"></a>Niestandardowe ciągi formatowania

Oprócz standardowych ciągów formatu, .NET definiuje niestandardowe ciągi formatu dla wartości liczbowych i wartości daty i godziny. Ciąg formatu niestandardowego składa się z jednego lub więcej specyfikatorów formatu niestandardowego, które definiują ciąg reprezentujący wartość. Na przykład, ciąg w niestandardowy formacie daty i godziny "yyyy/mm/dd hh:mm:ss.ffff t zzz" konwertuje datę na ciąg reprezentujący w formacie "2008/11/15 07:45:00.0000 P -08:00" dla kultury en-US. Podobnie, ciąg formatu niestandardowego "0000" konwertuje wartość całkowitą 12 na "0012". Aby zapoznać się z pełną listą niestandardowych ciągów formatujących, zobacz [Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) oraz [Niestandardowe ciągi formatujące liczbowe](../../../docs/standard/base-types/custom-numeric-format-strings.md).

Jeżeli ciąg formatu zawiera pojedynczy specyfikator formatu niestandardowego, specyfikator formatu powinien być poprzedzony symbolem procenta (%), aby uniknąć problemów ze specyfikatorem formatu standardowego. W poniższym przykładzie użyto specyfikatora formatu niestandardowego "M" do wyświetlania jedno- lub 2-cyfrowego numeru miesiąca z określonej daty.

[!code-csharp[Conceptual.Formatting.Overview#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/singlecustom1.cs#8)]
[!code-vb[Conceptual.Formatting.Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/singlecustom1.vb#8)]

Wiele ciągów formatu standardowego dla wartości daty i godziny to aliasy dla ciągów formatów niestandardowych, definiowanych przez właściwości obiektu <xref:System.Globalization.DateTimeFormatInfo> obiektu. Ciągi formatów niestandardowych oferują również znaczną elastyczność w dostarczaniu formatowania zdefiniowanego przez aplikację dla wartości numerycznych lub wartości daty i godziny. Możesz definiować własne niestandardowe ciągi wyników dla wartości numerycznych oraz wartości daty i godziny, łącząc wiele specyfikatorów formatu niestandardowego w jeden ciąg formatu niestandardowego. W poniższym przykładzie zdefiniowano ciąg formatu niestandardowego, który wyświetla dzień tygodnia w nawiasie po nazwie miesiąca, dnia i roku.

[!code-csharp[Conceptual.Formatting.Overview#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/custom1.cs#9)]
[!code-vb[Conceptual.Formatting.Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/custom1.vb#9)]

W poniższym przykładzie zdefiniowano ciąg formatu niestandardowego, który wyświetla wartość <xref:System.Int64> wartość jako standardowy amerykański 7-cyfrowy numer telefonu wraz z jego numerem kierunkowym.

[!code-csharp[Conceptual.Formatting.Overview#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/telnumber1.cs#21)]
[!code-vb[Conceptual.Formatting.Overview#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/telnumber1.vb#21)]

Chociaż ciągi formatów standardowych zazwyczaj mogą obsługiwać większość potrzeb formatowania dla Twoich typów zdefiniowanych przez aplikację, można również zdefiniować specyfikatory niestandardowego format, aby sformatować swoje typy.

### <a name="format-strings-and-net-types"></a>Ciągi formatujące i typy .NET

Wszystkie typy liczbowe (czyli <xref:System.Byte>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>i <xref:System.Numerics.BigInteger>), a także <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, <xref:System.Guid>i wszystkie typy wyliczeniowe, obsługują formatowanie ciągów formatu. Informacje o określonych ciągach formatu obsługiwanych przez poszczególne typy można znaleźć w następujących tematach:

|Tytuł|Definicja|
|-----------|----------------|
|[Standardowe ciągi formatujące liczby](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Opisuje ciągi w standardowym formacie, które są używane do tworzenia często stosowanych ciągów reprezentujących wartości numeryczne.|
|[Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Opisuje tworzenie niestandardowych formatów ciągów, które tworzą formaty wartości numerycznych charakterystyczne dla aplikacji.|
|[Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Opisuje ciągi formatu standardowego, które tworzą często używane reprezentacje ciągu dla <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości.|
|[Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Opisuje niestandardowe ciągi formatujące, które tworzą formaty charakterystyczne dla aplikacji dla <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości.|
|[Standardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Opisuje ciągi w standardowym formacie, które są używane do tworzenia często stosowanych ciągów reprezentujących odstępy czasu.|
|[Niestandardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Opisuje tworzenie niestandardowych formatów ciągów, które tworzą formaty charakterystyczne dla aplikacji dla przedziałów czasowych.|
|[Ciągi formatujące wyliczenia](../../../docs/standard/base-types/enumeration-format-strings.md)|Opisuje ciągi w standardowym formacie, które są używane do tworzenia ciągów reprezentujących wartości wyliczenia.|
|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|Opisuje ciągi formatu standardowego dla wartości <xref:System.Guid>.|

## <a name="culture-sensitive-formatting-with-format-providers"></a>Uwzględnianie kulturowe formatowania z dostawcami formatowania

Chociaż specyfikatory formatu pozwalają dostosować formatowanie obiektów, wygenerowanie reprezentacji obiektów w postaci ciągów mających znaczenie często wymaga dodatkowych informacji o formatowaniu. Na przykład, formatowanie liczby jako wartości walutowej przy użyciu standardowego formatu ciągu "C" lub niestandardowego, takiego jak "$ #, #. 00", wymaga przynajmniej informacji o poprawnym symbolu waluty, separatorze grupy i separatorze dziesiętnym, które można uwzględnić w sformatowanym ciągu. W programie .NET te dodatkowe informacje o formatowaniu są udostępniane za pomocą interfejsu <xref:System.IFormatProvider>, który jest dostarczany jako parametr do jednego lub większej liczby przeciążeń metody `ToString` typów liczbowych i typów dat i godzin. implementacje <xref:System.IFormatProvider> są używane w programie .NET do obsługi formatowania specyficznego dla kultury. Poniższy przykład ilustruje, jak ciąg reprezentujący obiekt zmienia się podczas formatowania z trzema obiektami <xref:System.IFormatProvider>, które reprezentują różne kultury.

[!code-csharp[Conceptual.Formatting.Overview#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformatprovider1.cs#11)]
[!code-vb[Conceptual.Formatting.Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformatprovider1.vb#11)]

Interfejs <xref:System.IFormatProvider> zawiera jedną metodę, <xref:System.IFormatProvider.GetFormat%28System.Type%29>, która ma jeden parametr, określający typ obiektu, który zawiera informacje o formatowaniu. Jeżeli metoda może dostarczyć obiekt tego typu, zwraca go. W przeciwnym razie zwraca odwołanie o wartości null (`Nothing` w Visual Basic).

<xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> jest metodą wywołania zwrotnego. Gdy wywołujesz przeciążenie metody `ToString`, które zawiera parametr <xref:System.IFormatProvider>, wywołuje ono metodę <xref:System.IFormatProvider.GetFormat%2A> tego obiektu <xref:System.IFormatProvider>. Metoda <xref:System.IFormatProvider.GetFormat%2A> jest odpowiedzialna za zwrócenie obiektu, który dostarcza niezbędne informacje formatowania, określone przez jego parametr `formatType`, do metody `ToString`.

Wiele metod formatowania lub konwersji ciągów zawiera parametr typu <xref:System.IFormatProvider>, ale w wielu przypadkach wartość tego parametru jest ignorowana, gdy metoda jest wywoływana. Poniższa tabela zawiera listę niektórych metod formatowania, które używają parametru i typu obiektu <xref:System.Type>, który przekazują do metody <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType>.

|Metoda|Typ parametru `formatType`|
|------------|------------------------------------|
|Metoda `ToString` typów numerycznych|<xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>|
|Metoda `ToString` typów daty i godziny|<xref:System.Globalization.DateTimeFormatInfo?displayProperty=nameWithType>|
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|

> [!NOTE]
> Metody `ToString` typów numerycznych oraz typów daty i godziny są przeciążone, a tylko niektóre przeciążenia zawierają parametr <xref:System.IFormatProvider>. Jeśli metoda nie ma parametru typu <xref:System.IFormatProvider>, obiekt, który jest zwracany przez właściwość <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>, jest przekazywany zamiast tego. Na przykład, wywołanie domyślnej metody <xref:System.Int32.ToString?displayProperty=nameWithType> ostatecznie powoduje wywołanie metody, takie jak to: `Int32.ToString("G", System.Globalization.CultureInfo.CurrentCulture)`.

Platforma .NET udostępnia trzy klasy, które implementują <xref:System.IFormatProvider>:

- <xref:System.Globalization.DateTimeFormatInfo>, klasa, która zawiera informacje o formatowaniu dla wartości daty i godziny dla określonej kultury. Jego implementacja <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> zwraca instancję samego siebie.

- <xref:System.Globalization.NumberFormatInfo>, klasa, która dostarcza informacje o formatowaniu numerycznym specyficzne dla danej kultury. Jego implementacja <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> zwraca instancję samego siebie.

- <xref:System.Globalization.CultureInfo>. Jego implementacja <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> może zwracać albo obiekt <xref:System.Globalization.NumberFormatInfo>, aby zapewnić informacje dotyczące formatowania numerycznego, albo obiekt <xref:System.Globalization.DateTimeFormatInfo>, aby zapewnić informacje o formatowaniu dla wartości daty i godziny.

Możesz także zaimplementować własnego dostawcę formatu, aby zastąpić dowolną z tych klas. Jednak twoja implementacja metody <xref:System.IFormatProvider.GetFormat%2A> musi zwracać obiekt typu wymienionego w powyższej tabeli, jeśli musi zapewnić informacje o formatowaniu dla metody `ToString`.

### <a name="culture-sensitive-formatting-of-numeric-values"></a>Czułe na kulturę formatowanie wartości liczbowych

Domyślnie formatowanie wartości liczbowych uwzględnia kulturę. Jeśli nie określisz kultury przy wywołaniu metody formatowania, stosowane są konwencje formatowania kultury bieżącego wątku. Jest to zilustrowane w poniższym przykładzie, który zmienia bieżący wątek kultury cztery razy, a następnie wywołuje metodę <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>. W każdym przypadku ciąg wynikowy odzwierciedla konwencje formatowania bieżącej kultury. Dzieje się tak dlatego, że metody `ToString` i `ToString(String)` owijają odwołania do każdej metody typu numerycznego `ToString(String, IFormatProvider)`.

[!code-csharp[Conceptual.Formatting.Overview#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific3.cs#19)]
[!code-vb[Conceptual.Formatting.Overview#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific3.vb#19)]

Możesz również sformatować wartość numeryczną dla określonej kultury poprzez wywołanie przeciążenia `ToString`, które ma parametr `provider`, i podając mu jedno z następujących:

- Obiekt <xref:System.Globalization.CultureInfo> reprezentujący kulturę, której konwencje formatowania mają zostać użyte. Jego metoda <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> zwraca wartość właściwości <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType>, która jest obiektem <xref:System.Globalization.NumberFormatInfo>, który zawiera charakterystyczne dla kultury informacje o formatowaniu wartości numerycznych.

- Obiekt <xref:System.Globalization.NumberFormatInfo> definiujący konwencje formatowania specyficzne dla kultury, które mają być używane. Jego metoda <xref:System.Globalization.NumberFormatInfo.GetFormat%2A> zwraca instancję samego siebie.

W poniższym przykładzie użyto obiektów <xref:System.Globalization.NumberFormatInfo>, które reprezentują kultury angielska (Stany Zjednoczone) i angielska (Wielka Brytania) oraz kultury neutralne francuska i rosyjska w celu sformatowania liczby zmiennopozycyjnej.

[!code-csharp[Conceptual.Formatting.Overview#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific4.cs#20)]
[!code-vb[Conceptual.Formatting.Overview#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific4.vb#20)]

### <a name="culture-sensitive-formatting-of-date-and-time-values"></a>Czułe na kulturowe formatowanie wartości daty i godziny

Domyślnie formatowanie wartości daty i godziny uwzględnia kulturę. Jeśli nie określisz kultury przy wywołaniu metody formatowania, stosowane są konwencje formatowania kultury bieżącego wątku. Jest to zilustrowane w poniższym przykładzie, który zmienia bieżący wątek kultury cztery razy, a następnie wywołuje metodę <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>. W każdym przypadku ciąg wynikowy odzwierciedla konwencje formatowania bieżącej kultury. Dzieje się tak dlatego, że metody <xref:System.DateTime.ToString?displayProperty=nameWithType>, <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType> i <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> owijają wywołania do metod <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> i <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>.

[!code-csharp[Conceptual.Formatting.Overview#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific1.cs#17)]
[!code-vb[Conceptual.Formatting.Overview#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific1.vb#17)]

Możesz również sformatować wartość daty i godziny dla określonej kultury poprzez wywołanie przeciążenia <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> , które ma parametr `provider`, i podając mu jedno z następujących:

- Obiekt <xref:System.Globalization.CultureInfo> reprezentujący kulturę, której konwencje formatowania mają zostać użyte. Jego metoda <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> zwraca wartość właściwości <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>, która jest obiektem <xref:System.Globalization.DateTimeFormatInfo>, który zawiera charakterystyczne dla kultury informacje o formatowaniu wartości daty i godziny.

- Obiekt <xref:System.Globalization.DateTimeFormatInfo> definiujący konwencje formatowania specyficzne dla kultury, które mają być używane. Jego metoda <xref:System.Globalization.DateTimeFormatInfo.GetFormat%2A> zwraca instancję samego siebie.

W poniższym przykładzie użyto obiektów <xref:System.Globalization.DateTimeFormatInfo>, które reprezentują kultury angielska (Stany Zjednoczone) i angielska (Wielka Brytania) oraz kultury neutralne francuska i rosyjska w celu sformatowania daty.

[!code-csharp[Conceptual.Formatting.Overview#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific2.cs#18)]
[!code-vb[Conceptual.Formatting.Overview#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific2.vb#18)]

## <a name="the-iformattable-interface"></a>Interfejs IFormattable

Zwykle typy, które przeciążają metodę `ToString` ciągiem formatowania i parametrem <xref:System.IFormatProvider>, implementują też interfejs <xref:System.IFormattable>. Ten interfejs ma jeden element członkowski, <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, który jako parametry zawiera zarówno ciąg formatu, jak i dostawcę formatu.

Iplementacja interfejsu <xref:System.IFormattable> w klasie zdefiniowanej przez aplikację ma dwie zalety:

- Obsługa konwersji ciągów przez klasę <xref:System.Convert>. Wywołania metod <xref:System.Convert.ToString%28System.Object%29?displayProperty=nameWithType> i <xref:System.Convert.ToString%28System.Object%2CSystem.IFormatProvider%29?displayProperty=nameWithType> wywołują implementację metody <xref:System.IFormattable> automatycznie.

- Obsługa formatowania złożonego. Jeśli element formatu, który zawiera ciąg formatu, jest używany do formatowania niestandardowego typu, aparat plików wykonywalnych języka wspólnego automatycznie wywołuje twoją implementację <xref:System.IFormattable> i przekazuje jej ciąg formatu. Aby uzyskać więcej informacji na temat formatowania złożonego przy użyciu metod, takich jak <xref:System.String.Format%2A?displayProperty=nameWithType> lub <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, zobacz sekcję [formatowanie złożone](#composite-formatting) .

W poniższym przykładzie zdefiniowano klasę `Temperature` implementującą interfejs <xref:System.IFormattable>. Obsługuje ona specyfikatory formatu "C" lub "G" wyświetlające temperaturę w stopniach Celsjusza, specyfikator formatu "F" wyświetlający temperaturę w stopniach Fahrenheita oraz specyfikator formatu "K" wyświetlający temperaturę w kelwinach.

[!code-csharp[Conceptual.Formatting.Overview#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#12)]
[!code-vb[Conceptual.Formatting.Overview#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#12)]

Poniższy przykład tworzy wystąpienie obiektu `Temperature`. Następnie wywołuje metodę <xref:System.Convert.ToString%2A> i stosuje kilka ciągów formatowania złożonego w celu uzyskania różnych reprezentacji ciągów obiektu `Temperature`. Każda z tych wywołań metody wywołuje z kolei implementację <xref:System.IFormattable> klasy `Temperature`.

[!code-csharp[Conceptual.Formatting.Overview#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#13)]
[!code-vb[Conceptual.Formatting.Overview#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#13)]

## <a name="composite-formatting"></a>Formatowanie złożone

Niektóre metody, takie jak <xref:System.String.Format%2A?displayProperty=nameWithType> i <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, obsługują formatowanie złożone. Złożony ciąg formatu jest to rodzaj szablonu, który zwraca jeden ciąg, który zawiera ciąg reprezentujący zero, jeden lub więcej obiektów. Każdy obiekt jest reprezentowany w ciągu w złożonym formacie przez indeksowany element formatu. Indeks elementu formatu odnosi się do położenia obiektu, który reprezentuje on na liście parametrów metody. Indeksy są od zera. Na przykład, w następującym wywołaniu metody <xref:System.String.Format%2A?displayProperty=nameWithType>, pierwszy element formatu, `{0:D}`, jest zastępowany ciągiem reprezentującym `thatDate`; drugi element formatu `{1}`, jest zastępowany ciągiem reprezentującym `item1`; a trzeci element formatu `{2:C2}` jest zastępowany ciągiem reprezentującym `item1.Value`.

[!code-csharp[Conceptual.Formatting.Overview#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite1.cs#14)]
[!code-vb[Conceptual.Formatting.Overview#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite1.vb#14)]

Oprócz zamiany elementu formatu na ciąg reprezentujący odpowiadający mu obiekt, elementy formatu umożliwiają również kontrolę następujących elementów:

- Określony sposób, w którym obiekt jest reprezentowany jako ciąg, jeśli obiekt implementuje interfejs <xref:System.IFormattable> i obsługuje ciągi formatu. Można to zrobić, wykonując indeks elementu formatowania z `:` (dwukropek), po którym następuje prawidłowy ciąg formatu. W poprzednim przykładzie pokazano, jak sformatować wartość daty za pomocą ciągu formatu "d" (krótkiej daty) (np., `{0:d}`) i przez sformatowanie wartości liczbowej z ciągiem formatu "C2" (np., `{2:C2}` do reprezentowania liczby jako wartości walutowej z dwiema cyframi dziesiętnymi.

- Szerokość pola zawierającego reprezentację ciągu obiektu oraz wyrównanie ciągu reprezentującego w tym polu. W tym celu należy postępować zgodnie z indeksem elementu formatowania z `,` (przecinkiem). Ciąg jest wyrównany do prawej w polu, jeśli szerokość pola jest wartością dodatnią i jest wyrównany do lewej, jeśli szerokość pola jest wartością ujemną. Poniższy przykład wyrównuje wartości dat w polu 20-znakowym i wyrównuje wartości dziesiętne z jedną cyfrą ułamkową w polu 11-znakowym.

     [!code-csharp[Conceptual.Formatting.Overview#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite2.cs#22)]
     [!code-vb[Conceptual.Formatting.Overview#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite2.vb#22)]

     Należy zauważyć, że jeśli zarówno składnik ciągu wyrównania, jak i składnik ciągu formatu są obecne, dawniej poprzedza ostatni (na przykład `{0,-20:g}`.

Aby uzyskać więcej informacji na temat formatowania złożonego, zobacz [formatowanie złożone](../../../docs/standard/base-types/composite-formatting.md).

## <a name="custom-formatting-with-icustomformatter"></a>Niestandardowe formatowanie za pomocą ICustomFormatter

Dwie metody formatowania złożonego, <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> i <xref:System.Text.StringBuilder.AppendFormat%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, obejmują parametr dostawcy formatowania, który obsługuje formatowanie niestandardowe. Kiedy wywoływana jest któraś z tych metod formatowania, przekazuje obiekt <xref:System.Type>, który reprezentuje interfejs <xref:System.ICustomFormatter> dla metody dostawcy formatowania <xref:System.IFormatProvider.GetFormat%2A>. Metoda <xref:System.IFormatProvider.GetFormat%2A> jest następnie odpowiedzialna za zwrócenie implementacji <xref:System.ICustomFormatter>, która zawiera niestandardowe formatowanie.

Interfejs <xref:System.ICustomFormatter> zawiera jedną metodę <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29>, która jest wywoływana automatycznie przez metodę formatowania złożonego, jeden raz dla każdego elementu formatu w ciągu formatowania złożonego. Metoda <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29> ma trzy parametry: ciąg formatu, który reprezentuje argument `formatString` w elemencie formatu, formatowany obiekt oraz obiekt <xref:System.IFormatProvider>, który dostarcza usługi formatowania. Zazwyczaj klasa, która implementuje <xref:System.ICustomFormatter>, implementuje również <xref:System.IFormatProvider>, więc ten ostatni parametr jest odwołaniem do samej klasy formatowania niestandardowego. Metoda zwraca reprezentację ciągu formatu niestandardowego obiektu, który ma zostać sformatowany. Jeśli metoda nie może sformatować obiektu, powinna zwrócić odwołanie o wartości null (`Nothing` w języku Visual Basic).

W poniższym przykładzie przedstawiono implementację <xref:System.ICustomFormatter> o nazwie `ByteByByteFormatter`, która wyświetla wartości całkowite jako sekwencję dwucyfrowych wartości szesnastkowych, po których występuje spacja.

[!code-csharp[Conceptual.Formatting.Overview#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#15)]
[!code-vb[Conceptual.Formatting.Overview#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#15)]

W poniższym przykładzie użyto klasy `ByteByByteFormatter` w celu formatowania wartości całkowitych. Należy zauważyć, że metoda <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> jest wywoływana więcej niż raz w drugim wywołaniu metody <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> i że domyślny dostawca <xref:System.Globalization.NumberFormatInfo> jest używany w trzecim wywołaniu metody, ponieważ.`ByteByByteFormatter.Format` Metoda nie rozpoznaje ciągu formatu "N0" i zwraca odwołanie o wartości null (`Nothing` w Visual Basic).

[!code-csharp[Conceptual.Formatting.Overview#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#16)]
[!code-vb[Conceptual.Formatting.Overview#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#16)]

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Definicja|
|-----------|----------------|
|[Standardowe ciągi formatujące liczby](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Opisuje ciągi w standardowym formacie, które są używane do tworzenia często stosowanych ciągów reprezentujących wartości numeryczne.|
|[Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Opisuje tworzenie niestandardowych formatów ciągów, które tworzą formaty wartości numerycznych charakterystyczne dla aplikacji.|
|[Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Opisuje ciągi w standardowym formacie, które są używane do tworzenia często stosowanych ciągów reprezentujących wartości <xref:System.DateTime>.|
|[Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Opisuje tworzenie niestandardowych formatów ciągów, które tworzą formaty charakterystyczne dla aplikacji dla wartości <xref:System.DateTime>.|
|[Standardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Opisuje ciągi w standardowym formacie, które są używane do tworzenia często stosowanych ciągów reprezentujących odstępy czasu.|
|[Niestandardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Opisuje tworzenie niestandardowych formatów ciągów, które tworzą formaty charakterystyczne dla aplikacji dla przedziałów czasowych.|
|[Ciągi formatujące wyliczenia](../../../docs/standard/base-types/enumeration-format-strings.md)|Opisuje ciągi w standardowym formacie, które są używane do tworzenia ciągów reprezentujących wartości wyliczenia.|
|[Złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md)|Opisuje, jak osadzić jedną lub więcej sformatowanych wartości w ciągu. Następnie ciąg może być wyświetlany w konsoli lub zapisywany do strumienia.|
|[Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)|Zawiera listę tematów, które oferują instrukcje krok po kroku dotyczące wykonywania określonych operacji formatowania.|
|[Analizowanie ciągów](../../../docs/standard/base-types/parsing-strings.md)|Opisuje sposób inicjowania obiektów do wartości opisanych przez ciąg reprezentujący te obiekty. Analizowanie jest odwróconą operacją formatowania.|

## <a name="reference"></a>Tematy pomocy

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- <xref:System.ICustomFormatter?displayProperty=nameWithType>
