---
title: DateTime — Składnia XAML
ms.date: 03/30/2017
helpviewer_keywords:
- DateTime XAML syntax [WPF], strings for
- DateTime XAML syntax [WPF], where used
- short date format [WPF], DateTime
- DateTime XAML syntax [WPF]
- DateTime XAML text [WPF]
- DateTime XAML syntax [WPF], format strings for
ms.assetid: 5901710a-609b-40c8-9d65-f0016cd9090b
ms.openlocfilehash: 57b73d3b80f0392b99aacfbfac4d8709f72d52e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186331"
---
# <a name="datetime-xaml-syntax"></a>DateTime — Składnia XAML
Niektóre formanty, takie jak <xref:System.Windows.Controls.Calendar> i <xref:System.Windows.Controls.DatePicker> <xref:System.DateTime> , mają właściwości, które używają typu. Chociaż zazwyczaj określa się początkową datę lub godzinę dla tych formantów w czasie wykonywania, można określić początkową datę lub godzinę w języku XAML. Analizator WPF XAML obsługuje analizowanie <xref:System.DateTime> wartości przy użyciu wbudowanej składni tekstu XAML. W tym temacie opisano <xref:System.DateTime> specyfikę składni tekstu XAML.  

<a name="where_datetime_xaml_syntax_is_used"></a>
## <a name="when-to-use-datetime-xaml-syntax"></a>Kiedy używać składni XAML DateTime  
 Ustawianie dat w języku XAML nie zawsze jest konieczne i może nawet nie być pożądane. Na przykład można użyć <xref:System.DateTime.Now%2A?displayProperty=nameWithType> właściwości do zainicjowania daty w czasie wykonywania lub można wykonać wszystkie korekty daty dla kalendarza w kodzie na podstawie danych wejściowych użytkownika. Istnieją jednak scenariusze, w których można chcieć <xref:System.Windows.Controls.Calendar> kod <xref:System.Windows.Controls.DatePicker> twardy daty do i w szablonie formantu. Składnia <xref:System.DateTime> XAML musi być używana dla tych scenariuszy.  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a>Składnia XAML DateTime jest zachowaniem macierzystym  
 <xref:System.DateTime>jest klasą zdefiniowaną w bibliotekach klas podstawowych CLR. Ze względu na to, jak biblioteki klasy podstawowej odnoszą się <xref:System.ComponentModel.TypeConverterAttribute> do reszty CLR, nie jest możliwe zastosowanie do klasy <xref:System.DateTime> i użyć konwertera typów do przetwarzania ciągów z XAML i konwertować je w modelu obiektów czasu wykonywania. Nie ma `DateTimeConverter` żadnej klasy, która zapewnia zachowanie konwersji; zachowanie konwersji opisane w tym temacie jest natywna dla analizatora WPF XAML.  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>
## <a name="format-strings-for-datetime-xaml-syntax"></a>Formatowanie ciągów dla składni XAML DateTime  
 Można określić format <xref:System.DateTime> ciągu formatu. Formatowanie ciągów sformalizowania składni tekstu, która może służyć do tworzenia wartości. <xref:System.DateTime>wartości dla istniejących formantów WPF zazwyczaj <xref:System.DateTime> używają tylko składników daty, a nie składników czasu.  
  
 Podczas określania <xref:System.DateTime> w XAML, można użyć dowolnego ciągu formatu zamiennie.  
  
 Można również użyć formatów i ciągów formatu, które nie są wyraźnie wyświetlane w tym temacie. Technicznie XAML dla dowolnej <xref:System.DateTime> wartości, która jest określona, a następnie analizowane przez analizatorA <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>XAML WPF używa wewnętrznego <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> wywołania do , w związku z tym można użyć dowolnego ciągu akceptowane przez dla danych wejściowych XAML. Aby uzyskać więcej informacji, zobacz <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
> Składnia XAML DateTime zawsze `en-us` używa <xref:System.Globalization.CultureInfo> jako dla jego konwersji macierzystej. Nie ma na <xref:System.Windows.FrameworkElement.Language%2A> to `xml:lang` wpływu wartość lub wartość w XAML, ponieważ konwersja typu na poziomie atrybutu XAML działa bez tego kontekstu. Nie próbuj interpolować ciągów formatu wyświetlanych tutaj ze względu na różnice kulturowe, takie jak kolejność, w jakiej są wyświetlane dni i miesiąca. Ciągi formatu pokazane w tym miejscu są dokładne ciągi formatu używane podczas analizowania XAML, niezależnie od innych ustawień kultury.  
  
 W poniższych sekcjach opisano <xref:System.DateTime> niektóre typowe ciągi formatu.  
  
### <a name="short-date-pattern-d"></a>Wzór krótkiej daty ("d")  
 Poniżej przedstawiono format daty krótkiej dla formatu <xref:System.DateTime> XAML:  
  
 `M/d/YYYY`  
  
 Jest to najprostszy formularz, który określa wszystkie informacje niezbędne dla typowych użyciach przez formanty WPF i nie może mieć wpływu na przypadkowe przesunięcie strefy czasowej w porównaniu do składnika czasu i dlatego jest zalecane w stosunku do innych formatów.  
  
 Na przykład, aby określić datę 1 czerwca 2010 r., należy użyć następującego ciągu:  
  
 `3/1/2010`  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>.  
  
### <a name="sortable-datetime-pattern-s"></a>Sortowalny wzór datetime ("s")  
 Poniżej przedstawiono <xref:System.DateTime> sortowalny wzorzec w języku XAML:  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 Na przykład, aby określić datę 1 czerwca 2010 r., użyj następującego ciągu (wszystkie składniki czasu są wprowadzane jako 0):  
  
 `2010-06-01T000:00:00`  
  
### <a name="rfc1123-pattern-r"></a>Wzór RFC1123 ("r")  
 Wzorzec RFC1123 jest przydatne, ponieważ może to być ciąg danych wejściowych z innych generatorów daty, które również używają wzorca RFC1123 dla kultury niezmienne przyczyny. Poniżej przedstawiono wzorzec <xref:System.DateTime> RFC1123 w języku XAML:  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 Na przykład, aby określić datę 1 czerwca 2010 r., użyj następującego ciągu (wszystkie składniki czasu są wprowadzane jako 0):  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### <a name="other-formats-and-patterns"></a>Inne formaty i wzorce  
 Jak wspomniano wcześniej, <xref:System.DateTime> w XAML można określić jako dowolny <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>ciąg, który jest dopuszczalny jako dane wejściowe dla . Obejmuje to inne sformalizowane <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>formaty (na przykład ) i <xref:System.Globalization.DateTimeFormatInfo> formaty, które nie są sformalizowane jako określony formularz. Na przykład formularz `YYYY/mm/dd` jest dopuszczalny <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>jako dane wejściowe dla . W tym temacie nie próbuje opisać wszystkie możliwe formaty, które działają, a zamiast tego zaleca wzorzec daty krótkiej jako standardową praktykę.  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
