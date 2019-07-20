---
title: Przegląd Strukturyzowana nawigacja
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- structured navigation [WPF]
ms.assetid: 025d30ef-fec5-436d-ad7a-5d5483331c26
ms.openlocfilehash: 8760c847d9e73fdff9f10f0dfa55a6c674021667
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364176"
---
# <a name="structured-navigation-overview"></a>Przegląd Strukturyzowana nawigacja

Zawartość, która może być hostowana [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]przez, <xref:System.Windows.Controls.Frame>a lub, <xref:System.Windows.Navigation.NavigationWindow> składa się ze stron, które mogą być identyfikowane przez [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] program lub przez hiperłącza. Struktura stron i sposoby, w których można przechodzić, zgodnie z definicją za pomocą hiperłączy, jest znana jako topologia nawigacji. Taka topologia oferuje różne typy aplikacji, szczególnie te, które poruszają się za pomocą dokumentów. W przypadku takich aplikacji użytkownik może nawigować z jednej strony na inną stronę bez konieczności poznania innych elementów.

Jednak inne typy aplikacji mają strony, które muszą wiedzieć, kiedy zostały przejściu między. Rozważmy na przykład aplikację kadr, która ma jedną stronę, aby wyświetlić listę wszystkich pracowników w organizacji — stronę "Lista pracowników". Na tej stronie można również zezwolić użytkownikom na dodawanie nowego pracownika przez kliknięcie hiperłącza. Po kliknięciu strony przechodzi do strony "Dodaj pracownika", aby zebrać szczegóły nowego pracownika i zwrócić je do strony "Wyświetl pracowników", aby utworzyć nowego pracownika i zaktualizować listę. Ten styl nawigacji jest podobny do wywołania metody wykonywania niektórych operacji przetwarzania i zwracania wartości, która jest znana jako programowanie strukturalne. W związku z tym styl nawigacji jest znany jako *Nawigacja strukturalna*.

<xref:System.Windows.Controls.Page> Klasa nie implementuje obsługi nawigacji strukturalnej. Zamiast tego <xref:System.Windows.Controls.Page> Klasa dziedziczy z i rozszerza ją z podstawowymi konstrukcjami wymaganymi do nawigacji strukturalnej. <xref:System.Windows.Navigation.PageFunction%601> W tym temacie przedstawiono sposób ustanawiania strukturalnej <xref:System.Windows.Navigation.PageFunction%601>nawigacji przy użyciu programu.

<a name="Structured_Navigation"></a>

## <a name="structured-navigation"></a>Nawigacja strukturalna

Gdy jedna strona wywołuje inną stronę w nawigacji strukturalnej, wymagane są niektóre lub wszystkie następujące zachowania:

- Strona wywołująca nawiguje do wywoływanej strony, opcjonalnie przekazując parametry wymagane przez wywoływaną stronę.

- Wywoływana Strona, gdy użytkownik zakończył korzystanie z strony wywołującej, wraca do strony wywołującej, opcjonalnie:

  - Zwracanie informacji o stanie opisujących sposób ukończenia strony wywołującej (na przykład czy użytkownik naciśnie przycisk OK lub przycisk Anuluj).

  - Zwraca te dane, które zostały zebrane od użytkownika (na przykład nowe szczegóły pracownika).

- Gdy strona wywołująca wraca do wywoływanej strony, wywoływana strona jest usuwana z historii nawigacji, aby odizolować jedno wystąpienie wywoływanej strony od innej.

Te zachowania są zilustrowane na poniższej ilustracji:

![Zrzut ekranu przedstawia przepływ między stroną wywołującą i wywoływaną stroną.](./media/structured-navigation-overview/flow-between-calling-page-called-page.png)

Te zachowania można zaimplementować przy użyciu <xref:System.Windows.Navigation.PageFunction%601> jako strony wywoływanej.

<a name="Structured_Navigation_with_PageFunction"></a>

## <a name="structured-navigation-with-pagefunction"></a>Nawigacja strukturalna przy użyciu PageFunction

W tym temacie pokazano, jak zaimplementować podstawową Mechanics nawigacyjną strukturalną obejmującą <xref:System.Windows.Navigation.PageFunction%601>pojedynczą. W tym przykładzie <xref:System.Windows.Controls.Page> wywołanie a <xref:System.Windows.Navigation.PageFunction%601> , aby uzyskać <xref:System.String> wartość od użytkownika i zwrócić go.

### <a name="creating-a-calling-page"></a>Tworzenie strony wywołującej

Strona, która wywołuje <xref:System.Windows.Navigation.PageFunction%601> program, może być <xref:System.Windows.Controls.Page> albo lub <xref:System.Windows.Navigation.PageFunction%601>. W tym przykładzie jest <xref:System.Windows.Controls.Page>to, jak pokazano w poniższym kodzie.

[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup1)]
[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup2)]

[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind1)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind1)]
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind2)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind2)]
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind3)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind3)]

