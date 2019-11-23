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
ms.openlocfilehash: 2c120c6d71cb22bc38909f980b2f6faf2b5c3663
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395216"
---
# <a name="advanced-text-formatting"></a>Zaawansowane formatowanie tekstu
Windows Presentation Foundation (WPF) oferuje niezawodny zestaw interfejsów API do dołączania tekstu w aplikacji. Układy i [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]interfejsy API, takie jak <xref:System.Windows.Controls.TextBlock>, zapewniają najpopularniejsze i ogólne elementy do użycia na potrzeby prezentacji tekstowej. Rysowanie interfejsów API, takich jak <xref:System.Windows.Media.GlyphRunDrawing> i <xref:System.Windows.Media.FormattedText>, zapewniają metodę dołączenia tekstu sformatowanego na rysunku. Na najbardziej zaawansowanym poziomie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zapewnia rozszerzalny aparat formatowania tekstu do sterowania każdym aspektem prezentacji tekstu, taki jak zarządzanie magazynem tekstu, zarządzanie formatowaniem tekstu i zarządzanie obiektami osadzonymi.  
  
 Ten temat zawiera wprowadzenie do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] formatowania tekstu. Koncentruje się na implementacji klienta i korzystaniu z [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aparatu formatowania tekstu.  
  
> [!NOTE]
> Wszystkie przykłady kodu w tym dokumencie można znaleźć w [przykładowym formacie tekstu zaawansowanego](https://go.microsoft.com/fwlink/?LinkID=159965).  

<a name="prereq"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że znasz interfejsy API wyższego poziomu używane do prezentacji tekstowej. Większość scenariuszy użytkownika nie wymaga zaawansowanych interfejsów API formatowania tekstu opisanych w tym temacie. Aby zapoznać się z wprowadzeniem do różnych interfejsów API tekstu, zobacz [dokumenty w WPF](documents-in-wpf.md).  
  
<a name="section1"></a>   
## <a name="advanced-text-formatting"></a>Zaawansowane formatowanie tekstu  
 Układ tekstu i kontrolki [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] udostępniają właściwości formatowania, które umożliwiają łatwe dołączanie sformatowanego tekstu do aplikacji. Te kontrolki uwidaczniają wiele właściwości, które obsługują prezentację tekstu, w tym jej krój, rozmiar i kolor. W normalnych warunkach te kontrolki mogą obsługiwać większość prezentacji tekstowej w aplikacji. Jednak niektóre zaawansowane scenariusze wymagają kontroli nad przechowywaniem tekstu oraz prezentacji tekstowej. w tym celu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zapewnia rozszerzalny aparat formatowania tekstu.  
  
 Zaawansowane funkcje formatowania tekstu dostępne w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zawierają aparat formatowania tekstu, magazyn tekstu, przebiegi tekstowe i właściwości formatowania. Aparat formatowania tekstu <xref:System.Windows.Media.TextFormatting.TextFormatter>, tworzy wiersze tekstu, które mają być używane na potrzeby prezentacji. Jest to osiągane przez zainicjowanie procesu formatowania linii i wywołanie <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>programu formatującego tekstu. Program formatujący tekst pobiera przebiegi tekstowe z magazynu tekstu przez wywołanie metody <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> sklepu. Obiekty <xref:System.Windows.Media.TextFormatting.TextRun> są następnie tworzone w <xref:System.Windows.Media.TextFormatting.TextLine> obiektów przez program formatujący tekst i nadawane aplikacji do inspekcji lub wyświetlania.  
  
<a name="section2"></a>   
## <a name="using-the-text-formatter"></a>Korzystanie z programu formatującego tekstu  
 <xref:System.Windows.Media.TextFormatting.TextFormatter> jest aparatem formatowania tekstu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] i udostępnia usługi do formatowania i przerywania wierszy tekstu. Program formatujący tekst może obsługiwać różne formaty znaków tekstu i style akapitów, a także obsługuje międzynarodowy układ tekstu.  
  
 W przeciwieństwie do tradycyjnego interfejsu API tekstu, <xref:System.Windows.Media.TextFormatting.TextFormatter> współdziała z klientem układu tekstu za pomocą zestawu metod wywołania zwrotnego. Wymaga, aby klient dostarczał te metody w implementacji klasy <xref:System.Windows.Media.TextFormatting.TextSource>. Na poniższym diagramie przedstawiono interakcje układu tekstu między aplikacją kliencką a <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagram klienta układu tekstu i elementu textformatującego](./media/advanced-text-formatting/text-layout-textformatter-interaction.png)  
  
 Program formatujący tekst jest używany do pobierania wierszy tekstu sformatowanego z magazynu tekstu, który jest implementacją <xref:System.Windows.Media.TextFormatting.TextSource>. W tym celu należy najpierw utworzyć wystąpienie programu formatującego tekstu przy użyciu metody <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A>. Ta metoda tworzy wystąpienie programu formatującego tekst i ustawia maksymalną wysokość i szerokość wiersza. Zaraz po utworzeniu wystąpienia programu formatującego tekstu proces tworzenia linii jest uruchamiany przez wywołanie metody <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>. <xref:System.Windows.Media.TextFormatting.TextFormatter> wywołania zwrotne do źródła tekstu w celu pobrania parametrów tekstowych i formatowania dla przebiegów tekstu tworzących wiersz.  
  
 W poniższym przykładzie jest wyświetlany proces formatowania magazynu tekstu. Obiekt <xref:System.Windows.Media.TextFormatting.TextFormatter> jest używany do pobierania wierszy tekstu z magazynu tekstowego, a następnie formatowania wiersza tekstu do rysowania w <xref:System.Windows.Media.DrawingContext>.  
  
 [!code-csharp[TextFormatterExample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## <a name="implementing-the-client-text-store"></a>Implementowanie magazynu tekstowego klienta  
 Po rozbudowaniu aparatu formatowania tekstu wymagane jest zaimplementowanie wszystkich aspektów magazynu tekstowego i zarządzanie nimi. To nie jest zadanie proste. Magazyn tekstowy jest odpowiedzialny za śledzenie właściwości przebiegu tekstu, właściwości akapitu, osadzonych obiektów i innej podobnej zawartości. Udostępnia również program formatujący tekst z poszczególnymi obiektami <xref:System.Windows.Media.TextFormatting.TextRun>, których program formatujący tekstu używa do tworzenia obiektów <xref:System.Windows.Media.TextFormatting.TextLine>.  
  
 W celu obsługi wirtualizacji magazynu tekstowego magazyn tekstu musi pochodzić od <xref:System.Windows.Media.TextFormatting.TextSource>. <xref:System.Windows.Media.TextFormatting.TextSource> definiuje metodę używaną przez program formatujący Text do pobierania tekstu z magazynu tekstowego. <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> to metoda używana przez program formatujący tekst do pobierania przebiegów tekstowych używanych w formatowaniu wierszy. Wywołanie <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> jest wielokrotnie wykonywane przez program formatujący tekst do momentu wystąpienia jednego z następujących warunków:  
  
- Zwraca <xref:System.Windows.Media.TextFormatting.TextEndOfLine> lub podklasę.  
  
- Skumulowana szerokość przebiegów tekstu przekracza maksymalną szerokość linii określoną w wywołaniu, aby utworzyć program formatujący tekst, lub wywołanie metody <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> w programie formatującego tekstu.  
  
- Zwracana jest sekwencja wiersza w formacie Unicode, taka jak "CF", "LF" lub "CRLF".  
  
<a name="section4"></a>   
## <a name="providing-text-runs"></a>Udostępnianie tekstu  
 Podstawowym procesem formatowania tekstu jest interakcja między programem formatujący tekst i magazynem tekstu. Twoja implementacja <xref:System.Windows.Media.TextFormatting.TextSource> udostępnia program formatujący tekst z obiektami <xref:System.Windows.Media.TextFormatting.TextRun> i właściwościami, z których mają być formatowane uruchomienia tekstu. Ta interakcja jest obsługiwana przez metodę <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>, która jest wywoływana przez program formatujący tekst.  
  
 W poniższej tabeli przedstawiono niektóre wstępnie zdefiniowane obiekty <xref:System.Windows.Media.TextFormatting.TextRun>.  
  
|Typ TextRun|Użycie|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|Wyspecjalizowane uruchomienie tekstu używane do przekazywania reprezentacji symboli znaków z powrotem do programu formatującego tekstu.|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|Wyspecjalizowany przebieg tekstu służący do dostarczania zawartości, w której pomiary, testowanie trafień i Rysowanie odbywa się w całości, na przykład w postaci przycisku lub obrazu w tekście.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|Wyspecjalizowane uruchomienie tekstu używane do oznaczania końca wiersza.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|Wyspecjalizowany przebieg tekstowy używany do oznaczania końca akapitu.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|Wyspecjalizowany przebieg tekstowy używany do oznaczania końca segmentu, na przykład w celu zakończenia zakresu, na który ma wpływ poprzedni <xref:System.Windows.Media.TextFormatting.TextModifier> uruchomienie.|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|Wyspecjalizowane uruchomienie tekstu używane do oznaczania zakresu znaków ukrytych.|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|Wyspecjalizowany przebieg tekstu służący do modyfikowania właściwości tekstu jest w jego zakresie. Zakres rozciąga się na następny pasujący <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> przebiegu tekstu lub następny <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>.|  
  
 Wszystkie wstępnie zdefiniowane obiekty <xref:System.Windows.Media.TextFormatting.TextRun> mogą być podklasy. Dzięki temu Źródło tekstu będzie zawierać tekst programu formatującego z przebiegami tekstowymi, które zawierają dane niestandardowe.  
  
 Poniższy przykład ilustruje metodę <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>. Ten magazyn tekstowy zwraca <xref:System.Windows.Media.TextFormatting.TextRun> obiektów do programu formatującego tekstu w celu przetworzenia.  
  
 [!code-csharp[TextFormatterExample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
> W tym przykładzie magazyn tekstu zapewnia te same właściwości tekstowe do całego tekstu. Zaawansowane magazyny tekstowe muszą implementować własne zarządzanie zakresami, aby umożliwić indywidualnym znakom różne właściwości.  
  
<a name="section5"></a>   
## <a name="specifying-formatting-properties"></a>Określanie właściwości formatowania  
 obiekty <xref:System.Windows.Media.TextFormatting.TextRun> są formatowane przy użyciu właściwości dostarczonych przez magazyn tekstu. Te właściwości są dostępne w dwóch typach, <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> i <xref:System.Windows.Media.TextFormatting.TextRunProperties>. <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> obsługiwać właściwości z uwzględnieniem akapitu, takie jak <xref:System.Windows.TextAlignment> i <xref:System.Windows.FlowDirection>. <xref:System.Windows.Media.TextFormatting.TextRunProperties> to właściwości, które mogą być różne dla każdego tekstu w akapicie, takie jak Pędzel pierwszego planu, <xref:System.Windows.Media.Typeface>i rozmiar czcionki. Aby zaimplementować niestandardowe typy właściwości akapitu i niestandardowego tekstu, aplikacja musi utworzyć klasy, które pochodzą od <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> i <xref:System.Windows.Media.TextFormatting.TextRunProperties> odpowiednio.  
  
## <a name="see-also"></a>Zobacz także

- [Typografia w WPF](typography-in-wpf.md)
- [Dokumenty w WPF](documents-in-wpf.md)
