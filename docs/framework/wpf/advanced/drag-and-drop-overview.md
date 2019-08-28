---
title: Przegląd Przeciąganie i upuszczanie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], implementing
- drag sources [WPF], drag-and-drop
- data transfer [WPF], drag-and-drop
- drag-and-drop [WPF], about
- drag-and-drop [WPF], events
- drop targets [WPF], drag-and-drop
ms.assetid: 1a5b27b0-0ac5-4cdf-86c0-86ac0271fa64
ms.openlocfilehash: bb5766a3efc38750458ef0d354e8a2e3ab204000
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046406"
---
# <a name="drag-and-drop-overview"></a>Przegląd Przeciąganie i upuszczanie
Ten temat zawiera omówienie obsługi przeciągania i upuszczania w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacjach. Przeciąganie i upuszczanie często odnosi się do metody transferu danych, która polega na użyciu myszy (lub innego urządzenia wskazującego), aby wybrać jeden lub więcej obiektów, przeciągając je na wybrane miejsce docelowe [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]upuszczania w i upuszczając je.  

<a name="Drag_and_Drop_Support"></a>   
## <a name="drag-and-drop-support-in-wpf"></a>Obsługa przeciągania i upuszczania w programie WPF  
 Operacje przeciągania i upuszczania zwykle obejmują dwie strony: Źródło przeciągane, z którego pochodzi przeciągany obiekt, oraz miejsce docelowe upuszczania, które odbiera usunięty obiekt.  Obiekt docelowy przeciągania i upuszczania może być elementami interfejsu użytkownika w tej samej aplikacji lub innej aplikacji.  
  
 Typ i liczba obiektów, które mogą być manipulowane za pomocą przeciągania i upuszczania, są całkowicie arbitralne. Na przykład pliki, foldery i zaznaczenia zawartości to niektóre z bardziej popularnych obiektów manipulowanych przez operacje przeciągania i upuszczania.  
  
 Określone akcje wykonywane podczas operacji przeciągania i upuszczania są specyficzne dla aplikacji i często określane przez kontekstu.  Na przykład przeciąganie zaznaczenia plików z jednego folderu do drugiego na tym samym urządzeniu magazynującym powoduje przeniesienie plików domyślnie, natomiast przeciąganie plików z [!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)] udziału do folderu lokalnego kopiuje pliki domyślnie.  
  
 Urządzenia typu "przeciągnij i upuść" [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są zaprojektowane jako wysoce elastyczne i dostosowywalne w celu obsługi szerokiej gamy scenariuszy typu "przeciągnij i upuść".  Przeciąganie i upuszczanie obsługuje manipulowanie obiektami w ramach jednej aplikacji lub między różnymi aplikacjami. Przeciąganie i upuszczanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] między aplikacjami i innymi aplikacjami systemu Windows jest również w pełni obsługiwane.  
  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], dowolne <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement> może uczestniczyć w przeciąganiu i upuszczaniu. Zdarzenia i metody wymagane dla operacji przeciągania i upuszczania są zdefiniowane w <xref:System.Windows.DragDrop> klasie. <xref:System.Windows.UIElement> <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement> Klasy i <xref:System.Windows.ContentElement> zawierają aliasy dla dołączonychzdarzeń,dziękiczemuzdarzeniapojawiająsięnaliścieskładowychklasy,<xref:System.Windows.DragDrop> gdy lub jest dziedziczona jako element podstawowy. Programy obsługi zdarzeń dołączone do tych zdarzeń są dołączone do bazowego <xref:System.Windows.DragDrop> dołączonego zdarzenia i odbierają to samo wystąpienie danych zdarzenia. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.UIElement.Drop?displayProperty=nameWithType> zdarzenie.  
  
> [!IMPORTANT]
> Przeciąganie i upuszczanie OLE nie działa w strefie Internet.  
  
<a name="Data_Transfer"></a>   
## <a name="data-transfer"></a>Transfer danych  
 Przeciąganie i upuszczanie jest częścią bardziej ogólnego obszaru transferu danych. Transfer danych obejmuje operacje przeciągania i upuszczania oraz kopiowania i wklejania. Operacja przeciągania i upuszczania jest analogiczna do operacji kopiowania i wklejania lub wycinania i wklejania, która jest używana do transferowania danych z jednego obiektu lub aplikacji do innego przy użyciu schowka systemowego. Oba typy operacji wymagają:  
  
