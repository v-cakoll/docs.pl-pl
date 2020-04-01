---
title: Formatowanie typów w .NET
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
ms.openlocfilehash: 124c32a09a32dd90b8b96b39aa80352094030b23
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523942"
---
# <a name="format-types-in-net"></a>Formatowanie typów w sieci .NET

Formatowanie jest procesem konwersji wystąpienia klasy, struktury lub wartości wyliczenia na jego reprezentację ciągu, często tak, że wynikowy ciąg może być wyświetlany użytkownikom lub deserialized przywrócić oryginalny typ danych. Ta konwersja może stanowić szereg wyzwań:

- Sposób, w jaki wartości są przechowywane wewnętrznie, niekoniecznie odzwierciedla sposób, w jaki użytkownicy chcą je wyświetlać. Na przykład numer telefonu może być przechowywany w formularzu 8009999999, który nie jest przyjazny dla użytkownika. Zamiast tego powinien być wyświetlany jako 800-999-9999. Zobacz sekcję [Ciągi formatu niestandardowego,](#custom-format-strings) aby zapoznać się z przykładem, który formatuje liczbę w ten sposób.

- Czasami konwersja obiektu do jego reprezentacji ciągu nie jest intuicyjna. Na przykład nie jest jasne, jak powinna być wyświetlana reprezentacja ciągu obiektu Temperature lub Person. Na przykład, który formatuje Obiekt Temperature na różne sposoby, zobacz sekcję [Ciągi formatu standardowego.](#standard-format-strings)

- Wartości często wymagają formatowania uwzględniającego kulturę. Na przykład w aplikacji, która używa liczb do odzwierciedlenia wartości pieniężnych, ciągi liczbowe powinny zawierać symbol waluty bieżącej kultury, separator grupy (który w większości kultur jest separatorem tysięcy) i symbol dziesiętny. Na przykład zobacz [kultury zależne od formatowania z dostawcami formatów](#culture-sensitive-formatting-with-format-providers) sekcji.

- Aplikacja może być musiał wyświetlić tę samą wartość na różne sposoby. Na przykład aplikacja może reprezentować element członkowski wyliczenia, wyświetlając reprezentację ciągu jego nazwy lub wyświetlając jego wartość podstawową. Na przykład, który formatuje <xref:System.DayOfWeek> członka wyliczenia na różne sposoby, zobacz sekcję [Ciągi formatu standardowego.](#standard-format-strings)

> [!NOTE]
> Formatowanie konwertuje wartość typu na reprezentację ciągu. Analizowanie jest odwrotnością formatowania. Operacja analizowania tworzy wystąpienie typu danych z jego reprezentacji ciągu. Aby uzyskać informacje dotyczące konwertowania ciągów na inne typy danych, zobacz [Analizowanie ciągów](../../../docs/standard/base-types/parsing-strings.md)znaków .

.NET zapewnia obsługę formatowania zaawansowanego, która umożliwia deweloperom spełnianie tych wymagań.

## <a name="formatting-in-net"></a>Formatowanie w .NET

Podstawowym mechanizmem formatowania jest domyślna <xref:System.Object.ToString%2A?displayProperty=nameWithType> implementacja metody, która jest omówiona w [domyślnej sekcji Formatowanie przy użyciu metody ToString](#default-formatting-using-the-tostring-method) w dalszej części tego tematu. Jednak .NET udostępnia kilka sposobów modyfikowania i rozszerzania domyślnej obsługi formatowania. Należą do nich między innymi:

- Zastępowanie <xref:System.Object.ToString%2A?displayProperty=nameWithType> metody definiowania niestandardowej reprezentacji ciągu wartości obiektu. Aby uzyskać więcej informacji, zobacz [Zastąpienie ToString Metody](#override-the-tostring-method) sekcji w dalszej części tego tematu.

- Definiowanie specyfikatorów formatu, które umożliwiają reprezentację ciągu wartości obiektu, aby przybierać różne formy. Na przykład specyfikator formatu "X" w poniższej instrukcji konwertuje liczbę całkowitą na reprezentację ciągu wartości szesnastkowej.

     [!code-csharp[Conceptual.Formatting.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#3)]
     [!code-vb[Conceptual.Formatting.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#3)]

     Aby uzyskać więcej informacji na temat specyfikatorów formatu, zobacz [ToString Metody i Format ciągów](#the-tostring-method-and-format-strings) sekcji.

- Za pomocą dostawców formatu, aby skorzystać z konwencji formatowania określonej kultury. Na przykład następująca instrukcja wyświetla wartość waluty przy użyciu konwencji formatowania kultury en-US.

     [!code-csharp[Conceptual.Formatting.Overview#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#10)]
     [!code-vb[Conceptual.Formatting.Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#10)]

     Aby uzyskać więcej informacji na temat formatowania z dostawcami formatów, zobacz sekcję [Dostawcy formatów.](#culture-sensitive-formatting-with-format-providers)

- Implementowanie <xref:System.IFormattable> interfejsu do obsługi konwersji <xref:System.Convert> ciągów z klasy i formatowania złożonego. Aby uzyskać więcej informacji, zobacz [sekcję IFormattable Interface ( IFormatable Interface](#the-iformattable-interface) section.

- Za pomocą formatowania złożonego do osadzania reprezentacji ciągu wartości w większym ciągu. Aby uzyskać więcej informacji, zobacz sekcję [Formatowanie złożone.](#composite-formatting)

- Implementowanie <xref:System.ICustomFormatter> <xref:System.IFormatProvider> i zapewnienie kompletnego rozwiązania do formatowania niestandardowego. Aby uzyskać więcej informacji, zobacz sekcję [Formatowanie niestandardowe za pomocą iCustomFormatter.](#custom-formatting-with-icustomformatter)

W poniższych sekcjach należy zbadać te metody konwersji obiektu do jego reprezentacji ciągu.

## <a name="default-formatting-using-the-tostring-method"></a>Formatowanie domyślne przy użyciu metody ToString

Każdy typ, który <xref:System.Object?displayProperty=nameWithType> jest pochodną automatycznie `ToString` dziedziczy metodę bez parametrów, która zwraca nazwę typu domyślnie. Poniższy przykład ilustruje metodę domyślną. `ToString` Definiuje klasę o `Automobile` nazwie, która nie ma implementacji. Gdy klasa jest tworzone, `ToString` a jej metoda jest wywoływana, wyświetla jego nazwę typu. Należy zauważyć, że `ToString` metoda nie jest jawnie wywoływana w przykładzie. Metoda <xref:System.Console.WriteLine%28System.Object%29?displayProperty=nameWithType> niejawnie `ToString` wywołuje metodę obiektu przekazany do niego jako argument.

[!code-csharp[Conceptual.Formatting.Overview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/default1.cs#1)]
[!code-vb[Conceptual.Formatting.Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/default1.vb#1)]

> [!WARNING]
> Począwszy od systemu Windows 8.1, <xref:Windows.Foundation.IStringable> środowisko wykonawcze systemu Windows zawiera interfejs z jedną metodą [IStringable.ToString](xref:Windows.Foundation.IStringable.ToString%2A), która zapewnia domyślną obsługę formatowania. Jednak zaleca się, że typy `IStringable` zarządzane nie implementują interfejsu. Aby uzyskać więcej informacji, zobacz sekcję "Środowisko wykonawcze systemu Windows i `IStringable` interfejs" na stronie referencyjnej. <xref:System.Object.ToString%2A?displayProperty=nameWithType>

Ponieważ wszystkie typy inne niż <xref:System.Object>interfejsy pochodzą z , ta funkcja jest automatycznie udostępniana do klas niestandardowych lub struktur. Jednak funkcje oferowane przez metodę `ToString` domyślną, jest ograniczona: Mimo, że identyfikuje typ, nie dostarcza żadnych informacji o wystąpieniu typu. Aby zapewnić reprezentację ciągu obiektu, który zawiera informacje o tym `ToString` obiekcie, należy zastąpić metodę.

> [!NOTE]
> Struktury dziedziczą <xref:System.ValueType>z , który z <xref:System.Object>kolei pochodzi od . Chociaż <xref:System.ValueType> zastępuje <xref:System.Object.ToString%2A?displayProperty=nameWithType>, jego implementacja jest identyczna.

## <a name="override-the-tostring-method"></a>Zastąpać Metodę ToString

Wyświetlanie nazwy typu jest często ograniczonego użycia i nie pozwala konsumentom typów do odróżnienia jednego wystąpienia od innego. Można jednak zastąpić `ToString` metodę, aby zapewnić bardziej użyteczną reprezentację wartości obiektu. Poniższy przykład definiuje `Temperature` obiekt i zastępuje `ToString` jego metodę wyświetlania temperatury w stopniach Celsjusza.

[!code-csharp[Conceptual.Formatting.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/overrides1.cs#2)]
[!code-vb[Conceptual.Formatting.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/overrides1.vb#2)]

W .NET `ToString` metoda każdego pierwotnego typu wartości została zastąpiona w celu wyświetlenia wartości obiektu zamiast jego nazwy. W poniższej tabeli przedstawiono zastąpienie dla każdego typu pierwotnego. Należy zauważyć, że większość metod zastąpione wywołać inne przeciążenie `ToString` metody i przekazać go specyfikator formatu "G", który definiuje ogólny format dla jego typu i obiekt, <xref:System.IFormatProvider> który reprezentuje bieżącą kulturę.

|Typ|Zastępowanie tostrowania|
|----------|-----------------------|
|<xref:System.Boolean>|Zwraca albo <xref:System.Boolean.TrueString?displayProperty=nameWithType> <xref:System.Boolean.FalseString?displayProperty=nameWithType>.|
|<xref:System.Byte>|Wywołania `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` formatowania <xref:System.Byte> wartości dla bieżącej kultury.|
|<xref:System.Char>|Zwraca znak jako ciąg.|
|<xref:System.DateTime>|Wywołania `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` formatowania wartości daty i godziny dla bieżącej kultury.|
|<xref:System.Decimal>|Wywołania `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` formatowania <xref:System.Decimal> wartości dla bieżącej kultury.|
|<xref:System.Double>|Wywołania `Double.ToString("G", NumberFormatInfo.CurrentInfo)` formatowania <xref:System.Double> wartości dla bieżącej kultury.|
|<xref:System.Int16>|Wywołania `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` formatowania <xref:System.Int16> wartości dla bieżącej kultury.|
|<xref:System.Int32>|Wywołania `Int32.ToString("G", NumberFormatInfo.CurrentInfo)` formatowania <xref:System.Int32> wartości dla bieżącej kultury.|
|<xref:System.Int64>|Wywołania `Int64.ToString("G", NumberFormatInfo.CurrentInfo)` formatowania <xref:System.Int64> wartości dla bieżącej kultury.|
|<xref:System.SByte>|Wywołania `SByte.ToString("G", NumberFormatInfo.CurrentInfo)` formatowania <xref:System.SByte> wartości dla bieżącej kultury.|
|<xref:System.Single>|Wywołania `Single.ToString("G", NumberFormatInfo.CurrentInfo)` formatowania <xref:System.Single> wartości dla bieżącej kultury.|
|<xref:System.UInt16>|Wywołania `UInt16.ToString("G", NumberFormatInfo.CurrentInfo)` formatowania <xref:System.UInt16> wartości dla bieżącej kultury.|
|<xref:System.UInt32>|Wywołania `UInt32.ToString("G", NumberFormatInfo.CurrentInfo)` formatowania <xref:System.UInt32> wartości dla bieżącej kultury.|
|<xref:System.UInt64>|Wywołania `UInt64.ToString("G", NumberFormatInfo.CurrentInfo)` formatowania <xref:System.UInt64> wartości dla bieżącej kultury.|

## <a name="the-tostring-method-and-format-strings"></a>Metoda ToString i ciągi formatu

Poleganie na `ToString` metodzie domyślnej `ToString` lub zastępowanie jest właściwe, gdy obiekt ma reprezentację pojedynczego ciągu. Jednak wartość obiektu często ma wiele reprezentacji. Na przykład temperatura może być wyrażona w stopniach Fahrenheita, stopni Celsjusza lub kelwinach. Podobnie wartość całkowita 10 może być reprezentowana na wiele sposobów, w tym 10, 10,0, 1,0e01 lub 10,00 USD.

Aby włączyć pojedynczą wartość, aby mieć wiele reprezentacji ciągów, .NET używa ciągów formatu. Ciąg formatu to ciąg zawierający co najmniej jeden wstępnie zdefiniowany format specyfikatorów, które `ToString` są pojedynczymi znakami lub grupami znaków definiustrujących sposób formatowania jej danych wyjściowych. Ciąg formatu jest następnie przekazywany jako `ToString` parametr do metody obiektu i określa, jak powinna pojawić się reprezentacja ciągu wartości tego obiektu.

Wszystkie typy liczbowe, typy dat i godzin oraz typy wyliczenia w obszarze .NET obsługują wstępnie zdefiniowany zestaw specyfikatorów formatu. Można również użyć ciągów formatu do definiowania wielu reprezentacji ciągów typów danych zdefiniowanych przez aplikację.

### <a name="standard-format-strings"></a>Ciągi formatu standardowego

Ciąg formatu standardowego zawiera specyfikator pojedynczego formatu, który jest znakiem alfabetycznym definiutywnym, który definiuje reprezentację ciągu obiektu, do którego jest stosowany, wraz z opcjonalnym specyfikatorem precyzji, który wpływa na liczbę cyfr wyświetlanych w ciągu wynikowym. Jeśli specyfikator precyzji zostanie pominięty lub nie jest obsługiwany, specyfikator formatu standardowego jest odpowiednikiem ciągu formatu standardowego.

.NET definiuje zestaw specyfikatorów formatu standardowego dla wszystkich typów liczbowych, wszystkich typów daty i godziny oraz wszystkich typów wyliczeń. Na przykład każda z tych kategorii obsługuje specyfikator standardowego formatu "G", który definiuje ogólną reprezentację ciągu wartości tego typu.

Ciągi formatu standardowego dla typów wyliczenia bezpośrednio kontrolują reprezentację ciągu wartości. Ciągi formatu przekazywane do metody wartości `ToString` wyliczenia określają, czy wartość jest wyświetlana przy użyciu nazwy ciągu (specyfikatory formatu "G" i "F"), jego podstawowej wartości integralnej (specyfikator formatu "D") lub jej wartości szesnastowej (specyfikator formatu "X"). Poniższy przykład ilustruje użycie ciągów formatu standardowego do formatowania wartości wyliczenia. <xref:System.DayOfWeek>

[!code-csharp[Conceptual.Formatting.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/standard1.cs#4)]
[!code-vb[Conceptual.Formatting.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/standard1.vb#4)]

Aby uzyskać informacje o ciągach formatu wyliczenia, zobacz [Ciągi formatu wyliczenia](../../../docs/standard/base-types/enumeration-format-strings.md).

Ciągi formatu standardowego dla typów liczbowych zwykle definiują ciąg wynikowy, którego dokładny wygląd jest kontrolowany przez jedną lub więcej wartości właściwości. Na przykład specyfikator formatu "C" formatuje liczbę jako wartość waluty. Po wywołaniu `ToString` metody z specyfikatorem formatu "C" jako jedynym parametrem, <xref:System.Globalization.NumberFormatInfo> następujące wartości właściwości z obiektu bieżącej kultury są używane do definiowania reprezentacji ciągu wartości liczbowej:

- Właściwość, <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A> która określa symbol waluty bieżącej kultury.

- Lub <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> <xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A> właściwość, która zwraca liczbę całkowitą, która określa następujące wartości:

  - Położenie symbolu waluty.

  - Czy wartości ujemne są wskazywane przez wiodący znak ujemny, końcowy znak ujemny lub nawiasy.

  - Określa, czy spacja jest wyświetlana między wartością liczbową a symbolem waluty.

- Właściwość, <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A> która definiuje liczbę cyfr ułamkowych w ciągu wynikowym.

- Właściwość, <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A> która definiuje symbol separatora dziesiętnego w ciągu wynikowym.

- Właściwość, <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A> która definiuje symbol separatora grupy.

- Właściwość, <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A> która definiuje liczbę cyfr w każdej grupie po lewej stronie miejsca dziesiętnego.

- Właściwość, <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> która określa znak ujemny używany w ciągu wynik, jeśli nawiasy nie są używane do wskazywania wartości ujemnych.

Ponadto ciągi formatu numerycznego mogą zawierać specyfikator precyzji. Znaczenie tego specyfikatora zależy od ciągu formatu, z którym jest używany, ale zazwyczaj wskazuje całkowitą liczbę cyfr lub liczbę cyfr ułamkowych, które powinny pojawić się w ciągu wynikowym. Na przykład w poniższym przykładzie użyto standardowego ciągu numerycznego "X4" i specyfikatora precyzji, aby utworzyć wartość ciągu, która ma cztery cyfry szesnastkowe.

[!code-csharp[Conceptual.Formatting.Overview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/precisionspecifier1.cs#6)]
[!code-vb[Conceptual.Formatting.Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/precisionspecifier1.vb#6)]

Aby uzyskać więcej informacji na temat standardowych ciągów formatowania liczbowego, zobacz [Standardowe ciągi formatu numerycznego](../../../docs/standard/base-types/standard-numeric-format-strings.md).

Ciągi formatu standardowego dla wartości daty i godziny są <xref:System.Globalization.DateTimeFormatInfo> aliasami dla ciągów formatu niestandardowego przechowywanych przez określoną właściwość. Na przykład wywołanie `ToString` metody wartości daty i godziny z specyfikatorem formatu "D" wyświetla datę i godzinę <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> przy użyciu ciągu formatu niestandardowego przechowywanego we właściwości bieżącej kultury. (Aby uzyskać więcej informacji na temat ciągów formatu niestandardowego, zobacz [następną sekcję](#custom-format-strings).) Poniższy przykład ilustruje tę relację.

[!code-csharp[Conceptual.Formatting.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/alias1.cs#5)]
[!code-vb[Conceptual.Formatting.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/alias1.vb#5)]

Aby uzyskać więcej informacji o standardowych ciągach formatu daty i godziny, zobacz [Ciągi formatu daty standardowej i godziny](../../../docs/standard/base-types/standard-date-and-time-format-strings.md).

Można również użyć ciągów formatu standardowego, aby zdefiniować reprezentację ciągu obiektu `ToString(String)` zdefiniowanego przez aplikację, który jest produkowany przez metodę obiektu. Można zdefiniować specyfikatory określonego formatu standardowego, które obsługuje obiekt, i można określić, czy są one rozróżniane wielkość liter, czy niewrażliwe na wielkość liter. Implementacja `ToString(String)` metody powinna obsługiwać następujące elementy:

- Specyfikator formatu "G", który reprezentuje niestandardowy lub wspólny format obiektu. Bezparametrowe przeciążenie `ToString` metody obiektu `ToString(String)` należy wywołać jego przeciążenie i przekazać go ciąg formatu standardowego "G".

- Obsługa specyfikatora formatu, który jest`Nothing` równy odwołaniu zerowemu (w języku Visual Basic). Specyfikator formatu, który jest równy odwołani null należy uznać za równoważne specyfikatora formatu "G".

Na przykład `Temperature` klasa może wewnętrznie przechowywać temperaturę w stopniach Celsjusza i `Temperature` używać specyfikatorów formatu do reprezentowania wartości obiektu w stopniach Celsjusza, stopni Celsjusza i kelwinach. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.Formatting.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/appstandard1.cs#7)]
[!code-vb[Conceptual.Formatting.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/appstandard1.vb#7)]

### <a name="custom-format-strings"></a>Niestandardowe ciągi formatowania

Oprócz ciągów formatu standardowego program .NET definiuje ciągi niestandardowego formatu zarówno dla wartości liczbowych, jak i wartości daty i godziny. Ciąg formatu niestandardowego składa się z co najmniej jednego specyfikatora formatu niestandardowego, które definiują reprezentację ciągu wartości. Na przykład niestandardowy ciąg formatu daty i godziny "rrrr/mm/dd hh:mm:ss.ffff t zzz" konwertuje datę na jego reprezentację ciągu w postaci "2008/11/15 07:45:00.0000 P -08:00" dla kultury en-US. Podobnie ciąg formatu niestandardowego "0000" konwertuje wartość całkowitą 12 na "0012". Aby uzyskać pełną listę ciągów formatu niestandardowego, zobacz [Niestandardowe ciągi formatu daty i godziny](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) oraz [Niestandardowe ciągi formatu numerycznego](../../../docs/standard/base-types/custom-numeric-format-strings.md).

Jeśli ciąg formatu składa się z jednego specyfikatora formatu niestandardowego, specyfikator formatu powinien być poprzedzony procentem (%) aby uniknąć pomyłek ze standardowym specyfikatorem formatu. W poniższym przykładzie użyto specyfikatora formatu niestandardowego "M", aby wyświetlić jednocyfrowy lub dwucyfrowy numer miesiąca określonej daty.

[!code-csharp[Conceptual.Formatting.Overview#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/singlecustom1.cs#8)]
[!code-vb[Conceptual.Formatting.Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/singlecustom1.vb#8)]

Wiele ciągów w formacie standardowym dla wartości daty i godziny to aliasy dla ciągów formatu niestandardowego, które są definiowane przez właściwości <xref:System.Globalization.DateTimeFormatInfo> obiektu. Ciągi formatu niestandardowego oferują również znaczną elastyczność w dostarczaniu formatowania zdefiniowanego przez aplikację dla wartości liczbowych lub wartości daty i godziny. Można zdefiniować własne niestandardowe ciągi wyników dla wartości liczbowych oraz wartości daty i godziny, łącząc wiele specyfikatorów formatu niestandardowego w jeden ciąg formatu niestandardowego. Poniższy przykład definiuje ciąg formatu niestandardowego, który wyświetla dzień tygodnia w nawiasach po nazwie miesiąca, dniu i roku.

[!code-csharp[Conceptual.Formatting.Overview#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/custom1.cs#9)]
[!code-vb[Conceptual.Formatting.Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/custom1.vb#9)]

Poniższy przykład definiuje ciąg formatu <xref:System.Int64> niestandardowego, który wyświetla wartość jako standardowy, siedmiocyfrowy numer telefonu w USA wraz z jego numerem kierunkowym.

[!code-csharp[Conceptual.Formatting.Overview#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/telnumber1.cs#21)]
[!code-vb[Conceptual.Formatting.Overview#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/telnumber1.vb#21)]

Mimo że ciągi formatów standardowych mogą zazwyczaj obsługiwać większość potrzeb formatowania dla typów zdefiniowanych przez aplikację, można również zdefiniować niestandardowe specyfikatory formatów w celu formatowania typów.

### <a name="format-strings-and-net-types"></a>Formatowanie ciągów i typów .NET

Wszystkie <xref:System.Byte>typy liczbowe (czyli <xref:System.Decimal> <xref:System.Double>, <xref:System.Int16> <xref:System.Int32>, <xref:System.Int64> <xref:System.SByte>, <xref:System.Single> <xref:System.UInt16>, <xref:System.UInt32> <xref:System.UInt64>, <xref:System.Numerics.BigInteger> , , , <xref:System.DateTime>, <xref:System.DateTimeOffset> <xref:System.TimeSpan>, <xref:System.Guid>, , i typy), a także , , , , i wszystkie typy wyliczenia, obsługa formatowania z ciągami formatu. Aby uzyskać informacje na temat określonych ciągów formatu obsługiwanych przez każdy typ, zobacz następujące tematy:

|Tytuł|Definicja|
|-----------|----------------|
|[Standardowe ciągi formatujące liczby](../../../docs/standard/base-types/standard-numeric-format-strings.md)|W tym artykule opisano ciągi formatu standardowego, które tworzą często używane reprezentacje ciągów wartości liczbowych.|
|[Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)|W tym artykule opisano ciągi formatów niestandardowych, które tworzą formaty specyficzne dla aplikacji dla wartości liczbowych.|
|[Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|W tym artykule opisano ciągi formatu <xref:System.DateTime> <xref:System.DateTimeOffset> standardowego, które tworzą często używane reprezentacje ciągów i wartości.|
|[Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|W tym artykule opisano ciągi formatu niestandardowego, które tworzą formaty specyficzne dla <xref:System.DateTime> aplikacji i <xref:System.DateTimeOffset> wartości.|
|[Standardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)|W tym artykule opisano ciągi formatu standardowego, które tworzą często używane reprezentacje ciągów interwałów czasu.|
|[Niestandardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|W tym artykule opisano ciągi formatów niestandardowych, które tworzą formaty specyficzne dla aplikacji dla interwałów czasowych.|
|[Wyliczanie ciągów formatujących](../../../docs/standard/base-types/enumeration-format-strings.md)|W tym artykule opisano ciągi formatu standardowego, które są używane do tworzenia reprezentacji ciągów wartości wyliczenia.|
|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|Opisuje standardowe ciągi <xref:System.Guid> formatu dla wartości.|

## <a name="culture-sensitive-formatting-with-format-providers"></a>Formatowanie z uwzględnieniem kultury z dostawcami formatów

Chociaż specyfikatory formatów umożliwiają dostosowanie formatowania obiektów, tworzenie znaczącej reprezentacji ciągów obiektów często wymaga dodatkowych informacji o formatowaniu. Na przykład formatowanie liczby jako wartości waluty przy użyciu ciągu formatu standardowego "C" lub ciągu formatu niestandardowego, takiego jak "$ #,#.00", wymaga co najmniej informacji o prawidłowym symbolu waluty, separatorze grupy i separatorze dziesiętnym, które mają być dostępne do uwzględnienia w sformatowanym ciągu. W .NET te dodatkowe informacje o formatowaniu są udostępniane za pośrednictwem <xref:System.IFormatProvider> interfejsu, który jest `ToString` dostarczany jako parametr do jednego lub więcej przeciążeń metody typów liczbowych oraz typów daty i godziny. <xref:System.IFormatProvider>implementacje są używane w .NET do obsługi formatowania specyficznego dla kultury. Poniższy przykład ilustruje, jak zmienia się reprezentacja ciągu <xref:System.IFormatProvider> obiektu, gdy jest sformatowany z trzema obiektami reprezentującymi różne kultury.

[!code-csharp[Conceptual.Formatting.Overview#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformatprovider1.cs#11)]
[!code-vb[Conceptual.Formatting.Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformatprovider1.vb#11)]

Interfejs <xref:System.IFormatProvider> zawiera jedną <xref:System.IFormatProvider.GetFormat%28System.Type%29>metodę, która ma pojedynczy parametr, który określa typ obiektu, który zawiera informacje o formatowaniu. Jeśli metoda może dostarczyć obiekt tego typu, zwraca go. W przeciwnym razie zwraca`Nothing` odwołanie null (w języku Visual Basic).

<xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType>jest metodą wywołania zwrotnego. Po wywołaniu `ToString` przeciążenia metody, który <xref:System.IFormatProvider> zawiera <xref:System.IFormatProvider.GetFormat%2A> parametr, <xref:System.IFormatProvider> wywołuje metodę tego obiektu. Metoda <xref:System.IFormatProvider.GetFormat%2A> jest odpowiedzialna za zwracanie obiektu, który zawiera niezbędne informacje `formatType` o formatowaniu, określone przez jego parametr, do `ToString` metody.

Wiele metod formatowania lub konwersji ciągów <xref:System.IFormatProvider>zawiera parametr typu , ale w wielu przypadkach wartość parametru jest ignorowana, gdy metoda jest wywoływana. W poniższej tabeli wymieniono niektóre metody formatowania, <xref:System.Type> które używają parametru <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> i typ obiektu, który przechodzą do metody.

|Metoda|Typ `formatType` parametru|
|------------|------------------------------------|
|`ToString`metoda typów liczbowych|<xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>|
|`ToString`metoda typów daty i godziny|<xref:System.Globalization.DateTimeFormatInfo?displayProperty=nameWithType>|
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|

> [!NOTE]
> Metody `ToString` typów liczbowych i typów daty i godziny są przeciążone, a <xref:System.IFormatProvider> tylko niektóre przeciążenia zawierają parametr. Jeśli metoda nie ma parametru <xref:System.IFormatProvider>typu , obiekt, <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> który jest zwracany przez właściwość jest przekazywana zamiast. Na przykład wywołanie metody <xref:System.Int32.ToString?displayProperty=nameWithType> domyślnej ostatecznie powoduje wywołanie metody, takie jak: `Int32.ToString("G", System.Globalization.CultureInfo.CurrentCulture)`.

.NET udostępnia trzy <xref:System.IFormatProvider>klasy, które implementują:

- <xref:System.Globalization.DateTimeFormatInfo>, klasa, która zawiera informacje o formatowaniu wartości daty i godziny dla określonej kultury. Jego <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementacja zwraca wystąpienie siebie.

- <xref:System.Globalization.NumberFormatInfo>, klasa, która zawiera informacje o formatowaniu numerycznym dla określonej kultury. Jego <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementacja zwraca wystąpienie siebie.

- <xref:System.Globalization.CultureInfo>. Jego <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementacja może <xref:System.Globalization.NumberFormatInfo> zwrócić obiekt w celu zapewnienia <xref:System.Globalization.DateTimeFormatInfo> informacji o formatowaniu liczbowym lub obiekt, aby zapewnić informacje o formatowaniu wartości daty i godziny.

Można również zaimplementować własnego dostawcy formatu, aby zastąpić jedną z tych klas. Jednak <xref:System.IFormatProvider.GetFormat%2A> metoda implementacji musi zwrócić obiekt typu wymienionego w poprzedniej tabeli, jeśli musi `ToString` dostarczyć informacje o formatowaniu do metody.

### <a name="culture-sensitive-formatting-of-numeric-values"></a>Formatowanie wartości liczbowych z uwzględnieniem kultury

Domyślnie formatowanie wartości liczbowych jest zależne od kultury. Jeśli nie określisz kultury podczas wywoływania metody formatowania, używane są konwencje formatowania bieżącej kultury wątku. Jest to zilustrowane w poniższym przykładzie, który zmienia bieżącą kulturę wątku cztery razy, a następnie wywołuje <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> metodę. W każdym przypadku ciąg wynik odzwierciedla konwencje formatowania bieżącej kultury. Jest to `ToString` spowodowane `ToString(String)` i metody zawijają wywołania do każdego typu numerycznego `ToString(String, IFormatProvider)` metody.

[!code-csharp[Conceptual.Formatting.Overview#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific3.cs#19)]
[!code-vb[Conceptual.Formatting.Overview#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific3.vb#19)]

Można również sformatować wartość liczbową dla `ToString` określonej kultury, wywołując przeciążenie, które ma `provider` parametr i przekazując go jedną z następujących czynności:

- Obiekt, <xref:System.Globalization.CultureInfo> który reprezentuje kultury, których konwencje formatowania mają być używane. Jego <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> metoda zwraca wartość <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> właściwości, która <xref:System.Globalization.NumberFormatInfo> jest obiektem, który zawiera informacje o formatowaniu specyficzne dla kultury dla wartości liczbowych.

- Obiekt, <xref:System.Globalization.NumberFormatInfo> który definiuje konwencje formatowania specyficzne dla kultury, które mają być używane. Jego <xref:System.Globalization.NumberFormatInfo.GetFormat%2A> metoda zwraca wystąpienie siebie.

W poniższym <xref:System.Globalization.NumberFormatInfo> przykładzie użyto obiektów, które reprezentują kultury angielski (Stany Zjednoczone) i Angielski (Wielka Brytania) oraz kultury neutralne francuskie i rosyjskie do formatowania liczby zmiennoprzecinkowej.

[!code-csharp[Conceptual.Formatting.Overview#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific4.cs#20)]
[!code-vb[Conceptual.Formatting.Overview#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific4.vb#20)]

### <a name="culture-sensitive-formatting-of-date-and-time-values"></a>Formatowanie wartości daty i godziny uwzględniające kulturę

Domyślnie formatowanie wartości daty i godziny jest zależne od kultury. Jeśli nie określisz kultury podczas wywoływania metody formatowania, używane są konwencje formatowania bieżącej kultury wątku. Jest to zilustrowane w poniższym przykładzie, który zmienia bieżącą kulturę wątku cztery razy, a następnie wywołuje <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> metodę. W każdym przypadku ciąg wynik odzwierciedla konwencje formatowania bieżącej kultury. Dzieje się <xref:System.DateTime.ToString?displayProperty=nameWithType>tak <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType>dlatego, <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> że , <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> , <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> i metody zawijają wywołania i metody.

[!code-csharp[Conceptual.Formatting.Overview#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific1.cs#17)]
[!code-vb[Conceptual.Formatting.Overview#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific1.vb#17)]

Można również sformatować wartość daty i <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> godziny <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> dla określonej `provider` kultury, wywołując lub przeciążenie, które ma parametr i przekazując go jedną z następujących czynności:

- Obiekt, <xref:System.Globalization.CultureInfo> który reprezentuje kultury, których konwencje formatowania mają być używane. Jego <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> metoda zwraca wartość <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> właściwości, która <xref:System.Globalization.DateTimeFormatInfo> jest obiektem, który zawiera informacje o formatowaniu specyficzne dla kultury dla wartości daty i godziny.

- Obiekt, <xref:System.Globalization.DateTimeFormatInfo> który definiuje konwencje formatowania specyficzne dla kultury, które mają być używane. Jego <xref:System.Globalization.DateTimeFormatInfo.GetFormat%2A> metoda zwraca wystąpienie siebie.

W poniższym <xref:System.Globalization.DateTimeFormatInfo> przykładzie użyto obiektów, które reprezentują kultury angielski (Stany Zjednoczone) i Angielski (Wielka Brytania) oraz kultury neutralne francuskie i rosyjskie do formatowania daty.

[!code-csharp[Conceptual.Formatting.Overview#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific2.cs#18)]
[!code-vb[Conceptual.Formatting.Overview#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific2.vb#18)]

## <a name="the-iformattable-interface"></a>Interfejs IFormattable

Zazwyczaj typy, które `ToString` przeciążają metodę <xref:System.IFormatProvider> ciągiem <xref:System.IFormattable> formatu i parametrem również implementują interfejs. Ten interfejs ma jeden <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>element członkowski, który zawiera zarówno ciąg formatu, jak i dostawcę formatu jako parametry.

Implementacja <xref:System.IFormattable> interfejsu dla klasy zdefiniowanej przez aplikację oferuje dwie zalety:

- Obsługa konwersji ciągów <xref:System.Convert> przez klasę. Wywołania <xref:System.Convert.ToString%28System.Object%29?displayProperty=nameWithType> i <xref:System.Convert.ToString%28System.Object%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody <xref:System.IFormattable> wywołać implementacji automatycznie.

- Obsługa formatowania kompozytowego. Jeśli element formatu, który zawiera ciąg formatu jest używany do formatowania <xref:System.IFormattable> typu niestandardowego, środowisko uruchomieniowe języka wspólnego automatycznie wywołuje implementację i przekazuje go ciąg formatu. Aby uzyskać więcej informacji na temat <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>formatowania złożonego za pomocą metod, takich jak lub , zobacz sekcję [Formatowanie kompozytowe.](#composite-formatting)

Poniższy przykład definiuje `Temperature` klasę, która <xref:System.IFormattable> implementuje interfejs. Obsługuje specyfikatory formatu "C" lub "G", aby wyświetlić temperaturę w stopniach Celsjusza, specyfikator formatu "F", aby wyświetlić temperaturę w Fahrenheita, oraz specyfikator formatu "K", aby wyświetlić temperaturę w kelwinach.

[!code-csharp[Conceptual.Formatting.Overview#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#12)]
[!code-vb[Conceptual.Formatting.Overview#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#12)]

Poniższy przykład wystąpienia `Temperature` obiektu. Następnie wywołuje <xref:System.Convert.ToString%2A> metodę i używa kilku ciągów formatu złożonego, `Temperature` aby uzyskać różne reprezentacje ciągów obiektu. Każda z tych wywołań metody, <xref:System.IFormattable> z `Temperature` kolei wywołuje implementację klasy.

[!code-csharp[Conceptual.Formatting.Overview#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#13)]
[!code-vb[Conceptual.Formatting.Overview#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#13)]

## <a name="composite-formatting"></a>Formatowanie kompozytowe

Niektóre metody, <xref:System.String.Format%2A?displayProperty=nameWithType> takie <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>jak i , obsługują formatowanie złożone. Ciąg formatu złożonego jest rodzajem szablonu, który zwraca pojedynczy ciąg, który zawiera reprezentację ciągu zero, jeden lub więcej obiektów. Każdy obiekt jest reprezentowany w ciągu formatu złożonego przez element formatu indeksowanego. Indeks elementu formatu odpowiada położeniu obiektu, który reprezentuje na liście parametrów metody. Indeksy są oparte na wartościach zerowych. Na przykład w następującym <xref:System.String.Format%2A?displayProperty=nameWithType> wywołaniu metody, pierwszy `{0:D}`element formatu, , `thatDate`jest zastępowany przez reprezentację ciągu ; drugi element formatu, `{1}`jest zastępowany `item1`przez reprezentację ciągu ; a element trzeciego `{2:C2}`formatu, jest zastępowany `item1.Value`przez reprezentację ciągu .

[!code-csharp[Conceptual.Formatting.Overview#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite1.cs#14)]
[!code-vb[Conceptual.Formatting.Overview#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite1.vb#14)]

Oprócz zastąpienia elementu formatu reprezentacją ciągu odpowiedniego obiektu, elementy formatu umożliwiają również kontrolowanie następujących elementów:

- Określony sposób, w jaki obiekt jest reprezentowany jako ciąg, <xref:System.IFormattable> jeśli obiekt implementuje interfejs i obsługuje ciągi formatu. Można to zrobić, wykonując indeks elementu `:` formatu z (dwukropek), a następnie ciąg prawidłowego formatu. W poprzednim przykładzie zrobiliśmy to, formatując wartość daty z ciągiem formatu `{0:d}`"d" (wzorzec daty krótkiej) (np. ) i `{2:C2}` formatując wartość liczbową za pomocą ciągu formatu "C2" (np. reprezentując liczbę jako wartość waluty z dwiema ułamkowymi cyframi dziesiętnymi.

- Szerokość pola zawierającego reprezentację ciągu obiektu i wyrównanie reprezentacji ciągu w tym polu. Można to zrobić, postępowo indeks elementu `,` formatu z (przecinek) po szerokości pola. Ciąg jest wyrównany do prawej w polu, jeśli szerokość pola jest wartością dodatnią i jest wyrównany do lewej, jeśli szerokość pola jest wartością ujemną. Poniższy przykład wyrównuje wartości daty w polu 20-znakowym i wyrównuje wartości dziesiętne z jedną cyfrą ułamkową w polu 11-znakowym.

     [!code-csharp[Conceptual.Formatting.Overview#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite2.cs#22)]
     [!code-vb[Conceptual.Formatting.Overview#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite2.vb#22)]

     Należy zauważyć, że jeśli obecny jest zarówno składnik ciągu wyrównania, jak i `{0,-20:g}`składnik ciągu formatu, pierwszy z nich poprzedza ten ostatni (na przykład .

Aby uzyskać więcej informacji na temat formatowania złożonego, zobacz [Formatowanie złożone](../../../docs/standard/base-types/composite-formatting.md).

## <a name="custom-formatting-with-icustomformatter"></a>Formatowanie niestandardowe za pomocą formatu ICustomFormatter

Dwie metody formatowania <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> <xref:System.Text.StringBuilder.AppendFormat%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>złożonego i , obejmują parametr dostawcy formatu, który obsługuje formatowanie niestandardowe. Gdy wywoływana jest żadna z tych <xref:System.Type> metod formatowania, przekazuje obiekt reprezentujący <xref:System.ICustomFormatter> interfejs do metody dostawcy formatu. <xref:System.IFormatProvider.GetFormat%2A> Metoda <xref:System.IFormatProvider.GetFormat%2A> jest następnie odpowiedzialny za <xref:System.ICustomFormatter> zwracanie implementacji, która zapewnia niestandardowe formatowanie.

Interfejs <xref:System.ICustomFormatter> ma jedną metodę, <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29>która jest wywoływana automatycznie przez metodę formatowania złożonego, raz dla każdego elementu formatu w ciągu formatu złożonego. Metoda <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29> ma trzy parametry: ciąg formatu, który reprezentuje `formatString` argument w elemencie formatu, obiekt do formatowania i obiekt, <xref:System.IFormatProvider> który zapewnia usługi formatowania. Zazwyczaj klasa, która implementuje <xref:System.ICustomFormatter> również <xref:System.IFormatProvider>implementuje, więc ten ostatni parametr jest odwołaniem do samej klasy formatowania niestandardowego. Metoda zwraca niestandardową sformatowaną reprezentację ciągu obiektu, który ma być sformatowany. Jeśli metoda nie może sformatować obiektu,`Nothing` należy zwrócić odwołanie null (w języku Visual Basic).

Poniższy przykład <xref:System.ICustomFormatter> zawiera `ByteByByteFormatter` implementację o nazwie, która wyświetla wartości całkowite jako sekwencję dwucyfrowych wartości szesnastkowy, po którym następuje spacja.

[!code-csharp[Conceptual.Formatting.Overview#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#15)]
[!code-vb[Conceptual.Formatting.Overview#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#15)]

Poniższy przykład używa `ByteByByteFormatter` klasy do formatowania wartości całkowitych. Należy zauważyć, że <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> metoda jest wywoływana więcej niż jeden raz w drugim <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> wywołaniu metody i że domyślny <xref:System.Globalization.NumberFormatInfo> dostawca jest używany w trzecim wywołaniu metody, ponieważ .`ByteByByteFormatter.Format` metoda nie rozpoznaje ciągu formatu "N0"`Nothing` i zwraca odwołanie null (w języku Visual Basic).

[!code-csharp[Conceptual.Formatting.Overview#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#16)]
[!code-vb[Conceptual.Formatting.Overview#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#16)]

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Definicja|
|-----------|----------------|
|[Standardowe ciągi formatujące liczby](../../../docs/standard/base-types/standard-numeric-format-strings.md)|W tym artykule opisano ciągi formatu standardowego, które tworzą często używane reprezentacje ciągów wartości liczbowych.|
|[Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)|W tym artykule opisano ciągi formatów niestandardowych, które tworzą formaty specyficzne dla aplikacji dla wartości liczbowych.|
|[Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|W tym artykule opisano ciągi formatu <xref:System.DateTime> standardowego, które tworzą często używane reprezentacje znaków wartości.|
|[Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|W tym artykule opisano ciągi formatów niestandardowych, które tworzą formaty specyficzne dla aplikacji dla <xref:System.DateTime> wartości.|
|[Standardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)|W tym artykule opisano ciągi formatu standardowego, które tworzą często używane reprezentacje ciągów interwałów czasu.|
|[Niestandardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|W tym artykule opisano ciągi formatów niestandardowych, które tworzą formaty specyficzne dla aplikacji dla interwałów czasowych.|
|[Wyliczanie ciągów formatujących](../../../docs/standard/base-types/enumeration-format-strings.md)|W tym artykule opisano ciągi formatu standardowego, które są używane do tworzenia reprezentacji ciągów wartości wyliczenia.|
|[Złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md)|W tym artykule opisano sposób osadzania jednej lub kilku sformatowanych wartości w ciągu. Ciąg może być następnie wyświetlany na konsoli lub zapisywany w strumieniu.|
|[Analiza składniowa ciągów](../../../docs/standard/base-types/parsing-strings.md)|Opisuje sposób inicjowania obiektów do wartości opisanych przez reprezentacje ciągów tych obiektów. Analizowanie jest odwrotną operacją formatowania.|

## <a name="reference"></a>Tematy pomocy

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- <xref:System.ICustomFormatter?displayProperty=nameWithType>
