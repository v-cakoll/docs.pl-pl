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
ms.openlocfilehash: 745d20e0bd4f877f9d4559f9fc7829b56689d35c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185940"
---
# <a name="advanced-text-formatting"></a>Zaawansowane formatowanie tekstu
Windows Presentation Foundation (WPF) zapewnia niezawodny zestaw interfejsów API do dołączania tekstu w aplikacji. Układ [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] i interfejsy API, takie jak <xref:System.Windows.Controls.TextBlock>, zapewniają najbardziej typowe i ogólne elementy do prezentacji tekstu. Rysowanie interfejsów API, takich jak <xref:System.Windows.Media.GlyphRunDrawing> i <xref:System.Windows.Media.FormattedText>, zapewniają środki do włączenia sformatowanego tekstu do rysunków. Na najbardziej zaawansowanym poziomie WPF WPF zapewnia rozszerzalny aparat formatowania tekstu do kontrolowania każdego aspektu prezentacji tekstu, takich jak zarządzanie magazynem tekstu, zarządzanie formatowaniem uruchamiania tekstu i zarządzanie obiektami osadzonymi.  
  
 Ten temat zawiera wprowadzenie do formatowania tekstu WPF. Koncentruje się na implementacji klienta i korzystania z aparatu formatowania tekstu WPF.  
  
> [!NOTE]
> Wszystkie przykłady kodu w tym dokumencie można znaleźć w [przykładzie zaawansowanego formatowania tekstu](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI/TextFormatting).  

<a name="prereq"></a>
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie przyjęto założenie, że znasz interfejsy API wyższego poziomu używane do prezentacji tekstu. Większość scenariuszy użytkowników nie będzie wymagać zaawansowanych interfejsów API formatowania tekstu omówionych w tym temacie. Aby zapoznać się z wprowadzeniem do różnych interfejsów API tekstu, zobacz [Dokumenty w WPF](documents-in-wpf.md).  
  
<a name="section1"></a>
## <a name="advanced-text-formatting"></a>Zaawansowane formatowanie tekstu  
 Układ tekstu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] i formanty w WPF zapewniają właściwości formatowania, które umożliwiają łatwe dołączanie sformatowanego tekstu w aplikacji. Te formanty uwidaczniają szereg właściwości do obsługi prezentacji tekstu, który zawiera jego krój pisma, rozmiar i kolor. W zwykłych okolicznościach te formanty mogą obsługiwać większość prezentacji tekstu w aplikacji. Jednak niektóre zaawansowane scenariusze wymagają kontroli przechowywania tekstu, a także prezentacji tekstu. WPF WPF zapewnia rozszerzalny aparat formatowania tekstu w tym celu.  
  
 Zaawansowane funkcje formatowania tekstu znalezione w WPF składają się z aparatu formatowania tekstu, magazynu tekstu, przebiegów tekstu i właściwości formatowania. Aparat formatowania tekstu <xref:System.Windows.Media.TextFormatting.TextFormatter>, tworzy wiersze tekstu, który ma być używany do prezentacji. Osiąga się to poprzez inicjowanie procesu formatowania linii <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>i wywołanie formatera tekstu . Formater tekstu pobiera tekst uruchamia się z magazynu tekstu, wywołując <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metodę sklepu. Obiekty <xref:System.Windows.Media.TextFormatting.TextRun> są następnie <xref:System.Windows.Media.TextFormatting.TextLine> formowane w obiekty przez formater tekstu i przekazywane aplikacji do inspekcji lub wyświetlania.  
  
