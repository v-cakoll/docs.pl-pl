---
title: "Przegląd Strukturyzowana nawigacja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- structured navigation [WPF]
ms.assetid: 025d30ef-fec5-436d-ad7a-5d5483331c26
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f9d20fb5b16fbf44bdf8431ae32afee105af7676
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="structured-navigation-overview"></a>Przegląd Strukturyzowana nawigacja
Zawartość, która może być obsługiwany przez [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)], <xref:System.Windows.Controls.Frame>, lub <xref:System.Windows.Navigation.NavigationWindow> składa się z stron, które mogą zostać zidentyfikowane przez pakiet [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] i nawigacji do hiperłącza. Struktura stron i sposoby, w którym one może zostać przesłane, zgodnie z definicją hiperłącza, jest określany jako topologii nawigacji. Takie topologii pasujące do różnych typów aplikacji, zwłaszcza tych, które przeglądanie dokumentów. Dla takich aplikacji użytkownika można przejść z jednej strony na innej stronie bez dowolnej stronie znajomości o innych.  
  
 Jednak inne typy aplikacji zawierają stron, które trzeba wiedzieć, kiedy mają zostać nawigację między. Rozważmy na przykład aplikacji kadr, która zawiera jedną stronę, aby wyświetlić listę wszystkich pracowników w organizacji — na stronie "Listy pracowników". Ta strona może także umożliwić użytkownikom dodawanie nowych pracowników, klikając hiperłącza. Po kliknięciu strony przechodzi do strony "Dodaj pracownika", do zbierania szczegóły nowych pracowników i zwraca je do strony "Listy pracowników" do tworzenia nowych pracowników i aktualizacji listy. Ten styl nawigacji jest podobny do wywoływania metody do wykonywania niektórych przetwarzania i zwracać wartość, która jest nazywany programowania structured. W efekcie ten styl nawigacji nosi nazwę *strukturę nawigacji*.  
  
 <xref:System.Windows.Controls.Page> Klasa nie implementuje obsługę strukturze nawigacji. Zamiast tego <xref:System.Windows.Navigation.PageFunction%601> pochodną klasy <xref:System.Windows.Controls.Page> i rozszerza ją z konstrukcji podstawowe, wymagane w strukturze nawigacji. W tym temacie pokazano, jak nawiązać za pomocą strukturze nawigacji <xref:System.Windows.Navigation.PageFunction%601>.  
  
 
  
<a name="Structured_Navigation"></a>   
## <a name="structured-navigation"></a>Nawigacja w strukturze  
 Po jednej stronie innej strony w strukturze nawigacji, wymagane są niektóre lub wszystkie z następujących problemów:  
  
-   Strona wywoływania przechodzi do strony o nazwie, opcjonalnie przekazywanie parametrów wymaganych przez stronę wywołany.  
  
-   Stronie wywołane po zakończeniu przez użytkownika za pomocą wywołania strony, zwraca specjalnie do wywoływania strony, opcjonalnie:  
  
    -   Zwraca informacje o stanie, który opisuje sposób wywoływania strony zostało wykonane (na przykład, czy użytkownik po naciśnięciu przycisku OK lub przycisk Anuluj).  
  
    -   Zwraca te dane zebrane przez użytkownika (na przykład nowych pracowników szczegóły).  
  
-   Po powrocie do strony o nazwie wywoływania strony wywołana strona zostanie usunięty z historii przeglądania do izolowania jedno wystąpienie o nazwie strony z innej.  
  
 Te zachowania są zilustrowane w poniższym rysunku.  
  
 ![Przepływ między wywoływania i strony o nazwie](../../../../docs/framework/wpf/app-development/media/structurednavigationoverviewfigure1.png "StructuredNavigationOverviewFigure1")  
  
 Takie zachowanie można wdrożyć przy użyciu <xref:System.Windows.Navigation.PageFunction%601> jako o nazwie strony.  
  
<a name="Structured_Navigation_with_PageFunction"></a>   
## <a name="structured-navigation-with-pagefunction"></a>Strukturalne nawigacja z użyciem PageFunction  
 W tym temacie przedstawiono sposób wdrożenia podstawowa mechanika strukturze nawigacji obejmujące jeden <xref:System.Windows.Navigation.PageFunction%601>. W tym przykładzie <xref:System.Windows.Controls.Page> wywołania <xref:System.Windows.Navigation.PageFunction%601> uzyskanie <xref:System.String> wartość od użytkownika, a następnie przywrócić go.  
  
### <a name="creating-a-calling-page"></a>Tworzenie strony wywołania  
 Strona, która wywołuje <xref:System.Windows.Navigation.PageFunction%601> mogą być <xref:System.Windows.Controls.Page> lub <xref:System.Windows.Navigation.PageFunction%601>. W tym przykładzie jest <xref:System.Windows.Controls.Page>, jak pokazano w poniższym kodzie.  
  
 [!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup1)]  
[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup2)]  
  
 [!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind1)]
 [!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind1)]  
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind2)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind2)]  
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind3)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind3)]  
  
