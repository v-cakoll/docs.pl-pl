---
title: Przegląd Strukturyzowana nawigacja
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- structured navigation [WPF]
ms.assetid: 025d30ef-fec5-436d-ad7a-5d5483331c26
ms.openlocfilehash: 2264686f34123e74bf7d24ce80877742d952f35d
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45617412"
---
# <a name="structured-navigation-overview"></a>Przegląd Strukturyzowana nawigacja
Zawartość, która może być obsługiwany przez [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)], <xref:System.Windows.Controls.Frame>, lub <xref:System.Windows.Navigation.NavigationWindow> składa się z stron, zidentyfikowane przez pakiet [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] i przejście przez hiperłącza. Struktura stron i sposoby, w którym ich można nawigować, zgodnie z definicją hiperłącza, jest określany jako topologia nawigacji. Takie topologii pasujące do różnych typów aplikacji, zwłaszcza tych, które nawigowania w dokumentach. Na potrzeby takich aplikacji użytkownik może przejść z jednej strony do innej strony bez dowolnej stronie znajomości o innych.  
  
 Jednak inne typy aplikacji ma stron, które trzeba wiedzieć, kiedy zostały przejście między. Rozważmy na przykład aplikacja zarządzania zasobami ludzkimi, która ma jedną stronę, aby wyświetlić listę wszystkich pracowników w organizacji — na stronie "Listy Employees". Na tej stronie może także umożliwić użytkownikom dodawanie nowych pracowników, klikając hiperłącze. Po kliknięciu strony powoduje przejście do strony "Dodaj Employee" w taki sposób, aby zebrać szczegółowe dane nowych pracownika i przywrócić je do strony "Listy Employees" do tworzenia nowych pracowników i aktualizowania listy. Ten styl nawigacji jest podobny do wywoływania metody do przetworzenia i zwracają wartość, który jest znany jako programowania ze strukturą. W efekcie ten styl nawigacji jest znany jako *strukturę nawigacji*.  
  
 <xref:System.Windows.Controls.Page> Klasa nie implementuje obsługę strukturyzowana Nawigacja. Zamiast tego <xref:System.Windows.Navigation.PageFunction%601> klasa pochodzi od <xref:System.Windows.Controls.Page> i rozszerza je z podstawowymi konstrukcjami, które są wymagane dla strukturyzowana Nawigacja. W tym temacie pokazano, jak nawiązać strukturyzowana Nawigacja przy użyciu <xref:System.Windows.Navigation.PageFunction%601>.  
  
 
  
<a name="Structured_Navigation"></a>   
## <a name="structured-navigation"></a>Strukturyzowana Nawigacja  
 Gdy jedna strona wywołuje innej strony w strukturyzowana Nawigacja, wymagane są niektóre lub wszystkie z następujących problemów:  
  
-   Strony wywołania powoduje przejście do strony o nazwie, opcjonalnie przekazując parametrów wymaganych przez stronę o nazwie.  
  
-   Stronę o nazwie po ukończeniu przez użytkownika, za pomocą strony wywołania zwraca specjalnie do wywoływania strony, opcjonalnie:  
  
    -   Zwraca informacje o stanie, który opisuje sposób wywoływania strony zostało zakończone (na przykład, czy użytkownik nacisnął przycisk OK lub przycisk Anuluj).  
  
    -   Zwracanie danych zebranych od użytkownika (na przykład nowe szczegóły pracowników).  
  
-   Po powrocie do strony o nazwie wywoływania strony strony o nazwie zostanie usunięty z historii przeglądania do izolowania jedno wystąpienie o nazwie strony z innego.  
  
 Te zachowania zostały przedstawione w poniższej ilustracji.  
  
 ![Przepływ między wywoływania i strony o nazwie](../../../../docs/framework/wpf/app-development/media/structurednavigationoverviewfigure1.png "StructuredNavigationOverviewFigure1")  
  
 Te zachowania można wdrożyć przy użyciu <xref:System.Windows.Navigation.PageFunction%601> jako o nazwie strony.  
  
<a name="Structured_Navigation_with_PageFunction"></a>   
## <a name="structured-navigation-with-pagefunction"></a>Strukturyzowana Nawigacja przy użyciu PageFunction  
 W tym temacie pokazano, jak zaimplementować podstawowa mechanika strukturyzowana Nawigacja obejmujące jeden <xref:System.Windows.Navigation.PageFunction%601>. W tym przykładzie <xref:System.Windows.Controls.Page> wywołania <xref:System.Windows.Navigation.PageFunction%601> można pobrać <xref:System.String> wartości przez użytkownika i przywrócić go.  
  
### <a name="creating-a-calling-page"></a>Tworzenie strony wywołania  
 Strona, która wywołuje <xref:System.Windows.Navigation.PageFunction%601> może być <xref:System.Windows.Controls.Page> lub <xref:System.Windows.Navigation.PageFunction%601>. W tym przykładzie jest <xref:System.Windows.Controls.Page>, jak pokazano w poniższym kodzie.  
  
 [!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup1)]  
