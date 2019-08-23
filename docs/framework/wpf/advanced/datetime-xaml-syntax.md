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
ms.openlocfilehash: 36066d6b2405051a3d35befffe53af8895e26220
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964837"
---
# <a name="datetime-xaml-syntax"></a>DateTime — Składnia XAML
Niektóre kontrolki, takie <xref:System.Windows.Controls.Calendar> jak <xref:System.Windows.Controls.DatePicker>i, <xref:System.DateTime> mają właściwości, które używają typu. Chociaż zwykle określasz początkową datę lub godzinę dla tych kontrolek w kodzie w czasie wykonywania, możesz określić początkową datę lub godzinę w kodzie XAML. Analizator XAML WPF obsługuje analizowanie <xref:System.DateTime> wartości przy użyciu wbudowanej składni tekstu XAML. W tym temacie opisano szczegóły <xref:System.DateTime> składni tekstu XAML.  

<a name="where_datetime_xaml_syntax_is_used"></a>   
## <a name="when-to-use-datetime-xaml-syntax"></a>Kiedy używać składni XAML DateTime  
 Ustawianie dat w języku XAML nie zawsze jest konieczne i może nie być jeszcze pożądane. Na przykład można użyć <xref:System.DateTime.Now%2A?displayProperty=nameWithType> właściwości, aby zainicjować datę w czasie wykonywania, lub można wykonać wszystkie korekty dat dla kalendarza w kodzie w oparciu o dane wejściowe użytkownika. Istnieją jednak scenariusze, w których możesz chcieć, aby dane <xref:System.Windows.Controls.Calendar> <xref:System.Windows.Controls.DatePicker> były zakodowane w szablonie kontrolki. Dla tych scenariuszy należy użyć składni XAML.<xref:System.DateTime>  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a>Składnia XAML DateTime jest zachowaniem natywnym  
 <xref:System.DateTime>jest klasą, która jest zdefiniowana w podstawowych bibliotekach klas środowiska CLR. Ze względu na to, jak biblioteki klas bazowych odnoszą się do reszty środowiska CLR, nie <xref:System.ComponentModel.TypeConverterAttribute> można zastosować do klasy i użyć konwertera typów w celu przetworzenia ciągów z XAML i <xref:System.DateTime> przekonwertowania ich do w modelu obiektu czasu wykonywania. Nie `DateTimeConverter` istnieje Klasa, która zapewnia zachowanie konwersji; zachowanie konwersji opisane w tym temacie jest natywne dla analizatora XAML WPF.  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>   
## <a name="format-strings-for-datetime-xaml-syntax"></a>Ciągi formatowania dla składni XAML DateTime  
 Można określić format <xref:System.DateTime> z ciągiem formatu. Ciągi formatujące prace prowadzone składnię tekstu, której można użyć do utworzenia wartości. <xref:System.DateTime>wartości dla istniejących formantów WPF zazwyczaj używają wyłącznie składników <xref:System.DateTime> daty, a nie składników czasu.  
  
 Podczas określania <xref:System.DateTime> w języku XAML można zamiennie używać dowolnych ciągów formatu.  
  
 Można również użyć formatów i ciągów formatowania, które nie są w sposób opisany w tym temacie. Technicznie, kod XAML dla <xref:System.DateTime> każdej wartości, która jest określona, a następnie analizowany przez analizator WPF XAML używa wywołania wewnętrznego do <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>, dlatego można użyć dowolnego ciągu akceptowanego przez <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> dane wejściowe XAML. Aby uzyskać więcej informacji, zobacz <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
> Składnia XAML DateTime jest zawsze stosowana `en-us` <xref:System.Globalization.CultureInfo> jako dla konwersji natywnej. Nie ma to wpływu <xref:System.Windows.FrameworkElement.Language%2A> na wartość ani `xml:lang` wartość w kodzie XAML, ponieważ konwersja typu na poziomie atrybutu XAML działa bez tego kontekstu. Nie należy podejmować prób interpolacji ciągów formatu przedstawionych w tym miejscu ze względu na różnice kulturowe, takie jak kolejność, w której pojawiają się dni i miesiące. Ciągi formatu wyświetlane w tym miejscu to dokładne ciągi formatu używane podczas analizowania kodu XAML niezależnie od innych ustawień kultury.  
  
 W poniższych sekcjach opisano niektóre typowe <xref:System.DateTime> ciągi formatujące.  
  
### <a name="short-date-pattern-d"></a>Wzorzec daty krótkiej ("d")  
 Poniżej przedstawiono krótki format daty dla <xref:System.DateTime> kodu XAML:  
  
 `M/d/YYYY`  
  
 Jest to najprostsza forma, która określa wszystkie informacje niezbędne do typowych zastosowań przez formanty WPF i nie może mieć wpływu na przesunięcia strefy czasowej w stosunku do składnika czasu i dlatego jest zalecane w przypadku innych formatów.  
  
 Na przykład aby określić datę 1 czerwca 2010, użyj następującego ciągu:  
  
 `3/1/2010`  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>.  
  
### <a name="sortable-datetime-pattern-s"></a>Sortowanie wzorca DateTime ("s")  
 Poniżej przedstawiono wzorzec sortowania <xref:System.DateTime> w języku XAML:  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 Na przykład aby określić datę 1 czerwca 2010, należy użyć następującego ciągu (wszystkie składniki czasu są wprowadzane jako 0):  
  
 `2010-06-01T000:00:00`  
  
### <a name="rfc1123-pattern-r"></a>Wzorzec RFC1123 ("r")  
 Wzorzec RFC1123 jest przydatny, ponieważ może być ciągiem wejściowym z innych generatorów dat, które również używają wzorca RFC1123 dla powodów niezmiennej kultury. Poniżej przedstawiono wzorzec RFC1123 <xref:System.DateTime> w języku XAML:  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 Na przykład aby określić datę 1 czerwca 2010, należy użyć następującego ciągu (wszystkie składniki czasu są wprowadzane jako 0):  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### <a name="other-formats-and-patterns"></a>Inne formaty i wzorce  
 Jak wspomniano wcześniej, <xref:System.DateTime> w języku XAML można określić dowolny ciąg, który jest akceptowalny jako <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>dane wejściowe. Obejmuje to inne formalne formaty (na przykład <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>) i formaty, które nie są formalne jako określony <xref:System.Globalization.DateTimeFormatInfo> formularz. Na przykład formularz `YYYY/mm/dd` jest akceptowalny jako <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>dane wejściowe. Ten temat nie próbuje opisać wszystkich możliwych formatów, które działają, a zamiast tego zaleca wzorzec daty krótkiej jako praktyczną.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