### <a name="creating-a-page-function-to-call"></a>Tworzenie funkcji strony, aby wywołać  
 Ponieważ wywoływania strony wywołana strona służy do zbierania i zwracać dane z użytkownikiem, <xref:System.Windows.Navigation.PageFunction%601> jest zaimplementowany jako klasy ogólnej, którego argument typu określa typ o nazwie strony, którą będzie zwracać wartość. Poniższy kod przedstawia implementację początkowej wywołane strony przy użyciu <xref:System.Windows.Navigation.PageFunction%601>, która zwraca wartość <xref:System.String>.  
  
 [!code-xaml[StructuredNavigationSample#CalledPageFunctionMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml#calledpagefunctionmarkup)]  
  
 [!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind1)]
 [!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind1)]  
[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind2)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind2)]  
  
 Deklaracja <xref:System.Windows.Navigation.PageFunction%601> jest podobny do deklaracji <xref:System.Windows.Controls.Page> z uwzględnieniem argumentów typu. Jak widać w przykładzie kodu, argumenty typu są określone w obu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników, przy użyciu `x:TypeArguments` atrybut i kodem, przy użyciu składni argumentu typu ogólnego standardowa.  
  
 Nie trzeba używać tylko [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] klas jako argumentów typu. A <xref:System.Windows.Navigation.PageFunction%601> może być wywołane w celu zbierania danych specyficznego dla domeny, która jest pobieranej jako typu niestandardowego. Poniższy kod przedstawia sposób użycia niestandardowego typu jako argumentu typu dla <xref:System.Windows.Navigation.PageFunction%601>.  
  
 [!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode1)]
 [!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode1)]  
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode2)]  
  
 [!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup1)]  
[!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup2)]  
  
 [!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind1)]
 [!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind1)]  
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind2)]  
  
 Argumentów typu dla <xref:System.Windows.Navigation.PageFunction%601> stanowią podstawę dla komunikacji między wywoływania strony i stroną wywoływaną, które opisano w poniższych sekcjach.  
  
 Jak można zauważyć, typ, który jest identyfikowany z deklaracją <xref:System.Windows.Navigation.PageFunction%601> odgrywa ważną rolę w zwracać dane z <xref:System.Windows.Navigation.PageFunction%601> do wywoływania strony.  
  