[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup2)]  
  
 [!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind1)]
 [!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind1)]  
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind2)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind2)]  
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind3)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind3)]  
  
### <a name="creating-a-page-function-to-call"></a>Tworzenie funkcji strony do wywołania  
 Ponieważ wywoływania strony o nazwie strona służy do zbierania i zwrócić dane od użytkownika, <xref:System.Windows.Navigation.PageFunction%601> jest implementowany jako klasy ogólnej, którego argument typu określa typ wartości, który zwraca stronę o nazwie. Poniższy kod przedstawia wstępne wdrożenie funkcji o nazwie strony, <xref:System.Windows.Navigation.PageFunction%601>, co powoduje zwrócenie <xref:System.String>.  
  
 [!code-xaml[StructuredNavigationSample#CalledPageFunctionMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml#calledpagefunctionmarkup)]  
  
 [!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind1)]
 [!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind1)]  
[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind2)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind2)]  
  
 Deklaracja <xref:System.Windows.Navigation.PageFunction%601> jest podobny do deklaracji <xref:System.Windows.Controls.Page> dodając argumentów typu. Jak widać w przykładzie kodu, argumenty typu są określone w obu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników, za pomocą `x:TypeArguments` atrybut i związane z kodem, przy użyciu składni argumentów standardowym typu rodzajowego.  
  
 Nie trzeba używać tylko [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] klasy jako argumentów typu. Element <xref:System.Windows.Navigation.PageFunction%601> może być wywołane w celu zbierania danych specyficznych dla domeny, które jest wyodrębniony jako typ niestandardowy. Poniższy kod przedstawia sposób użycia typ niestandardowy typ argumentu dla <xref:System.Windows.Navigation.PageFunction%601>.  
  
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
  
 Argumenty typu <xref:System.Windows.Navigation.PageFunction%601> stanowią podstawę dla komunikacji między stroną wywoływania i stronę o nazwie, które zostały omówione w poniższych sekcjach.  
  
 Jak można zauważyć, typ, który jest identyfikowany za pomocą deklaracji <xref:System.Windows.Navigation.PageFunction%601> odgrywa ważną rolę w zwracający dane z <xref:System.Windows.Navigation.PageFunction%601> do wywoływania strony.  
  
### <a name="calling-a-pagefunction-and-passing-parameters"></a>Wywoływanie PageFunction i przekazywanie parametrów  
 Aby wywołać strony, strony wywoływania musi tworzyć wystąpienie strony o nazwie i przejdź do niego przy użyciu <xref:System.Windows.Navigation.NavigationService.Navigate%2A> metody. Dzięki temu wywoływania strony do przekazania danych początkowych do strony o nazwie, takie jak wartości domyślne dla dane są zbierane przez stronę o nazwie.  
  
 Poniższy kod przedstawia stronę o nazwie za pomocą konstruktora innych niż domyślne, aby akceptował parametry ze strony wywołania.  
  
 [!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind1)]
 [!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind1)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind2)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind2)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind3)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind3)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind4)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind4)]  
  
 Poniższy kod przedstawia wywoływania obsługi strony <xref:System.Windows.Documents.Hyperlink.Click> zdarzenia <xref:System.Windows.Documents.Hyperlink> do tworzenia instancji o nazwie stronę i przekaż go na wartość początkową ciągu.  
  
 [!code-xaml[StructuredNavigationSample#PassingDataMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#passingdatamarkup2)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind1)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind1)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind2)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind2)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind3)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind3)]  
  
 Nie jest wymagane w celu przekazania parametrów do strony o nazwie. Zamiast tego można wykonać następujące czynności:  
  
-   Ze strony wywołania:  
  
    1.  Wystąpienia o nazwie <xref:System.Windows.Navigation.PageFunction%601> przy użyciu domyślnego konstruktora.  
  
    2.  Store parametrów w <xref:System.Windows.Application.Properties%2A>.  
  
    3.  Przechodzenie do wywoływanego <xref:System.Windows.Navigation.PageFunction%601>.  
  
-   Z o nazwie <xref:System.Windows.Navigation.PageFunction%601>:  
  
    -   Pobrać i używać parametrów przechowywanych w <xref:System.Windows.Application.Properties%2A>.  
  
 Jednak ponieważ pojawi się wkrótce, nadal konieczne użyjesz kodu do tworzenia instancji i przejdź do strony o nazwie do zbierania danych zwracanych przez stronę o nazwie. Z tego powodu <xref:System.Windows.Navigation.PageFunction%601> musi znajdować się aktywny; w przeciwnym razie, przy następnym przejściu do sekcji <xref:System.Windows.Navigation.PageFunction%601>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tworzy <xref:System.Windows.Navigation.PageFunction%601> przy użyciu domyślnego konstruktora.  
  
 Zanim strony o nazwie może zwracać, jednak musi zwrócić dane, które mogą być pobierane przez wywołującego stronę.  
  
### <a name="returning-task-result-and-task-data-from-a-task-to-a-calling-page"></a>Zwracanie wyniku zadania i dane zadania z zadaniem do strony wywołania  
 Po użytkownik zakończył, za pomocą strony o nazwie, oznaczony w tym przykładzie, naciskając przycisk OK lub Anuluj przyciski, potrzeb wywołana strona do zwrócenia. Ponieważ wywołujący strony używane strony o nazwie do zbierania danych przez użytkownika, wywoływania strona wymaga dwóch typów informacji:  
  
1.  Czy użytkownik anulował strony o nazwie (przez naciśnięcie klawisza przycisk OK lub przycisk Anuluj, w tym przykładzie). Dzięki temu wywoływania stronę, aby ustalić, czy do przetwarzania danych, który wywoływania strony zebranych od użytkownika.  
  
2.  Dane, które zostało dostarczone przez użytkownika.  
  
 Aby zostały zwrócone informacje, <xref:System.Windows.Navigation.PageFunction%601> implementuje <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> metody. Poniższy kod przedstawia sposób wywołania go.  
  
 [!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind1)]
 [!code-vb[StructuredNavigationSample#ReturnCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind1)]  
[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind2)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind2)]  
  
 W tym przykładzie, jeśli użytkownik naciśnie przycisk Anuluj, wartość `null` jest zwracany do wywołującego strony. Jeśli zamiast tego naciśnięciu przycisku OK, zwracana jest wartość ciągu, dostarczone przez użytkownika. <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> jest `protected virtual` metody należy wywołać, aby zwrócić dane do wywoływania strony. Dane muszą być zapakowane w wystąpieniu ogólnego <xref:System.Windows.Navigation.ReturnEventArgs%601> wartość typu, którego argument typu określa typ, który <xref:System.Windows.Navigation.ReturnEventArgs%601.Result%2A> zwraca. W ten sposób, w przypadku deklarowania <xref:System.Windows.Navigation.PageFunction%601> z argumentem określonego typu, są stwierdzające, że <xref:System.Windows.Navigation.PageFunction%601> zwróci wystąpienia typu, który jest określony przez argument typu. W tym przykładzie argument typu, a w związku z tym, zwracana wartość jest typu <xref:System.String>.  
  
 Gdy <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> jest wywoływana, wywołujący musi strony odbiera wartość zwracaną przez jakiś sposób <xref:System.Windows.Navigation.PageFunction%601>. Z tego powodu <xref:System.Windows.Navigation.PageFunction%601> implementuje <xref:System.Windows.Navigation.PageFunction%601.Return> zdarzeń do wywoływania strony do obsługi. Gdy <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> jest wywoływana, <xref:System.Windows.Navigation.PageFunction%601.Return> jest wywoływane, więc wywoływania strony można zarejestrować w usłudze <xref:System.Windows.Navigation.PageFunction%601.Return> otrzymujących powiadomienie.  
  
 [!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind1)]
 [!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind1)]  
