---
title: Zaawansowane formatowanie tekstu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [WPF]
- text [WPF]
- typography [WPF], text formatting
ms.assetid: f0a7986e-f5b2-485c-a27d-f8e922022212
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1828b6ffe2d24c2bfb98b4668a9540adf5978e5f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="advanced-text-formatting"></a>Zaawansowane formatowanie tekstu
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Oferuje niezawodny zestaw [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] dla łącznie z tekstem w aplikacji. Układ i [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], takich jak <xref:System.Windows.Controls.TextBlock>, podaj najbardziej typowe i ogólne użycie elementy prezentacji tekstu. Rysowanie [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], takich jak <xref:System.Windows.Media.GlyphRunDrawing> i <xref:System.Windows.Media.FormattedText>, pozwalają na tym tekst sformatowany na rysunkach. Najbardziej zaawansowane poziom [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] oferuje rozszerzalny aparat do sterowania wszystkie aspekty prezentacji tekstu, takich jak zarządzanie magazynem tekstu, zarządzania formatowania tekstu, uruchom i zarządzania osadzonego obiektu formatowania tekstu.  
  
 Ten temat zawiera wprowadzenie do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] formatowania tekstu. Dotyczy on implementacja klienta i korzystania z [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aparat formatowania tekstu.  
  
> [!NOTE]
>  Wszystkie przykłady kodu, w tym dokumencie znajdują się w [zaawansowane próbki formatowania tekstu](http://go.microsoft.com/fwlink/?LinkID=159965).  
  

  
<a name="prereq"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że czytelnik zna wyższego poziomu [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] użyte do prezentowania tekstu. Większość scenariuszy użytkownika nie będzie wymagać formatowania tekstu zaawansowane [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] omówione w tym temacie. Aby obejrzeć wprowadzenie do różnych tekst [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], zobacz [dokumentów na platformie WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
<a name="section1"></a>   
## <a name="advanced-text-formatting"></a>Zaawansowane formatowanie tekstu  
 Układu tekstu i [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] formantów w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Podaj właściwości formatowania, które umożliwiają łatwe dołączanie tekst sformatowany w aplikacji. Tych kontrolek ujawnia szereg właściwości do obsługi prezentacji tekst, który zawiera jego krój czcionki, rozmiaru i koloru. W normalnych okolicznościach tych kontrolek można obsługiwać Większość prezentacji tekstu w aplikacji. Jednak niektóre zaawansowane scenariusze wymagają kontroli przechowywanie tekstu, a także tekst prezentacji. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]oferuje rozszerzalny aparat do tego celu formatowania tekstu.  
  
 Znaleziono tekst zaawansowane funkcje formatowania w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] składają się z tekstu formatowanie aparatu magazynu tekstu, uruchomienia tekstu i formatowanie właściwości. Aparat, formatowania tekstu <xref:System.Windows.Media.TextFormatting.TextFormatter>, tworzy wierszy tekstu używanego do prezentacji. Jest to osiągane przez inicjowanie proces formatowania wiersza i wywoływania elementu formatującego tekstu <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>. Program formatujący tekst pobiera uruchomienia tekstu z magazynu tekstu przez wywołanie metody sklepu <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metody. <xref:System.Windows.Media.TextFormatting.TextRun> Obiekty są następnie utworzone w <xref:System.Windows.Media.TextFormatting.TextLine> obiektów przez program formatujący tekstu i kontroli lub wyświetlania aplikacji.  
  
<a name="section2"></a>   
## <a name="using-the-text-formatter"></a>Przy użyciu elementu formatującego tekstu  
 <xref:System.Windows.Media.TextFormatting.TextFormatter>jest [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] formatowania tekstu aparat i udostępnia usługi dotyczące formatowania i dzielenia wierszy tekstu. Program formatujący tekst może obsłużyć w różnych formatach znaków i akapitu style i obsługuje układu tekstu międzynarodowe.  
  
 W przeciwieństwie do tradycyjnych tekst [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)], <xref:System.Windows.Media.TextFormatting.TextFormatter> wchodzi w interakcję z klientem układu tekstu za pomocą zestawu metod wywołania zwrotnego. Wymaga od klienta zapewnienia tych metod w celu wykonania <xref:System.Windows.Media.TextFormatting.TextSource> klasy. Na poniższym diagramie przedstawiono układu tekstu współdziałanie aplikacji klienckiej i <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagram klienta układu tekstu i obiekt TextFormatter](../../../../docs/framework/wpf/advanced/media/textformatter01.png "TextFormatter01")  
