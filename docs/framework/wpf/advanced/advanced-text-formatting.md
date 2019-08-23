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
ms.openlocfilehash: 469c62691ff38a8c5a01bec3ddfd7b324bab7eca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969067"
---
# <a name="advanced-text-formatting"></a>Zaawansowane formatowanie tekstu
Windows Presentation Foundation (WPF) oferuje niezawodny zestaw interfejsów API do dołączania tekstu w aplikacji. Układ i [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]interfejsy API, takie <xref:System.Windows.Controls.TextBlock>jak, zapewniają najpopularniejsze i ogólne elementy używane do prezentacji tekstowej. Rysowanie interfejsów API, takich <xref:System.Windows.Media.GlyphRunDrawing> jak <xref:System.Windows.Media.FormattedText>i, zapewnia metodę dołączenia tekstu sformatowanego na rysunku. Na najbardziej zaawansowanym poziomie program [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zapewnia rozszerzalny aparat formatowania tekstu do sterowania każdym aspektem prezentacji tekstowej, taki jak zarządzanie magazynem tekstu, zarządzanie formatowaniem tekstu i zarządzanie obiektami osadzonymi.  
  
 Ten temat zawiera wprowadzenie do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] formatowania tekstu. Koncentruje się na implementacji klienta i korzystaniu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] z aparatu formatowania tekstu.  
  