- Obiekt źródłowy, który udostępnia dane.  
  
- Sposób tymczasowego przechowywania przesłanych danych.  
  
- Obiekt docelowy, który odbiera dane.  
  
 W operacji kopiowania i wklejania do tymczasowego przechowywania transferowanych danych używany jest schowek systemowy. w operacji <xref:System.Windows.DataObject> przeciągania i upuszczania jest używana do przechowywania danych. Koncepcyjnie obiekt danych składa się z co najmniej jednej pary <xref:System.Object> zawierającej rzeczywiste dane oraz odpowiedniego identyfikatora formatu danych.  
  
 Źródło przeciągania Inicjuje operację przeciągania i upuszczania przez wywołanie metody statycznej <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> i przekazanie do niej przesłanych danych. Metoda automatycznie zawija dane <xref:System.Windows.DataObject> w razie potrzeby. <xref:System.Windows.DragDrop.DoDragDrop%2A> Aby uzyskać większą kontrolę nad formatem danych, można otoczyć dane <xref:System.Windows.DataObject> przed przekazaniem ich <xref:System.Windows.DragDrop.DoDragDrop%2A> do metody. Element docelowy upuszczania jest odpowiedzialny za wyodrębnienie danych z <xref:System.Windows.DataObject>. Aby uzyskać więcej informacji na temat pracy z obiektami danych, zobacz [dane i obiekty danych](data-and-data-objects.md).  
  
 Źródłem i elementem docelowym operacji przeciągania i upuszczania są elementy interfejsu użytkownika; Jednak dane, które faktycznie są transferowane zazwyczaj nie mają wizualnej reprezentacji. Można napisać kod, aby zapewnić wizualną reprezentację przeciąganych danych, na przykład podczas przeciągania plików w Eksploratorze Windows. Domyślnie informacje zwrotne są przekazywane użytkownikowi przez zmianę kursora w celu reprezentowania efektu operacji przeciągania i upuszczania na danych, na przykład czy dane zostaną przeniesione lub skopiowane.  
  
### <a name="drag-and-drop-effects"></a>Efekty przeciągania i upuszczania  
 Operacje przeciągania i upuszczania mogą mieć różny wpływ na przesyłane dane. Można na przykład skopiować dane lub przenieść dane. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.DragDropEffects> definiuje wyliczenie, którego można użyć, aby określić efekt operacji przeciągania i upuszczania. W źródle przeciągnij możesz określić efekty, które będą dozwolone przez źródło w <xref:System.Windows.DragDrop.DoDragDrop%2A> metodzie. W miejscu docelowym upuść można określić efekt, który obiekt docelowy ma w <xref:System.Windows.DragEventArgs.Effects%2A> właściwości <xref:System.Windows.DragEventArgs> klasy. Gdy element docelowy upuszczania określa zamierzony efekt w <xref:System.Windows.DragDrop.DragOver> zdarzeniu, te informacje są przesyłane z powrotem do źródła przeciągania <xref:System.Windows.DragDrop.GiveFeedback> w zdarzeniu. Źródło przeciągania używa tych informacji do informowania użytkownika o tym, że obiekt docelowy upuszczania ma wpływ na dane. Gdy dane zostaną usunięte, cel upuszczania określa swój rzeczywisty efekt w <xref:System.Windows.DragDrop.Drop> zdarzeniu. Te informacje są przesyłane z powrotem do źródła przeciągania jako wartość <xref:System.Windows.DragDrop.DoDragDrop%2A> zwracana metody. Jeśli obiekt docelowy upuszczania zwraca efekt, którego nie ma na liście `allowedEffects`źródeł przeciągania, operacja przeciągania i upuszczania zostanie anulowana bez żadnego transferu danych.  
  
 Należy pamiętać, że w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.DragDropEffects> wartości są używane tylko w celu zapewnienia komunikacji między źródłem przeciągania a obiektem docelowym upuszczania w odniesieniu do efektów operacji przeciągania i upuszczania. Rzeczywisty efekt operacji przeciągania i upuszczania zależy od tego, w jaki sposób napisać odpowiedni kod w aplikacji.  
  
 Na przykład obiekt docelowy upuszczania może określać, że efektem upuszczania danych jest przeniesienie danych. Jednak aby przenieść dane, należy je dodać do elementu docelowego i usunąć z elementu źródłowego. Element źródłowy może wskazywać, że umożliwia przenoszenie danych, ale jeśli nie podasz kodu, aby usunąć dane z elementu źródłowego, wynik końcowy będzie kopiowany i nie przenoszony.  
  
