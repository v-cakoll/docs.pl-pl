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
ms.openlocfilehash: a1f4d9107427140bcfa6b49bc8a850432fb204f7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348249"
---
# <a name="format-types-in-net"></a>Typy formatów w programie .NET

Formatowanie to proces konwersji wystąpienia klasy, struktury lub wartości wyliczenia na reprezentację ciągu, często tak, aby otrzymany ciąg można było wyświetlić użytkownikom lub deserializacji w celu przywrócenia oryginalnego typu danych. Ta konwersja może stanowić wiele wyzwań:

- Sposób, w jaki są przechowywane wartości wewnętrznie, niekoniecznie odzwierciedla sposób, w jaki użytkownicy chcą je wyświetlić. Na przykład numer telefonu może być przechowywany w postaci 8009999999, który nie jest przyjazny dla użytkownika. Zamiast tego powinna być wyświetlana jako 800-999-9999. Zapoznaj się z sekcją [ciągów formatów niestandardowych](#custom-format-strings) , aby zapoznać się z przykładem, który formatuje liczbę w ten sposób.

- Czasami Konwersja obiektu na jego reprezentację w postaci ciągu nie jest intuicyjna. Na przykład nie jest jasne, jak powinna zostać wyświetlona Reprezentacja ciągu obiektu temperatury lub osoby. Aby zapoznać się z przykładem, który formatuje obiekt temperatury na różne sposoby, zobacz sekcję [ciągi formatu standardowego](#standard-format-strings) .

- Wartości często wymagają formatowania z uwzględnieniem kultury. Na przykład w aplikacji, która używa liczb do odzwierciedlenia wartości pieniężnych, ciągi numeryczne powinny zawierać symbol waluty bieżącej kultury, separator grupy (który w większości kultur jest separatorem tysięcy) i symbol dziesiętny. Aby zapoznać się z przykładem, zobacz [Formatowanie wrażliwe na kulturę z sekcją dostawcy formatu](#culture-sensitive-formatting-with-format-providers) .

- Aplikacja może mieć taką samą wartość na różne sposoby. Na przykład aplikacja może reprezentować element członkowski wyliczenia, wyświetlając ciąg reprezentujący jego nazwę lub wyświetlając jego wartość podstawową. Aby zapoznać się z przykładem, który formatuje element członkowski wyliczenia <xref:System.DayOfWeek> na różne sposoby, zobacz sekcję [ciągi formatu standardowego](#standard-format-strings) .

> [!NOTE]
> Formatowanie konwertuje wartość typu na reprezentację w postaci ciągu. Analizowanie jest odwrotnością formatowania. Operacja analizowania tworzy wystąpienie typu danych z jego reprezentacji w postaci ciągu. Aby uzyskać informacje o konwertowaniu ciągów na inne typy danych, zobacz [Analizowanie ciągów](../../../docs/standard/base-types/parsing-strings.md).

Platforma .NET zapewnia obsługę formatowania zaawansowanego, która umożliwia deweloperom rozwiązywanie tych wymagań.

## <a name="formatting-in-net"></a>Formatowanie w programie .NET

Podstawowym mechanizmem formatowania jest domyślna implementacja metody <xref:System.Object.ToString%2A?displayProperty=nameWithType>, która została omówiona w [domyślnym formatowaniu przy użyciu metody ToString](#default-formatting-using-the-tostring-method) w dalszej części tego tematu. Jednak platforma .NET oferuje kilka sposobów modyfikowania i zwiększania obsługi formatowania domyślnego. Należą do nich między innymi:

- Zastępowanie metody <xref:System.Object.ToString%2A?displayProperty=nameWithType>, aby zdefiniować niestandardową reprezentację obiektu w postaci ciągu. Aby uzyskać więcej informacji, zobacz sekcję [Zastępowanie metody ToString](#override-the-tostring-method) w dalszej części tego tematu.

- Definiowanie specyfikatorów formatu, które umożliwiają reprezentację ciągu obiektu w celu przejęcia wielu formularzy. Na przykład, specyfikator formatu "X" w poniższej instrukcji konwertuje liczbę całkowitą na ciąg reprezentujący wartość szesnastkową.

     [!code-csharp[Conceptual.Formatting.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#3)]
     [!code-vb[Conceptual.Formatting.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#3)]

     Aby uzyskać więcej informacji na temat specyfikatorów formatu, zobacz sekcję [metody ToString i ciągi formatu](#the-tostring-method-and-format-strings) .

- Korzystanie z dostawców formatu w celu wykorzystania Konwencji formatowania określonej kultury. Na przykład poniższa instrukcja wyświetla wartość waluty przy użyciu Konwencji formatowania kultury en-US.

     [!code-csharp[Conceptual.Formatting.Overview#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#10)]
     [!code-vb[Conceptual.Formatting.Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#10)]

     Aby uzyskać więcej informacji o formatowaniu z dostawcami formatu, zobacz sekcję about [Providers (dostawcy formatu](#culture-sensitive-formatting-with-format-providers) ).

- Implementowanie interfejsu <xref:System.IFormattable> do obsługi obydwu konwersji ciągów z klasą <xref:System.Convert> i formatowaniem złożonym. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [interfejsu IFormattable](#the-iformattable-interface) .

- Użycie formatowania złożonego do osadzenia ciągu reprezentującego wartość w większym ciągu. Aby uzyskać więcej informacji, zobacz sekcję [formatowanie złożone](#composite-formatting) .

- Implementowanie <xref:System.ICustomFormatter> i <xref:System.IFormatProvider> w celu zapewnienia kompletnego rozwiązania do formatowania niestandardowego. Aby uzyskać więcej informacji, zobacz sekcję [formatowanie niestandardowe z ICustomFormatter](#custom-formatting-with-icustomformatter) .

Poniższe sekcje przedstawiają te metody konwertowania obiektu na jego reprezentację w postaci ciągu.

## <a name="default-formatting-using-the-tostring-method"></a>Formatowanie domyślne przy użyciu metody ToString

Każdy typ, który pochodzi od <xref:System.Object?displayProperty=nameWithType> automatycznie dziedziczy bezparametrowo metodę `ToString`, która domyślnie zwraca nazwę typu. Poniższy przykład ilustruje domyślną metodę `ToString`. Definiuje klasę o nazwie `Automobile`, która nie ma implementacji. Po utworzeniu wystąpienia klasy i wywołaniu metody `ToString` zostanie wyświetlona nazwa typu. Należy zauważyć, że metoda `ToString` nie jest jawnie wywoływana w przykładzie. Metoda <xref:System.Console.WriteLine%28System.Object%29?displayProperty=nameWithType> niejawnie wywołuje metodę `ToString` obiektu przekazaną do niego jako argument.

[!code-csharp[Conceptual.Formatting.Overview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/default1.cs#1)]
[!code-vb[Conceptual.Formatting.Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/default1.vb#1)]

> [!WARNING]
> Począwszy od Windows 8.1, środowisko wykonawcze systemu Windows zawiera interfejs <xref:Windows.Foundation.IStringable> z pojedynczą metodą [IStringable. ToString](xref:Windows.Foundation.IStringable.ToString%2A), która zapewnia obsługę formatowania domyślnego. Jednak zaleca się, aby typy zarządzane nie implementują interfejsu `IStringable`. Aby uzyskać więcej informacji, zobacz sekcję "środowisko wykonawcze systemu Windows i interfejs `IStringable`" na stronie odwołania <xref:System.Object.ToString%2A?displayProperty=nameWithType>.

Ponieważ wszystkie typy inne niż interfejsy są wyprowadzane z <xref:System.Object>, ta funkcja jest automatycznie dostarczana do niestandardowych klas lub struktur. Jednak funkcje oferowane przez domyślną metodę `ToString` są ograniczone: Chociaż identyfikuje typ, nie zawiera on informacji o wystąpieniu typu. Aby zapewnić ciąg reprezentujący obiekt, który zawiera informacje o tym obiekcie, należy zastąpić metodę `ToString`.

> [!NOTE]
> Struktury dziedziczą z <xref:System.ValueType>, które z kolei są wyprowadzane z <xref:System.Object>. Mimo że <xref:System.ValueType> przesłania <xref:System.Object.ToString%2A?displayProperty=nameWithType>, jego implementacja jest taka sama.

## <a name="override-the-tostring-method"></a>Zastąp metodę ToString

Wyświetlanie nazwy typu jest często ograniczonym zastosowaniem i nie pozwala na odbiorców typów odróżnienia jednego wystąpienia od drugiego. Można jednak zastąpić metodę `ToString`, aby zapewnić bardziej przydatną reprezentację wartości obiektu. Poniższy przykład definiuje obiekt `Temperature` i zastępuje jego metodę `ToString`, aby wyświetlić temperaturę w stopniach Celsjusza.

[!code-csharp[Conceptual.Formatting.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/overrides1.cs#2)]
[!code-vb[Conceptual.Formatting.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/overrides1.vb#2)]

W programie .NET Metoda `ToString` każdego typu wartości pierwotnej została zastąpiona, aby wyświetlić wartość obiektu zamiast jego nazwy. W poniższej tabeli przedstawiono przesłonięcie dla każdego typu pierwotnego. Należy zauważyć, że większość zastąpionych metod wywołuje inne Przeciążenie metody `ToString` i przekazuje ją specyfikator formatu "G", który definiuje format ogólny dla jego typu, a obiekt <xref:System.IFormatProvider>, który reprezentuje bieżącą kulturę.

|Typ|Zastąpienie metody ToString|
|----------|-----------------------|
|<xref:System.Boolean>|Zwraca <xref:System.Boolean.TrueString?displayProperty=nameWithType> lub <xref:System.Boolean.FalseString?displayProperty=nameWithType>.|
|<xref:System.Byte>|Wywołuje `Byte.ToString("G", NumberFormatInfo.CurrentInfo)`, aby sformatować <xref:System.Byte> wartość dla bieżącej kultury.|
|<xref:System.Char>|Zwraca znak jako ciąg.|
|<xref:System.DateTime>|Wywołuje `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)`, aby sformatować wartość daty i godziny dla bieżącej kultury.|
|<xref:System.Decimal>|Wywołuje `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)`, aby sformatować <xref:System.Decimal> wartość dla bieżącej kultury.|
|<xref:System.Double>|Wywołuje `Double.ToString("G", NumberFormatInfo.CurrentInfo)`, aby sformatować <xref:System.Double> wartość dla bieżącej kultury.|
|<xref:System.Int16>|Wywołuje `Int16.ToString("G", NumberFormatInfo.CurrentInfo)`, aby sformatować <xref:System.Int16> wartość dla bieżącej kultury.|
|<xref:System.Int32>|Wywołuje `Int32.ToString("G", NumberFormatInfo.CurrentInfo)`, aby sformatować <xref:System.Int32> wartość dla bieżącej kultury.|
|<xref:System.Int64>|Wywołuje `Int64.ToString("G", NumberFormatInfo.CurrentInfo)`, aby sformatować <xref:System.Int64> wartość dla bieżącej kultury.|
|<xref:System.SByte>|Wywołuje `SByte.ToString("G", NumberFormatInfo.CurrentInfo)`, aby sformatować <xref:System.SByte> wartość dla bieżącej kultury.|
|<xref:System.Single>|Wywołuje `Single.ToString("G", NumberFormatInfo.CurrentInfo)`, aby sformatować <xref:System.Single> wartość dla bieżącej kultury.|
|<xref:System.UInt16>|Wywołuje `UInt16.ToString("G", NumberFormatInfo.CurrentInfo)`, aby sformatować <xref:System.UInt16> wartość dla bieżącej kultury.|
|<xref:System.UInt32>|Wywołuje `UInt32.ToString("G", NumberFormatInfo.CurrentInfo)`, aby sformatować <xref:System.UInt32> wartość dla bieżącej kultury.|
|<xref:System.UInt64>|Wywołuje `UInt64.ToString("G", NumberFormatInfo.CurrentInfo)`, aby sformatować <xref:System.UInt64> wartość dla bieżącej kultury.|

## <a name="the-tostring-method-and-format-strings"></a>Metody ToString i ciągi formatujące

Opieranie się na domyślnej metodzie `ToString` lub zastępowanie `ToString` jest odpowiednie, gdy obiekt ma pojedynczą reprezentację ciągu. Jednak wartość obiektu często ma wiele reprezentacji. Na przykład temperatura może być wyrażona w stopniach Fahrenheita, stopniach Celsjusza i kelwinach. Podobnie wartość całkowita 10 może być reprezentowana na wiele sposobów, w tym 10, 10,0, 1.0 E01 lub $10,00.

Aby włączyć pojedynczą wartość, aby zawierała wiele reprezentacji ciągów, platforma .NET używa ciągów formatu. Ciąg formatu jest ciągiem zawierającym co najmniej jeden wstępnie zdefiniowany specyfikator formatu, które są pojedynczymi znakami lub grupami znaków, które definiują sposób formatowania danych wyjściowych przez metodę `ToString`. Ciąg formatu jest następnie przenoszona jako parametr do metody `ToString` obiektu i określa, jak będzie wyglądać ciąg reprezentujący wartość tego obiektu.

Wszystkie typy liczbowe, typy daty i godziny oraz typy wyliczeniowe w programie .NET obsługują wstępnie zdefiniowany zestaw specyfikatorów formatu. Można również użyć ciągów formatowania do zdefiniowania wielu reprezentacji ciągów dla typów danych zdefiniowanych przez aplikację.

### <a name="standard-format-strings"></a>Ciągi formatu standardowego

Ciąg formatu standardowego zawiera pojedynczy specyfikator formatu, który jest znakiem alfabetycznym, który definiuje ciąg reprezentujący obiekt, do którego jest stosowany, wraz z opcjonalnym specyfikatorem dokładności, który ma wpływ na liczbę cyfr wyświetlanych w Ciąg wynikowy. Jeśli specyfikator dokładności zostanie pominięty lub nie jest obsługiwany, specyfikator formatu standardowego jest równoznaczny z ciągiem formatu standardowego.

Platforma .NET definiuje zestaw specyfikatorów formatu standardowego dla wszystkich typów liczbowych, wszystkich typów daty i godziny oraz wszystkich typów wyliczeniowych. Na przykład każda z tych kategorii obsługuje specyfikator formatu standardowego "G", który definiuje ogólną reprezentację ciągu wartości tego typu.

Ciągi formatu standardowego dla typów wyliczeniowych bezpośrednio kontrolują reprezentację ciągu wartości. Ciągi formatu przesłane do metody `ToString` wartości wyliczenia określają, czy wartość jest wyświetlana przy użyciu nazwy ciągu (specyfikatory formatu "G" i "F"), jej podstawowej wartości całkowitej (specyfikator formatu "D") lub jej wartości szesnastkowej (specyfikator formatu "X"). Poniższy przykład ilustruje użycie ciągów formatu standardowego do formatowania <xref:System.DayOfWeek> Wyliczenie wartości.

[!code-csharp[Conceptual.Formatting.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/standard1.cs#4)]
[!code-vb[Conceptual.Formatting.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/standard1.vb#4)]

Aby uzyskać informacje na temat ciągów formatu wyliczenia, zobacz [ciągi formatujące Wyliczenie](../../../docs/standard/base-types/enumeration-format-strings.md).

Ciągi formatu standardowego dla typów liczbowych zwykle definiują ciąg wynikowy, którego dokładny wygląd jest kontrolowany przez jedną lub więcej wartości właściwości. Na przykład specyfikator formatu "C" formatuje liczbę jako wartość walutową. Po wywołaniu metody `ToString` ze specyfikatorem formatu "C" jako jedynego parametru, następujące wartości właściwości z obiektu <xref:System.Globalization.NumberFormatInfo> bieżącej kultury są używane do definiowania ciągu reprezentującego wartość liczbową:

- Właściwość <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A>, która określa symbol waluty bieżącej kultury.

- Właściwość <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> lub <xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A>, która zwraca liczbę całkowitą, która określa następujące elementy:

  - Położenie symbolu waluty.

  - Czy wartości ujemne są wskazywane przez wiodący znak ujemny, końcowy znak minus lub nawiasy.

  - Określa, czy spacja jest wyświetlana między wartością liczbową, a symbolem waluty.

- Właściwość <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A>, która definiuje liczbę cyfr dziesiętnych w ciągu wynikowym.

- Właściwość <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A>, która definiuje symbol separatora dziesiętnego w ciągu wynikowym.

- Właściwość <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A>, która definiuje symbol separatora grupy.

- Właściwość <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A>, która definiuje liczbę cyfr w każdej grupie po lewej stronie wartości dziesiętnej.

- Właściwość <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>, która określa znak ujemny używany w ciągu wynikowym, jeśli nawiasy nie są używane do wskazania wartości ujemnych.

Ponadto ciągi formatu liczbowego mogą zawierać specyfikator dokładności. Znaczenie tego specyfikatora zależy od ciągu formatu, z którym jest używany, ale zazwyczaj wskazuje całkowitą liczbę cyfr lub liczbę cyfr, które powinny być wyświetlane w ciągu wynikowym. Na przykład w poniższym przykładzie użyto standardowego ciągu numerycznego "X4" i specyfikatora dokładności, aby utworzyć wartość ciągu, która ma cztery cyfry szesnastkowe.

[!code-csharp[Conceptual.Formatting.Overview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/precisionspecifier1.cs#6)]
[!code-vb[Conceptual.Formatting.Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/precisionspecifier1.vb#6)]

Aby uzyskać więcej informacji na temat standardowych ciągów formatowania liczbowego, zobacz [Standardowe ciągi formatujące](../../../docs/standard/base-types/standard-numeric-format-strings.md).

Ciągi formatu standardowego dla wartości daty i godziny to aliasy dla ciągów formatów niestandardowych przechowywanych przez określoną właściwość <xref:System.Globalization.DateTimeFormatInfo>. Na przykład wywołanie metody `ToString` wartości daty i godziny przy użyciu specyfikatora formatu "D" powoduje wyświetlenie daty i godziny przy użyciu ciągu formatu niestandardowego, który jest przechowywany we właściwości <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> bieżącej kultury. (Aby uzyskać więcej informacji na temat ciągów formatu niestandardowego, zobacz [następną sekcję](#custom-format-strings)). Poniższy przykład ilustruje tę relację.

[!code-csharp[Conceptual.Formatting.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/alias1.cs#5)]
[!code-vb[Conceptual.Formatting.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/alias1.vb#5)]

Aby uzyskać więcej informacji na temat standardowych ciągów formatu daty i godziny, zobacz [ciągi standardowych formatów daty i godziny](../../../docs/standard/base-types/standard-date-and-time-format-strings.md).

Za pomocą ciągów formatu standardowego można także zdefiniować ciąg reprezentujący obiekt zdefiniowany przez aplikację, który jest generowany przez metodę `ToString(String)` obiektu. Można zdefiniować określone specyfikatory formatu standardowego, które obsługuje dany obiekt, i można określić, czy są one rozróżniane wielkości liter czy nie są rozróżniane wielkości liter. Implementacja metody `ToString(String)` powinna obsługiwać następujące elementy:

- Specyfikator formatu "G", który reprezentuje niestandardowy lub typowy format obiektu. Przeciążenie bezparametrowego metody `ToString` obiektu powinna wywołać swój `ToString(String)` Przeciążenie i przekazać go do ciągu formatu standardowego "G".

- Obsługa specyfikatora formatu, który jest równy odwołaniu o wartości null (`Nothing` w Visual Basic). Specyfikator formatu, który jest równy odwołaniu o wartości null, powinien być uważany za równoważny specyfikatorowi formatu "G".

Na przykład Klasa `Temperature` może wewnętrznie przechowywać temperaturę w stopniach Celsjusza i używać specyfikatorów formatu do reprezentowania wartości obiektu `Temperature` w stopniach Celsjusza, stopniach Fahrenheita i kelwinach. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.Formatting.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/appstandard1.cs#7)]
[!code-vb[Conceptual.Formatting.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/appstandard1.vb#7)]

### <a name="custom-format-strings"></a>Niestandardowe ciągi formatowania

Oprócz standardowych ciągów formatu, .NET definiuje niestandardowe ciągi formatu dla wartości liczbowych i wartości daty i godziny. Niestandardowy ciąg formatu składa się z co najmniej jednego specyfikatora formatu niestandardowego, który definiuje reprezentację ciągu wartości. Na przykład niestandardowy ciąg formatu daty i godziny "rrrr/mm/dd hh: mm: SS. FFFF t ZZZ" konwertuje datę na reprezentację ciągu w postaci "2008/11/15 07:45:00.0000 P-08:00" dla kultury en-US. Podobnie ciąg formatu niestandardowego "0000" konwertuje wartość całkowitą 12 na "0012". Aby zapoznać się z pełną listą niestandardowych ciągów formatujących, zobacz [Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) oraz [Niestandardowe ciągi formatujące liczbowe](../../../docs/standard/base-types/custom-numeric-format-strings.md).

Jeśli ciąg formatu składa się z pojedynczego specyfikatora formatu niestandardowego, specyfikator formatu powinien być poprzedzony wartością procentową (%) symbol, aby uniknąć nieporozumień ze specyfikatorem formatu standardowego. Poniższy przykład używa specyfikatora formatu niestandardowego "M", aby wyświetlić jedną cyfrę lub dwucyfrową liczbę miesięcy w danym dniu.

[!code-csharp[Conceptual.Formatting.Overview#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/singlecustom1.cs#8)]
[!code-vb[Conceptual.Formatting.Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/singlecustom1.vb#8)]

Wiele ciągów formatu standardowego dla wartości daty i godziny to aliasy dla ciągów formatów niestandardowych, które są zdefiniowane przez właściwości obiektu <xref:System.Globalization.DateTimeFormatInfo>. Niestandardowe ciągi formatujące oferują również znaczną elastyczność w dostarczaniu formatowania zdefiniowanego przez aplikację dla wartości numerycznych lub wartości daty i godziny. Można zdefiniować własne niestandardowe ciągi wynikowe dla wartości liczbowych i wartości daty i godziny, łącząc wiele niestandardowych specyfikatorów formatu w jeden ciąg formatu niestandardowego. W poniższym przykładzie zdefiniowano ciąg formatu niestandardowego, który wyświetla dzień tygodnia w nawiasach po nazwie miesiąca, dzień i roku.

[!code-csharp[Conceptual.Formatting.Overview#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/custom1.cs#9)]
[!code-vb[Conceptual.Formatting.Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/custom1.vb#9)]

W poniższym przykładzie zdefiniowano ciąg formatu niestandardowego, który wyświetla <xref:System.Int64> wartość jako standardowy, 7-cyfrowy numer telefonu amerykańskiego wraz z jego numerem kierunkowym.

[!code-csharp[Conceptual.Formatting.Overview#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/telnumber1.cs#21)]
[!code-vb[Conceptual.Formatting.Overview#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/telnumber1.vb#21)]

Chociaż ciągi formatu standardowego mogą ogólnie obsłużyć większość potrzeb formatowania dla typów zdefiniowanych przez aplikację, można także zdefiniować specyfikatory formatu niestandardowego, aby sformatować typy.

### <a name="format-strings-and-net-types"></a>Ciągi formatujące i typy .NET

Wszystkie typy liczbowe (czyli <xref:System.Byte>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>i <xref:System.Numerics.BigInteger>), a także <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, <xref:System.Guid>i wszystkie typy wyliczeniowe, obsługują formatowanie ciągów formatu. Informacje o określonych ciągach formatu obsługiwanych przez poszczególne typy można znaleźć w następujących tematach:

|Tytuł|Definicja|
|-----------|----------------|
|[Standardowe ciągi formatujące liczby](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Opisuje ciągi formatu standardowego, które tworzą często używane reprezentacje ciągów wartości liczbowych.|
|[Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Opisuje niestandardowe ciągi formatujące, które tworzą formaty specyficzne dla aplikacji dla wartości liczbowych.|
|[Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Opisuje ciągi formatu standardowego, które tworzą często używane reprezentacje ciągu dla <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości.|
|[Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Opisuje niestandardowe ciągi formatujące, które tworzą formaty charakterystyczne dla aplikacji dla <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości.|
|[Standardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Opisuje ciągi formatu standardowego, które tworzą często używane reprezentacje ciągów przedziałów czasu.|
|[Niestandardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Opisuje niestandardowe ciągi formatujące, które tworzą formaty specyficzne dla aplikacji dla przedziałów czasu.|
|[Ciągi formatujące wyliczenia](../../../docs/standard/base-types/enumeration-format-strings.md)|Opisuje ciągi formatu standardowego, które są używane do tworzenia reprezentacji ciągów wartości wyliczenia.|
|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|Opisuje ciągi formatu standardowego dla wartości <xref:System.Guid>.|

## <a name="culture-sensitive-formatting-with-format-providers"></a>Uwzględnianie kulturowe formatowania z dostawcami formatowania

Chociaż specyfikatory formatu pozwalają dostosować formatowanie obiektów, generowanie znaczących reprezentacji obiektów często wymaga dodatkowych informacji o formatowaniu. Na przykład formatowanie liczby jako wartości walutowej przy użyciu standardowego ciągu formatu "C" lub niestandardowego ciągu formatu, takiego jak "$ #, #. 00" wymaga co najmniej informacji o poprawnym symbolu waluty, separatorze grup i separatorze dziesiętnym, który ma być dostępny do uwzględnienia w sformatowanym ciągu. W programie .NET te dodatkowe informacje o formatowaniu są udostępniane za pomocą interfejsu <xref:System.IFormatProvider>, który jest dostarczany jako parametr do jednego lub większej liczby przeciążeń metody `ToString` typów liczbowych i typów dat i godzin. implementacje <xref:System.IFormatProvider> są używane w programie .NET do obsługi formatowania specyficznego dla kultury. Poniższy przykład ilustruje sposób, w jaki ciąg reprezentujący obiekt ulega zmianie, gdy jest sformatowany przy użyciu trzech <xref:System.IFormatProvider> obiektów, które reprezentują różne kultury.

[!code-csharp[Conceptual.Formatting.Overview#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformatprovider1.cs#11)]
[!code-vb[Conceptual.Formatting.Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformatprovider1.vb#11)]

Interfejs <xref:System.IFormatProvider> zawiera jedną metodę, <xref:System.IFormatProvider.GetFormat%28System.Type%29>, która ma jeden parametr, który określa typ obiektu, który zawiera informacje o formatowaniu. Jeśli metoda może dostarczyć obiekt tego typu, zwraca go. W przeciwnym razie zwraca odwołanie o wartości null (`Nothing` w Visual Basic).

<xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> jest metodą wywołania zwrotnego. Po wywołaniu przeciążenia metody `ToString`, która zawiera parametr <xref:System.IFormatProvider>, wywołuje metodę <xref:System.IFormatProvider.GetFormat%2A> tego obiektu <xref:System.IFormatProvider>. Metoda <xref:System.IFormatProvider.GetFormat%2A> jest odpowiedzialna za zwracanie obiektu, który dostarcza niezbędne informacje o formatowaniu, zgodnie z parametrem `formatType`, do metody `ToString`.

Kilka metod formatowania lub konwersji ciągów zawiera parametr typu <xref:System.IFormatProvider>, ale w wielu przypadkach wartość parametru jest ignorowana, gdy wywoływana jest metoda. W poniższej tabeli wymieniono niektóre metody formatowania, które używają parametru i typu obiektu <xref:System.Type> przekazanego do metody <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType>.

|Metoda|Typ parametru `formatType`|
|------------|------------------------------------|
|Metoda `ToString` typów liczbowych|<xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>|
|`ToString` Metoda typów daty i godziny|<xref:System.Globalization.DateTimeFormatInfo?displayProperty=nameWithType>|
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|

> [!NOTE]
> Metody `ToString` typów liczbowych i daty i godziny są przeciążone, a tylko niektóre przeciążenia zawierają parametr <xref:System.IFormatProvider>. Jeśli metoda nie ma parametru typu <xref:System.IFormatProvider>, zamiast tego zostanie przekazana obiekt, który jest zwracany przez właściwość <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>. Na przykład wywołanie domyślnej metody <xref:System.Int32.ToString?displayProperty=nameWithType> ostatecznie powoduje wywołanie metody, takie jak: `Int32.ToString("G", System.Globalization.CultureInfo.CurrentCulture)`.

Platforma .NET udostępnia trzy klasy, które implementują <xref:System.IFormatProvider>:

- <xref:System.Globalization.DateTimeFormatInfo>, Klasa, która dostarcza informacji o formatowaniu dla wartości daty i godziny dla określonej kultury. Jego implementacja <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> zwraca wystąpienie samego siebie.

- <xref:System.Globalization.NumberFormatInfo>, Klasa, która zawiera informacje o formatowaniu liczb dla określonej kultury. Jego implementacja <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> zwraca wystąpienie samego siebie.

- <xref:System.Globalization.CultureInfo>. Jego implementacja <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> może zwrócić obiekt <xref:System.Globalization.NumberFormatInfo> w celu udostępnienia informacji o formatowaniu liczb lub obiektu <xref:System.Globalization.DateTimeFormatInfo>, aby zapewnić informacje o formatowaniu dla wartości daty i godziny.

Możesz również zaimplementować własnego dostawcę formatu, aby zastąpić każdą z tych klas. Jednak Metoda <xref:System.IFormatProvider.GetFormat%2A> implementacji musi zwracać obiekt typu wymienionego w poprzedniej tabeli, jeśli musi dostarczyć informacje o formatowaniu do metody `ToString`.

### <a name="culture-sensitive-formatting-of-numeric-values"></a>Czułe na kulturę formatowanie wartości liczbowych

Domyślnie formatowanie wartości liczbowych jest zależne od kultury. Jeśli nie określisz kultury podczas wywoływania metody formatowania, używane są konwencje formatowania bieżącej kultury wątku. Jest to zilustrowane w poniższym przykładzie, który zmienia bieżącą kulturę wątku czterokrotnie, a następnie wywołuje metodę <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>. W każdym przypadku ciąg wynikowy odzwierciedla konwencje formatowania bieżącej kultury. Wynika to z faktu, że metody `ToString` i `ToString(String)` zawijają wywołania do każdej metody `ToString(String, IFormatProvider)` typu liczbowego.

[!code-csharp[Conceptual.Formatting.Overview#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific3.cs#19)]
[!code-vb[Conceptual.Formatting.Overview#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific3.vb#19)]

Możesz również sformatować wartość numeryczną dla określonej kultury, wywołując Przeciążenie `ToString`, które ma parametr `provider` i przekazując go:

- Obiekt <xref:System.Globalization.CultureInfo>, który reprezentuje kulturę, której konwencje formatowania mają być używane. Metoda <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> zwraca wartość właściwości <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType>, która jest obiektem <xref:System.Globalization.NumberFormatInfo>, który zawiera informacje o formatowaniu specyficzne dla kultury dla wartości liczbowych.

- Obiekt <xref:System.Globalization.NumberFormatInfo>, który definiuje konwencje formatowania specyficzne dla kultury, które mają być używane. Metoda <xref:System.Globalization.NumberFormatInfo.GetFormat%2A> zwraca wystąpienie samego siebie.

W poniższym przykładzie używane są <xref:System.Globalization.NumberFormatInfo> obiektów, które reprezentują kultury angielskie (Stany Zjednoczone) i angielskie (Zjednoczone Królestwo) oraz kultury neutralne w języku francuskim i rosyjskim, aby sformatować liczbę zmiennoprzecinkową.

[!code-csharp[Conceptual.Formatting.Overview#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific4.cs#20)]
[!code-vb[Conceptual.Formatting.Overview#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific4.vb#20)]

### <a name="culture-sensitive-formatting-of-date-and-time-values"></a>Czułe na kulturowe formatowanie wartości daty i godziny

Domyślnie formatowanie wartości daty i godziny jest zależne od kultury. Jeśli nie określisz kultury podczas wywoływania metody formatowania, używane są konwencje formatowania bieżącej kultury wątku. Jest to zilustrowane w poniższym przykładzie, który zmienia bieżącą kulturę wątku czterokrotnie, a następnie wywołuje metodę <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>. W każdym przypadku ciąg wynikowy odzwierciedla konwencje formatowania bieżącej kultury. Wynika to z faktu, że metody <xref:System.DateTime.ToString?displayProperty=nameWithType>, <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType>i <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> zawijają wywołania do metod <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> i <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>.

[!code-csharp[Conceptual.Formatting.Overview#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific1.cs#17)]
[!code-vb[Conceptual.Formatting.Overview#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific1.vb#17)]

Możesz również sformatować wartość daty i godziny dla określonej kultury poprzez wywołanie <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> lub przeciążenia <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType>, które ma `provider` parametr i przekazanie go:

- Obiekt <xref:System.Globalization.CultureInfo>, który reprezentuje kulturę, której konwencje formatowania mają być używane. Metoda <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> zwraca wartość właściwości <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>, która jest obiektem <xref:System.Globalization.DateTimeFormatInfo>, który zawiera informacje o formatowaniu specyficzne dla kultury dla wartości daty i godziny.

- Obiekt <xref:System.Globalization.DateTimeFormatInfo>, który definiuje konwencje formatowania specyficzne dla kultury, które mają być używane. Metoda <xref:System.Globalization.DateTimeFormatInfo.GetFormat%2A> zwraca wystąpienie samego siebie.

W poniższym przykładzie zastosowano <xref:System.Globalization.DateTimeFormatInfo> obiektów, które reprezentują kultury angielskie (Stany Zjednoczone) i angielskie (Zjednoczone Królestwo) oraz kulturę neutralną w języku francuskim i rosyjskim do formatowania daty.

[!code-csharp[Conceptual.Formatting.Overview#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific2.cs#18)]
[!code-vb[Conceptual.Formatting.Overview#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific2.vb#18)]

## <a name="the-iformattable-interface"></a>Interfejs IFormattable

Zazwyczaj typy, które przeciążą metodę `ToString` z ciągiem formatu i parametrem <xref:System.IFormatProvider> również implementują interfejs <xref:System.IFormattable>. Ten interfejs ma jeden element członkowski, <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, który zawiera ciąg formatu i dostawcę formatowania jako parametry.

Implementacja interfejsu <xref:System.IFormattable> dla klasy zdefiniowanej przez aplikację oferuje dwie zalety:

- Obsługa konwersji ciągów przez klasę <xref:System.Convert>. Wywołania metod <xref:System.Convert.ToString%28System.Object%29?displayProperty=nameWithType> i <xref:System.Convert.ToString%28System.Object%2CSystem.IFormatProvider%29?displayProperty=nameWithType> powodują automatyczne wywoływanie implementacji <xref:System.IFormattable>.

- Obsługa formatowania złożonego. Jeśli element formatu, który zawiera ciąg formatu, jest używany do formatowania typu niestandardowego, środowisko uruchomieniowe języka wspólnego automatycznie wywoła implementację <xref:System.IFormattable> i przekazuje go ciąg formatu. Aby uzyskać więcej informacji na temat formatowania złożonego przy użyciu metod, takich jak <xref:System.String.Format%2A?displayProperty=nameWithType> lub <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, zobacz sekcję [formatowanie złożone](#composite-formatting) .

W poniższym przykładzie zdefiniowano klasę `Temperature` implementującą interfejs <xref:System.IFormattable>. Obsługuje specyfikatory formatu "C" lub "G", aby wyświetlić temperaturę w c, specyfikator formatu "F", aby wyświetlić temperaturę w stopniach Fahrenheita i specyfikator formatu "K", aby wyświetlić temperaturę w Kelvin.

[!code-csharp[Conceptual.Formatting.Overview#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#12)]
[!code-vb[Conceptual.Formatting.Overview#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#12)]

Poniższy przykład tworzy wystąpienie obiektu `Temperature`. Następnie wywołuje metodę <xref:System.Convert.ToString%2A> i używa kilku ciągów formatu złożonego, aby uzyskać różne reprezentacje ciągów obiektu `Temperature`. Z kolei każda z tych wywołań metod wywołuje implementację <xref:System.IFormattable> klasy `Temperature`.

[!code-csharp[Conceptual.Formatting.Overview#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#13)]
[!code-vb[Conceptual.Formatting.Overview#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#13)]

## <a name="composite-formatting"></a>Formatowanie złożone

Niektóre metody, takie jak <xref:System.String.Format%2A?displayProperty=nameWithType> i <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, obsługują formatowanie złożone. Ciąg formatu złożonego jest rodzajem szablonu, który zwraca pojedynczy ciąg, który zawiera ciąg reprezentujący zero, jeden lub więcej obiektów. Każdy obiekt jest reprezentowany w ciągu formatu złożonego przez element formatu indeksowanego. Indeks elementu formatu odnosi się do położenia obiektu reprezentowanego na liście parametrów metody. Indeksy są oparte na zero. Na przykład w poniższym wywołaniu metody <xref:System.String.Format%2A?displayProperty=nameWithType> pierwszy element formatu `{0:D}`, jest zamieniany na ciąg reprezentujący `thatDate`; drugi element formatu, `{1}`, jest zastępowany ciągiem reprezentującym `item1`; i trzeci element formatu, `{2:C2}`, jest zastępowany ciągiem reprezentującym `item1.Value`.

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

Dwie metody formatowania złożonego, <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> i <xref:System.Text.StringBuilder.AppendFormat%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, zawierają parametr dostawcy formatu obsługujący niestandardowe formatowanie. Gdy każda z tych metod formatowania jest wywoływana, przekazuje obiekt <xref:System.Type>, który reprezentuje interfejs <xref:System.ICustomFormatter> do metody <xref:System.IFormatProvider.GetFormat%2A> dostawcy formatowania. Metoda <xref:System.IFormatProvider.GetFormat%2A> jest następnie odpowiedzialna za zwrócenie <xref:System.ICustomFormatter> implementacji, która zapewnia niestandardowe formatowanie.

Interfejs <xref:System.ICustomFormatter> ma pojedynczą metodę, <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29>, która jest wywoływana automatycznie przez metodę formatowania złożonego, jednokrotnie dla każdego elementu formatu w ciągu formatu złożonego. Metoda <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29> ma trzy parametry: ciąg formatu, który reprezentuje argument `formatString` w elemencie formatu, obiekt do sformatowania i obiekt <xref:System.IFormatProvider>, który zapewnia usługi formatowania. Zazwyczaj Klasa implementująca <xref:System.ICustomFormatter> również implementuje <xref:System.IFormatProvider>, dlatego ostatni parametr jest odwołaniem do samej klasy formatowania niestandardowego. Metoda zwraca niestandardową reprezentację ciągu obiektu do sformatowania. Jeśli metoda nie może sformatować obiektu, powinna zwrócić odwołanie o wartości null (`Nothing` w Visual Basic).

W poniższym przykładzie przedstawiono implementację <xref:System.ICustomFormatter> o nazwie `ByteByByteFormatter`, która wyświetla wartości całkowite jako sekwencję dwucyfrowych wartości szesnastkowych, po których następuje spacja.

[!code-csharp[Conceptual.Formatting.Overview#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#15)]
[!code-vb[Conceptual.Formatting.Overview#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#15)]

Poniższy przykład używa klasy `ByteByByteFormatter` do formatowania wartości całkowitych. Należy zauważyć, że metoda <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> jest wywoływana więcej niż raz w drugim wywołaniu metody <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> i że domyślny dostawca <xref:System.Globalization.NumberFormatInfo> jest używany w trzecim wywołaniu metody, ponieważ.`ByteByByteFormatter.Format` Metoda nie rozpoznaje ciągu formatu "N0" i zwraca odwołanie o wartości null (`Nothing` w Visual Basic).

[!code-csharp[Conceptual.Formatting.Overview#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#16)]
[!code-vb[Conceptual.Formatting.Overview#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#16)]

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Definicja|
|-----------|----------------|
|[Standardowe ciągi formatujące liczby](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Opisuje ciągi formatu standardowego, które tworzą często używane reprezentacje ciągów wartości liczbowych.|
|[Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Opisuje niestandardowe ciągi formatujące, które tworzą formaty specyficzne dla aplikacji dla wartości liczbowych.|
|[Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Opisuje ciągi formatu standardowego, które tworzą często używane reprezentacje ciągu wartości <xref:System.DateTime>.|
|[Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Opisuje niestandardowe ciągi formatujące, które tworzą formaty charakterystyczne dla aplikacji dla <xref:System.DateTime> wartości.|
|[Standardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Opisuje ciągi formatu standardowego, które tworzą często używane reprezentacje ciągów przedziałów czasu.|
|[Niestandardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Opisuje niestandardowe ciągi formatujące, które tworzą formaty specyficzne dla aplikacji dla przedziałów czasu.|
|[Ciągi formatujące wyliczenia](../../../docs/standard/base-types/enumeration-format-strings.md)|Opisuje ciągi formatu standardowego, które są używane do tworzenia reprezentacji ciągów wartości wyliczenia.|
|[Złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md)|Opisuje sposób osadzenia jednej lub więcej sformatowanych wartości w ciągu. Ciąg można następnie wyświetlić w konsoli lub zapisać w strumieniu.|
|[Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)|Wyświetla listę tematów, które zawierają instrukcje krok po kroku dotyczące wykonywania określonych operacji formatowania.|
|[Analizowanie ciągów](../../../docs/standard/base-types/parsing-strings.md)|Opisuje sposób inicjowania obiektów do wartości opisanych przez ciąg reprezentujący te obiekty. Analizowanie jest operacją odwrotną formatowania.|

## <a name="reference"></a>Tematy pomocy

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- <xref:System.ICustomFormatter?displayProperty=nameWithType>
