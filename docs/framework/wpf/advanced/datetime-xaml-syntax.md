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
ms.openlocfilehash: d7fe5f15f79ab068e88c3fb6f7b7cac0986aa636
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146500"
---
# <a name="datetime-xaml-syntax"></a>DateTime — Składnia XAML
Niektóre kontrolki, takie jak <xref:System.Windows.Controls.Calendar> i <xref:System.Windows.Controls.DatePicker>, mają właściwości, które używają <xref:System.DateTime> typu. Chociaż zwykle określisz początkowej daty lub godziny dla tych formantów w kodem w czasie wykonywania, można określić początkową daty lub godziny w XAML. Analizator WPF XAML obsługuje analizowanie <xref:System.DateTime> wartości przy użyciu wbudowanych składni tekstu XAML. W tym temacie opisano specyfikę <xref:System.DateTime> XAML składnia tekstu.  

<a name="where_datetime_xaml_syntax_is_used"></a>   
## <a name="when-to-use-datetime-xaml-syntax"></a>Kiedy należy używać składnia XAML DateTime  
 Ustawienie daty w XAML nie zawsze jest konieczne i może nie być pożądane. Na przykład można użyć <xref:System.DateTime.Now%2A?displayProperty=nameWithType> właściwość w celu zainicjowania datę w czasie wykonywania, lub może zrobić wszystkie zmiany daty w kalendarzu w kodem na podstawie danych wejściowych użytkownika. Jednak istnieją scenariusze, w którym może chcesz trwale kodować daty do <xref:System.Windows.Controls.Calendar> i <xref:System.Windows.Controls.DatePicker> w szablonie formantu. <xref:System.DateTime> Składnia XAML musi być używany dla tych scenariuszy.  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a>Składnia XAML DateTime jest natywny zachowanie  
 <xref:System.DateTime> jest klasą, która jest zdefiniowana w bibliotek klas bazowych środowiska CLR. Ze względu na sposób bibliotek klas bazowych odnoszą się do pozostałej części środowiska CLR, nie jest możliwe, stosowanie <xref:System.ComponentModel.TypeConverterAttribute> klasy i używania konwertera typów do przetwarzania ciągów z XAML i konwertować je na <xref:System.DateTime> w modelu obiektów czasu wykonywania. Istnieje nie `DateTimeConverter` klasy zapewniający zachowanie konwersji; zachowanie konwersji opisane w tym temacie jest natywnym analizatora WPF XAML.  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>   
## <a name="format-strings-for-datetime-xaml-syntax"></a>Ciągi formatu dla składnia XAML DateTime  
 Można określić format <xref:System.DateTime> z ciągiem formatu. Ciągi formatujące formalnego składni tekstu, który może służyć do utworzenia wartości. <xref:System.DateTime> wartości dla istniejących WPF steruje użyciem ogólnie tylko składniki daty <xref:System.DateTime> a nie na składnikach czasu.  
  
 Podczas określania <xref:System.DateTime> w XAML, można użyć dowolnego z ciągów formatu zamiennie.  
  
 Można również użyć formatów i formatów ciągów, które nie są szczegółowo przedstawione w tym temacie. Technicznie rzecz biorąc, XAML dla każdego <xref:System.DateTime> wartość, która jest określona, a następnie analizowane przez parser WPF XAML używa wewnętrznego wywołanie <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>, w związku z tym można użyć dowolnego ciągu zaakceptowane przez <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> jako swojej XAML. Aby uzyskać więcej informacji, zobacz <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
>  Składnia XAML DateTime zawsze używa `en-us` jako <xref:System.Globalization.CultureInfo> jego natywnych konwersji. To nie wpływają <xref:System.Windows.FrameworkElement.Language%2A> wartość lub `xml:lang` wartości w XAML, ponieważ konwersja typu poziom atrybutu XAML działa bez tego kontekstu. Nie należy próbować interpolacji ciągów formatu, pokazano poniżej, z powodu zmian kultury, na przykład kolejność, w jakiej są wyświetlane dzień i miesiąc. Ciągi formatu pokazane tutaj są ciągami dokładny format używany podczas analizowania XAML, niezależnie od innych ustawień kultury.  
  
 W poniższych sekcjach opisano niektóre typowe <xref:System.DateTime> ciągi formatujące.  
  
### <a name="short-date-pattern-d"></a>Wzorzec daty krótkiej ("d")  
 Poniżej pokazano formatu daty krótkiej dla <xref:System.DateTime> w XAML:  
  
 `M/d/YYYY`  
  
 Jest to najprostsza forma, która określa wszystkie informacje niezbędne dla typowego użycia za pomocą kontrolek WPF i nie może zależeć od przesunięcia przypadkowym strefy czasowej i składnik czasu i z tego powodu zaleca się za pośrednictwem innych formatach.  
  
 Na przykład aby określić datę 1 czerwca 2010, należy użyć następujący ciąg:  
  
 `3/1/2010`  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>.  
  
### <a name="sortable-datetime-pattern-s"></a>Wzorzec sortowalnej daty/godziny wzorca ("s")  
 Poniżej pokazano sortowanie <xref:System.DateTime> wzorca w XAML:  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 Na przykład aby określić datę 1 czerwca 2010 r., należy użyć następującego ciągu (czas, które składniki są wprowadzane jako 0):  
  
 `2010-06-01T000:00:00`  
  
### <a name="rfc1123-pattern-r"></a>Wzorzec RFC1123 ("r")  
 Wzorzec RFC1123 jest przydatne, ponieważ może to być ciąg wejściowy z innych generatorów daty, które także używają wzorzec RFC1123 przyczyn niezmiennej kultury. Poniżej pokazano RFC1123 <xref:System.DateTime> wzorca w XAML:  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 Na przykład aby określić datę 1 czerwca 2010 r., należy użyć następującego ciągu (czas, które składniki są wprowadzane jako 0):  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### <a name="other-formats-and-patterns"></a>Inne formaty i wzorce  
 Jak wspomniano wcześniej, <xref:System.DateTime> w XAML może być określona jako dowolny ciąg, który jest dopuszczalna jako danych wejściowych dla <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>. W tym inne formaty nadzorowanym środowisku (na przykład <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>) i formatów, które nie są sformalizowane jako określonego <xref:System.Globalization.DateTimeFormatInfo> formularza. Na przykład formularz `YYYY/mm/dd` jest dopuszczalna jako danych wejściowych dla <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>. W tym temacie nie podjęto próby opisania wszystkich możliwych formatów, które działają, a zamiast tego zaleca się wzorzec daty krótkiej jako standardową praktyką.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie XAML (WPF)](xaml-overview-wpf.md)