<a name="Drag_and_Drop_Events"></a>   
## <a name="drag-and-drop-events"></a>Zdarzenia przeciągania i upuszczania  
 Operacje przeciągania i upuszczania obsługują model oparty na zdarzeniach.  Zarówno źródło Przeciągnij, jak i miejsce docelowe umożliwiają użycie standardowego zestawu zdarzeń do obsługi operacji przeciągania i upuszczania.  W poniższej tabeli zestawiono standardowe zdarzenia przeciągania i upuszczania. Są to dołączone zdarzenia w <xref:System.Windows.DragDrop> klasie. Aby uzyskać więcej informacji o załączonych zdarzeniach, zobacz [Omówienie załączonych zdarzeń](attached-events-overview.md).  
  
### <a name="drag-source-events"></a>Przeciągnij zdarzenia źródłowe  
  
|Zdarzenie|Podsumowanie|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.GiveFeedback>|To zdarzenie występuje w sposób ciągły podczas operacji przeciągania i upuszczania oraz umożliwia źródło informacji zwrotnych dla użytkownika. Ta opinia jest zwykle wyrażana przez zmianę wyglądu wskaźnika myszy w celu wskazania efektów dozwolonych przez element docelowy upuszczania.  Jest to zdarzenie propagacji.|  
|<xref:System.Windows.DragDrop.QueryContinueDrag>|To zdarzenie występuje w przypadku zmiany stanu przycisku klawiatury lub myszy podczas operacji przeciągania i upuszczania, a następnie umożliwienie źródłowej operacji przeciągania i upuszczania w zależności od Stanów klawiszy/przycisków. Jest to zdarzenie propagacji.|  
|<xref:System.Windows.DragDrop.PreviewGiveFeedback>|Tunelowanie wersji programu <xref:System.Windows.DragDrop.GiveFeedback>.|  
|<xref:System.Windows.DragDrop.PreviewQueryContinueDrag>|Tunelowanie wersji programu <xref:System.Windows.DragDrop.QueryContinueDrag>.|  
  
### <a name="drop-target-events"></a>Upuść zdarzenia docelowe  
  