> [!NOTE]
> Wszystkie przykłady kodu w tym dokumencie można znaleźć w przykładowym [formacie tekstu zaawansowanego](https://go.microsoft.com/fwlink/?LinkID=159965).  

<a name="prereq"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że znasz interfejsy API wyższego poziomu używane do prezentacji tekstowej. Większość scenariuszy użytkownika nie wymaga zaawansowanych interfejsów API formatowania tekstu opisanych w tym temacie. Aby zapoznać się z wprowadzeniem do różnych interfejsów API tekstu, zobacz [dokumenty w WPF](documents-in-wpf.md).  
  
<a name="section1"></a>   
## <a name="advanced-text-formatting"></a>Zaawansowane formatowanie tekstu  
 Układ tekstu i [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kontrolki w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] programie udostępniają właściwości formatowania, które umożliwiają łatwe dołączanie sformatowanego tekstu do aplikacji. Te kontrolki uwidaczniają wiele właściwości, które obsługują prezentację tekstu, w tym jej krój, rozmiar i kolor. W normalnych warunkach te kontrolki mogą obsługiwać większość prezentacji tekstowej w aplikacji. Jednak niektóre zaawansowane scenariusze wymagają kontroli nad przechowywaniem tekstu oraz prezentacji tekstowej. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]zapewnia do tego celu aparat Extensible formating Text.  
  
 Zaawansowane funkcje formatowania tekstu, które są [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dostępne w programie, składają się z aparatu formatowania tekstu, magazynu tekstowego, tekstu i właściwości formatowania. Aparat formatowania tekstu, <xref:System.Windows.Media.TextFormatting.TextFormatter>tworzy wiersze tekstu, które mają być używane na potrzeby prezentacji. Jest to osiągane przez zainicjowanie procesu formatowania wiersza i wywołanie programu formatującego <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>tekstu. Program formatujący tekst pobiera przebiegi tekstowe z magazynu tekstu przez wywołanie <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metody magazynu. Obiekty są następnie tworzone do <xref:System.Windows.Media.TextFormatting.TextLine> obiektów przez program formatujący tekst i nadawane aplikacji do inspekcji lub wyświetlania. <xref:System.Windows.Media.TextFormatting.TextRun>  
  
<a name="section2"></a>   
## <a name="using-the-text-formatter"></a>Korzystanie z programu formatującego tekstu  
 <xref:System.Windows.Media.TextFormatting.TextFormatter>jest aparatem formatowania tekstu i udostępnia usługi do formatowania i przerywania wierszy tekstu. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Program formatujący tekst może obsługiwać różne formaty znaków tekstu i style akapitów, a także obsługuje międzynarodowy układ tekstu.  
  
 W <xref:System.Windows.Media.TextFormatting.TextFormatter> przeciwieństwie do tradycyjnego interfejsu API tekstu, współdziała z klientem układu tekstu za pomocą zestawu metod wywołania zwrotnego. Wymaga, aby klient dostarczał te metody w implementacji <xref:System.Windows.Media.TextFormatting.TextSource> klasy. Na poniższym diagramie przedstawiono interakcje układu tekstu między aplikacją kliencką i <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagram klienta układu tekstu i elementu textformatującego](./media/advanced-text-formatting/text-layout-textformatter-interaction.png)  
  
 Program formatujący tekst jest używany do pobierania wierszy tekstu sformatowanego z magazynu tekstu, który jest implementacją <xref:System.Windows.Media.TextFormatting.TextSource>programu. W tym celu należy najpierw utworzyć wystąpienie programu formatującego tekstu przy użyciu <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A> metody. Ta metoda tworzy wystąpienie programu formatującego tekst i ustawia maksymalną wysokość i szerokość wiersza. Zaraz po utworzeniu wystąpienia programu formatującego tekstu proces tworzenia linii jest uruchamiany przez wywołanie <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> metody. <xref:System.Windows.Media.TextFormatting.TextFormatter>wywołuje z powrotem do źródła tekstu, aby pobrać parametry tekstu i formatowania dla przebiegów tekstu tworzących wiersz.  
  
 W poniższym przykładzie jest wyświetlany proces formatowania magazynu tekstu. Obiekt jest używany do pobierania wierszy tekstu z magazynu tekstowego, a następnie formatowania wiersza tekstu do rysowania <xref:System.Windows.Media.DrawingContext>w. <xref:System.Windows.Media.TextFormatting.TextFormatter>  
  
 [!code-csharp[TextFormatterExample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## <a name="implementing-the-client-text-store"></a>Implementowanie magazynu tekstowego klienta  
 Po rozbudowaniu aparatu formatowania tekstu wymagane jest zaimplementowanie wszystkich aspektów magazynu tekstowego i zarządzanie nimi. To nie jest zadanie proste. Magazyn tekstowy jest odpowiedzialny za śledzenie właściwości przebiegu tekstu, właściwości akapitu, osadzonych obiektów i innej podobnej zawartości. Udostępnia również program formatujący tekst z poszczególnymi <xref:System.Windows.Media.TextFormatting.TextRun> obiektami, których program formatujący tekstu używa do tworzenia <xref:System.Windows.Media.TextFormatting.TextLine> obiektów.  
  
 Do obsługi wirtualizacji magazynu tekstowego magazyn tekstu musi pochodzić od <xref:System.Windows.Media.TextFormatting.TextSource>. <xref:System.Windows.Media.TextFormatting.TextSource>definiuje metodę używaną przez program formatujący Text do pobierania tekstu z magazynu tekstowego. <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>to metoda używana przez program formatujący tekst do pobierania przebiegów tekstowych używanych w formatowaniu wierszy. Wywołanie <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> jest wielokrotnie wykonywane przez program formatujący tekst do momentu wystąpienia jednego z następujących warunków:  
  
- Zwracana <xref:System.Windows.Media.TextFormatting.TextEndOfLine> jest lub podklasa.  
  
- Skumulowana szerokość przebiegów tekstu przekracza maksymalną szerokość linii określoną w wywołaniu, aby utworzyć program formatujący tekst lub wywołanie <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> metody programu formatującego tekstu.  
  
- Zwracana jest sekwencja nowego wiersza, taka jak "CF", "LF" lub "CRLF". [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]  
  
<a name="section4"></a>   
## <a name="providing-text-runs"></a>Udostępnianie tekstu  
 Podstawowym procesem formatowania tekstu jest interakcja między programem formatujący tekst i magazynem tekstu. Twoja implementacja programu <xref:System.Windows.Media.TextFormatting.TextSource> udostępnia <xref:System.Windows.Media.TextFormatting.TextRun> program formatujący tekst z obiektami i właściwościami, za pomocą których można formatować uruchomienia tekstu. Ta interakcja jest obsługiwana przez <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metodę, która jest wywoływana przez program formatujący tekst.  
  
 W poniższej tabeli przedstawiono niektóre ze wstępnie zdefiniowanych <xref:System.Windows.Media.TextFormatting.TextRun> obiektów.  
  
|Typ TextRun|Użycie|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|Wyspecjalizowane uruchomienie tekstu używane do przekazywania reprezentacji symboli znaków z powrotem do programu formatującego tekstu.|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|Wyspecjalizowany przebieg tekstu służący do dostarczania zawartości, w której pomiary, testowanie trafień i Rysowanie odbywa się w całości, na przykład w postaci przycisku lub obrazu w tekście.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|Wyspecjalizowane uruchomienie tekstu używane do oznaczania końca wiersza.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|Wyspecjalizowany przebieg tekstowy używany do oznaczania końca akapitu.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|Wyspecjalizowany przebieg tekstowy używany do oznaczania końca segmentu, na przykład w celu zakończenia zakresu, na który miało wpływ <xref:System.Windows.Media.TextFormatting.TextModifier> poprzednie uruchomienie.|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|Wyspecjalizowane uruchomienie tekstu używane do oznaczania zakresu znaków ukrytych.|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|Wyspecjalizowany przebieg tekstu służący do modyfikowania właściwości tekstu jest w jego zakresie. Zakres wykracza do następnego pasującego <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> przebiegu tekstu lub do następnego. <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|  
  
 Każdy ze wstępnie zdefiniowanych <xref:System.Windows.Media.TextFormatting.TextRun> obiektów może być podklasą. Dzięki temu Źródło tekstu będzie zawierać tekst programu formatującego z przebiegami tekstowymi, które zawierają dane niestandardowe.  
  
 Poniższy przykład ilustruje <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metodę. Ten magazyn tekstowy zwraca <xref:System.Windows.Media.TextFormatting.TextRun> obiekty do programu formatującego tekstu do przetworzenia.  
  
 [!code-csharp[TextFormatterExample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
> W tym przykładzie magazyn tekstu zapewnia te same właściwości tekstowe do całego tekstu. Zaawansowane magazyny tekstowe muszą implementować własne zarządzanie zakresami, aby umożliwić indywidualnym znakom różne właściwości.  
  
<a name="section5"></a>   
## <a name="specifying-formatting-properties"></a>Określanie właściwości formatowania  
 <xref:System.Windows.Media.TextFormatting.TextRun>obiekty są formatowane przy użyciu właściwości dostarczonych przez magazyn tekstu. Te właściwości są dostępne w dwóch typach <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> , <xref:System.Windows.Media.TextFormatting.TextRunProperties>a. <xref:System.Windows.Media.TextFormatting.TextParagraphProperties>Obsługuj właściwości z uwzględnieniem akapitu <xref:System.Windows.FlowDirection>, takie jak <xref:System.Windows.TextAlignment> i. <xref:System.Windows.Media.TextFormatting.TextRunProperties>są właściwościami, które mogą być różne dla każdego tekstu w akapicie, takie jak Pędzel <xref:System.Windows.Media.Typeface>pierwszego planu, i rozmiar czcionki. Aby zaimplementować niestandardowe typy właściwości akapitu i niestandardowego tekstu, aplikacja musi utworzyć klasy, które pochodzą z <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> i <xref:System.Windows.Media.TextFormatting.TextRunProperties> odpowiednio.  
  
## <a name="see-also"></a>Zobacz także

- [Typografia w WPF](typography-in-wpf.md)
- [Dokumenty w WPF](documents-in-wpf.md)