[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind2)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind2)]  
  
### <a name="removing-task-pages-when-a-task-completes"></a>Usuwanie strony zadania po zakończeniu zadania  
 Zwraca stronę o nazwie, gdy użytkownik nie Anuluj o nazwie strony, strony wywoływania przetworzy dane, które zostały dostarczone przez użytkownika, a także zwracany ze strony o nazwie. Pozyskiwanie danych w ten sposób jest zazwyczaj izolowane działanie; Po powrocie z strony o nazwie wywoływania strony musi utworzyć i przejdź do nowej strony wywołania do przechwytywania większej ilości danych.  
  
 Jednakże chyba że strona o nazwie zostanie usunięty z arkusza, użytkownik będzie można przejdź z powrotem do poprzedniego wystąpienia wywoływania strony. Czy <xref:System.Windows.Navigation.PageFunction%601> są przechowywane w dzienniku jest określana przez <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> właściwości. Domyślnie funkcja strony są automatycznie usuwane podczas <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> jest wywoływana, ponieważ <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> ustawiono `true`. Aby zachować funkcji strony w historii nawigacji po <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> jest wywoływana, ustaw <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> do `false`.  
  
<a name="Other_Types_of_Structured_Navigation"></a>   
## <a name="other-types-of-structured-navigation"></a>Inne rodzaje Strukturyzowana Nawigacja  
 W tym temacie przedstawiono podstawowe użycie <xref:System.Windows.Navigation.PageFunction%601> do obsługi rozmów/powrotu strukturę nawigacji. Takim fundamencie zapewnia możliwość tworzenia bardziej złożonych typów strukturyzowana Nawigacja.  
  
 Na przykład czasami wiele stron są wymagane przez wywołującego strony do zebrania wystarczającej ilości danych przez użytkownika lub do wykonania zadania. Używanie wielu stron nazywa się "Kreator".  
  
 W innych przypadkach aplikacje mogą mieć topologie nawigacji złożonych, które są zależne od strukturyzowana Nawigacja do efektywnego prowadzenia działalności. Aby uzyskać więcej informacji, zobacz [Przegląd topologia nawigacji](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Navigation.PageFunction%601>  
 <xref:System.Windows.Navigation.NavigationService>  
 [Topologia nawigacji — omówienie](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md)
