---
title: Typy formatowania w .NET
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
ms.openlocfilehash: a1f4d9107427140bcfa6b49bc8a850432fb204f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75348249"
---
# <a name="format-types-in-net"></a>Formatowanie typów w .NET

Formatowanie to proces konwertowania wystąpienia klasy, struktury lub wartości wyliczenia na jego reprezentację ciągu, często w taki sposób, aby wynikowy ciąg mógł być wyświetlany użytkownikom lub deserializowany w celu przywrócenia oryginalnego typu danych. Konwersja ta może stanowić szereg wyzwań:

- Sposób, w jaki wartości są przechowywane wewnętrznie, niekoniecznie odzwierciedla sposób, w jaki użytkownicy chcą je wyświetlać. Na przykład numer telefonu może być przechowywany w formularzu 800999999999, który nie jest przyjazny dla użytkownika. Zamiast tego powinien być wyświetlany jako 800-999-9999. Zobacz [sekcję Ciągi formatu niestandardowego](#custom-format-strings) dla przykładu, który formatuje liczbę w ten sposób.

- Czasami konwersja obiektu na jego reprezentację ciągu nie jest intuicyjna. Na przykład nie jest jasne, jak powinna wyglądać reprezentacja ciągu obiektu Temperature lub Person. Na przykład, który formatuje Temperature obiektu na różne sposoby, zobacz [standardowy format ciągi](#standard-format-strings) sekcji.

- Wartości często wymagają formatowania zależnego od kultury. Na przykład w aplikacji, która używa liczb do odzwierciedlenia wartości pieniężnych, ciągi liczbowe powinny zawierać symbol waluty bieżącej kultury, separator grupy (który w większości kultur jest separatorem tysięcy) i symbol dziesiętny. Na przykład zobacz [formatowanie zależne od kultury z dostawcami formatów](#culture-sensitive-formatting-with-format-providers) sekcji.

- Aplikacja może być musiała wyświetlić tę samą wartość na różne sposoby. Na przykład aplikacja może reprezentować element członkowski wyliczenia, wyświetlając reprezentację ciągu jego nazwy lub wyświetlając jego wartość podstawową. Na przykład, który formatuje <xref:System.DayOfWeek> element członkowski wyliczenia na różne sposoby, zobacz [standardowe ciągi formatu](#standard-format-strings) sekcji.

> [!NOTE]
> Formatowanie konwertuje wartość typu na reprezentację ciągu. Analizowanie jest odwrotnością formatowania. Operacja analizy tworzy wystąpienie typu danych z jego reprezentacji ciągu. Aby uzyskać informacje dotyczące konwertowania ciągów na inne typy danych, zobacz [Analizowanie ciągów](../../../docs/standard/base-types/parsing-strings.md).

Platforma .NET zapewnia obsługę formatowania rozbudowane, które umożliwia deweloperom spełnienie tych wymagań.

## <a name="formatting-in-net"></a>Formatowanie w .NET

Podstawowy mechanizm formatowania jest domyślną implementacją <xref:System.Object.ToString%2A?displayProperty=nameWithType> metody, która została omówiona w [domyślnego formatowania przy użyciu metody ToString](#default-formatting-using-the-tostring-method) w dalszej części tego tematu. Jednak platforma .NET udostępnia kilka sposobów modyfikowania i rozszerzania domyślnej obsługi formatowania. Należą do nich między innymi:

- Zastępowanie <xref:System.Object.ToString%2A?displayProperty=nameWithType> metody w celu zdefiniowania niestandardowej reprezentacji ciągu wartości obiektu. Aby uzyskać więcej informacji, zobacz [Zastępowanie Metody ciągów](#override-the-tostring-method) w dalszej części tego tematu.

- Definiowanie specyfikatorów formatu, które umożliwiają reprezentację ciągu wartości obiektu do wielu form. Na przykład specyfikator formatu "X" w poniższej instrukcji konwertuje liczbę całkowitą na reprezentację ciągu wartości szesnastkowej.

     [!code-csharp[Conceptual.Formatting.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#3)]
     [!code-vb[Conceptual.Formatting.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#3)]

     Aby uzyskać więcej informacji na temat specyfikatorów formatu, zobacz [ToString Metoda i Format ciągi](#the-tostring-method-and-format-strings) sekcji.

- Korzystanie z dostawców formatów, aby korzystać z konwencji formatowania określonej kultury. Na przykład w poniższej instrukcji wyświetla wartość waluty przy użyciu konwencji formatowania kultury en-US.

     [!code-csharp[Conceptual.Formatting.Overview#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#10)]
     [!code-vb[Conceptual.Formatting.Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#10)]

     Aby uzyskać więcej informacji na temat formatowania dostawców formatów, zobacz sekcję [Dostawcy formatów.](#culture-sensitive-formatting-with-format-providers)

- Implementowanie <xref:System.IFormattable> interfejsu do obsługi konwersji <xref:System.Convert> ciągów z klasy i formatowania złożonego. Aby uzyskać więcej informacji, zobacz [sekcję IFormattable Interface](#the-iformattable-interface) section.

- Za pomocą formatowania złożonego, aby osadzić reprezentację ciągu wartości w większym ciągu. Aby uzyskać więcej informacji, zobacz sekcję [Formatowanie kompozytowe.](#composite-formatting)

- <xref:System.ICustomFormatter> Implementowanie <xref:System.IFormatProvider> i zapewnienie kompletnego niestandardowego rozwiązania do formatowania. Aby uzyskać więcej informacji, zobacz [sekcję Formatowanie niestandardowe z iCustomFormatter.](#custom-formatting-with-icustomformatter)

W poniższych sekcjach zbadać te metody konwertowania obiektu do jego reprezentacji ciągu.

## <a name="default-formatting-using-the-tostring-method"></a>Domyślne formatowanie przy użyciu metody ToString

Każdy typ, który <xref:System.Object?displayProperty=nameWithType> jest pochodną automatycznie `ToString` dziedziczy metodę bezparametrową, która zwraca domyślnie nazwę typu. W poniższym przykładzie `ToString` przedstawiono metodę domyślną. Definiuje klasę o `Automobile` nazwie, która nie ma implementacji. Gdy klasa jest tworzone i `ToString` jego metoda jest wywoływana, wyświetla jego nazwę typu. Należy zauważyć, że `ToString` metoda nie jest jawnie wywoływana w przykładzie. Metoda <xref:System.Console.WriteLine%28System.Object%29?displayProperty=nameWithType> niejawnie `ToString` wywołuje metodę obiektu przekazywane do niego jako argument.

[!code-csharp[Conceptual.Formatting.Overview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/default1.cs#1)]
[!code-vb[Conceptual.Formatting.Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/default1.vb#1)]

> [!WARNING]
> Począwszy od systemu Windows 8.1, <xref:Windows.Foundation.IStringable> środowisko uruchomieniowe systemu Windows zawiera interfejs z jedną [metodą, IStringable.ToString](xref:Windows.Foundation.IStringable.ToString%2A), który zapewnia obsługę formatowania domyślnego. Jednak zaleca się, że typy `IStringable` zarządzane nie implementują interfejsu. Aby uzyskać więcej informacji, zobacz sekcję `IStringable` "Środowisko uruchomieniowe systemu Windows i interfejs" na stronie referencyjnej. <xref:System.Object.ToString%2A?displayProperty=nameWithType>

Ponieważ wszystkie typy inne niż interfejsy są uzyskiwane z, <xref:System.Object>ta funkcja jest automatycznie dostarczane do klas lub struktur niestandardowych. Jednak funkcjonalność oferowana przez `ToString` metodę domyślną jest ograniczona: Mimo że identyfikuje typ, nie dostarcza żadnych informacji o wystąpieniu typu. Aby zapewnić reprezentację ciągu obiektu, który zawiera informacje o `ToString` tym obiekcie, należy zastąpić metodę.

> [!NOTE]
> Struktury dziedziczą z <xref:System.ValueType>, co <xref:System.Object>z kolei pochodzi z . Mimo <xref:System.ValueType> że <xref:System.Object.ToString%2A?displayProperty=nameWithType>zastępuje, jego implementacja jest identyczna.

## <a name="override-the-tostring-method"></a>Zastąp metodę ToString

Wyświetlanie nazwy typu jest często ograniczone zastosowanie i nie pozwala konsumentom typów odróżnić jedno wystąpienie od innego. Można jednak zastąpić `ToString` metodę, aby zapewnić bardziej użyteczną reprezentację wartości obiektu. Poniższy przykład definiuje `Temperature` obiekt i zastępuje `ToString` jego metodę wyświetlania temperatury w stopniach Celsjusza.

[!code-csharp[Conceptual.Formatting.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/overrides1.cs#2)]
[!code-vb[Conceptual.Formatting.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/overrides1.vb#2)]

W .NET `ToString` metoda każdego typu wartości pierwotnej została zastąpiona, aby wyświetlić wartość obiektu zamiast jego nazwy. W poniższej tabeli przedstawiono zastąpienie dla każdego typu pierwotnego. Należy zauważyć, że większość zastąpionych metod wywołać inne przeciążenie `ToString` metody i przekazać go specyfikator formatu <xref:System.IFormatProvider> "G", który definiuje format ogólny dla jego typu i obiekt, który reprezentuje bieżącą kulturę.

|Typ|Zastępowanie ciągiem|
|----------|-----------------------|
|<xref:System.Boolean>|Zwraca <xref:System.Boolean.TrueString?displayProperty=nameWithType> wartość <xref:System.Boolean.FalseString?displayProperty=nameWithType>lub wartość .|
|<xref:System.Byte>|Wywołania, `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` <xref:System.Byte> aby sformatować wartość dla bieżącej kultury.|
|<xref:System.Char>|Zwraca znak jako ciąg znaków.|
|<xref:System.DateTime>|Wywołania, `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` aby sformatować wartość daty i godziny dla bieżącej kultury.|
|<xref:System.Decimal>|Wywołania, `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` <xref:System.Decimal> aby sformatować wartość dla bieżącej kultury.|
|<xref:System.Double>|Wywołania, `Double.ToString("G", NumberFormatInfo.CurrentInfo)` <xref:System.Double> aby sformatować wartość dla bieżącej kultury.|
|<xref:System.Int16>|Wywołania, `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` <xref:System.Int16> aby sformatować wartość dla bieżącej kultury.|
|<xref:System.Int32>|Wywołania, `Int32.ToString("G", NumberFormatInfo.CurrentInfo)` <xref:System.Int32> aby sformatować wartość dla bieżącej kultury.|
|<xref:System.Int64>|Wywołania, `Int64.ToString("G", NumberFormatInfo.CurrentInfo)` <xref:System.Int64> aby sformatować wartość dla bieżącej kultury.|
|<xref:System.SByte>|Wywołania, `SByte.ToString("G", NumberFormatInfo.CurrentInfo)` <xref:System.SByte> aby sformatować wartość dla bieżącej kultury.|
|<xref:System.Single>|Wywołania, `Single.ToString("G", NumberFormatInfo.CurrentInfo)` <xref:System.Single> aby sformatować wartość dla bieżącej kultury.|
|<xref:System.UInt16>|Wywołania, `UInt16.ToString("G", NumberFormatInfo.CurrentInfo)` <xref:System.UInt16> aby sformatować wartość dla bieżącej kultury.|
|<xref:System.UInt32>|Wywołania, `UInt32.ToString("G", NumberFormatInfo.CurrentInfo)` <xref:System.UInt32> aby sformatować wartość dla bieżącej kultury.|
|<xref:System.UInt64>|Wywołania, `UInt64.ToString("G", NumberFormatInfo.CurrentInfo)` <xref:System.UInt64> aby sformatować wartość dla bieżącej kultury.|

## <a name="the-tostring-method-and-format-strings"></a>Ciągi metody ToString i format

Poleganie na `ToString` domyślnej metody `ToString` lub zastępowanie jest odpowiednie, gdy obiekt ma reprezentację pojedynczego ciągu. Jednak wartość obiektu często ma wiele reprezentacji. Na przykład, temperatura może być wyrażona w stopniach Fahrenheita, stopni Celsjusza lub kelwinów. Podobnie wartość całkowita 10 może być reprezentowana na wiele sposobów, w tym 10, 10.0, 1.0e01 lub $10.00.

Aby włączyć pojedynczą wartość, aby mieć wiele reprezentacji ciągów, .NET używa ciągów formatu. Ciąg formatu to ciąg zawierający co najmniej jeden wstępnie zdefiniowany specyfikatory formatu, `ToString` które są pojedynczymi znakami lub grupami znaków, które definiują sposób formatowania jej danych wyjściowych przez metodę. Ciąg formatu jest następnie przekazywany jako `ToString` parametr do metody obiektu i określa, jak powinna wyglądać reprezentacja ciągu wartości tego obiektu.

Wszystkie typy liczbowe, typy dat i godzin oraz typy wyliczenia w .NET obsługują wstępnie zdefiniowany zestaw specyfikatorów formatów. Ciągi formatu można również użyć do zdefiniowania wielu reprezentacji ciągów typów danych zdefiniowanych przez aplikację.

### <a name="standard-format-strings"></a>Ciągi formatu standardowego

Standardowy ciąg formatu zawiera specyfikator pojedynczego formatu, który jest znakiem alfabetycznym, który definiuje reprezentację ciągu obiektu, do którego jest stosowany, wraz z opcjonalnym specyfikatorem precyzji, który wpływa na liczbę cyfr wyświetlanych w ciąg wynik. Jeśli specyfikator precyzji zostanie pominięty lub nie jest obsługiwany, specyfikator formatu standardowego jest odpowiednikiem standardowego ciągu formatu.

Program .NET definiuje zestaw specyfikatorów formatu standardowego dla wszystkich typów liczbowych, wszystkich typów dat i godzin oraz wszystkich typów wyliczania. Na przykład każda z tych kategorii obsługuje specyfikator formatu standardowego "G", który definiuje ogólne reprezentacji ciągów wartości tego typu.

Standardowe ciągi formatu dla typów wyliczenia bezpośrednio sterują reprezentacją ciągu wartości. Ciągi formatu przekazywane do metody wartości `ToString` wyliczenia określają, czy wartość jest wyświetlana przy użyciu jej nazwy ciągu (specyfikatory formatu "G" i "F"), jego podstawowej wartości integralnej (specyfikator formatu "D") lub jego wartości szesnastkowej (specyfikator formatu "X"). W poniższym przykładzie przedstawiono użycie standardowych ciągów <xref:System.DayOfWeek> formatu do formatowania wartości wyliczenia.

[!code-csharp[Conceptual.Formatting.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/standard1.cs#4)]
[!code-vb[Conceptual.Formatting.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/standard1.vb#4)]

Aby uzyskać informacje o ciągach formatu wyliczenia, zobacz [Ciągi formatu wyliczenia](../../../docs/standard/base-types/enumeration-format-strings.md).

Standardowe ciągi formatu dla typów numerycznych zwykle definiują ciąg wynikowy, którego dokładny wygląd jest kontrolowany przez jedną lub więcej wartości właściwości. Na przykład specyfikator formatu "C" formatuje liczbę jako wartość waluty. Podczas wywoływania `ToString` metody z specyfikatorem formatu "C" jako tylko parametr, <xref:System.Globalization.NumberFormatInfo> następujące wartości właściwości z obiektu bieżącej kultury są używane do definiowania reprezentacji ciągu wartości liczbowej:

- Właściwość, <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A> która określa symbol waluty bieżącej kultury.

- <xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A> Właściwość, <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> która zwraca wartość całkowitą, która określa następujące elementy:

  - Umieszczenie symbolu waluty.

  - Czy wartości ujemne są oznaczone przez wiodący znak ujemny, końcowy znak ujemny lub nawiasy.

  - Określa, czy między wartością liczbową a symbolem waluty jest wyświetlana spacja.

- Właściwość, <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A> która definiuje liczbę cyfr ułamkowych w ciągu wynikowym.

- Właściwość, <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A> która definiuje symbol separatora dziesiętnego w ciągu wynikowym.

- Właściwość, <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A> która definiuje symbol separatora grupy.

- Właściwość, <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A> która określa liczbę cyfr w każdej grupie po lewej stronie dziesiętnego.

- Właściwość, <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> która określa znak ujemny używany w ciągu wynikowym, jeśli nawiasy nie są używane do wskazywania wartości ujemnych.

Ponadto ciągi formatu numerycznego mogą zawierać specyfikator dokładności. Znaczenie tego specyfikatora zależy od ciągu formatu, z którym jest używany, ale zazwyczaj wskazuje całkowitą liczbę cyfr lub liczbę cyfr ułamkowych, które powinny pojawić się w ciągu wyników. Na przykład w poniższym przykładzie użyto standardowego ciągu liczbowego "X4" i specyfikatora dokładności do utworzenia wartości ciągu, która ma cztery cyfry szesnastkowe.

[!code-csharp[Conceptual.Formatting.Overview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/precisionspecifier1.cs#6)]
[!code-vb[Conceptual.Formatting.Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/precisionspecifier1.vb#6)]

Aby uzyskać więcej informacji na temat standardowych ciągów formatowania numerycznego, zobacz [Standardowe ciągi formatu numerycznego](../../../docs/standard/base-types/standard-numeric-format-strings.md).

Standardowe ciągi formatu dla wartości daty i godziny są aliasami dla ciągów formatu niestandardowego przechowywanych przez określoną <xref:System.Globalization.DateTimeFormatInfo> właściwość. Na przykład wywołanie `ToString` metody wartości daty i godziny za pomocą specyfikatora formatu "D" wyświetla datę <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> i godzinę przy użyciu niestandardowego ciągu formatu przechowywanego we właściwości bieżącej kultury. (Aby uzyskać więcej informacji na temat ciągów formatu niestandardowego, zobacz [następną sekcję](#custom-format-strings).) Poniższy przykład ilustruje tę relację.

[!code-csharp[Conceptual.Formatting.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/alias1.cs#5)]
[!code-vb[Conceptual.Formatting.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/alias1.vb#5)]

Aby uzyskać więcej informacji na temat standardowych ciągów formatu daty i godziny, zobacz [Standardowe ciągi formatu daty i godziny](../../../docs/standard/base-types/standard-date-and-time-format-strings.md).

Można również użyć standardowych ciągów formatu, aby zdefiniować reprezentację ciągu obiektu zdefiniowanego `ToString(String)` przez aplikację, który jest tworzony przez metodę obiektu. Można zdefiniować specyfikatory określonego formatu standardowego, które obsługuje obiekt, i określić, czy są one rozróżniane od wielkości liter, czy bez uwzględniania wielkości liter. Implementacja `ToString(String)` metody powinna obsługiwać następujące elementy:

- Specyfikator formatu "G", który reprezentuje zwyczajowy lub wspólny format obiektu. Bezparametrowe przeciążenie `ToString` metody obiektu należy `ToString(String)` wywołać jego przeciążenia i przekazać go "G" standardowy ciąg formatu.

- Obsługa specyfikatora formatu, który jest`Nothing` równy odwołaniu zerowemu (w języku Visual Basic). Specyfikator formatu równy odwołaniu zerowemu powinien być uważany za równoważny specyfikatorowi formatu "G".

Na przykład `Temperature` klasa może wewnętrznie przechowywać temperaturę w stopniach Celsjusza i używać `Temperature` specyfikatorów formatu do reprezentowania wartości obiektu w stopniach Celsjusza, stopniach Fahrenheita i kelwinach. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.Formatting.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/appstandard1.cs#7)]
[!code-vb[Conceptual.Formatting.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/appstandard1.vb#7)]

### <a name="custom-format-strings"></a>Niestandardowe ciągi formatowania

Oprócz standardowych ciągów formatu program .NET definiuje niestandardowe ciągi formatu zarówno dla wartości liczbowych, jak i wartości daty i godziny. Ciąg formatu niestandardowego składa się z jednego lub więcej specyfikatorów formatu niestandardowego, które definiują reprezentację ciągu wartości. Na przykład niestandardowy ciąg formatu daty i godziny "rrrr/mm/dd hh:mm:ss.ffff t zzz" konwertuje datę na jego reprezentację ciągu w postaci "2008/11/15 07:45:00.0000 P -08:00" dla kultury en-US. Podobnie ciąg formatu niestandardowego "0000" konwertuje wartość całkowitą 12 na "0012". Aby uzyskać pełną listę ciągów formatu niestandardowego, zobacz [Niestandardowe ciągi formatu daty i godziny](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) oraz niestandardowe [ciągi formatu liczbowego](../../../docs/standard/base-types/custom-numeric-format-strings.md).

Jeśli ciąg formatu składa się z pojedynczego specyfikatora formatu niestandardowego, specyfikator formatu powinien być poprzedzony procentem (%) symbolu, aby uniknąć pomylenia ze standardowym specyfikatorem formatu. W poniższym przykładzie użyto specyfikatora formatu niestandardowego "M", aby wyświetlić jednocyfrowy lub dwucyfrowy numer miesiąca określonej daty.

[!code-csharp[Conceptual.Formatting.Overview#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/singlecustom1.cs#8)]
[!code-vb[Conceptual.Formatting.Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/singlecustom1.vb#8)]

Wiele standardowych ciągów formatu dla wartości daty i godziny to aliasy dla <xref:System.Globalization.DateTimeFormatInfo> ciągów formatu niestandardowego, które są zdefiniowane przez właściwości obiektu. Niestandardowe ciągi formatu oferują również znaczną elastyczność w zapewnianiu formatowania zdefiniowanego przez aplikację dla wartości liczbowych lub wartości daty i godziny. Można zdefiniować własne niestandardowe ciągi wyników zarówno dla wartości liczbowych, jak i wartości daty i godziny, łącząc wiele specyfikatorów formatu niestandardowego w jeden ciąg formatu niestandardowego. W poniższym przykładzie zdefiniowano ciąg formatu niestandardowego, który wyświetla dzień tygodnia w nawiasach po nazwie miesiąca, dniu i roku.

[!code-csharp[Conceptual.Formatting.Overview#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/custom1.cs#9)]
[!code-vb[Conceptual.Formatting.Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/custom1.vb#9)]

W poniższym przykładzie zdefiniowano niestandardowy <xref:System.Int64> ciąg formatu, który wyświetla wartość jako standardowy, siedmiocyfrowy numer telefonu w STANACH USA wraz z jego numerem kierunkowym.

[!code-csharp[Conceptual.Formatting.Overview#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/telnumber1.cs#21)]
[!code-vb[Conceptual.Formatting.Overview#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/telnumber1.vb#21)]

Chociaż standardowe ciągi formatu zazwyczaj mogą obsługiwać większość potrzeb formatowania dla typów zdefiniowanych przez aplikację, można również zdefiniować specyfikatory formatu niestandardowego w celu formatowania typów.

### <a name="format-strings-and-net-types"></a>Formatowanie ciągów i typów .NET

<xref:System.Byte>Wszystkie typy liczbowe (tj. , <xref:System.SByte>, <xref:System.Single> <xref:System.UInt16> <xref:System.UInt32> <xref:System.UInt64> <xref:System.Numerics.BigInteger> <xref:System.DateTime> <xref:System.DateTimeOffset> <xref:System.TimeSpan> <xref:System.Decimal>, <xref:System.Double> <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, , , , i typy), a także , , , <xref:System.Guid>i wszystkie typy wyliczenia, formatowanie obsługi za pomocą ciągów formatu. Aby uzyskać informacje na temat ciągów określonego formatu obsługiwanych przez poszczególne typy, zobacz następujące tematy:

|Tytuł|Definicja|
|-----------|----------------|
|[Standardowe ciągi formatujące liczby](../../../docs/standard/base-types/standard-numeric-format-strings.md)|W tym artykule opisano standardowe ciągi formatu, które tworzą często używane reprezentacje ciągów wartości liczbowych.|
|[Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)|W tym artykule opisano niestandardowe ciągi formatu, które tworzą formaty specyficzne dla aplikacji dla wartości liczbowych.|
|[Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|W tym artykule opisano ciągi formatu <xref:System.DateTime> <xref:System.DateTimeOffset> standardowego, które tworzą często używane reprezentacje ciągów i wartości.|
|[Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|W tym artykule opisano niestandardowe ciągi <xref:System.DateTime> <xref:System.DateTimeOffset> formatu, które tworzą formaty specyficzne dla aplikacji i wartości.|
|[Standardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)|W tym artykule opisano standardowe ciągi formatu, które tworzą często używane reprezentacje ciągów interwałów czasowych.|
|[Niestandardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|W tym artykule opisano niestandardowe ciągi formatu, które tworzą formaty specyficzne dla aplikacji dla interwałów czasowych.|
|[Ciągi formatujące wyliczenia](../../../docs/standard/base-types/enumeration-format-strings.md)|W tym artykule opisano ciągi formatu standardowego, które są używane do tworzenia reprezentacji ciągów wartości wyliczenia.|
|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|W tym artykule <xref:System.Guid> opisano standardowe ciągi formatu dla wartości.|

## <a name="culture-sensitive-formatting-with-format-providers"></a>Formatowanie zależne od kultury z dostawcami formatów

Chociaż specyfikatory formatów umożliwiają dostosowywanie formatowania obiektów, tworzenie znaczącej reprezentacji ciągów obiektów często wymaga dodatkowych informacji o formatowaniu. Na przykład formatowanie liczby jako wartości waluty przy użyciu standardowego ciągu formatu "C" lub niestandardowego ciągu formatu, takiego jak "$ #,#.00", wymaga co najmniej informacji o poprawnym symbolu waluty, separatorze grup i separatorze dziesiętnym, które mają być dostępne do uwzględnienia w sformatowanym ciągu. W .NET te dodatkowe informacje o formatowaniu <xref:System.IFormatProvider> są udostępniane za pośrednictwem interfejsu, który jest `ToString` dostarczany jako parametr do jednego lub więcej przeciążeń metody typów liczbowych i typów daty i godziny. <xref:System.IFormatProvider>implementacje są używane w .NET do obsługi formatowania specyficzne dla kultury. W poniższym przykładzie przedstawiono, jak zmienia się reprezentacja ciągu <xref:System.IFormatProvider> obiektu, gdy jest on sformatowany za pomocą trzech obiektów reprezentujących różne kultury.

[!code-csharp[Conceptual.Formatting.Overview#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformatprovider1.cs#11)]
[!code-vb[Conceptual.Formatting.Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformatprovider1.vb#11)]

Interfejs <xref:System.IFormatProvider> zawiera jedną <xref:System.IFormatProvider.GetFormat%28System.Type%29>metodę, która ma jeden parametr, który określa typ obiektu, który zawiera informacje o formatowaniu. Jeśli metoda może dostarczyć obiekt tego typu, zwraca go. W przeciwnym razie zwraca`Nothing` odwołanie null (w języku Visual Basic).

<xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType>jest metodą wywołania wywołania. Podczas wywoływania `ToString` przeciążenia metody, który zawiera <xref:System.IFormatProvider.GetFormat%2A> parametr, <xref:System.IFormatProvider> <xref:System.IFormatProvider> wywołuje metodę tego obiektu. Metoda <xref:System.IFormatProvider.GetFormat%2A> jest odpowiedzialna za zwracanie obiektu, który zapewnia niezbędne informacje `formatType` formatowania, `ToString` zgodnie z jego parametrem, do metody.

Liczba metod formatowania lub konwersji ciągów zawiera <xref:System.IFormatProvider>parametr typu, ale w wielu przypadkach wartość parametru jest ignorowana, gdy metoda jest wywoływana. W poniższej tabeli wymieniono niektóre metody formatowania, które <xref:System.Type> używają parametru i <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> typ obiektu, który przekazują do metody.

|Metoda|Typ `formatType` parametru|
|------------|------------------------------------|
|`ToString`metoda typów numerycznych|<xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>|
|`ToString`metoda typów dat i godzin|<xref:System.Globalization.DateTimeFormatInfo?displayProperty=nameWithType>|
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|

> [!NOTE]
> Metody `ToString` typów numerycznych oraz typy dat i godzin są przeciążone, a <xref:System.IFormatProvider> tylko niektóre przeciążenia zawierają parametr. Jeśli metoda nie ma parametru <xref:System.IFormatProvider>typu, obiekt, który <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> jest zwracany przez właściwość jest przekazywana zamiast tego. Na przykład wywołanie metody <xref:System.Int32.ToString?displayProperty=nameWithType> domyślnej ostatecznie powoduje wywołanie metody, `Int32.ToString("G", System.Globalization.CultureInfo.CurrentCulture)`takie jak: .

.NET udostępnia trzy <xref:System.IFormatProvider>klasy, które implementują:

- <xref:System.Globalization.DateTimeFormatInfo>, klasa, która zawiera informacje o formatowaniu dla wartości daty i godziny dla określonej kultury. Jego <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementacja zwraca wystąpienie samego siebie.

- <xref:System.Globalization.NumberFormatInfo>, klasa, która zawiera informacje formatowania liczbowego dla określonej kultury. Jego <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementacja zwraca wystąpienie samego siebie.

- <xref:System.Globalization.CultureInfo>. Jego <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementacja może <xref:System.Globalization.NumberFormatInfo> zwrócić obiekt, aby zapewnić informacje <xref:System.Globalization.DateTimeFormatInfo> formatowania liczbowego lub obiekt, aby zapewnić informacje o formatowaniu dla wartości daty i godziny.

Można również zaimplementować własnego dostawcy formatu, aby zastąpić jedną z tych klas. Jednak <xref:System.IFormatProvider.GetFormat%2A> metoda implementacji musi zwrócić obiekt typu wymienionego w poprzedniej tabeli, jeśli ma dostarczyć `ToString` informacje o formatowaniu do metody.

### <a name="culture-sensitive-formatting-of-numeric-values"></a>Formatowanie wartości liczbowych uwzględniające kulturę

Domyślnie formatowanie wartości liczbowych jest zależne od kultury. Jeśli nie określisz kultury podczas wywoływania metody formatowania, używane są konwencje formatowania bieżącej kultury wątku. Jest to zilustrowane w poniższym przykładzie, który zmienia bieżącą <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> kulturę wątku cztery razy, a następnie wywołuje metodę. W każdym przypadku ciąg wynik odzwierciedla konwencje formatowania bieżącej kultury. Jest tak, `ToString` `ToString(String)` ponieważ i metody zawijania `ToString(String, IFormatProvider)` wywołania do każdego typu liczbowego metody.

[!code-csharp[Conceptual.Formatting.Overview#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific3.cs#19)]
[!code-vb[Conceptual.Formatting.Overview#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific3.vb#19)]

Można również sformatować wartość liczbową dla `ToString` określonej kultury, `provider` wywołując przeciążenie, które ma parametr i przekazując go jedną z następujących czynności:

- Obiekt, <xref:System.Globalization.CultureInfo> który reprezentuje kulturę, której konwencje formatowania mają być używane. Jego <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> metoda zwraca wartość <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> właściwości, która <xref:System.Globalization.NumberFormatInfo> jest obiektem, który zawiera informacje formatowania specyficzne dla kultury dla wartości liczbowych.

- Obiekt, <xref:System.Globalization.NumberFormatInfo> który definiuje konwencje formatowania specyficzne dla kultury, które mają być używane. Jego <xref:System.Globalization.NumberFormatInfo.GetFormat%2A> metoda zwraca wystąpienie samego siebie.

W poniższym <xref:System.Globalization.NumberFormatInfo> przykładzie użyto obiektów reprezentujących angielski (Stany Zjednoczone) i angielski (Wielka Brytania) kultur i francuskich i rosyjskich kultur neutralnych do formatowania liczby zmiennoprzecinkowej.

[!code-csharp[Conceptual.Formatting.Overview#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific4.cs#20)]
[!code-vb[Conceptual.Formatting.Overview#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific4.vb#20)]

### <a name="culture-sensitive-formatting-of-date-and-time-values"></a>Formatowanie wartości daty i godziny uwzględniające kulturę

Domyślnie formatowanie wartości daty i godziny jest zależne od kultury. Jeśli nie określisz kultury podczas wywoływania metody formatowania, używane są konwencje formatowania bieżącej kultury wątku. Jest to zilustrowane w poniższym przykładzie, który zmienia bieżącą <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> kulturę wątku cztery razy, a następnie wywołuje metodę. W każdym przypadku ciąg wynik odzwierciedla konwencje formatowania bieżącej kultury. Dzieje się <xref:System.DateTime.ToString?displayProperty=nameWithType>tak, <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType>ponieważ <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> , <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>, i <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody zawijają wywołania i metody.

[!code-csharp[Conceptual.Formatting.Overview#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific1.cs#17)]
[!code-vb[Conceptual.Formatting.Overview#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific1.vb#17)]

Można również sformatować wartość daty i godziny <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> dla <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> określonej kultury, `provider` wywołując lub przeciążenia, który ma parametr i przekazując go jedną z następujących czynności:

- Obiekt, <xref:System.Globalization.CultureInfo> który reprezentuje kulturę, której konwencje formatowania mają być używane. Jego <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> metoda zwraca wartość <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> właściwości, która <xref:System.Globalization.DateTimeFormatInfo> jest obiektem, który zawiera informacje o formatowaniu specyficzne dla kultury dla wartości daty i godziny.

- Obiekt, <xref:System.Globalization.DateTimeFormatInfo> który definiuje konwencje formatowania specyficzne dla kultury, które mają być używane. Jego <xref:System.Globalization.DateTimeFormatInfo.GetFormat%2A> metoda zwraca wystąpienie samego siebie.

W poniższym <xref:System.Globalization.DateTimeFormatInfo> przykładzie użyto obiektów reprezentujących angielski (Stany Zjednoczone) i angielski (Wielka Brytania) kultur i francuskich i rosyjskich kultur neutralnych do formatowania daty.

[!code-csharp[Conceptual.Formatting.Overview#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific2.cs#18)]
[!code-vb[Conceptual.Formatting.Overview#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific2.vb#18)]

## <a name="the-iformattable-interface"></a>Interfejs IFormattable

Zazwyczaj typy, które przeciążają `ToString` metodę za <xref:System.IFormatProvider> pomocą ciągu <xref:System.IFormattable> formatu i parametru również implementują interfejs. Ten interfejs ma jeden <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>element członkowski, który zawiera zarówno ciąg formatu, jak i dostawcę formatu jako parametry.

Implementacja <xref:System.IFormattable> interfejsu dla klasy zdefiniowanej przez aplikację oferuje dwie zalety:

- Obsługa konwersji ciągów <xref:System.Convert> przez klasę. Wywołania <xref:System.Convert.ToString%28System.Object%29?displayProperty=nameWithType> i <xref:System.Convert.ToString%28System.Object%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody wywołać implementację <xref:System.IFormattable> automatycznie.

- Obsługa formatowania kompozytowego. Jeśli element formatu, który zawiera ciąg formatu jest używany do formatowania <xref:System.IFormattable> typu niestandardowego, czas wykonywania języka wspólnego automatycznie wywołuje implementacji i przekazuje go ciąg formatu. Aby uzyskać więcej informacji na temat formatowania złożonego z metodami, takimi jak <xref:System.String.Format%2A?displayProperty=nameWithType> lub <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, zobacz sekcję [Formatowanie złożone.](#composite-formatting)

W poniższym `Temperature` przykładzie definiuje klasę, <xref:System.IFormattable> która implementuje interfejs. Obsługuje specyfikatory formatu "C" lub "G", aby wyświetlić temperaturę w stopniach Celsjusza, specyfikator formatu "F", aby wyświetlić temperaturę w Fahrenheita i specyfikator formatu "K", aby wyświetlić temperaturę w kelwinach.

[!code-csharp[Conceptual.Formatting.Overview#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#12)]
[!code-vb[Conceptual.Formatting.Overview#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#12)]

Poniższy przykład tworzy obiekt. `Temperature` Następnie wywołuje <xref:System.Convert.ToString%2A> metodę i używa kilku ciągów formatu złożonego, aby uzyskać różne reprezentacje ciągów `Temperature` obiektu. Każda z tych metod wywołuje z <xref:System.IFormattable> kolei `Temperature` wywołuje implementację klasy.

[!code-csharp[Conceptual.Formatting.Overview#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#13)]
[!code-vb[Conceptual.Formatting.Overview#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#13)]

## <a name="composite-formatting"></a>Formatowanie kompozytowe

Niektóre metody, takie <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>jak i , obsługują formatowanie złożone. Ciąg formatu złożonego jest rodzajem szablonu, który zwraca pojedynczy ciąg, który zawiera reprezentację ciągu zero, jeden lub więcej obiektów. Każdy obiekt jest reprezentowany w ciągu formatu złożonego przez element formatu indeksowany. Indeks elementu format odpowiada pozycji obiektu, który reprezentuje na liście parametrów metody. Indeksy są oparte na zeru. Na przykład w następującym <xref:System.String.Format%2A?displayProperty=nameWithType> wywołaniu metody pierwszy `{0:D}`element formatu , zastępuje `thatDate`się reprezentacją ciągu ; drugi element formatu, `{1}`zastępuje się reprezentacją `item1`ciągu ; a element trzeciego `{2:C2}`formatu, zastępuje się `item1.Value`reprezentacją ciągu .

[!code-csharp[Conceptual.Formatting.Overview#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite1.cs#14)]
[!code-vb[Conceptual.Formatting.Overview#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite1.vb#14)]

Oprócz zastąpienia elementu formatu reprezentacją ciągu odpowiadającego mu obiektu, elementy formatu umożliwiają również sterowanie następującymi elementami:

- Określony sposób, w jaki obiekt jest reprezentowany jako ciąg, <xref:System.IFormattable> jeśli obiekt implementuje interfejs i obsługuje ciągi formatu. Można to zrobić, wykonując indeks elementu `:` formatu z (dwukropek), po którym następuje prawidłowy ciąg formatu. W poprzednim przykładzie zostało to zdane przez formatowanie wartości daty za pomocą ciągu formatu `{0:d}`"d" (wzorzec daty krótkiej) (np. ) oraz `{2:C2}` przez formatowanie wartości liczbowej za pomocą ciągu formatu "C2" (np. w celu reprezentowania liczby jako wartości waluty z dwiema ułamkowymi cyframi dziesiętnym.

- Szerokość pola zawierającego reprezentację ciągu obiektu i wyrównanie reprezentacji ciągu w tym polu. Można to zrobić, wykonując indeks elementu `,` formatu z (przecinek) po szerokości pola. Ciąg jest wyrównany do prawej w polu, jeśli szerokość pola jest wartością dodatnią i jest wyrównany do lewej, jeśli szerokość pola jest wartością ujemną. Poniższy przykład wyrównuje wartości daty w polu 20-znakowym i wyrównuje wartości dziesiętne do jednej cyfry ułamkowej w polu 11-znakowym.

     [!code-csharp[Conceptual.Formatting.Overview#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite2.cs#22)]
     [!code-vb[Conceptual.Formatting.Overview#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite2.vb#22)]

     Należy zauważyć, że jeśli zarówno składnik ciągu wyrównania, jak i składnik ciągu `{0,-20:g}`formatu są obecne, pierwszy poprzedza ten ostatni (na przykład .

Aby uzyskać więcej informacji na temat formatowania złożonego, zobacz [Formatowanie złożone](../../../docs/standard/base-types/composite-formatting.md).

## <a name="custom-formatting-with-icustomformatter"></a>Niestandardowe formatowanie z iCustomFormatter

Dwie złożone metody formatowania <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> <xref:System.Text.StringBuilder.AppendFormat%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>i , zawiera parametr dostawcy formatu, który obsługuje formatowanie niestandardowe. Po wywołaniu jednej z tych metod formatowania <xref:System.Type> przekazuje obiekt, <xref:System.ICustomFormatter> który reprezentuje interfejs <xref:System.IFormatProvider.GetFormat%2A> do metody dostawcy formatu. Metoda <xref:System.IFormatProvider.GetFormat%2A> jest następnie odpowiedzialny za <xref:System.ICustomFormatter> zwracanie implementacji, która zapewnia niestandardowe formatowanie.

Interfejs <xref:System.ICustomFormatter> ma jedną metodę, <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29>która jest wywoływana automatycznie przez metodę formatowania złożonego, raz dla każdego elementu formatu w ciągu formatu złożonego. Metoda <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29> ma trzy parametry: ciąg formatu, `formatString` który reprezentuje argument w elemencie <xref:System.IFormatProvider> formatu, obiekt do formatu i obiekt, który zapewnia usługi formatowania. Zazwyczaj klasa, która implementuje <xref:System.ICustomFormatter> również <xref:System.IFormatProvider>implementuje , więc ten ostatni parametr jest odwołaniem do klasy formatowania niestandardowego się. Metoda zwraca niestandardowy sformatowany ciąg reprezentacji obiektu, który ma być sformatowany. Jeśli metoda nie może sformatować obiektu,`Nothing` powinna zwrócić odwołanie null (w języku Visual Basic).

Poniższy przykład zawiera <xref:System.ICustomFormatter> implementację o nazwie, `ByteByByteFormatter` która wyświetla wartości całkowite jako sekwencję dwucyfrowych wartości szesnastkowych, po których następuje spacja.

[!code-csharp[Conceptual.Formatting.Overview#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#15)]
[!code-vb[Conceptual.Formatting.Overview#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#15)]

W poniższym `ByteByByteFormatter` przykładzie użyto klasy do formatowania wartości całkowitych. Należy zauważyć, że <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> metoda jest wywoływana więcej niż jeden raz w drugim <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> wywołaniu metody i że domyślny <xref:System.Globalization.NumberFormatInfo> dostawca jest używany w trzecim wywołaniu metody, ponieważ .`ByteByByteFormatter.Format` metoda nie rozpoznaje ciągu formatu "N0" i`Nothing` zwraca odwołanie null (w języku Visual Basic).

[!code-csharp[Conceptual.Formatting.Overview#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#16)]
[!code-vb[Conceptual.Formatting.Overview#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#16)]

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Definicja|
|-----------|----------------|
|[Standardowe ciągi formatujące liczby](../../../docs/standard/base-types/standard-numeric-format-strings.md)|W tym artykule opisano standardowe ciągi formatu, które tworzą często używane reprezentacje ciągów wartości liczbowych.|
|[Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)|W tym artykule opisano niestandardowe ciągi formatu, które tworzą formaty specyficzne dla aplikacji dla wartości liczbowych.|
|[Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|W tym artykule opisano standardowe ciągi <xref:System.DateTime> formatu, które tworzą często używane reprezentacje ciągów wartości.|
|[Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|W tym artykule opisano niestandardowe ciągi <xref:System.DateTime> formatu, które tworzą formaty specyficzne dla aplikacji dla wartości.|
|[Standardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)|W tym artykule opisano standardowe ciągi formatu, które tworzą często używane reprezentacje ciągów interwałów czasowych.|
|[Niestandardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|W tym artykule opisano niestandardowe ciągi formatu, które tworzą formaty specyficzne dla aplikacji dla interwałów czasowych.|
|[Ciągi formatujące wyliczenia](../../../docs/standard/base-types/enumeration-format-strings.md)|W tym artykule opisano ciągi formatu standardowego, które są używane do tworzenia reprezentacji ciągów wartości wyliczenia.|
|[Złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md)|Opisuje sposób osadzania co najmniej jednej sformatowanej wartości w ciągu. Ciąg może być następnie wyświetlany na konsoli lub zapisywany w strumieniu.|
|[Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)|Wyświetla listę tematów, które zawierają instrukcje krok po kroku dotyczące wykonywania określonych operacji formatowania.|
|[Analiza składniowa ciągów](../../../docs/standard/base-types/parsing-strings.md)|Opisuje sposób inicjowania obiektów do wartości opisanych przez reprezentacje ciągów tych obiektów. Analizowanie jest odwrotną operacją formatowania.|

## <a name="reference"></a>Dokumentacja

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- <xref:System.ICustomFormatter?displayProperty=nameWithType>
