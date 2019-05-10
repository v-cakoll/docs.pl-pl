---
title: Zaawansowane formatowanie tekstu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [WPF]
- text [WPF]
- typography [WPF], text formatting
ms.assetid: f0a7986e-f5b2-485c-a27d-f8e922022212
ms.openlocfilehash: ef07e1acd250ceeb7c0e30f8a78dd8d7b196fdcd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64655540"
---
# <a name="advanced-text-formatting"></a>Zaawansowane formatowanie tekstu
Windows Presentation Foundation (WPF) zapewnia niezawodny zestaw [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] , w tym tekst w aplikacji. Układ i [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], takich jak <xref:System.Windows.Controls.TextBlock>, najbardziej typowe i ogólne elementy prezentacji tekstu. Rysowanie [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], takich jak <xref:System.Windows.Media.GlyphRunDrawing> i <xref:System.Windows.Media.FormattedText>, pozwalają na rysunkach, w tym tekstu sformatowanego. Najbardziej zaawansowane poziom [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zawiera tekst extensible formatowania aparatu do kontrolowania każdy aspekt prezentacji tekstu, takie jak zarządzanie magazynem tekstu, zarządzania formatowania tekstu, uruchom i zarządzania osadzonego obiektu.  
  
 Ten temat zawiera wprowadzenie do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] formatowania tekstu. Koncentruje się ona na wdrożenie klienta i stosowanie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aparatu formatowania tekstu.  
  