### <a name="creating-a-page-function-to-call"></a>Tworzenie funkcji strony do wywołania

Ze względu na to, że strona wywołująca może używać wywoływanej strony do zbierania i <xref:System.Windows.Navigation.PageFunction%601> zwracania danych od użytkownika, jest implementowana jako Klasa ogólna, której argument typu określa typ wartości zwracanej przez wywoływana strona. Poniższy kod pokazuje początkową implementację wywoływanej strony przy użyciu <xref:System.Windows.Navigation.PageFunction%601>, która <xref:System.String>zwraca.

[!code-xaml[StructuredNavigationSample#CalledPageFunctionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml#calledpagefunctionmarkup)]

[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind1)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind1)]
[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind2)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind2)]

Deklaracja a <xref:System.Windows.Navigation.PageFunction%601> jest podobna do deklaracji a <xref:System.Windows.Controls.Page> z dodaniem argumentów typu. Jak widać w przykładzie kodu, argumenty typu są określane w obu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znakach, `x:TypeArguments` przy użyciu atrybutu i kodu, przy użyciu standardowej składni argumentu typu ogólnego.

Nie trzeba używać tylko .NET Framework klas jako argumentów typu. <xref:System.Windows.Navigation.PageFunction%601> Może zostać wywołana w celu zebrania danych specyficznych dla domeny, które są abstrakcyjne jako typ niestandardowy. Poniższy kod pokazuje, jak używać typu niestandardowego jako argumentu typu dla <xref:System.Windows.Navigation.PageFunction%601>.

[!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode1)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode1)]
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode2)]

[!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup1)]
[!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup2)]

[!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind1)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind1)]
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind2)]

Argumenty typu dla <xref:System.Windows.Navigation.PageFunction%601> stanowią podstawę komunikacji między stroną wywołującą a wywoływaną stroną, która została omówiona w poniższych sekcjach.

Jak widać, typ, który jest identyfikowany z deklaracją <xref:System.Windows.Navigation.PageFunction%601> , odgrywa ważną rolę w zwracaniu danych <xref:System.Windows.Navigation.PageFunction%601> z do strony wywołującej.

### <a name="calling-a-pagefunction-and-passing-parameters"></a>Wywoływanie PageFunction i przekazywanie parametrów

Aby wywołać stronę, wywołująca musi utworzyć wystąpienie wywoływanej strony i przejść do niej przy użyciu <xref:System.Windows.Navigation.NavigationService.Navigate%2A> metody. Umożliwia to stronie wywołującej przekazywanie początkowych danych do wywoływanej strony, takich jak wartości domyślne dla danych zbieranych przez wywoływaną stronę.

Poniższy kod przedstawia wywoływanej strony z konstruktorem bez parametrów, aby akceptować parametry na stronie wywołującej.

[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind1)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind1)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind2)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind2)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind3)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind3)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind4)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind4)]

Poniższy kod pokazuje stronę wywołującą obsługującą <xref:System.Windows.Documents.Hyperlink.Click> zdarzenie <xref:System.Windows.Documents.Hyperlink> w celu utworzenia wystąpienia wywoływanej strony i przekazania jej początkowej wartości ciągu.

[!code-xaml[StructuredNavigationSample#PassingDataMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#passingdatamarkup2)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind1)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind1)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind2)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind2)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind3)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind3)]

Nie jest wymagane przekazywanie parametrów do wywoływanej strony. Zamiast tego można wykonać następujące czynności:

- Na stronie wywołującej:

  1. Utwórz wystąpienie wywołane <xref:System.Windows.Navigation.PageFunction%601> przy użyciu konstruktora bez parametrów.

  2. Parametry są przechowywane w <xref:System.Windows.Application.Properties%2A>.

  3. Przejdź do wywoływanej <xref:System.Windows.Navigation.PageFunction%601>metody.

- Od wywołanego <xref:System.Windows.Navigation.PageFunction%601>:

  - Pobierz i Użyj parametrów przechowywanych w <xref:System.Windows.Application.Properties%2A>.

Mimo że zobaczysz się wkrótce, będziesz potrzebować użyć kodu do utworzenia wystąpienia i przejścia do wywoływanej strony, aby zebrać dane zwrócone przez wywoływaną stronę. Z <xref:System.Windows.Navigation.PageFunction%601> tego powodu należy zachować aktywność; w przeciwnym razie przy następnym przejściu <xref:System.Windows.Navigation.PageFunction%601>do, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tworzy wystąpienie <xref:System.Windows.Navigation.PageFunction%601> przy użyciu konstruktora bez parametrów.

Zanim wywoływana strona będzie mogła zwracać, musi zwrócić dane, które mogą być pobierane przez stronę wywołującą.

### <a name="returning-task-result-and-task-data-from-a-task-to-a-calling-page"></a>Zwracanie danych wynikowych zadania i zadania z zadania na stronę wywołującą

Gdy użytkownik zakończył korzystanie z wywoływanej strony, w tym przykładzie, naciskając przycisk OK lub Anuluj, wywoływana strona musi zwrócić. Ze względu na to, że strona wywołująca używa wywoływanej strony do zbierania danych od użytkownika, na stronie wywołującej wymagane są dwa rodzaje informacji:

1. Czy użytkownik anulował wywoływaną stronę (naciskając przycisk OK lub przycisk Anuluj w tym przykładzie). Dzięki temu na stronie wywołującej można określić, czy przetwarzać dane wywoływane przez stronę wywołującą od użytkownika.

2. Dane dostarczone przez użytkownika.

Aby zwrócić informacje, <xref:System.Windows.Navigation.PageFunction%601> <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> implementuje metodę. Poniższy kod przedstawia sposób wywoływania go.

[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind1)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind1)]
[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind2)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind2)]