<a name="section2"></a>
## <a name="using-the-text-formatter"></a>Korzystanie z formatera tekstu  
 <xref:System.Windows.Media.TextFormatting.TextFormatter>jest aparat formatowania tekstu WPF i zapewnia usługi formatowania i przerywania wierszy tekstu. Formater tekstu może obsługiwać różne formaty znaków tekstowych i style akapitów, a także obsługuje międzynarodowy układ tekstu.  
  
 W przeciwieństwie do tradycyjnego interfejsu API tekstu <xref:System.Windows.Media.TextFormatting.TextFormatter> współdziała z klientem układu tekstu za pomocą zestawu metod wywołania zwrotnego. Wymaga klienta, aby zapewnić te metody <xref:System.Windows.Media.TextFormatting.TextSource> w implementacji klasy. Na poniższym diagramie przedstawiono interakcję układu <xref:System.Windows.Media.TextFormatting.TextFormatter>tekstu między aplikacją kliencką i .  
  
 ![Diagram klienta układu tekstu i textformatter](./media/advanced-text-formatting/text-layout-textformatter-interaction.png)  
  
 Program formatowania tekstu służy do pobierania sformatowanych wierszy tekstu <xref:System.Windows.Media.TextFormatting.TextSource>z magazynu tekstu, który jest implementacją programu . Odbywa się to przez pierwsze utworzenie wystąpienia formatera <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A> tekstu przy użyciu metody. Ta metoda tworzy wystąpienie formatera tekstu i ustawia maksymalne wartości wysokości i szerokości linii. Jak tylko zostanie utworzone wystąpienie formatera tekstu, proces tworzenia wiersza jest uruchamiany przez wywołanie <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> metody. <xref:System.Windows.Media.TextFormatting.TextFormatter>wywołuje z powrotem do źródła tekstu, aby pobrać tekst i parametry formatowania dla przebiegów tekstu, które tworzą wiersz.  
  
 W poniższym przykładzie wyświetlany jest proces formatowania magazynu tekstu. Obiekt <xref:System.Windows.Media.TextFormatting.TextFormatter> służy do pobierania wierszy tekstu z magazynu tekstu, a następnie <xref:System.Windows.Media.DrawingContext>formatowania wiersza tekstu w celu wciągnania do pliku .  
  
 [!code-csharp[TextFormatterExample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>
## <a name="implementing-the-client-text-store"></a>Implementacja magazynu tekstu klienta  
 Po rozszerzeniu aparatu formatowania tekstu, należy zaimplementować i zarządzać wszystkimi aspektami magazynu tekstu. Nie jest to banalne zadanie. Magazyn tekstu jest odpowiedzialny za śledzenie właściwości uruchamiania tekstu, właściwości akapitu, obiektów osadzonych i innych podobnych treści. Zapewnia również program do formatowania tekstu z poszczególnych <xref:System.Windows.Media.TextFormatting.TextRun> obiektów, które program text formater używa do tworzenia <xref:System.Windows.Media.TextFormatting.TextLine> obiektów.  
  
 Aby obsługiwać wirtualizację magazynu tekstu, magazyn tekstu <xref:System.Windows.Media.TextFormatting.TextSource>musi pochodzić z pliku . <xref:System.Windows.Media.TextFormatting.TextSource>definiuje metodę używana przez formater tekstu do pobierania przebiegów tekstu z magazynu tekstu. <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>jest metodą używaną przez formater tekstu do pobierania przebiegów tekstu używanych w formatowaniu linii. Wywołanie <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> jest wielokrotnie przez formater tekstu, aż wystąpi jeden z następujących warunków:  
  
- A <xref:System.Windows.Media.TextFormatting.TextEndOfLine> lub podklasa jest zwracana.  
  
- Skumulowana szerokość przebiegów tekstu przekracza maksymalną szerokość linii określoną w wywołaniu w celu utworzenia <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> formatera tekstu lub wywołania metody formatera tekstu.  
  
- Zwracana jest sekwencja nowego linii Unicode, taka jak "CF", "LF" lub "CRLF".  
  
<a name="section4"></a>
## <a name="providing-text-runs"></a>Dostarczanie uruchomień tekstu  
 Rdzeniem procesu formatowania tekstu jest interakcja między formaterem tekstu a magazynem tekstu. Implementacja <xref:System.Windows.Media.TextFormatting.TextSource> udostępnia formater tekstu <xref:System.Windows.Media.TextFormatting.TextRun> z obiektów i właściwości, za pomocą których do formatowania tekstu jest uruchamiany. Ta interakcja jest <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> obsługiwana przez metodę, która jest wywoływana przez formater tekstu.  
  
 W poniższej tabeli przedstawiono <xref:System.Windows.Media.TextFormatting.TextRun> niektóre wstępnie zdefiniowane obiekty.  
  
|TekstRun Typ|Sposób użycia|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|Uruchamianie tekstu specjalistycznego używane do przekazywania reprezentacji glifów znaków z powrotem do formatera tekstu.|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|Wyspecjalizowany tekst uruchamiany używany do dostarczania zawartości, w której pomiar, testowanie trafień i rysowanie odbywa się w całości, na przykład przycisk lub obraz w tekście.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|Tekst specjalny jest używany do oznaczania końca wiersza.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|Tekst specjalny jest używany do oznaczania końca akapitu.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|Uruchomione tekst wyspecjalizowany używany do oznaczania końca segmentu, na przykład <xref:System.Windows.Media.TextFormatting.TextModifier> w celu zakończenia zakresu, którego dotyczy poprzednie uruchomienie.|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|Wyspecjalizowany tekst jest używany do oznaczania zakresu ukrytych znaków.|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|Uruchamianie tekstu specjalistycznego używane do modyfikowania właściwości tekstu jest uruchamiane w jego zakresie. Zakres rozciąga się na <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> następne pasujące uruchomienie <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>tekstu lub następny .|  
  
 Każdy ze wstępnie zdefiniowanych <xref:System.Windows.Media.TextFormatting.TextRun> obiektów może być podklasyfikowany. Dzięki temu źródło tekstu, aby zapewnić program do formatowania tekstu z uruchomień tekstu, które zawierają dane niestandardowe.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metodę. Ten magazyn <xref:System.Windows.Media.TextFormatting.TextRun> tekstu zwraca obiekty do formatera tekstu do przetwarzania.  
  
 [!code-csharp[TextFormatterExample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
> W tym przykładzie magazyn tekstu udostępnia te same właściwości tekstu do wszystkich tekstu. Zaawansowane magazyny tekstu musiałyby zaimplementować własne zarządzanie zakresem, aby umożliwić poszczególnym znakom posiadanie różnych właściwości.  
  
<a name="section5"></a>
## <a name="specifying-formatting-properties"></a>Określanie właściwości formatowania  
 <xref:System.Windows.Media.TextFormatting.TextRun>obiekty są formatowane przy użyciu właściwości dostarczonych przez magazyn tekstu. Właściwości te są dostępne <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> w <xref:System.Windows.Media.TextFormatting.TextRunProperties>dwóch typach i . <xref:System.Windows.Media.TextFormatting.TextParagraphProperties>obsługa właściwości akapitu <xref:System.Windows.TextAlignment> <xref:System.Windows.FlowDirection>włącznie, takich jak i . <xref:System.Windows.Media.TextFormatting.TextRunProperties>to właściwości, które mogą być różne dla każdego tekstu uruchamianego <xref:System.Windows.Media.Typeface>w akapicie, takie jak pędzel pierwszego planu i rozmiar czcionki. Aby zaimplementować niestandardowe typy właściwości uruchamiania akapitu i tekstu niestandardowego, aplikacja musi utworzyć klasy, które pochodzą z <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> i <xref:System.Windows.Media.TextFormatting.TextRunProperties> odpowiednio.  
  
## <a name="see-also"></a>Zobacz też

- [Typografia w WPF](typography-in-wpf.md)
- [Dokumenty w WPF](documents-in-wpf.md)