### <a name="calling-a-pagefunction-and-passing-parameters"></a>Wywołuje element PageFunction oraz przekazywanie parametrów  
 Aby wywołać strony, strony wywoływania musi wystąpienia wywoływanego strony i przejdź do przy użyciu <xref:System.Windows.Navigation.NavigationService.Navigate%2A> metody. Dzięki temu wywoływania strony do przekazania do wywoływanego strony, takie jak wartości domyślne dla danych zbierana przez stronę o nazwie początkowe dane.  
  
 Poniższy kod przedstawia stronie wywoływane przy użyciu konstruktora innych niż domyślne, aby zaakceptować parametry ze strony wywołania.  
  
 [!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind1)]
 [!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind1)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind2)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind2)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind3)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind3)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind4)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind4)]  
  
 Poniższy kod przedstawia wywoływania obsługi strony <xref:System.Windows.Documents.Hyperlink.Click> zdarzenie <xref:System.Windows.Documents.Hyperlink> do wystąpienia o nazwie strony i przekaż go na wartość początkową ciągu.  
  
 [!code-xaml[StructuredNavigationSample#PassingDataMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#passingdatamarkup2)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind1)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind1)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind2)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind2)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind3)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind3)]  
  
 Nie jest wymagane do przekazania parametrów do strony o nazwie. Zamiast tego można wykonać następujące czynności:  
  
-   Na stronie wywołania:  
  
    1.  Utwórz wystąpienie o nazwie <xref:System.Windows.Navigation.PageFunction%601> za pomocą konstruktora domyślnego.  
  
    2.  Przechowywanie parametrów w <xref:System.Windows.Application.Properties%2A>.  
  
    3.  Przejdź do wywoływanego <xref:System.Windows.Navigation.PageFunction%601>.  
  
-   W nazwie <xref:System.Windows.Navigation.PageFunction%601>:  
  
    -   Pobieranie i użyj parametrów przechowywanych w <xref:System.Windows.Application.Properties%2A>.  
  
 Jednak ponieważ pojawi się wkrótce, nadal konieczne użyjesz kodu wystąpienia i przejdź na stronę o nazwie służąca do gromadzenia danych zwróconych przez stronę o nazwie. Z tego powodu <xref:System.Windows.Navigation.PageFunction%601> musi znajdować się aktywności, w przeciwnym, następnym razem po przejściu do <xref:System.Windows.Navigation.PageFunction%601>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tworzy <xref:System.Windows.Navigation.PageFunction%601> przy użyciu domyślnego konstruktora.  
  
 Przed stroną wywoływaną może zwracać, jednak należy zwrócić dane, które mogą być pobierane przez stronę wywołującego.  
  
### <a name="returning-task-result-and-task-data-from-a-task-to-a-calling-page"></a>Zwracanie wyniku zadania i dane zadanie z zadaniem do strony wywołania  
 Gdy użytkownik zakończy, za pomocą strony wywołany, oznaczony w tym przykładzie, naciskając przycisk OK lub Anuluj przycisków, potrzeb wywołana strona do zwrócenia. Ponieważ wywołujący strony używane wywołane strony do zbierania danych od użytkownika, wywołujący strona wymaga dwóch typów informacji:  
  
1.  Określa, czy została anulowana przez użytkownika o nazwie strony (naciskając przycisk OK lub przycisk Anuluj w tym przykładzie). Dzięki temu wywoływania stronę, aby określić, czy do przetwarzania danych, które strony wywoływania zebranych od użytkownika.  
  
2.  Dane, które zostały dostarczone przez użytkownika.  
  
 Zwraca informacje, <xref:System.Windows.Navigation.PageFunction%601> implementuje <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> metody. Poniższy kod przedstawia sposób wywołania go.  
  
 [!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind1)]
 [!code-vb[StructuredNavigationSample#ReturnCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind1)]  
[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind2)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind2)]  
  
 W tym przykładzie użytkownik naciśnie przycisk Anuluj, wartość `null` jest zwracana do wywoływania strony. Jeśli zamiast tego naciśnięciu przycisku OK jest zwracana wartość ciągu podanego przez użytkownika. <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>jest `protected``virtual` metody należy wywołać, aby zwrócić dane do wywoływania strony. Danych musi być spakowany w wystąpieniu ogólnego <xref:System.Windows.Navigation.ReturnEventArgs%601> wartość typu, którego argument typu określa typ, który <xref:System.Windows.Navigation.ReturnEventArgs%601.Result%2A> zwraca. W ten sposób, przy deklarowaniu <xref:System.Windows.Navigation.PageFunction%601> z argumentem typu, jest zawarcie tej <xref:System.Windows.Navigation.PageFunction%601> zwróci wystąpienia typu określonego przez argument typu. W tym przykładzie argument typu i, w związku z tym, zwracana wartość jest typu <xref:System.String>.  
  
 Gdy <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> jest nazywany wywołujący musi strony jakiś sposób odbierania zwracanej wartości <xref:System.Windows.Navigation.PageFunction%601>. Z tego powodu <xref:System.Windows.Navigation.PageFunction%601> implementuje <xref:System.Windows.Navigation.PageFunction%601.Return> zdarzeń wywoływania stron do obsługi. Gdy <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> jest nazywany <xref:System.Windows.Navigation.PageFunction%601.Return> jest wywoływane, aby zarejestrować wywoływania strony z <xref:System.Windows.Navigation.PageFunction%601.Return> do odbioru powiadomienia.  
  
 [!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind1)]
 [!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind1)]  
[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind2)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind2)]  
  
### <a name="removing-task-pages-when-a-task-completes"></a>Usuwanie strony zadania po zakończeniu zadania  
 Kiedy zwraca stronę o nazwie, a użytkownik nie Anuluj o nazwie strony, strony wywoływania będzie przetwarzać dane, które zostało podane przez użytkownika i również zwracane z wywołanego strony. Uzyskiwanie danych w ten sposób jest zwykle izolowanego działanie; Po powrocie z wywołana strona wywoływania strony musi utworzyć i przejdź do nowej strony wywołania do przechwytywania danych.  
  
 Jednak chyba że wywołana strona zostanie usunięty z dziennika, użytkownik będzie można Przejdź wstecz do poprzedniego wystąpienia wywoływania strony. Czy <xref:System.Windows.Navigation.PageFunction%601> są przechowywane w dzienniku jest określany przez <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> właściwości. Domyślnie funkcja strony jest automatycznie usuwane podczas <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> nazywa się ponieważ <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> ma ustawioną wartość `true`. Aby zachować funkcja strony w historii nawigacji po <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> jest wywoływana, ustaw <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> do `false`.  
  
<a name="Other_Types_of_Structured_Navigation"></a>   
## <a name="other-types-of-structured-navigation"></a>Inne typy strukturalne nawigacji  
 W tym temacie przedstawiono użycie najprostsze <xref:System.Windows.Navigation.PageFunction%601> do obsługi wywołania/powrotu strukturę nawigacji. Ta podstawa pozwala tworzyć bardziej złożone typy strukturalne nawigacji.  
  
 Na przykład czasami wiele stron są wymagane przez wywołanie strony można zebrać wystarczającej ilości danych przez użytkownika lub wykonać zadania. Używanie wielu stron nazywa się "Kreator".  
  
 W pozostałych przypadkach aplikacje mogą mieć topologie złożonych nawigacji, które są zależne od strukturze nawigacji sprawnego działania. Aby uzyskać więcej informacji, zobacz [— omówienie topologii nawigacji](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Navigation.PageFunction%601>  
 <xref:System.Windows.Navigation.NavigationService>  
 [Topologia nawigacji — omówienie](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md)
