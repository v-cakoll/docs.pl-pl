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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10dd7e007ecd24ec3f127ab9c102cd758dfc7d75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579850"
---
# <a name="formatting-types-in-net"></a>Typy formatowania w .NET
<a name="Introduction"></a> Formatowanie to proces konwertowania wystąpienia klasy, struktury lub wyliczenia wartości do reprezentacji ciągu, często, tak aby wynikowy ciąg może być widoczny dla użytkowników lub deserializacji, aby przywrócić oryginalny typ danych. Ta konwersja może stanowić wiele wyzwań:  
  
-   Sposób, że wartości są przechowywane wewnętrznie nie odzwierciedlać sposób użytkowników chcesz przeglądać. Na przykład numer telefonu mogą być przechowywane w postaci 8009999999, który nie jest przyjazną dla użytkownika. Zamiast tego go powinna być wyświetlana jako 800-999-9999. Zobacz [niestandardowe ciągi formatów](#customStrings) sekcji, na przykład, w którym formatuje liczbę w ten sposób.  
  
-   Czasami konwersji obiektu do reprezentacji ciągu nie jest intuicyjny. Na przykład nie jest jasne wygląd reprezentację ciągu obiektu temperatury lub osoby. Na przykład, które formatuje obiektu temperatury na różne sposoby, zobacz [standardowe ciągi formatujące](#standardStrings) sekcji.  
  
-   Wartości często wymagają formatowania zależne od kultury. Na przykład w aplikacji, która używa liczb do wartości walutowej, ciągi numeryczne powinna zawierać symbol waluty bieżącej kultury, grupy separatora (które w większości kultur jest tysięcy separatora) i dziesiętny. Na przykład zobacz [zależne od kultury formatowania z dostawców formatu i interfejsem IFormatProvider](#FormatProviders) sekcji.  
  
-   Aplikacja może być wyświetlić tę samą wartość na różne sposoby. Na przykład aplikacja może reprezentować elementu członkowskiego wyliczenia, wyświetlając reprezentację ciągu nazwy i wyświetlając jego odpowiednia wartość. Na przykład, że formaty członkiem <xref:System.DayOfWeek> wyliczenia na różne sposoby, zobacz [standardowe ciągi formatujące](#standardStrings) sekcji.  
  
> [!NOTE]
>  Reprezentacja ciągu formatowania konwertuje wartość typu. Analiza jest odwrotność formatowania. Operacja związana tworzy wystąpienie typu danych z reprezentacji ciągu. Aby uzyskać informacje o konwertowanie ciągów na inne typy danych, zobacz [analizowanie ciągów](../../../docs/standard/base-types/parsing-strings.md).  
  
 .NET udostępnia bogate formatowania pomocy technicznej, który umożliwia deweloperom spełnić te wymagania.  
  
 Ten przegląd zawiera następujące sekcje:  
  
-   [Formatowanie w .NET](#NetFormatting)  
  
-   [Domyślna formatowania przy użyciu metody ToString](#DefaultToString)  
  
-   [Zastępowanie metody ToString](#OverrideToString)  
  
-   [ToString — metoda i ciągi formatujące](#FormatStrings)  
  
    -   [Standardowe ciągi formatujące](#standardStrings)  
  
    -   [Ciągi formatu niestandardowego](#customStrings)  
  
    -   [Formatowanie ciągów i typy biblioteki klas .NET](#stringRef)  
  
-   [Zależne od kultury formatowania z dostawców formatu i IFormatProvider — interfejs](#FormatProviders)  
  
    -   [Zależne od kultury formatowanie wartości numerycznych](#numericCulture)  
  
    -   [Zależne od kultury formatowania wartości daty i godziny](#dateCulture)  
  
-   [Interfejs IFormattable](#IFormattable)  
  
-   [Złożone formatowanie](#CompositeFormatting)  
  
-   [Niestandardowe formatowanie z ICustomFormatter](#Custom)  
  
-   [Tematy pokrewne](#RelatedTopics)  
  
-   [Dokumentacja](#Reference)  
  
<a name="NetFormatting"></a>   
## <a name="formatting-in-net"></a>Formatowanie w .NET  
 Mechanizm podstawowe formatowanie jest domyślna implementacja <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodę, która została omówiona w [domyślne formatowania za pomocą metody ToString](#DefaultToString) później w tym temacie. Jednak .NET udostępnia kilka metod modyfikowania i rozszerzyć domyślnej formatowania pomocy technicznej. Należą do nich między innymi:  
  
-   Zastępowanie <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodę, aby zdefiniować niestandardowy ciąg reprezentację wartość obiektu. Aby uzyskać więcej informacji, zobacz [Zastępowanie metody ToString](#OverrideToString) później w tym temacie.  
  
-   Definiowanie specyfikatory formatu, umożliwiających reprezentację ciągu wartość obiektu do mieć wiele form. Na przykład "X" specyfikatora formatu w następującej instrukcji konwertuje całkowitą wartość szesnastkową reprezentację ciągu.  
  
     [!code-csharp[Conceptual.Formatting.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#3)]
     [!code-vb[Conceptual.Formatting.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#3)]  
  
     Aby uzyskać więcej informacji na temat specyfikatory formatu, zobacz [metody ToString i ciągi formatujące](#FormatStrings) sekcji.  
  
-   Aby móc korzystać z Konwencji formatowania określonej kultury przy użyciu dostawców formatu. Na przykład następująca instrukcja wyświetla wartość waluty przy użyciu konwencji formatowania kultury en US.  
  
     [!code-csharp[Conceptual.Formatting.Overview#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#10)]
     [!code-vb[Conceptual.Formatting.Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#10)]  
  
     Aby uzyskać więcej informacji na temat formatowania z dostawców formatu, zobacz [dostawców formatu i interfejs IFormatProvider](#FormatProviders) sekcji.  
  
-   Implementowanie <xref:System.IFormattable> interfejs do obsługi zarówno Konwersja ciągu z <xref:System.Convert> klasy i złożone formatowanie. Aby uzyskać więcej informacji, zobacz [interfejsu IFormattable](#IFormattable) sekcji.  
  
-   Przy użyciu złożonego formatowania do osadzenia reprezentacja ciągu wartości w ciągu większy. Aby uzyskać więcej informacji, zobacz [złożone formatowanie](#CompositeFormatting) sekcji.  
  
-   Implementowanie <xref:System.ICustomFormatter> i <xref:System.IFormatProvider> kompletne rozwiązanie formatowania niestandardowych. Aby uzyskać więcej informacji, zobacz [niestandardowe formatowanie ICustomFormatter](#Custom) sekcji.  
  
 Poniższe sekcje Sprawdź, czy te metody konwersji obiektu do reprezentacji ciągu.  
  
 [Powrót do początku](#Introduction)  
  
<a name="DefaultToString"></a>   
## <a name="default-formatting-using-the-tostring-method"></a>Domyślne formatowania przy użyciu metody ToString  
 Każdy typ pochodzący od <xref:System.Object?displayProperty=nameWithType> automatycznie dziedziczy bez parametrów `ToString` metody, która zwraca nazwę typu domyślnie. Poniższy przykład przedstawia domyślnie `ToString` metody. Definiuje klasę o nazwie `Automobile` mający żadnej implementacji. Podczas tworzenia wystąpienia klasy i jej `ToString` metoda jest wywoływana, wyświetla jego nazwy. Należy pamiętać, że `ToString` — metoda nie została jawnie wywołana w przykładzie. <xref:System.Console.WriteLine%28System.Object%29?displayProperty=nameWithType> Metoda niejawnie wywołuje `ToString` metody obiektu przekazanego do niego jako argument.  
  
 [!code-csharp[Conceptual.Formatting.Overview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/default1.cs#1)]
 [!code-vb[Conceptual.Formatting.Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/default1.vb#1)]  
  
> [!WARNING]
>  Począwszy od [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[wrt](../../../includes/wrt-md.md)] obejmuje [IStringable](http://msdn.microsoft.com/library/windows/apps/windows.foundation.istringable.aspx) interfejsu z jedną metodę [IStringable.ToString](http://msdn.microsoft.com/library/windows/apps/windows.foundation.istringable.tostring.aspx), zapewniające domyślne formatowanie pomocy technicznej. Firma Microsoft zaleca jednak typy zarządzane nie implementują `IStringable` interfejsu. Aby uzyskać więcej informacji, zobacz " [!INCLUDE[wrt](../../../includes/wrt-md.md)] i `IStringable` interfejsu" sekcja na <xref:System.Object.ToString%2A?displayProperty=nameWithType> strony odwołania.  
  
 Ponieważ wszystkich typów innych niż interfejsy są pochodnymi <xref:System.Object>, ta funkcja jest teraz udostępniana automatycznie do niestandardowej klasy lub struktury. Jednak funkcje oferowane przez domyślny `ToString` metody, jest ograniczona: mimo że identyfikuje typ, nie zawierają wszystkie informacje dotyczące wystąpienia typu. Aby zapewnić reprezentację ciągu obiektu, który zawiera informacje o obiekcie, konieczne jest przesłonięcie `ToString` metody.  
  
> [!NOTE]
>  Dziedzicz struktury <xref:System.ValueType>, który z kolei jest określana na podstawie <xref:System.Object>. Mimo że <xref:System.ValueType> zastępuje <xref:System.Object.ToString%2A?displayProperty=nameWithType>, jego implementacja jest identyczny.  
  
 [Powrót do początku](#Introduction)  
  
<a name="OverrideToString"></a>   
## <a name="overriding-the-tostring-method"></a>Zastąpienie metody ToString  
 Wyświetlanie nazwy typu jest często ograniczone użycie i nie zezwala na konsumentów typów do odróżnienia jednego wystąpienia z innej. Jednak można zastąpić `ToString` metodę w celu zapewnienia bardziej praktyczne odwzorowanie wartość obiektu. W poniższym przykładzie zdefiniowano `Temperature` obiektu i zastąpień jego `ToString` metodę w celu wyświetlenia temperatura w stopniach c.  
  
 [!code-csharp[Conceptual.Formatting.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/overrides1.cs#2)]
 [!code-vb[Conceptual.Formatting.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/overrides1.vb#2)]  
  
 W środowisku .NET `ToString` metody każdego typu wartości pierwotnej została zastąpiona do wyświetlania wartości obiektu zamiast jego nazwy. W poniższej tabeli przedstawiono zastąpienie dla każdego typu pierwotnego. Należy zauważyć, że większość przesłoniętych metod wywołać innego przeciążenia metody `ToString` — metoda i przekaż go specyfikator formatu "G", który definiuje format Ogólne dla jego typu, i <xref:System.IFormatProvider> obiekt, który reprezentuje bieżącej kultury.  
  
|Typ|Zastąpienie ToString|  
|----------|-----------------------|  
|<xref:System.Boolean>|Zwraca jedną <xref:System.Boolean.TrueString?displayProperty=nameWithType> lub <xref:System.Boolean.FalseString?displayProperty=nameWithType>.|  
|<xref:System.Byte>|Wywołania `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` do formatowania <xref:System.Byte> wartość dla bieżącej kultury.|  
|<xref:System.Char>|Zwraca znak jako ciąg.|  
|<xref:System.DateTime>|Wywołania `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` do formatowania wartości daty i godziny dla bieżącej kultury.|  
|<xref:System.Decimal>|Wywołania `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` do formatowania <xref:System.Decimal> wartość dla bieżącej kultury.|  
|<xref:System.Double>|Wywołania `Double.ToString("G", NumberFormatInfo.CurrentInfo)` do formatowania <xref:System.Double> wartość dla bieżącej kultury.|  
|<xref:System.Int16>|Wywołania `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` do formatowania <xref:System.Int16> wartość dla bieżącej kultury.|  
|<xref:System.Int32>|Wywołania `Int32.ToString("G", NumberFormatInfo.CurrentInfo)` do formatowania <xref:System.Int32> wartość dla bieżącej kultury.|  
|<xref:System.Int64>|Wywołania `Int64.ToString("G", NumberFormatInfo.CurrentInfo)` do formatowania <xref:System.Int64> wartość dla bieżącej kultury.|  
|<xref:System.SByte>|Wywołania `SByte.ToString("G", NumberFormatInfo.CurrentInfo)` do formatowania <xref:System.SByte> wartość dla bieżącej kultury.|  
|<xref:System.Single>|Wywołania `Single.ToString("G", NumberFormatInfo.CurrentInfo)` do formatowania <xref:System.Single> wartość dla bieżącej kultury.|  
|<xref:System.UInt16>|Wywołania `UInt16.ToString("G", NumberFormatInfo.CurrentInfo)` do formatowania <xref:System.UInt16> wartość dla bieżącej kultury.|  
|<xref:System.UInt32>|Wywołania `UInt32.ToString("G", NumberFormatInfo.CurrentInfo)` do formatowania <xref:System.UInt32> wartość dla bieżącej kultury.|  
|<xref:System.UInt64>|Wywołania `UInt64.ToString("G", NumberFormatInfo.CurrentInfo)` do formatowania <xref:System.UInt64> wartość dla bieżącej kultury.|  
  
 [Powrót do początku](#Introduction)  
  
<a name="FormatStrings"></a>   
## <a name="the-tostring-method-and-format-strings"></a>Metoda ToString i ciągi formatujące  
 Opierając się na domyślnej `ToString` metody lub zastępowanie `ToString` jest odpowiednia, jeśli obiekt nie ma reprezentacji w postaci jednego ciągu. Wartość obiektu ma często wiele oświadczeń. Na przykład temperatury mogą być wyrażone w stopniach f, stopni c lub Kel. Podobnie, wartość całkowita 10 może być reprezentowany na wiele sposobów, łącznie z 10, 10.0, 1.0e01 lub 10,00 $.  
  
 Aby włączyć pojedynczą wartość ma wiele reprezentacji ciągu, .NET używa ciągi formatów. Ciąg formatu jest ciąg, który zawiera jeden lub więcej wstępnie zdefiniowanych specyfikatory formatu, które są pojedynczy znaki lub grup znaków, które definiują sposób `ToString` metody należy sformatować dane wyjściowe. Ciąg formatu są następnie przekazywane jako parametr do obiektu `ToString` — metoda i określa wygląd reprezentację ciągu wartość tego obiektu.  
  
 Wszystkie typy liczbowe, daty i czasu typy i typy wyliczeniowe w .NET obsługuje zestaw wstępnie zdefiniowanych specyfikatory formatu. Ciągi formatujące służy również do definiowania wielu reprezentacji ciągu typów danych zdefiniowanych przez aplikację.  
  
<a name="standardStrings"></a>   
### <a name="standard-format-strings"></a>Standardowe ciągi formatujące  
 Ciąg formatu standardowych zawiera specyfikator formatu jednej, która jest znakiem alfabetycznym, który definiuje reprezentację ciągu obiektu, do którego jest stosowana, wraz z Specyfikator dokładności opcjonalne, które wpływa na liczbę cyfr są wyświetlane w ciąg wyniku. Specyfikator dokładności zostanie pominięty lub nie jest obsługiwana, specyfikator formatu standardowych jest odpowiednikiem standardowego formatu ciągu.  
  
 .NET definiuje zestaw specyfikatory formatu standardowe dla wszystkich typów numerycznych, wszystkie daty i czasu typów i wszystkie typy wyliczeniowe. Na przykład każdej z tych kategorii obsługuje specyfikatora formatu standardowych "G", który definiuje parametry ogólne reprezentację wartości tego typu.  
  
 Standardowe ciągi formatujące dla typów wyliczenia kontrolować bezpośrednio reprezentacja ciągu wartości. Ciągi formatu przekazany do wartością wyliczenia `ToString` metody określają, czy wartość jest wyświetlany za pomocą nazwy ciągu ("G" i "F" format specyfikatory), jego odpowiednia wartość całkowitą (specyfikator formatu "D") lub jego wartość szesnastkowa ("X "specyfikator formatu). Poniższy przykład przedstawia użycie standardowe ciągi formatujące do formatowania <xref:System.DayOfWeek> wartości wyliczenia.  
  
 [!code-csharp[Conceptual.Formatting.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/standard1.cs#4)]
 [!code-vb[Conceptual.Formatting.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/standard1.vb#4)]  
  
 Aby uzyskać informacje o wyliczanie ciągów formatujących, zobacz [wyliczanie ciągów formatujących](../../../docs/standard/base-types/enumeration-format-strings.md).  
  
 Standardowe ciągi formatujące na typy liczbowe zazwyczaj Definiowanie ciąg wyniku, którego wygląd dokładne jest kontrolowane przez jedną lub więcej wartości właściwości. Na przykład specyfikator formatu "C" formatuje liczbę jako wartość walutową. Podczas wywoływania `ToString` metody z specyfikator formatu "C", jako parametr tylko, następujące wartości właściwości z bieżącej kultury <xref:System.Globalization.NumberFormatInfo> obiektu są używane do definiowania reprezentację ciągu wartość liczbowa:  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A> Właściwość, która określa symbol waluty bieżącej kultury.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> Lub <xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A> właściwość, która zwraca liczbę całkowitą, która określa następujące:  
  
    -   Umieszczenie symbolu waluty.  
  
    -   Określa, czy wartości ujemne są oznaczone znakiem minus wiodące, końcowe znaku minus lub nawiasów.  
  
    -   Określa, czy między wartością liczbową i symbol waluty pojawia się spacja.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A> Właściwość, która określa liczbę cyfr ułamkowych w ciągu wynik.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A> Właściwość, która definiuje symbol separatora dziesiętnego w ciągu wynik.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A> Właściwość, która definiuje symbol separatora grupy.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A> Właściwość, która definiuje liczbę miejsc po przecinku w każdej grupie, do lewej strony dziesiętnego.  
  
-   <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> Właściwość, która określa znakiem minus użytego w ciągu wyniku, jeśli nawiasy nie są używane do wskazywania wartości ujemnych.  
  
 Ponadto ciągi formatujące mogą obejmować Specyfikator dokładności. Znaczenie w tym specyfikatorze zależy od ciąg formatu, z którym jest używany, ale zwykle wskazuje całkowitą liczbę cyfr lub liczba cyfr ułamkowych, które powinny być wyświetlane w ciągu wynik. Na przykład w poniższym przykładzie użyto "X 4" liczbowych ciągu standardowym i Specyfikator dokładności utworzyć wartość ciągu, która ma cztery cyfry szesnastkowe.  
  
 [!code-csharp[Conceptual.Formatting.Overview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/precisionspecifier1.cs#6)]
 [!code-vb[Conceptual.Formatting.Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/precisionspecifier1.vb#6)]  
  
 Aby uzyskać więcej informacji na temat liczbowe standardowe ciągi formatujące, zobacz [standardowe ciągi formatu liczbowego](../../../docs/standard/base-types/standard-numeric-format-strings.md).  
  
 Standardowe ciągi formatujące dla wartości daty i godziny są aliasami ciągi formatujące niestandardowe przechowywane na określony <xref:System.Globalization.DateTimeFormatInfo> właściwości. Na przykład wywołanie elementu `ToString` metody wartość daty i godziny w specyfikatorze formatu "D" Wyświetla datę i godzinę za pomocą ciąg formatu niestandardowe przechowywane w bieżącej kultury <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> właściwości. (Aby uzyskać więcej informacji o niestandardowych ciągów formatu, zobacz [następnej sekcji](#customStrings).) Poniższy przykład przedstawia tę relację.  
  
 [!code-csharp[Conceptual.Formatting.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/alias1.cs#5)]
 [!code-vb[Conceptual.Formatting.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/alias1.vb#5)]  
  
 Aby uzyskać więcej informacji o standardowych ciągów daty i godziny format, zobacz [standardowe ciągi daty i godziny Format](../../../docs/standard/base-types/standard-date-and-time-format-strings.md).  
  
 Standardowe ciągi formatujące również służy do definiowania reprezentację ciągu obiektu zdefiniowanym przez aplikację, który jest generowany przez obiektu `ToString(String)` metody. Można zdefiniować specyfikatory określonego formatu standardowych, które obsługuje obiektu, a następnie można określić, czy są one z uwzględnieniem wielkości liter lub bez uwzględniania wielkości liter. Implementacji `ToString(String)` metoda powinna obsługiwać następujące:  
  
-   Specyfikator formatu "G", reprezentujący zwyczajowe lub wspólnych format obiektu. Przeciążenia bez parametrów do obiektu `ToString` powinny wywoływać metodę jego `ToString(String)` przeciążenia i przekaż go ciągu standardowego formatu: "G".  
  
-   Obsługa specyfikatora formatu, który jest taki sam, jak odwołanie o wartości null (`Nothing` w języku Visual Basic). Specyfikator formatu, który jest taki sam, jak odwołanie o wartości null powinny być traktowane jako równoważne specyfikator formatu "G".  
  
 Na przykład `Temperature` klasy wewnętrznie i można przechowywać temperatura w stopniach c Użyj specyfikatory formatu w celu przedstawienia wartość `Temperature` obiektu w stopniach c, f stopni i Kel. Poniższy przykład stanowi ilustrację.  
  
 [!code-csharp[Conceptual.Formatting.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/appstandard1.cs#7)]
 [!code-vb[Conceptual.Formatting.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/appstandard1.vb#7)]  
  
 [Powrót do początku](#Introduction)  
  
<a name="customStrings"></a>   
### <a name="custom-format-strings"></a>Niestandardowe ciągi formatujące  
 Oprócz standardowe ciągi formatujące .NET definiuje niestandardowych ciągów formatu dla wartości liczbowych i wartości daty i godziny. Niestandardowy ciąg formatu składa się z specyfikatorów formatu niestandardowego, definiujące wartość reprezentację ciągu. Na przykład niestandardowe datę i godzinę formatu ciągu "rrrr/mm/dd. hh:mm:ss.ffff t zzz" Konwertuje datę reprezentacji ciągu w postaci "07:45:00.0000 11/2008/15 P -08:00" dla kultury en US. Podobnie niestandardowy ciąg formatu "0000" konwertuje wartość całkowita 12, aby "0012". Aby uzyskać pełną listę niestandardowych ciągów formatu, zobacz [niestandardowe ciągi daty i godziny Format](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) i [niestandardowych ciągów formatu liczbowego](../../../docs/standard/base-types/custom-numeric-format-strings.md).  
  
 Jeśli ciąg formatu zawiera specyfikatora formatu niestandardowego pojedynczego, specyfikator formatu powinien być poprzedzony symbol procentu (%), aby uniknąć pomylenia z specyfikator formatu standardowych. W poniższym przykładzie użyto specyfikator formatu niestandardowego "M", aby wyświetlić liczbę jedno- lub dwucyfrowe miesiąc od określonej daty.  
  
 [!code-csharp[Conceptual.Formatting.Overview#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/singlecustom1.cs#8)]
 [!code-vb[Conceptual.Formatting.Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/singlecustom1.vb#8)]  
  
 Wiele standardowe ciągi formatujące dla wartości daty i godziny są aliasami niestandardowych ciągów formatu zdefiniowane przez właściwości <xref:System.Globalization.DateTimeFormatInfo> obiektu. Ciągi formatu niestandardowego oferują także dużą elastyczność w zapewnianiu zdefiniowanym przez aplikację formatowanie wartości numerycznych lub wartości daty i godziny. Łączenie wielu specyfikatorów formatu niestandardowego w jednym niestandardowy ciąg formatu można zdefiniować własny ciągów wynikowych niestandardowych dla wartości liczbowych i wartości daty i godziny. W poniższym przykładzie zdefiniowano ciąg formatu niestandardowego, który wyświetla dzień tygodnia w nawiasach po nazwie miesiąc, dzień i roku.  
  
 [!code-csharp[Conceptual.Formatting.Overview#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/custom1.cs#9)]
 [!code-vb[Conceptual.Formatting.Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/custom1.vb#9)]  
  
 W poniższym przykładzie zdefiniowano ciąg formatu niestandardowego, który wyświetla <xref:System.Int64> wartość jako liczbę telefon Stanów Zjednoczonych standardowe, 7 cyfr wraz z jego numer kierunkowy.  
  
 [!code-csharp[Conceptual.Formatting.Overview#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/telnumber1.cs#21)]
 [!code-vb[Conceptual.Formatting.Overview#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/telnumber1.vb#21)]  
  
 Mimo że standardowe ciągi formatujące ogólnie może obsługiwać większość formatowania potrzeb Twojej typy danych zdefiniowane przez aplikację, mogą również określić specyfikatorów formatu niestandardowego do Twojej typy formatowania.  
  
 [Powrót do początku](#Introduction)  
  
<a name="stringRef"></a>   
### <a name="format-strings-and-net-types"></a>Ciągi formatujące i typów .NET  
 Wszystkie typy liczbowe (to znaczy <xref:System.Byte>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>i <xref:System.Numerics.BigInteger>typy), a także <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, <xref:System.Guid>, i obsługują wszystkie typy wyliczeniowe, formatowanie z ciągami formatu. Uzyskać informacji o obsługiwanych przez każdy typ ciągi określonego formatu zobacz następujące tematy:  
  
|Tytuł|Definicja|  
|-----------|----------------|  
|[Standardowe ciągi formatujące liczby](../../../docs/standard/base-types/standard-numeric-format-strings.md)|W tym artykule opisano standardowe ciągi formatujące utworzonych reprezentacji ciągu często używane wartości liczbowych.|  
|[Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)|W tym artykule opisano tworzenie formatów specyficzne dla aplikacji dla wartości liczbowych ciągi formatu niestandardowego.|  
|[Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Opisuje standardowe ciągi formatujące utworzonych często używanych ciągów <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości.|  
|[Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|W tym artykule opisano tworzenie formatów specyficzne dla aplikacji dla ciągi formatu niestandardowego <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości.|  
|[Standardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)|W tym artykule opisano standardowe ciągi formatujące utworzonych reprezentacji ciągu często używane odstępach czasu.|  
|[Niestandardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|W tym artykule opisano tworzenie formatów specyficzne dla aplikacji dla przedziały czasu ciągi formatu niestandardowego.|  
|[Ciągi formatujące wyliczenia](../../../docs/standard/base-types/enumeration-format-strings.md)|W tym artykule opisano standardowym formacie ciągów, które zostaną użyte do utworzenia reprezentacji ciągu wartości wyliczenia.|  
|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|Opisuje standardowe ciągi formatujące dla <xref:System.Guid> wartości.|  
  
<a name="FormatProviders"></a>   
## <a name="culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface"></a>Wrażliwość na ustawienia kulturowe — mechanizm formatowania i interfejs IFormatProvider  
 Mimo że specyfikatory formatu umożliwiają dostosowanie, formatowanie obiektów, produkujących znaczący reprezentację ciągu obiektów często wymaga dodatkowe informacje dotyczące formatowania. Na przykład formatowania liczbę jako wartość walutową przy użyciu standardowego formatu ciągu "C" lub niestandardowy ciąg formatu, takie jak "$ #, #. 00" wymaga, co najmniej informacje dotyczące symbol waluty poprawne, separatora grupy i separatora dziesiętnego jako dostępne do dołączenia ciągu w formacie. W środowisku .NET, to dodatkowe informacje dotyczące formatowania ma zostać udostępnione za pośrednictwem <xref:System.IFormatProvider> interfejsu, który jest dostarczany jako parametr do co najmniej jeden przeciążeń `ToString` metody typami numerycznymi i typy daty i godziny. <xref:System.IFormatProvider> implementacje są używane w środowisku .NET do obsługuje specyficzne dla kultury. Poniższy przykład przedstawia, jak zmienia reprezentację ciągu obiektu, gdy jest on formatowany z trzema <xref:System.IFormatProvider> obiektów, które reprezentują innych kultur.  
  
 [!code-csharp[Conceptual.Formatting.Overview#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformatprovider1.cs#11)]
 [!code-vb[Conceptual.Formatting.Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformatprovider1.vb#11)]  
  
 <xref:System.IFormatProvider> Interfejs zawiera jedną metodę <xref:System.IFormatProvider.GetFormat%28System.Type%29>, który ma jeden parametr, który określa typ obiektu, który zawiera informacje dotyczące formatowania. Jeśli metoda zapewniają tego typu obiektu, zwraca go. W przeciwnym razie zwraca odwołanie o wartości null (`Nothing` w języku Visual Basic).  
  
 <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> jest to metoda wywołania zwrotnego. Podczas wywoływania `ToString` przeciążenie metody, która obejmuje <xref:System.IFormatProvider> parametru wywołuje <xref:System.IFormatProvider.GetFormat%2A> metoda tego <xref:System.IFormatProvider> obiektu. <xref:System.IFormatProvider.GetFormat%2A> Metoda jest odpowiedzialna za zwraca obiekt, który dostarcza niezbędne informacje formatowania, określony przez jego `formatType` parametru, do `ToString` metody.  
  
 Parametr typu obejmują wiele metod konwersji formatowania lub ciąg <xref:System.IFormatProvider>, ale w wielu przypadkach wartość parametru jest ignorowany podczas wywoływania metody. W poniższej tabeli przedstawiono niektóre metody formatowania używających parametr i typ <xref:System.Type> obiektów, które przekazują do <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metody.  
  
|Metoda|Typ `formatType` parametru|  
|------------|------------------------------------|  
|`ToString` Metoda typy liczbowe|<xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>|  
|`ToString` Metoda typy daty i godziny|<xref:System.Globalization.DateTimeFormatInfo?displayProperty=nameWithType>|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|  
  
> [!NOTE]
>  `ToString` Są przeciążone metody typami numerycznymi i typy daty i godziny, a tylko przeciążeń między innymi <xref:System.IFormatProvider> parametru. Jeśli metoda nie ma parametru typu <xref:System.IFormatProvider>, obiekt, który jest zwracany przez <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwość jest przekazywana zamiast tego. Na przykład wywołanie domyślne <xref:System.Int32.ToString?displayProperty=nameWithType> metody ostatecznie wynikiem wywołania metody, takie jak następujące: `Int32.ToString("G", System.Globalization.CultureInfo.CurrentCulture)`.  
  
 .NET udostępnia trzy klasy, które implementują <xref:System.IFormatProvider>:  
  
-   <xref:System.Globalization.DateTimeFormatInfo>, klasy, która zawiera informacje dotyczące formatowania dla wartości daty i godziny dla określonej kultury. Jego <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementacja zwraca wystąpienia samej siebie.  
  
-   <xref:System.Globalization.NumberFormatInfo>, Klasa udostępniająca informacje numeryczne formatowania dla określonej kultury. Jego <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementacja zwraca wystąpienia samej siebie.  
  
-   <xref:System.Globalization.CultureInfo>. Jego <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementacja może zwracać <xref:System.Globalization.NumberFormatInfo> obiekt, aby podać informacje numeryczne formatowania lub <xref:System.Globalization.DateTimeFormatInfo> obiekt, aby podać informacje dotyczące formatowania dla wartości daty i godziny.  
  
 Można też wdrożyć własnego dostawcę formatowanie zastąpić któregokolwiek z tych klas. Jednak implementację programu <xref:System.IFormatProvider.GetFormat%2A> metoda musi zwracać obiekt typu wymienione w powyższej tabeli, jeśli musi podać informacje dotyczące formatowania do `ToString` metody.  
  
 [Powrót do początku](#Introduction)  
  
<a name="numericCulture"></a>   
### <a name="culture-sensitive-formatting-of-numeric-values"></a>Wrażliwość na ustawienia kulturowe — formatowania wartości numerycznych  
 Domyślnie formatowanie wartości numerycznych jest zależne od kultury. Jeśli nie określisz kultury, gdy należy wywołać metodę formatowania, są używane konwencje formatowanie bieżącej kultury wątku. Jest to zilustrowane w poniższym przykładzie, który zmienia bieżącej kultury wątku cztery razy, a następnie wywołuje <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> metody. W każdym przypadku ciąg wyniku odzwierciedla Konwencji formatowania bieżącej kultury. Jest to spowodowane `ToString` i `ToString(String)` metody zawijać wywołania do każdego typu numerycznego `ToString(String, IFormatProvider)` metody.  
  
 [!code-csharp[Conceptual.Formatting.Overview#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific3.cs#19)]
 [!code-vb[Conceptual.Formatting.Overview#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific3.vb#19)]  
  
 Można również sformatować wartość liczbową dla określonej kultury, wywołując `ToString` przeciążenia, które ma `provider` parametr i przekazywanie jednej z następujących pozycji:  
  
-   A <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje kultury, na których Konwencji formatowania, które mają być używane. Jego <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> metoda zwraca wartość <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> właściwość, która jest <xref:System.Globalization.NumberFormatInfo> obiektu zawierającego informacje specyficzne dla kultury formatowania wartości liczbowych.  
  
-   A <xref:System.Globalization.NumberFormatInfo> obiektu, który definiuje Konwencji formatowania specyficzne dla kultury do użycia. Jego <xref:System.Globalization.NumberFormatInfo.GetFormat%2A> metoda zwraca wystąpienia samej siebie.  
  
 W poniższym przykładzie użyto <xref:System.Globalization.NumberFormatInfo> obiektów, które reprezentują angielski (Stany Zjednoczone) i kultur angielski (Polska) i francuskim i rosyjski neutralne kultury formatowanie liczby zmiennoprzecinkowej.  
  
 [!code-csharp[Conceptual.Formatting.Overview#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific4.cs#20)]
 [!code-vb[Conceptual.Formatting.Overview#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific4.vb#20)]  
  
<a name="dateCulture"></a>   
### <a name="culture-sensitive-formatting-of-date-and-time-values"></a>Wrażliwość na ustawienia kulturowe — formatowanie wartości daty i godziny  
 Domyślnie formatowania wartości daty i godziny jest zależne od kultury. Jeśli nie określisz kultury, gdy należy wywołać metodę formatowania, są używane konwencje formatowanie bieżącej kultury wątku. Jest to zilustrowane w poniższym przykładzie, który zmienia bieżącej kultury wątku cztery razy, a następnie wywołuje <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> metody. W każdym przypadku ciąg wyniku odzwierciedla Konwencji formatowania bieżącej kultury. Jest to spowodowane <xref:System.DateTime.ToString?displayProperty=nameWithType>, <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType>, i <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metody zawijać wywołań <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> i <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody.  
  
 [!code-csharp[Conceptual.Formatting.Overview#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific1.cs#17)]
 [!code-vb[Conceptual.Formatting.Overview#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific1.vb#17)]  
  
 Można również sformatować wartość daty i godziny dla określonej kultury, wywołując <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> przeciążenia, które ma `provider` parametr i przekazywanie jednej z następujących pozycji:  
  
-   A <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje kultury, na których Konwencji formatowania, które mają być używane. Jego <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> metoda zwraca wartość <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> właściwość, która jest <xref:System.Globalization.DateTimeFormatInfo> obiekt, który zawiera informacje dotyczące formatowania specyficzne dla kultury dla wartości daty i godziny.  
  
-   A <xref:System.Globalization.DateTimeFormatInfo> obiektu, który definiuje Konwencji formatowania specyficzne dla kultury do użycia. Jego <xref:System.Globalization.DateTimeFormatInfo.GetFormat%2A> metoda zwraca wystąpienia samej siebie.  
  
 W poniższym przykładzie użyto <xref:System.Globalization.DateTimeFormatInfo> obiektów, które reprezentują angielski (Stany Zjednoczone) i kultur angielski (Polska) i francuskim i rosyjski neutralne kultury formatowanie daty.  
  
 [!code-csharp[Conceptual.Formatting.Overview#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific2.cs#18)]
 [!code-vb[Conceptual.Formatting.Overview#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific2.vb#18)]  
  
<a name="IFormattable"></a>   
## <a name="the-iformattable-interface"></a>Interfejs IFormattable  
 Zazwyczaj typy tego przeciążenia `ToString` metody zawierające ciąg formatu i <xref:System.IFormatProvider> parametru także implementować <xref:System.IFormattable> interfejsu. Ten interfejs jest jeden element członkowski <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, który zawiera ciąg formatu i dostawca formatu jako parametry.  
  
 Implementowanie <xref:System.IFormattable> interfejs dla klasy zdefiniowanym przez aplikację oferuje dwie zalety:  
  
-   Obsługa konwersji ciągu <xref:System.Convert> klasy. Wywołuje się <xref:System.Convert.ToString%28System.Object%29?displayProperty=nameWithType> i <xref:System.Convert.ToString%28System.Object%2CSystem.IFormatProvider%29?displayProperty=nameWithType> wywołanie metody z <xref:System.IFormattable> implementacji automatycznie.  
  
-   Obsługa złożone formatowanie. Jeśli element formatu, który zawiera ciąg formatu używany do formatowania danego typu niestandardowego, automatycznie wywołuje środowisko uruchomieniowe języka wspólnego programu <xref:System.IFormattable> implementacji i przekazuje je ciąg formatu. Aby uzyskać więcej informacji na temat złożonego formatowania za pomocą metod takich jak <xref:System.String.Format%2A?displayProperty=nameWithType> lub <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, zobacz [złożone formatowanie](#CompositeFormatting) sekcji.  
  
 W poniższym przykładzie zdefiniowano `Temperature` klasa implementująca <xref:System.IFormattable> interfejsu. Obsługuje "C" lub "G" specyfikatory formatu, aby wyświetlić temperatury c, specyfikator formatu "F", aby wyświetlić temperatura w f i specyfikator formatu "K" do wyświetlenia temperatury w kelvin —.  
  
 [!code-csharp[Conceptual.Formatting.Overview#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#12)]
 [!code-vb[Conceptual.Formatting.Overview#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#12)]  
  
 Poniższy przykład tworzy `Temperature` obiektu. Następnie wywołuje <xref:System.Convert.ToString%2A> — metoda i używa kilku ciągi formatujące złożonego uzyskać różne ciągu reprezentacje `Temperature` obiektu. Każdy z tych wywołań metody z kolei wywołuje <xref:System.IFormattable> implementacja `Temperature` klasy.  
  
 [!code-csharp[Conceptual.Formatting.Overview#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#13)]
 [!code-vb[Conceptual.Formatting.Overview#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#13)]  
  
 [Powrót do początku](#Introduction)  
  
<a name="CompositeFormatting"></a>   
## <a name="composite-formatting"></a>Złożone formatowanie  
 Niektóre metody, takie jak <xref:System.String.Format%2A?displayProperty=nameWithType> i <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, obsługuje złożone. Ciąg formatu złożonego jest rodzajem szablonu, który zwraca jeden ciąg zawierający reprezentację ciągu zero, co najmniej jeden obiekt. Każdego obiektu odpowiada w ciągu formatu złożonego elementu indeksowanego formatu. Indeks elementu formatu odnosi się do położenia obiekt reprezentujący na liście parametrów metody. Indeksy są liczony od zera. Na przykład poniższa wywołanie <xref:System.String.Format%2A?displayProperty=nameWithType> metoda, pierwszy element format `{0:D}`, zastępuje reprezentację ciągu `thatDate`; drugiego elementu formatu `{1}`, zastępuje reprezentację ciągu `item1`; a trzeci element format `{2:C2}`, zastępuje reprezentację ciągu `item1.Value`.  
  
 [!code-csharp[Conceptual.Formatting.Overview#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite1.cs#14)]
 [!code-vb[Conceptual.Formatting.Overview#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite1.vb#14)]  
  
 Oprócz zastępując element formatu reprezentację ciągu jego odpowiedni obiekt, format elementy pozwalają również kontrolują następujące elementy:  
  
-   Konkretnego sposobu, w której obiekt jest reprezentowany jako ciąg, jeśli obiekt implementuje <xref:System.IFormattable> interfejsu i obsługuje ciągi formatów. Aby to zrobić, po indeks elementu formatu o `:` (dwukropek), a następnie prawidłowym ciągiem formatu. Poprzedni przykład został to przez formatowania wartości typu date z ciąg formatu (wzorzec krótkiej daty) "d" (np. `{0:d}`) i przez formatowania wartość liczbową z "C2" ciąg formatu (np. `{2:C2}` reprezentujący liczbę jako wartość walutową przy użyciu dwóch ułamkowych cyfr dziesiętnych.  
  
-   Szerokość pola zawierający reprezentację ciągu obiektu i wyrównanie reprezentacja ciągu w tym polu. Aby to zrobić, po indeks elementu formatu o `,` (przecinek) po szerokości pola. Ten ciąg jest wyrównany do prawej w polu Jeśli szerokość pola wartość dodatnią, a jego jest wyrównane do lewej, jeśli szerokość pola jest wartością ujemną. Poniższy przykład powoduje wyrównanie lewej wartości daty w polu 20 znaków, a jego prawej wyrównuje wartości dziesiętnych z jedną cyfrę ułamkowych w polu 11 znaków.  
  
     [!code-csharp[Conceptual.Formatting.Overview#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite2.cs#22)]
     [!code-vb[Conceptual.Formatting.Overview#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite2.vb#22)]  
  
     Należy pamiętać, że jeśli występują zarówno składnik ciągu wyrównania, jak i składnik ciąg formatu poprzedniego poprzedza drugie (na przykład `{0,-20:g}`.  
  
 Aby uzyskać więcej informacji na temat złożone formatowanie, zobacz [złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md).  
  
 [Powrót do początku](#Introduction)  
  
<a name="Custom"></a>   
## <a name="custom-formatting-with-icustomformatter"></a>Niestandardowe formatowanie z ICustomFormatter  
 Dwie metody formatowania złożonego, <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> i <xref:System.Text.StringBuilder.AppendFormat%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, obejmują parametr dostawcy formatu, który obsługuje niestandardowe formatowanie. Gdy każda z tych metod formatowania jest wywoływana, przekazuje <xref:System.Type> obiekt, który reprezentuje <xref:System.ICustomFormatter> interfejsu do dostawcy formatu <xref:System.IFormatProvider.GetFormat%2A> metody. <xref:System.IFormatProvider.GetFormat%2A> Metody jest odpowiedzialny za zwracanie <xref:System.ICustomFormatter> implementację, która zawiera niestandardowe formatowanie.  
  
 <xref:System.ICustomFormatter> Interfejs zawiera tylko jedną metodę <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29>, która jest wywoływana automatycznie przez złożone formatowanie metody raz dla każdego elementu formatu ciągu formatu złożonego. <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29> Metoda ma trzy parametry: ciąg formatu, który reprezentuje `formatString` argumentów w elemencie formatu obiekt do formatu i <xref:System.IFormatProvider> obiekt, który zawiera formatowanie usług. Zazwyczaj klasa, która implementuje <xref:System.ICustomFormatter> implementuje również <xref:System.IFormatProvider>, więc jest to ostatni parametr odwołania do niestandardowego formatowania klasy sam. Metoda zwraca reprezentację niestandardowy ciąg sformatowany obiekt zostanie sformatowany. Jeśli metoda nie może sformatować obiekt, powinien on zwrócić odwołanie o wartości null (`Nothing` w języku Visual Basic).  
  
 W poniższym przykładzie przedstawiono <xref:System.ICustomFormatter> wdrożenia o nazwie `ByteByByteFormatter` wyświetlający wartości całkowitych jako sekwencja wartości szesnastkowych dwucyfrowe spację.  
  
 [!code-csharp[Conceptual.Formatting.Overview#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#15)]
 [!code-vb[Conceptual.Formatting.Overview#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#15)]  
  
 W poniższym przykładzie użyto `ByteByByteFormatter` klasy format liczby całkowitej wartości. Należy pamiętać, że <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> metoda jest wywoływana więcej niż raz w ciągu sekundy <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> wywołania metody, a wartość domyślna <xref:System.Globalization.NumberFormatInfo> dostawca jest używany w trzecim wywołania metody, ponieważ.`ByteByByteFormatter.Format` Metoda nie może rozpoznać ciągu formatu "N0" i zwraca odwołanie o wartości null (`Nothing` w języku Visual Basic).  
  
 [!code-csharp[Conceptual.Formatting.Overview#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#16)]
 [!code-vb[Conceptual.Formatting.Overview#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#16)]  
  
 [Powrót do początku](#Introduction)  
  
<a name="RelatedTopics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Definicja|  
|-----------|----------------|  
|[Standardowe ciągi formatujące liczby](../../../docs/standard/base-types/standard-numeric-format-strings.md)|W tym artykule opisano standardowe ciągi formatujące utworzonych reprezentacji ciągu często używane wartości liczbowych.|  
|[Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)|W tym artykule opisano tworzenie formatów specyficzne dla aplikacji dla wartości liczbowych ciągi formatu niestandardowego.|  
|[Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Opisuje standardowe ciągi formatujące utworzonych często używanych ciągów <xref:System.DateTime> wartości.|  
|[Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|W tym artykule opisano tworzenie formatów specyficzne dla aplikacji dla ciągi formatu niestandardowego <xref:System.DateTime> wartości.|  
|[Standardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)|W tym artykule opisano standardowe ciągi formatujące utworzonych reprezentacji ciągu często używane odstępach czasu.|  
|[Niestandardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|W tym artykule opisano tworzenie formatów specyficzne dla aplikacji dla przedziały czasu ciągi formatu niestandardowego.|  
|[Ciągi formatujące wyliczenia](../../../docs/standard/base-types/enumeration-format-strings.md)|W tym artykule opisano standardowym formacie ciągów, które zostaną użyte do utworzenia reprezentacji ciągu wartości wyliczenia.|  
|[Złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md)|Opisuje sposób osadzić w ciągu jednego lub więcej wartości sformatowane. Ciąg można następnie wyświetlane w konsoli lub w strumieniu.|  
|[Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)|Wyświetla listę tematów, które zawierają instrukcje krok po kroku do wykonywania określonych operacji formatowania.|  
|[Analizowanie ciągów](../../../docs/standard/base-types/parsing-strings.md)|Zawiera opis sposobu zainicjowania obiekty do wartości opisanego przez ciąg reprezentacje tych obiektów. Analiza jest odwrotny operacji formatowania.|  
  
 [Powrót do początku](#Introduction)  
  
<a name="Reference"></a>   
## <a name="reference"></a>Tematy pomocy  
 <xref:System.IFormattable?displayProperty=nameWithType>  
  
 <xref:System.IFormatProvider?displayProperty=nameWithType>  
  
 <xref:System.ICustomFormatter?displayProperty=nameWithType>