> [!NOTE]
>  Wszystkie przykłady kodu, w tym dokumencie znajdują się w [zaawansowane próbkę formatowania tekstu](https://go.microsoft.com/fwlink/?LinkID=159965).  

<a name="prereq"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że czytelnik zna wyższego poziomu [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] użyte do prezentowania tekstu. Większość scenariuszy użytkownika nie będzie wymagać formatowania tekstu zaawansowane [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] omówione w tym temacie. Aby zapoznać się z innym tekstem [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], zobacz [dokumenty w WPF](documents-in-wpf.md).  
  
<a name="section1"></a>   
## <a name="advanced-text-formatting"></a>Zaawansowane formatowanie tekstu  
 Układ tekstu i [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kontrolki w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Podaj właściwości formatowania, które umożliwiają łatwe dołączanie tekstu sformatowanego w aplikacji. Te formanty zmieniają wiele właściwości do obsługi prezentacji tekstu, który zawiera jej krój czcionki, rozmiarze i kolorze. W zwykłych okolicznościach te kontrolki mogą obsługiwać Większość prezentacji tekstu w aplikacji. Jednak niektórych zaawansowanych scenariuszach wymagają kontroli magazynu tekstu, a także prezentację tekstu. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zawiera tekst extensible formatowania aparatu do tego celu.  
  
 Zaawansowane funkcje do formatowania tekstu, znaleziono w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] składają się z tekstu formatowania aparatu, do przechowywania tekstu, tekst przebiegi i właściwości formatowania. Aparat do formatowania tekstu, <xref:System.Windows.Media.TextFormatting.TextFormatter>, tworzy wierszy tekstu ma być używany w prezentacji. Jest to osiągane przez inicjowanie proces formatowania wiersza i wywoływania elementu formatującego tekstu <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>. Element formatujący tekstu pobiera uruchomienia tekstu ze sklepu tekst, wywołując w sklepie <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metody. <xref:System.Windows.Media.TextFormatting.TextRun> Obiekty są następnie utworzone w <xref:System.Windows.Media.TextFormatting.TextLine> obiektów przez program formatujący tekstu oraz aplikacji na potrzeby inspekcji lub wyświetlania.  
  
<a name="section2"></a>   
## <a name="using-the-text-formatter"></a>Przy użyciu elementu formatującego tekstu  
 <xref:System.Windows.Media.TextFormatting.TextFormatter> jest [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] formatowania tekstu aparatu i zapewnia usługi dotyczące formatowania i istotne wierszy tekstu. Element formatujący tekstu może obsługiwać różnych formatach znak i style i obejmuje obsługę układu tekstu międzynarodowe.  
  
 W przeciwieństwie do tradycyjnych tekstu [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)], <xref:System.Windows.Media.TextFormatting.TextFormatter> wchodzi w interakcję z klientem układu tekstu za pomocą zestawu metod wywołania zwrotnego. Wymaga od klienta zapewnienia tych metod w celu wykonania <xref:System.Windows.Media.TextFormatting.TextSource> klasy. Na poniższym diagramie przedstawiono interakcje układu tekstu między aplikacji klienckiej i <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagram klienta układu tekstu i obiekt TextFormatter](./media/advanced-text-formatting/text-layout-textformatter-interaction.png)  
  
 Element formatujący tekstu służy do pobierania wierszy tekstu sformatowanego w sklepie tekst, który jest implementacją <xref:System.Windows.Media.TextFormatting.TextSource>. Jest to realizowane przez utworzenie wystąpienia programu formatującego tekstu przy użyciu <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A> metody. Ta metoda tworzy wystąpienie elementu formatującego tekstu i ustawia maksymalny wiersza wartości szerokości i wysokości. Zaraz po utworzeniu wystąpienia programu formatującego tekstu procesu tworzenia wiersza została uruchomiona przez wywołanie metody <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> metody. <xref:System.Windows.Media.TextFormatting.TextFormatter> ponownie wywołuje źródłem tekstu można pobrać tekstu i formatowania parametrów dla przebiegów tekstu tworzące wiersza.  
  
 W poniższym przykładzie przedstawiono proces formatowania do przechowywania tekstu. <xref:System.Windows.Media.TextFormatting.TextFormatter> Obiekt jest używany do pobierania wierszy tekstu w sklepie tekstu i następnie go sformatuj wiersza tekstu do rysowania w <xref:System.Windows.Media.DrawingContext>.  
  
 [!code-csharp[TextFormatterExample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## <a name="implementing-the-client-text-store"></a>Implementowanie Store tekstu klienta  
 Rozszerzając mechanizm formatowania tekstu, są wymagane do wdrożenia i zarządzać wszystkimi aspektami magazynu tekstu. Nie jest prostym zadaniem. Magazyn tekstu jest odpowiedzialny za śledzenie Uruchom właściwości, właściwości, obiekty osadzone i inne podobne zawartości tekstu. Udostępnia również program formatujący tekstu z poszczególnymi <xref:System.Windows.Media.TextFormatting.TextRun> obiekty, których używa program formatujący tekst w celu utworzenia <xref:System.Windows.Media.TextFormatting.TextLine> obiektów.  
  
 Aby obsługiwać wirtualizację magazynu tekstu, w sklepie tekstu musi pochodzić od <xref:System.Windows.Media.TextFormatting.TextSource>. <xref:System.Windows.Media.TextFormatting.TextSource> definiuje metodę, używanych przez program formatujący tekstu można pobrać przebiegów tekst z magazynu tekstu. <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> jest używany w formatowaniu wiersza uruchamia metodę używaną przez program formatujący tekstu do pobierania tekstu. Wywołanie <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> wielokrotnie jest tworzone przez program formatujący tekstu, dopóki nie wystąpi jedno z następujących warunków:  
  
- A <xref:System.Windows.Media.TextFormatting.TextEndOfLine> lub podklasa jest zwracana.  
  
- Skumulowana szerokość uruchomienia tekstu przekracza szerokość linii maksymalnej określonej w wywołanie do utworzenia elementu formatującego tekstu lub wywołanie elementu formatującego tekstu <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> metody.  
  
- A [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] sekwencji nowy wiersz, takie jak "CF", "LF" lub "CRLF", jest zwracana.  
  
<a name="section4"></a>   
## <a name="providing-text-runs"></a>Zapewnianie uruchomienia tekstu  
 Podstawowy proces formatowania tekstu jest interakcji między program formatujący tekstu i magazynem tekstu. Implementacja <xref:System.Windows.Media.TextFormatting.TextSource> zawiera element formatujący tekstu <xref:System.Windows.Media.TextFormatting.TextRun> obiektów i właściwości, za pomocą których można formatować tekst jest uruchamiany. Ta interakcja jest obsługiwany przez <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metody, która jest wywoływana przez program formatujący tekstu.  
  
 W poniższej tabeli przedstawiono niektóre z wstępnie zdefiniowanego <xref:System.Windows.Media.TextFormatting.TextRun> obiektów.  
  
|Typ TextRun|Użycie|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|Tekst wyspecjalizowane Uruchom używany do przekazania reprezentację symbole znaków tekstu elementu formatującego.|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|Wyspecjalizowane tekstu Uruchom umożliwia dostarczanie zawartości, w których pomiaru, testowania trafień i rysowanie odbywa się w całości, takich jak przycisku lub obrazu w tekście.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|Tekst wyspecjalizowane Uruchom używany do oznaczenia końca wiersza.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|Tekst wyspecjalizowane Uruchom używany do oznaczenia końca akapitu.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|Tekst specjalistyczne, uruchom używany do oznaczania końca segmentu, takie jak do końca zakresu wpływ poprzedniej <xref:System.Windows.Media.TextFormatting.TextModifier> uruchomienia.|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|Tekst wyspecjalizowane Uruchom używanych do oznaczania szereg ukrytych znaków.|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|Tekst wyspecjalizowane Uruchom umożliwia modyfikowanie właściwości tekstu działa w swoim zakresie. Zakres obejmuje następny zgodny <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> tekstu, uruchomić lub następnego <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>.|  
  
 Dowolnej z predefiniowanych <xref:System.Windows.Media.TextFormatting.TextRun> może być podklasą klasy obiektów. Dzięki temu źródła tekstu zapewnienie uruchomienia programu formatującego tekstu z tekstem zawierających dane niestandardowe.  
  
 W poniższym przykładzie pokazano <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metody. Zwraca ten magazyn tekstu <xref:System.Windows.Media.TextFormatting.TextRun> obiektów, aby element formatujący tekstu do przetworzenia.  
  
 [!code-csharp[TextFormatterExample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
>  W tym przykładzie store tekstu udostępnia te same właściwości tekstu do całego tekstu. Zaawansowane tekst, który magazynów musi implementować własne zakresu zarządzania, aby zezwolić na poszczególnych znaków mieć różne właściwości.  
  
<a name="section5"></a>   
## <a name="specifying-formatting-properties"></a>Określanie właściwości formatowania  
 <xref:System.Windows.Media.TextFormatting.TextRun> obiekty są formatowane przy użyciu właściwości udostępniane przez Magazyn tekstu. Te właściwości są dostępne w dwóch typów <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> i <xref:System.Windows.Media.TextFormatting.TextRunProperties>. <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> takie jak obsługa akapitu (włącznie) właściwości <xref:System.Windows.TextAlignment> i <xref:System.Windows.FlowDirection>. <xref:System.Windows.Media.TextFormatting.TextRunProperties> właściwości, które mogą być różne dla każdego tekstu, uruchom w akapicie, takich jak Pędzel pierwszego planu <xref:System.Windows.Media.Typeface>i rozmiar czcionki. Aby zaimplementować niestandardowy akapitu i niestandardowego tekstu, uruchom typów właściwości, aplikacji, należy utworzyć klasy, które wynikają z <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> i <xref:System.Windows.Media.TextFormatting.TextRunProperties> odpowiednio.  
  
## <a name="see-also"></a>Zobacz także

- [Typografia w WPF](typography-in-wpf.md)
- [Dokumenty w WPF](documents-in-wpf.md)