W tym przykładzie, jeśli użytkownik naciśnie przycisk Anuluj, wartość `null` jest zwracana do strony wywołującej. Jeśli zamiast tego przycisk OK zostanie naciśnięty, zwracana jest wartość ciągu podana przez użytkownika. <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>`protected virtual` to metoda wywoływana w celu zwrócenia danych na stronę wywołującą. Dane muszą być spakowane w wystąpieniu typu ogólnego <xref:System.Windows.Navigation.ReturnEventArgs%601> , którego argument typu określa typ <xref:System.Windows.Navigation.ReturnEventArgs%601.Result%2A> zwracanej wartości. W ten sposób, gdy deklarujesz <xref:System.Windows.Navigation.PageFunction%601> przy użyciu określonego argumentu typu, stwierdzasz <xref:System.Windows.Navigation.PageFunction%601> , że zwróci wystąpienie typu, który jest określony przez argument typu. W tym przykładzie argument typu i, w związku z tym, zwraca wartość typu <xref:System.String>.

Gdy <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> jest wywoływana, Strona wywołująca potrzebuje pewnego sposobu na otrzymanie wartości zwracanej przez <xref:System.Windows.Navigation.PageFunction%601>. Z tego powodu <xref:System.Windows.Navigation.PageFunction%601> <xref:System.Windows.Navigation.PageFunction%601.Return> implementuje zdarzenie dla wywoływania stron do obsługi. Gdy <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> jest wywoływany <xref:System.Windows.Navigation.PageFunction%601.Return> , jest wywoływany, więc strona <xref:System.Windows.Navigation.PageFunction%601.Return> wywołująca może zarejestrować się w usłudze, aby otrzymać powiadomienie.

[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind1)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind1)]
[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind2)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind2)]

### <a name="removing-task-pages-when-a-task-completes"></a>Usuwanie stron zadań po zakończeniu zadania

Gdy wywoływana strona zwraca wartość, a użytkownik nie anulował wywoływanej strony, wywołujący przetworzy dane dostarczone przez użytkownika, a także zwraca z wywoływanej strony. Pozyskiwanie danych w ten sposób jest zazwyczaj izolowaną aktywnością; gdy wywoływana strona zwraca, Strona wywołująca musi utworzyć nową stronę wywołującą i przejść do niej, aby przechwycić więcej danych.

Jednak jeśli nazwa wywoływanej strony nie zostanie usunięta z dziennika, użytkownik będzie mógł przejść z powrotem do poprzedniego wystąpienia strony wywołującej. Czy wartość <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> jest zachowywana w dzienniku jest określana przez właściwość. <xref:System.Windows.Navigation.PageFunction%601> Domyślnie funkcja strony jest automatycznie usuwana, gdy <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> jest wywoływana, ponieważ <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> jest ustawiona na. `true` Aby zachować funkcję strony w historii nawigacji po <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> wywołaniu, ustaw <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> jako `false`.

<a name="Other_Types_of_Structured_Navigation"></a>

## <a name="other-types-of-structured-navigation"></a>Inne typy nawigacji strukturalnej

W tym temacie przedstawiono najbardziej podstawowe użycie <xref:System.Windows.Navigation.PageFunction%601> programu do obsługi wywoływania/zwracania strukturalnej nawigacji. Ta podstawa zapewnia możliwość tworzenia bardziej złożonych typów nawigacji strukturalnej.

Na przykład czasami wiele stron jest wymaganych przez wywołującą stronę do zbierania wystarczającej ilości danych od użytkownika lub do wykonania zadania. Korzystanie z wielu stron jest nazywane "kreatorem".

W innych przypadkach aplikacje mogą mieć złożone topologie nawigacji, które zależą od współdziałania strukturalnej nawigacji. Aby uzyskać więcej informacji, zobacz [Omówienie topologii nawigacji](navigation-topologies-overview.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [Topologia nawigacji — omówienie](navigation-topologies-overview.md)
