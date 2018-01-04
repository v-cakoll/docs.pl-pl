---
title: "DateTime — Składnia XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DateTime XAML syntax [WPF], strings for
- DateTime XAML syntax [WPF], where used
- short date format [WPF], DateTime
- DateTime XAML syntax [WPF]
- DateTime XAML text [WPF]
- DateTime XAML syntax [WPF], format strings for
ms.assetid: 5901710a-609b-40c8-9d65-f0016cd9090b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3010d3123e78a5e292c5ac78ef4894962fb8f9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="datetime-xaml-syntax"></a>DateTime — Składnia XAML
Niektóre formanty, takie jak <xref:System.Windows.Controls.Calendar> i <xref:System.Windows.Controls.DatePicker>, właściwości, które używają <xref:System.DateTime> typu. Mimo że początkowej daty lub godziny dla tych kontrolek zazwyczaj określić w kodem w czasie wykonywania, można określić początkowej daty lub godziny w języku XAML. WPF XAML parser obsługuje analizowania <xref:System.DateTime> wartości przy użyciu składni wbudowanego tekstu XAML. W tym temacie opisano specyfice <xref:System.DateTime> składni tekstu XAML.  
  
  
<a name="where_datetime_xaml_syntax_is_used"></a>   
## <a name="when-to-use-datetime-xaml-syntax"></a>Kiedy należy używać składni języka XAML daty i godziny  
 Ustawienie daty w języku XAML nie zawsze jest konieczne i może nawet być niepożądane. Na przykład można użyć <xref:System.DateTime.Now%2A?displayProperty=nameWithType> właściwość w celu zainicjowania datę w czasie wykonywania, lub wykonaj wszystkie zmiany daty kalendarza w kodem oparte na danych wejściowych użytkownika. Istnieją jednak scenariusze, w których warto dat kodowane w <xref:System.Windows.Controls.Calendar> i <xref:System.Windows.Controls.DatePicker> w szablonie formantu. <xref:System.DateTime> Do tych scenariuszy należy użyć składni języka XAML.  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a>Składnia XAML DateTime jest zachowanie natywnego  
 <xref:System.DateTime>jest klasa, która jest zdefiniowana w klasie podstawowej bibliotekach środowiska CLR. Z powodu jak biblioteki klasy podstawowej są powiązane z resztą środowiska CLR, nie jest możliwa do stosowania <xref:System.ComponentModel.TypeConverterAttribute> klasy i użycia konwertera typu, aby przetworzyć ciągów z XAML i przekonwertować je na <xref:System.DateTime> w modelu obiektów czasu wykonywania. Brak nie `DateTimeConverter` klasy zapewnia zachowanie konwersji; macierzysty analizator WPF XAML zachowanie konwersji opisanych w tym temacie.  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>   
## <a name="format-strings-for-datetime-xaml-syntax"></a>Ciągi formatujące składnię daty/godziny XAML  
 Można określić format <xref:System.DateTime> zawierające ciąg formatu. Ciągi formatujące formalnego składni tekst, który może służyć do tworzenia wartości. <xref:System.DateTime>wartości dla istniejącego WPF steruje użyciem zwykle tylko składniki daty <xref:System.DateTime> i nie składniki czasu.  
  
 Podczas określania <xref:System.DateTime> w języku XAML, będzie można użyć dowolnego z ciągi formatujące zamiennie.  
  
 Można również użyć formaty i ciągi formatów, które nie są pokazywane w szczególności w tym temacie. Z technicznego punktu widzenia XAML dla każdego <xref:System.DateTime> wartość, która jest określona, a następnie przeanalizować przez parser WPF XAML używa wewnętrznego wywołanie <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>, w związku z tym można użyć dowolnego ciągu zaakceptowane przez <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> dla XAML z danych wejściowych. Aby uzyskać więcej informacji, zobacz <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
>  Zawsze używa składni języka XAML DateTime `en-us` jako <xref:System.Globalization.CultureInfo> jego natywnego konwersji. Nie jest to wpływu na <xref:System.Windows.FrameworkElement.Language%2A> wartość lub `xml:lang` wartość w języku XAML, ponieważ konwersja poziom atrybutu typu XAML działa bez tego kontekstu. Nie należy próbować interpolować ciągi formatujące pokazane z powodu zmian kultury, takie jak kolejność dnia i miesiąca. Ciągi formatujące pokazane są ciągami dokładnego formatu, używany podczas analizowania kodu w języku XAML, niezależnie od innych ustawień kultury.  
  
 W poniższych sekcjach opisano niektóre typowe <xref:System.DateTime> ciągi formatujące.  
  
### <a name="short-date-pattern-d"></a>Wzorzec krótkiej daty ("d")  
 Poniżej pokazano format daty krótkiej <xref:System.DateTime> w języku XAML:  
  
 `M/d/YYYY`  
  
 Jest to najprostsza forma, który określa wszystkie informacje niezbędne dla typowego użycia za pomocą formantów WPF i nie może zależeć od przesunięcia przypadkowemu strefy czasowej, a składnik czasu i dlatego zaleca się w innych formatach.  
  
 Na przykład aby określić datę 1 czerwca 2010, należy użyć następujący ciąg:  
  
 `3/1/2010`  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>.  
  
### <a name="sortable-datetime-pattern-s"></a>Sortowanie wzorzec DateTime ("s")  
 Poniżej pokazano umożliwiający sortowanie <xref:System.DateTime> wzorca w języku XAML:  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 Na przykład aby określić datę 1 czerwca 2010, należy użyć następującego ciągu (czas, które składniki są wprowadzane jako 0):  
  
 `2010-06-01T000:00:00`  
  
### <a name="rfc1123-pattern-r"></a>Wzorzec RFC1123 ("r")  
 Wzorzec RFC1123 jest przydatne, ponieważ może to być ciąg na wejściu z innych generatory date, również korzystających ze wzorca RFC1123 przyczyn Niezmienna kultura. Poniżej pokazano RFC1123 <xref:System.DateTime> wzorca w języku XAML:  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 Na przykład aby określić datę 1 czerwca 2010, należy użyć następującego ciągu (czas, które składniki są wprowadzane jako 0):  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### <a name="other-formats-and-patterns"></a>Inne formaty i wzorce  
 Jak wspomniano wcześniej, <xref:System.DateTime> w języku XAML może być określona jako dowolny ciąg, który jest dopuszczalna jako wejściowe dla <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>. Dotyczy to również inne formaty formalny (na przykład <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>) i formatów, które nie są sformalizowane jako określonego <xref:System.Globalization.DateTimeFormatInfo> formularza. Na przykład formularz `YYYY/mm/dd` jest dopuszczalna jako wejściowe dla <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>. W tym temacie podjęto próby opisania wszystkich możliwych formatów, które będzie działać, a zamiast tego zaleca wzorzec krótkiej daty jako standardowe rozwiązanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