Interakcja między aplikacją a obiekt TextFormatter  
  
 Program formatujący tekstu służy do pobierania wierszy tekstu sformatowanego w sklepie tekst, który jest implementacją <xref:System.Windows.Media.TextFormatting.TextSource>. Jest to realizowane przez utworzenie wystąpienia programu formatującego tekstu przy użyciu <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A> metody. Ta metoda tworzy wystąpienie elementu formatującego tekstu i ustawia maksymalną wiersza wartości szerokości i wysokości. Natychmiast po utworzeniu wystąpienia programu formatującego tekst procesu tworzenia wiersza jest uruchamiana przez wywołanie <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> metody. <xref:System.Windows.Media.TextFormatting.TextFormatter>wywołuje w źródle tekstu do pobierania tekstu i formatowania parametry serii tekstu formularza wiersza.  
  
 W poniższym przykładzie przedstawiono proces formatowania magazynu tekstu. <xref:System.Windows.Media.TextFormatting.TextFormatter> Obiekt jest używany do pobierania wierszy tekstu w sklepie tekstu, a następnie sformatować wiersza tekstu do rysowania do <xref:System.Windows.Media.DrawingContext>.  
  
 [!code-csharp[TextFormatterExample#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## <a name="implementing-the-client-text-store"></a>Implementacja magazynu tekst klienta  
 Rozszerzając aparat formatowania tekstu, są wymagane do wdrożenia i zarządzać wszystkimi aspektami magazynu tekstu. To nie jest prosta zadań. Magazyn tekst jest odpowiedzialny za śledzenie tekstu Uruchom właściwości, właściwości osadzonych obiektów i inne podobne zawartości. Zapewnia także program formatujący tekstu z poszczególnymi <xref:System.Windows.Media.TextFormatting.TextRun> obiektów, które używa programu formatującego tekst w celu utworzenia <xref:System.Windows.Media.TextFormatting.TextLine> obiektów.  
  
 Do obsługi wirtualizacji magazynu tekstu, magazynie tekst musi pochodzić z <xref:System.Windows.Media.TextFormatting.TextSource>. <xref:System.Windows.Media.TextFormatting.TextSource>definiuje metodę, którą program formatujący tekst używa do pobrania uruchomienia tekstu w sklepie tekstu. <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>jest używany w formatowaniu wiersza uruchamia metodę używaną przez program formatujący tekstu do pobierania tekstu. Wywołanie <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> wielokrotnie zostało utworzone przez program formatujący tekstu, dopóki nie wystąpi jedno z następujących warunków:  
  
-   A <xref:System.Windows.Media.TextFormatting.TextEndOfLine> lub zwracany jest podklasą klasy.  
  
-   Skumulowany szerokość uruchomienia tekstu przekracza szerokość linii maksymalny określony w albo wywołanie w celu utworzenia programu formatującego tekstu lub wywołanie elementu formatującego tekst <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> metody.  
  
-   A [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] sekwencji znaków nowego wiersza, takie jak "CF", "LF" lub "CRLF", jest zwracana.  
  
<a name="section4"></a>   
## <a name="providing-text-runs"></a>Zapewnianie uruchomienia tekstu  
 Podstawowy proces formatowania tekstu jest interakcji między program formatujący tekstu, a także przechowywać tekstu. Implementacji <xref:System.Windows.Media.TextFormatting.TextSource> zawiera element formatujący tekst <xref:System.Windows.Media.TextFormatting.TextRun> obiektów i właściwości, z którymi do formatowania tekstu jest uruchamiana. Ta interakcja jest obsługiwany przez <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metodę, która jest wywoływana przez element formatujący tekstu.  
  
 W poniższej tabeli przedstawiono niektóre z wstępnie zdefiniowane <xref:System.Windows.Media.TextFormatting.TextRun> obiektów.  
  
|Typ TextRun|Użycie|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|Tekst specjalne Uruchom używany do przekazania reprezentację symboli znak program formatujący tekstu.|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|Umożliwia dostarczanie zawartości, w których pomiaru, testowanie trafień Uruchom specjalne tekstu i rysunku odbywa się w całości, takich jak przycisk lub obrazu w tekście.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|Tekst specjalne Uruchom używane w celu oznaczenia zakończenia linii.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|Tekst specjalne Uruchom używane w celu oznaczenia zakończenia akapitu.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|Tekst specjalne, uruchom używany do oznaczenia zakończenia segmentu, takich jak do końca zakresu wpływ poprzedniej <xref:System.Windows.Media.TextFormatting.TextModifier> Uruchom.|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|Tekst specjalne Uruchom używany do oznaczania zakres znaków ukryte.|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|Uruchamia specjalne tekst Uruchom używane do modyfikowania właściwości tekstu w swoim zakresie. Zakres obejmuje dalej dopasowywania <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> tekst Uruchom lub następnych <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>.|  
  
 Dowolnych predefiniowanych <xref:System.Windows.Media.TextFormatting.TextRun> może być podklasą klasy obiektów. Dzięki temu źródła Tekst zapewnienie uruchamia program formatujący tekstu z tekstem obejmujących danych niestandardowych.  
  
 W poniższym przykładzie pokazano <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metody. Magazyn ten tekst zwraca <xref:System.Windows.Media.TextFormatting.TextRun> obiektów do tekstu elementu formatującego do przetwarzania.  
  
 [!code-csharp[TextFormatterExample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
>  W tym przykładzie store tekstu zapewnia te same właściwości tekstu, aby cały tekst. Zaawansowane tekst, który magazynów należy zaimplementować własnych span zarządzania, aby zezwalać na znaki poszczególnych ma inne właściwości.  
  
<a name="section5"></a>   
## <a name="specifying-formatting-properties"></a>Określanie właściwości formatowania  
 <xref:System.Windows.Media.TextFormatting.TextRun>obiekty są sformatowane przy użyciu właściwości udostępniane przez sklep tekstu. Te właściwości są dostępne w dwóch typów <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> i <xref:System.Windows.Media.TextFormatting.TextRunProperties>. <xref:System.Windows.Media.TextFormatting.TextParagraphProperties>takie jak obsługa właściwości włącznie <xref:System.Windows.TextAlignment> i <xref:System.Windows.FlowDirection>. <xref:System.Windows.Media.TextFormatting.TextRunProperties>nie ma właściwości, które mogą być różne dla każdego tekstu Uruchom akapitu, takie jak pędzla pierwszego planu <xref:System.Windows.Media.Typeface>i rozmiar czcionki. Wdrażanie niestandardowych akapitu i tekstu niestandardowego Uruchom typy właściwości, aplikacji, należy utworzyć klasy, które pochodzą z <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> i <xref:System.Windows.Media.TextFormatting.TextRunProperties> odpowiednio.  
  
## <a name="see-also"></a>Zobacz też  
 [Typografia na platformie WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [Dokumentów na platformie WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