|Zdarzenie|Podsumowanie|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.DragEnter>|To zdarzenie występuje, gdy obiekt zostanie przeciągnięty do granicy elementu docelowego upuszczania. Jest to zdarzenie propagacji.|  
|<xref:System.Windows.DragDrop.DragLeave>|To zdarzenie występuje, gdy obiekt zostanie przeciągnięty z granicy elementu docelowego upuszczania.  Jest to zdarzenie propagacji.|  
|<xref:System.Windows.DragDrop.DragOver>|To zdarzenie występuje w sposób ciągły, gdy obiekt zostanie przeciągnięty (przeniesiony) w obrębie granicy elementu docelowego upuszczania. Jest to zdarzenie propagacji.|  
|<xref:System.Windows.DragDrop.Drop>|To zdarzenie występuje, gdy obiekt zostanie usunięty z elementu docelowego upuszczania.  Jest to zdarzenie propagacji.|  
|<xref:System.Windows.DragDrop.PreviewDragEnter>|Tunelowanie wersji programu <xref:System.Windows.DragDrop.DragEnter>.|  
|<xref:System.Windows.DragDrop.PreviewDragLeave>|Tunelowanie wersji programu <xref:System.Windows.DragDrop.DragLeave>.|  
|<xref:System.Windows.DragDrop.PreviewDragOver>|Tunelowanie wersji programu <xref:System.Windows.DragDrop.DragOver>.|  
|<xref:System.Windows.DragDrop.PreviewDrop>|Tunelowanie wersji programu <xref:System.Windows.DragDrop.Drop>.|  
  
 Aby obsłużyć zdarzenia przeciągania i upuszczania dla wystąpień obiektu, należy dodać procedury obsługi dla zdarzeń wymienionych w poprzednich tabelach. Aby obsłużyć zdarzenia przeciągane i upuszczane na poziomie klasy, Zastąp odpowiednie wirtualne zdarzenie * i\*metody PreviewEvent. Aby uzyskać więcej informacji, zobacz temat [Obsługa zdarzeń kierowanych przez klasy bazowe formantów](marking-routed-events-as-handled-and-class-handling.md#Class_Handling_of_Routed_Events).  
  
<a name="Implementing_Drag_And_Drop"></a>   
## <a name="implementing-drag-and-drop"></a>Implementowanie przeciągania i upuszczania  
 Element interfejsu użytkownika może być źródłem przeciągania, elementem docelowym upuszczania lub jednocześnie. Aby zaimplementować podstawowe przeciąganie i upuszczanie, napisz kod w celu zainicjowania operacji przeciągania i upuszczania oraz przetworzenia porzuconych danych. Możesz ulepszyć środowisko przeciągania i upuszczania, obsługując opcjonalne zdarzenia przeciągania i upuszczania.  
  
 Aby zaimplementować podstawowe przeciąganie i upuszczanie, należy wykonać następujące zadania:  
  
- Zidentyfikuj element, który będzie źródłem przeciągania. Źródłem przeciągania może być <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement>lub.  
  
- Utwórz procedurę obsługi zdarzeń dla źródła przeciągania, które będzie inicjować operację przeciągania i upuszczania. Zdarzenie to zazwyczaj <xref:System.Windows.UIElement.MouseMove> zdarzenie.  
  
- W procedurze obsługi zdarzeń ze źródłem przeciągnij wywołanie <xref:System.Windows.DragDrop.DoDragDrop%2A> metody w celu zainicjowania operacji przeciągania i upuszczania. <xref:System.Windows.DragDrop.DoDragDrop%2A> W wywołaniu Określ źródło przeciągania, dane, które mają być transferowane oraz dozwolone efekty.  
  
- Określ element, który będzie elementem docelowym upuszczania. Obiekt docelowy upuszczania może być <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement>lub.  
  
- W miejscu docelowym upuść Ustaw <xref:System.Windows.UIElement.AllowDrop%2A> właściwość na. `true`  
  
- W miejscu docelowym upuść Utwórz <xref:System.Windows.DragDrop.Drop> procedurę obsługi zdarzeń, aby przetworzyć usunięte dane.  
  
- W programie obsługi <xref:System.Windows.DragEventArgs> <xref:System.Windows.DataObject.GetDataPresent%2A> <xref:System.Windows.DataObject.GetData%2A> zdarzeń Wyodrębnij dane z przy użyciu metod i. <xref:System.Windows.DragDrop.Drop>  
  
- W programie obsługi zdarzeń Użyj danych do wykonania odpowiedniej operacji przeciągania i upuszczania. <xref:System.Windows.DragDrop.Drop>  
  
 Można ulepszyć implementację typu "przeciągnij i upuść", tworząc niestandardowe <xref:System.Windows.DataObject> i obsługując opcjonalne zdarzenia przeciągania źródła i upuszczania, jak pokazano w następujących zadaniach:  
  
- Aby przesłać dane niestandardowe lub wiele elementów danych, Utwórz element <xref:System.Windows.DataObject> do przekazania <xref:System.Windows.DragDrop.DoDragDrop%2A> do metody.  
  
- Aby wykonać dodatkowe akcje w trakcie przeciągania, <xref:System.Windows.DragDrop.DragEnter>obsłużyć <xref:System.Windows.DragDrop.DragOver>zdarzenia, <xref:System.Windows.DragDrop.DragLeave> i w miejscu docelowym upuszczania.  
  
- Aby zmienić wygląd wskaźnika myszy, należy obsłużyć <xref:System.Windows.DragDrop.GiveFeedback> zdarzenie w źródle przeciągania.  
  
- Aby zmienić sposób anulowania operacji przeciągania i upuszczania, należy obsłużyć <xref:System.Windows.DragDrop.QueryContinueDrag> zdarzenie w źródle przeciągania.  
  
<a name="Drag_And_Drop_Example"></a>   
## <a name="drag-and-drop-example"></a>Przykład przeciągania i upuszczania  
 W tej sekcji opisano, jak zaimplementować przeciąganie i upuszczanie <xref:System.Windows.Shapes.Ellipse> dla elementu. <xref:System.Windows.Shapes.Ellipse> Jest to zarówno źródło przeciągania, jak i element docelowy upuszczania. Przesłane dane to ciąg reprezentujący <xref:System.Windows.Shapes.Shape.Fill%2A> Właściwość elipsy. Poniższy kod XAML pokazuje <xref:System.Windows.Shapes.Ellipse> element oraz zdarzenia związane z przeciąganiem i upuszczaniem, które obsługuje. Aby uzyskać pełne instrukcje dotyczące sposobu implementacji przeciągania i upuszczania, zobacz [Przewodnik: Włączanie przeciągania i upuszczania w kontrolce](walkthrough-enabling-drag-and-drop-on-a-user-control.md)użytkownika.  
  
 [!code-xaml[DragDropSnippets#EllipseXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#ellipsexaml)]  
  
### <a name="enabling-an-element-to-be-a-drag-source"></a>Włączanie elementu jako źródła przeciągania  
 Obiekt, który jest źródłem przeciągania, jest odpowiedzialny za:  
  
- Identyfikowanie, kiedy nastąpi przeciągnięcie.  
  
- Inicjowanie operacji przeciągania i upuszczania.  
  
- Identyfikowanie danych do przeniesienia.  
  
- Określanie wpływu operacji przeciągania i upuszczania na transferowane dane.  
  
 Źródło przeciągania może również przekazać użytkownikowi informacje zwrotne dotyczące dozwolonych akcji (przenoszenia, kopiowania, braku) i umożliwia anulowanie operacji przeciągania i upuszczania na podstawie dodatkowych danych wejściowych użytkownika, takich jak naciśnięcie klawisza ESC podczas przeciągania.  
  
 Jest odpowiedzialna za aplikację, aby określić, kiedy nastąpi przeciąganie, a następnie zainicjować operację przeciągania i upuszczania przez wywołanie <xref:System.Windows.DragDrop.DoDragDrop%2A> metody. Zwykle jest <xref:System.Windows.UIElement.MouseMove> to spowodowane tym, że zdarzenie dotyczy elementu, który ma być przeciągany podczas naciskania przycisku myszy. Poniższy przykład pokazuje, jak zainicjować operację przeciągania i upuszczania z <xref:System.Windows.UIElement.MouseMove> procedury obsługi <xref:System.Windows.Shapes.Ellipse> zdarzeń elementu, aby uczynić go źródłem przeciągania. Przesłane dane to ciąg reprezentujący <xref:System.Windows.Shapes.Shape.Fill%2A> Właściwość elipsy.  
  
 [!code-csharp[DragDropSnippets#DoDragDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dodragdrop)]
 [!code-vb[DragDropSnippets#DoDragDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dodragdrop)]  
  
 Wewnątrz procedury obsługi <xref:System.Windows.DragDrop.DoDragDrop%2A> zdarzeń Wywołaj metodę w celu zainicjowania operacji przeciągania i upuszczania. <xref:System.Windows.UIElement.MouseMove> <xref:System.Windows.DragDrop.DoDragDrop%2A> Metoda przyjmuje trzy parametry:  
  
- `dragSource`— Odwołanie do obiektu zależności, który jest źródłem przesłanych danych; jest to zazwyczaj źródłem <xref:System.Windows.UIElement.MouseMove> zdarzenia.  
  
- `data`-Obiekt, który zawiera przesyłane dane, opakowany w <xref:System.Windows.DataObject>.  
  
- `allowedEffects`-Jedna z <xref:System.Windows.DragDropEffects> wartości wyliczenia, która określa dozwolone skutki operacji przeciągania i upuszczania.  
  
 Dowolny możliwy do serializacji obiekt można przesłać do `data` parametru. Jeśli dane nie są jeszcze opakowane <xref:System.Windows.DataObject>, zostaną automatycznie opakowane w nową. <xref:System.Windows.DataObject> Aby przekazać wiele elementów danych, należy utworzyć <xref:System.Windows.DataObject> siebie i przekazać ją <xref:System.Windows.DragDrop.DoDragDrop%2A> do metody. Aby uzyskać więcej informacji, zobacz [obiekty danych i danych](data-and-data-objects.md).  
  
 `allowedEffects` Parametr służy do określania, jakie źródło przeciągania będzie zezwalać na miejsce docelowe upuszczania z transferowanymi danymi. Typowe wartości dla źródła przeciągania to <xref:System.Windows.DragDropEffects.Copy>, <xref:System.Windows.DragDropEffects.Move>i <xref:System.Windows.DragDropEffects.All>.  
  
> [!NOTE]
> Obiekt docelowy upuszczania umożliwia również określenie, jakie skutki ma w odpowiedzi na porzucone dane. Na przykład jeśli element docelowy upuszczania nie rozpoznaje typu danych, który ma zostać porzucony, może odmówić danych przez ustawienie jego dozwolonych efektów <xref:System.Windows.DragDropEffects.None>. Zwykle jest to wykonywane w ramach <xref:System.Windows.DragDrop.DragOver> programu obsługi zdarzeń.  
  
 Źródło przeciągania może opcjonalnie obsłużyć <xref:System.Windows.DragDrop.GiveFeedback> zdarzenia <xref:System.Windows.DragDrop.QueryContinueDrag> i. Te zdarzenia mają domyślne programy obsługi, które są używane, chyba że zostaną oznaczone zdarzenia jako obsłużone. Te zdarzenia są zwykle ignorowane, chyba że użytkownik ma konkretną potrzebę zmiany domyślnego zachowania.  
  
 <xref:System.Windows.DragDrop.GiveFeedback> Zdarzenie jest zgłaszane w sposób ciągły podczas przeciągania źródła przeciągania. Domyślne procedury obsługi dla tego zdarzenia sprawdzają, czy źródło przeciągania znajduje się w poprawnym elemencie docelowym upuszczania. Jeśli tak jest, sprawdza dozwolone efekty elementu docelowego upuszczania. Następnie przekazuje użytkownikowi końcowemu opinię na temat dozwolonych efektów upuszczania. Jest to zwykle wykonywane przez zmianę kursora myszy na kursor nie upuszczany, Kopiuj lub Przenieś. To zdarzenie należy obsłużyć tylko wtedy, gdy musisz użyć niestandardowych kursorów, aby przekazać użytkownikom informacje zwrotne. W przypadku obsługi tego zdarzenia Pamiętaj, aby oznaczyć je jako obsłużone, tak aby domyślna procedura obsługi nie przesłaniał programu obsługi.  
  
 <xref:System.Windows.DragDrop.QueryContinueDrag> Zdarzenie jest zgłaszane w sposób ciągły podczas przeciągania źródła przeciągania. Możesz obsłużyć to zdarzenie, aby określić, jaka akcja powoduje zakończenie operacji przeciągania i upuszczania na podstawie stanu klawiszy ESC, SHIFT, CTRL i ALT, jak również stanu przycisków myszy. Domyślna procedura obsługi dla tego zdarzenia powoduje anulowanie operacji przeciągania i upuszczania w przypadku naciśnięcia klawisza ESC i odrzucenie danych po udostępnieniu przycisku myszy.  
  
> [!CAUTION]
> Te zdarzenia są stale zgłaszane podczas operacji przeciągania i upuszczania. W związku z tym należy unikać zadań intensywnie korzystających z zasobów w programach obsługi zdarzeń.  Na przykład użyj buforowanego kursora zamiast tworzenia nowego kursora przy każdym <xref:System.Windows.DragDrop.GiveFeedback> wywołaniu zdarzenia.  
  
### <a name="enabling-an-element-to-be-a-drop-target"></a>Włączanie elementu jako miejsca docelowego upuszczania  
 Obiekt, który jest obiektem docelowym upuszczania, jest odpowiedzialny za:  
  
- Określanie, że jest to prawidłowy element docelowy upuszczania.  
  
- Odpowiadanie na źródło przeciągania, gdy jest ono przeciągane względem obiektu docelowego.  
  
- Sprawdzanie, czy transferowane dane są w formacie, który może zostać odebrany.  
  
- Przetwarzanie porzuconych danych.  
  
 Aby określić, że element jest obiektem docelowym upuszczania, ustaw jego <xref:System.Windows.UIElement.AllowDrop%2A> właściwość na `true`. Zdarzenia Drop Target zostaną następnie zgłoszone dla elementu, aby można było je obsłużyć. Podczas operacji przeciągania i upuszczania występuje następująca sekwencja zdarzeń w miejscu docelowym upuszczania:  
  
1. <xref:System.Windows.DragDrop.DragEnter>  
  
2. <xref:System.Windows.DragDrop.DragOver>  
  
3. <xref:System.Windows.DragDrop.DragLeave> lub <xref:System.Windows.DragDrop.Drop>  
  
 Zdarzenie <xref:System.Windows.DragDrop.DragEnter> występuje, gdy dane są przeciągane do granicy elementu docelowego upuszczania. To zdarzenie jest zwykle obsługiwane, aby zapewnić podgląd efektów operacji przeciągania i upuszczania, jeśli jest to odpowiednie dla aplikacji. Nie ustawiaj <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> właściwości <xref:System.Windows.DragDrop.DragEnter> w zdarzeniu, ponieważ zostanie ona zapisywana w <xref:System.Windows.DragDrop.DragOver> zdarzeniu.  
  
 Poniższy przykład pokazuje <xref:System.Windows.DragDrop.DragEnter> procedurę obsługi zdarzeń <xref:System.Windows.Shapes.Ellipse> dla elementu. Ten kod umożliwia wyświetlenie podglądu efektów operacji przeciągania i upuszczania przez zapisanie bieżącego <xref:System.Windows.Shapes.Shape.Fill%2A> pędzla. Następnie używa metody, <xref:System.Windows.DataObject.GetDataPresent%2A> aby sprawdzić, <xref:System.Windows.DataObject> czy przeciąganie przez wielokropek zawiera dane ciągu, które <xref:System.Windows.Media.Brush>można przekonwertować na. Jeśli tak, dane są wyodrębniane przy użyciu <xref:System.Windows.DataObject.GetData%2A> metody. Następnie jest konwertowany na <xref:System.Windows.Media.Brush> a i zastosowany do elipsy. Zmiana zostanie wycofana w programie <xref:System.Windows.DragDrop.DragLeave> obsługi zdarzeń. Jeśli nie można przekonwertować danych na obiekt <xref:System.Windows.Media.Brush>, nie jest wykonywana żadna akcja.  
  
 [!code-csharp[DragDropSnippets#DragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragenter)]
 [!code-vb[DragDropSnippets#DragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragenter)]  
  
 <xref:System.Windows.DragDrop.DragOver> Zdarzenie odbywa się w sposób ciągły, gdy dane są przeciągane na element docelowy upuszczania. To zdarzenie jest sparowane ze <xref:System.Windows.DragDrop.GiveFeedback> zdarzeniem w źródle przeciągania. W programie obsługi <xref:System.Windows.DataObject.GetDataPresent%2A> <xref:System.Windows.DataObject.GetData%2A> zdarzeń zwykle używasz metod i, aby sprawdzić, czy transferowane dane są w formacie, który może przetwarzać element docelowy upuszczania. <xref:System.Windows.DragDrop.DragOver> Możesz również sprawdzić, czy zostały naciśnięte jakiekolwiek klawisze modyfikujące, które zwykle wskazują, czy użytkownik zamierza wykonać akcję przenoszenia lub kopiowania. Po wykonaniu tych testów należy ustawić <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> właściwość w celu powiadomienia źródła przeciągania o tym, jaki efekt spowoduje porzucenie danych. Źródło przeciągania odbiera te informacje w <xref:System.Windows.DragDrop.GiveFeedback> argumentych zdarzeń i może ustawić odpowiedni kursor, aby przekazać użytkownikowi opinię.  
  
 Poniższy przykład pokazuje <xref:System.Windows.DragDrop.DragOver> procedurę obsługi zdarzeń <xref:System.Windows.Shapes.Ellipse> dla elementu. Ten kod sprawdza, czy <xref:System.Windows.DataObject> przeciąganie przez wielokropek zawiera dane ciągu, które można przekonwertować <xref:System.Windows.Media.Brush>na. Jeśli tak, ustawia <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> właściwość na. <xref:System.Windows.DragDropEffects.Copy> Wskazuje źródło przeciągania, które można skopiować dane na elipsę. Jeśli dane nie mogą być konwertowane na <xref:System.Windows.Media.Brush> <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> , właściwość jest ustawiona na <xref:System.Windows.DragDropEffects.None>. Wskazuje to na źródło przeciągania, którego Elipsa nie jest prawidłowym obiektem docelowym upuszczania dla danych.  
  
 [!code-csharp[DragDropSnippets#DragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragover)]
 [!code-vb[DragDropSnippets#DragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragover)]  
  
 Zdarzenie <xref:System.Windows.DragDrop.DragLeave> występuje, gdy dane są przeciągane z granicy elementu docelowego bez porzucenia. To zdarzenie jest obsługiwane w celu cofnięcia wszystkich elementów, które <xref:System.Windows.DragDrop.DragEnter> zostały wykonane w programie obsługi zdarzeń.  
  
 Poniższy przykład pokazuje <xref:System.Windows.DragDrop.DragLeave> procedurę obsługi zdarzeń <xref:System.Windows.Shapes.Ellipse> dla elementu. Ten kod odcofał się do wersji zapoznawczej wykonywanej w <xref:System.Windows.DragDrop.DragEnter> programie <xref:System.Windows.Media.Brush> obsługi zdarzeń przez zastosowanie zapisanego do elipsy.  
  
 [!code-csharp[DragDropSnippets#DragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragleave)]
 [!code-vb[DragDropSnippets#DragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragleave)]  
  
 <xref:System.Windows.DragDrop.Drop> Zdarzenie występuje, gdy dane są opuszczane przez element docelowy upuszczania; domyślnie dzieje się tak po wydaniu przycisku myszy. W programie obsługi <xref:System.Windows.DataObject.GetData%2A> <xref:System.Windows.DataObject> zdarzeń należy użyć metody, aby wyodrębnić przesłane dane z i wykonać wszelkie przetwarzanie danych wymagane przez aplikację. <xref:System.Windows.DragDrop.Drop> Zdarzenie <xref:System.Windows.DragDrop.Drop> ma koniec operacji przeciągania i upuszczania.  
  
 Poniższy przykład pokazuje <xref:System.Windows.DragDrop.Drop> procedurę obsługi zdarzeń <xref:System.Windows.Shapes.Ellipse> dla elementu. Ten kod stosuje efekty operacji przeciągania i upuszczania oraz jest podobny do kodu w programie <xref:System.Windows.DragDrop.DragEnter> obsługi zdarzeń. Sprawdza, czy <xref:System.Windows.DataObject> przeciąganie przez wielokropek zawiera dane ciągu, które można przekonwertować <xref:System.Windows.Media.Brush>na. Jeśli tak, <xref:System.Windows.Media.Brush> to jest stosowany do elipsy. Jeśli nie można przekonwertować danych na obiekt <xref:System.Windows.Media.Brush>, nie jest wykonywana żadna akcja.  
  
 [!code-csharp[DragDropSnippets#Drop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#drop)]
 [!code-vb[DragDropSnippets#Drop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#drop)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Clipboard>
- [Przewodnik: Włączanie przeciągania i upuszczania w kontrolce użytkownika](walkthrough-enabling-drag-and-drop-on-a-user-control.md)
- [Tematy z instrukcjami](drag-and-drop-how-to-topics.md)
- [Przeciąganie i upuszczanie](drag-and-drop.md)
