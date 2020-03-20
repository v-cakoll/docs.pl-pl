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
ms.openlocfilehash: dd42af77300a7a93bbcbfa4c8f1fc365fc3f5da1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185983"
---
# <a name="drag-and-drop-overview"></a>Przegląd Przeciąganie i upuszczanie
Ten temat zawiera omówienie obsługi przeciągania i upuszczania w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacjach. Przeciąganie i upuszczanie często odnosi się do metody transferu danych, która polega na użyciu myszy (lub innego urządzenia wskazującego), aby [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]zaznaczyć jeden lub więcej obiektów, przeciągając te obiekty nad żądanym celem upuszczania w urządzeniu , i upuszczając je.  

<a name="Drag_and_Drop_Support"></a>
## <a name="drag-and-drop-support-in-wpf"></a>Obsługa przeciągania i upuszczania w WPF  
 Operacje przeciągania i upuszczania zazwyczaj obejmują dwie strony: źródło przeciągania, z którego pochodzi przeciągany obiekt, oraz miejsce docelowe upuszczania, które odbiera upuszczony obiekt.  Miejsce docelowe źródła przeciągania i upuszczania może być elementami interfejsu użytkownika w tej samej aplikacji lub innej aplikacji.  
  
 Typ i liczba obiektów, którymi można manipulować za pomocą przeciągania i upuszczania, jest całkowicie dowolna. Na przykład pliki, foldery i zaznaczenia zawartości to niektóre z bardziej typowych obiektów manipulowanych za pomocą operacji przeciągania i upuszczania.  
  
 Określone akcje wykonywane podczas operacji przeciągania i upuszczania są specyficzne dla aplikacji i często określane przez kontekst.  Na przykład przeciąganie zaznaczenia plików z jednego folderu do drugiego na tym samym urządzeniu magazynującym domyślnie powoduje przeniesienie plików, podczas gdy przeciąganie plików z udziału Powszechnej Konwencji nazewnictwa (UNC) do folderu lokalnego domyślnie kopiuje pliki.  
  
 Oferowane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] urządzenia typu "przeciągnij i upuść" zostały zaprojektowane tak, aby były bardzo elastyczne i konfigurowalne, aby obsługiwać szeroką gamę scenariuszy przeciągania i upuszczania.  Funkcję przeciągania i upuszczania można manipulować obiektami w ramach jednej aplikacji lub między różnymi aplikacjami. Przeciąganie i upuszczanie między aplikacjami i innymi aplikacjami [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systemu Windows jest również w pełni obsługiwane.  
  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]programie <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement> , dowolnym lub może uczestniczyć w przeciąganiu i upuszczaniu. Zdarzenia i metody wymagane dla operacji przeciągania i <xref:System.Windows.DragDrop> upuszczania są zdefiniowane w klasie. Klasy <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement> i zawierają aliasy <xref:System.Windows.DragDrop> dla dołączonych zdarzeń, tak aby zdarzenia <xref:System.Windows.UIElement> pojawiały się na liście członków klasy, gdy lub <xref:System.Windows.ContentElement> jest dziedziczona jako element podstawowy. Programy obsługi zdarzeń, które są dołączone do tych <xref:System.Windows.DragDrop> zdarzeń są dołączone do źródłowego dołączonego zdarzenia i odbierają to samo wystąpienie danych zdarzeń. Aby uzyskać więcej <xref:System.Windows.UIElement.Drop?displayProperty=nameWithType> informacji, zobacz zdarzenie.  
  
> [!IMPORTANT]
> Ole przeciągania i upuszczania nie działa w strefie Internet.  
  
<a name="Data_Transfer"></a>
## <a name="data-transfer"></a>Transfer danych  
 Przeciąganie i upuszczanie jest częścią bardziej ogólnego obszaru transferu danych. Transfer danych obejmuje operacje przeciągania i upuszczania oraz kopiowania i wklejania. Operacja przeciągania i upuszczania jest analogiczna do operacji kopiowania i wklejania lub wycinania i wklejania, która służy do przesyłania danych z jednego obiektu lub aplikacji do innego przy użyciu schowka systemowego. Oba rodzaje operacji wymagają:  
  
- Obiekt źródłowy, który dostarcza dane.  
  
- Sposób tymczasowego przechowywania przesłanych danych.  
  
- Obiekt docelowy, który odbiera dane.  
  
 W operacji kopiowania i wklejania schowek systemowy jest używany do tymczasowego przechowywania przesłanych danych; w operacji przeciągania i <xref:System.Windows.DataObject> upuszczania a jest używany do przechowywania danych. Koncepcyjnie obiekt danych składa się z <xref:System.Object> jednej lub więcej par, która zawiera rzeczywiste dane i odpowiedni identyfikator formatu danych.  
  
 Źródło przeciągania inicjuje operację przeciągania <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> i upuszczania, wywołując metodę statyczną i przekazując do niej przesłane dane. Metoda <xref:System.Windows.DragDrop.DoDragDrop%2A> automatycznie zawija dane <xref:System.Windows.DataObject> w, jeśli to konieczne. Aby uzyskać większą kontrolę nad formatem danych, <xref:System.Windows.DataObject> można zawinąć <xref:System.Windows.DragDrop.DoDragDrop%2A> dane w przed przekazaniem go do metody. Cel upuszczania jest odpowiedzialny za <xref:System.Windows.DataObject>wyodrębnianie danych z pliku . Aby uzyskać więcej informacji na temat pracy z obiektami danych, zobacz [Obiekty danych i danych](data-and-data-objects.md).  
  
 Źródłem i celem operacji przeciągania i upuszczania są elementy interfejsu użytkownika; jednak dane, które są faktycznie przesyłane zazwyczaj nie ma wizualnej reprezentacji. Można napisać kod, aby zapewnić wizualną reprezentację przeciąganych danych, na przykład podczas przeciągania plików w Eksploratorze Windows. Domyślnie opinie są dostarczane do użytkownika, zmieniając kursor, aby reprezentować wpływ, że operacja przeciągania i upuszczania będzie miała na danych, takich jak czy dane zostaną przeniesione lub skopiowane.  
  
### <a name="drag-and-drop-effects"></a>Efekty przeciągania i upuszczania  
 Operacje przeciągania i upuszczania mogą mieć różny wpływ na przesyłane dane. Na przykład można skopiować dane lub przenieść dane. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]definiuje wyliczenie, <xref:System.Windows.DragDropEffects> którego można użyć do określenia efektu operacji przeciągania i upuszczania. W źródle przeciągania można określić efekty, które <xref:System.Windows.DragDrop.DoDragDrop%2A> źródło pozwoli w metodzie. W miejsce docelowe upuszczania można określić <xref:System.Windows.DragEventArgs.Effects%2A> efekt, <xref:System.Windows.DragEventArgs> który zamierza cel we właściwości klasy. Gdy miejsce docelowe upuszczania <xref:System.Windows.DragDrop.DragOver> określa jego zamierzony efekt w zdarzeniu, informacje te są przekazywane z powrotem do źródła przeciągania w zdarzeniu. <xref:System.Windows.DragDrop.GiveFeedback> Źródło przeciągania używa tych informacji, aby poinformować użytkownika, jaki wpływ docelowy upuszczania zamierza mieć na dane. Gdy dane są usuwane, miejsce docelowe upuszczania określa jego rzeczywisty efekt w zdarzeniu. <xref:System.Windows.DragDrop.Drop> Te informacje są przekazywane z powrotem do <xref:System.Windows.DragDrop.DoDragDrop%2A> źródła przeciągania jako wartość zwracaną metody. Jeśli obiekt docelowy upuszczania zwraca efekt, którego `allowedEffects`nie ma na liście źródeł przeciągania, operacja przeciągania i upuszczania jest anulowana bez konieczności przesyłania danych.  
  
 Należy pamiętać, że [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]w <xref:System.Windows.DragDropEffects> programie Wartości są używane tylko do komunikacji między źródłem przeciągania a celem upuszczania w odniesieniu do efektów operacji przeciągania i upuszczania. Rzeczywisty efekt operacji przeciągania i upuszczania zależy od tego, czy chcesz napisać odpowiedni kod w aplikacji.  
  
 Na przykład miejsce docelowe upuszczania może określić, że efektem upuszczania danych na nim jest przeniesienie danych. Jednak aby przenieść dane, musi być zarówno dodane do elementu docelowego i usunięte z elementu źródłowego. Element źródłowy może wskazywać, że umożliwia przenoszenie danych, ale jeśli nie podasz kodu, aby usunąć dane z elementu źródłowego, wynikiem końcowym będzie, że dane są kopiowane, a nie przenoszone.  
  
<a name="Drag_and_Drop_Events"></a>
## <a name="drag-and-drop-events"></a>Zdarzenia przeciągania i upuszczania  
 Operacje przeciągania i upuszczania obsługują model oparty na zdarzeniach.  Zarówno źródło przeciągania, jak i miejsce docelowe upuszczania używają standardowego zestawu zdarzeń do obsługi operacji przeciągania i upuszczania.  W poniższych tabelach podsumowano standardowe zdarzenia przeciągania i upuszczania. Są to dołączone zdarzenia <xref:System.Windows.DragDrop> w klasie. Aby uzyskać więcej informacji na temat załączonych zdarzeń, zobacz [Omówienie załączonych zdarzeń](attached-events-overview.md).  
  
### <a name="drag-source-events"></a>Przeciągnij zdarzenia źródłowe  
  
|Wydarzenie|Podsumowanie|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.GiveFeedback>|To zdarzenie występuje w sposób ciągły podczas operacji przeciągania i upuszczania i umożliwia źródło upuszczania, aby przekazać informacje zwrotne do użytkownika. Ta informacja zwrotna jest często przez zmianę wyglądu wskaźnika myszy, aby wskazać efekty dozwolone przez miejsce docelowe upuszczania.  Jest to wydarzenie bulgotanie.|  
|<xref:System.Windows.DragDrop.QueryContinueDrag>|To zdarzenie występuje, gdy występuje zmiana w stanach klawiatury lub myszy podczas operacji przeciągania i upuszczania i umożliwia źródło upuszczania anulowanie operacji przeciągania i upuszczania w zależności od stanów klawiszy/przycisków. Jest to wydarzenie bulgotanie.|  
|<xref:System.Windows.DragDrop.PreviewGiveFeedback>|Tunelowanie wersji <xref:System.Windows.DragDrop.GiveFeedback>.|  
|<xref:System.Windows.DragDrop.PreviewQueryContinueDrag>|Tunelowanie wersji <xref:System.Windows.DragDrop.QueryContinueDrag>.|  
  
### <a name="drop-target-events"></a>Upuszczanie zdarzeń celu  
  
|Wydarzenie|Podsumowanie|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.DragEnter>|To zdarzenie występuje, gdy obiekt jest przeciągany do granicy celu upuszczania. Jest to wydarzenie bulgotanie.|  
|<xref:System.Windows.DragDrop.DragLeave>|To zdarzenie występuje, gdy obiekt jest przeciągany poza granicę celu upuszczania.  Jest to wydarzenie bulgotanie.|  
|<xref:System.Windows.DragDrop.DragOver>|To zdarzenie występuje w sposób ciągły, gdy obiekt jest przeciągany (przenoszony) w granicach celu upuszczania. Jest to wydarzenie bulgotanie.|  
|<xref:System.Windows.DragDrop.Drop>|To zdarzenie występuje, gdy obiekt jest upuszczony na miejsce docelowe upuszczania.  Jest to wydarzenie bulgotanie.|  
|<xref:System.Windows.DragDrop.PreviewDragEnter>|Tunelowanie wersji <xref:System.Windows.DragDrop.DragEnter>.|  
|<xref:System.Windows.DragDrop.PreviewDragLeave>|Tunelowanie wersji <xref:System.Windows.DragDrop.DragLeave>.|  
|<xref:System.Windows.DragDrop.PreviewDragOver>|Tunelowanie wersji <xref:System.Windows.DragDrop.DragOver>.|  
|<xref:System.Windows.DragDrop.PreviewDrop>|Tunelowanie wersji <xref:System.Windows.DragDrop.Drop>.|  
  
 Aby obsłużyć zdarzenia przeciągania i upuszczania dla wystąpień obiektu, dodaj programy obsługi dla zdarzeń wymienionych w poprzednich tabelach. Aby obsłużyć zdarzenia przeciągania i upuszczania na poziomie\*klasy, należy zastąpić odpowiednie wirtualne metody On*Event i On PreviewEvent. Aby uzyskać więcej informacji, zobacz [Obsługa klas kierowanych zdarzeń według klas podstawowych sterowania](marking-routed-events-as-handled-and-class-handling.md#Class_Handling_of_Routed_Events).  
  
<a name="Implementing_Drag_And_Drop"></a>
## <a name="implementing-drag-and-drop"></a>Implementowanie przeciągania i upuszczania  
 Element interfejsu użytkownika może być źródłem przeciągania, celem upuszczania lub obu. Aby zaimplementować podstawowe przeciąganie i upuszczanie, należy napisać kod, aby zainicjować operację przeciągania i upuszczania i przetwarzać porzucone dane. Można poprawić środowisko przeciągania i upuszczania, obsługując opcjonalne zdarzenia przeciągania i upuszczania.  
  
 Aby zaimplementować podstawowe przeciąganie i upuszczanie, należy wykonać następujące zadania:  
  
- Zidentyfikuj element, który będzie źródłem przeciągania. Źródłem przeciągania <xref:System.Windows.UIElement> może <xref:System.Windows.ContentElement>być lub .  
  
- Utwórz program obsługi zdarzeń w źródle przeciągania, który zainicjuje operację przeciągania i upuszczania. Zdarzenie jest zazwyczaj <xref:System.Windows.UIElement.MouseMove> zdarzenie.  
  
- W programie obsługi zdarzeń źródła <xref:System.Windows.DragDrop.DoDragDrop%2A> przeciągania wywołaj metodę, aby zainicjować operację przeciągania i upuszczania. W <xref:System.Windows.DragDrop.DoDragDrop%2A> wywołaniu określ źródło przeciągania, dane, które mają zostać przesłane, oraz dozwolone efekty.  
  
- Zidentyfikuj element, który będzie celem upuszczania. Cel upuszczania <xref:System.Windows.UIElement> może <xref:System.Windows.ContentElement>być lub .  
  
- Na docelowym upuszczaniu `true`ustaw właściwość na <xref:System.Windows.UIElement.AllowDrop%2A> .  
  
- W miejsce docelowe <xref:System.Windows.DragDrop.Drop> upuszczania utwórz program obsługi zdarzeń do przetwarzania porzuconych danych.  
  
- W <xref:System.Windows.DragDrop.Drop> programie obsługi zdarzeń wyodrębnić <xref:System.Windows.DragEventArgs> dane <xref:System.Windows.DataObject.GetDataPresent%2A> z <xref:System.Windows.DataObject.GetData%2A> przy użyciu i metody.  
  
- W <xref:System.Windows.DragDrop.Drop> programie obsługi zdarzeń użyj danych, aby wykonać żądaną operację przeciągania i upuszczania.  
  
 Implementację przeciągania i upuszczania można <xref:System.Windows.DataObject> poprawić, tworząc niestandardowe i obsługując opcjonalne zdarzenia docelowe źródła przeciągania i upuszczania, jak pokazano w następujących zadaniach:  
  
- Aby przenieść dane niestandardowe lub <xref:System.Windows.DataObject> wiele elementów danych, utwórz do przekazania do <xref:System.Windows.DragDrop.DoDragDrop%2A> metody.  
  
- Aby wykonać dodatkowe akcje podczas <xref:System.Windows.DragDrop.DragEnter>przeciągania, obsłużyć <xref:System.Windows.DragDrop.DragOver>, i <xref:System.Windows.DragDrop.DragLeave> zdarzenia na celu upuszczania.  
  
- Aby zmienić wygląd wskaźnika myszy, obsłuż <xref:System.Windows.DragDrop.GiveFeedback> zdarzenie w źródle przeciągania.  
  
- Aby zmienić sposób anulowania operacji przeciągania <xref:System.Windows.DragDrop.QueryContinueDrag> i upuszczania, obsłuż zdarzenie w źródle przeciągania.  
  
<a name="Drag_And_Drop_Example"></a>
## <a name="drag-and-drop-example"></a>Przykład przeciągania i upuszczania  
 W tej sekcji opisano sposób implementacji <xref:System.Windows.Shapes.Ellipse> przeciągania i upuszczania dla elementu. Jest <xref:System.Windows.Shapes.Ellipse> zarówno źródłem przeciągania, jak i celem upuszczania. Przekazane dane są reprezentacją ciągu właściwości elipsy. <xref:System.Windows.Shapes.Shape.Fill%2A> Poniższy kod XAML pokazuje <xref:System.Windows.Shapes.Ellipse> element i zdarzenia związane z przeciągania i upuszczania, które obsługuje. Aby uzyskać pełne kroki dotyczące implementowania przeciągania i upuszczania, zobacz [Przewodnik: Włączanie przeciągania i upuszczania na formancie użytkownika](walkthrough-enabling-drag-and-drop-on-a-user-control.md).  
  
 [!code-xaml[DragDropSnippets#EllipseXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#ellipsexaml)]  
  
### <a name="enabling-an-element-to-be-a-drag-source"></a>Włączanie, że element jest źródłem przeciągania  
 Obiekt, który jest źródłem przeciągania jest odpowiedzialny za:  
  
- Identyfikowanie, kiedy następuje przeciąganie.  
  
- Inicjowanie operacji przeciągania i upuszczania.  
  
- Identyfikacja danych, które mają zostać przesłane.  
  
- Określanie efektów, jakie operacja przeciągania i upuszczania może mieć na przesyłanych danych.  
  
 Źródło przeciągania może również przekazywać użytkownikowi informacje zwrotne dotyczące dozwolonych akcji (przenoszenie, kopiowanie, brak) i może anulować operację przeciągania i upuszczania na podstawie dodatkowych danych wejściowych użytkownika, takich jak naciśnięcie klawisza ESC podczas przeciągania.  
  
 Jest odpowiedzialny za aplikację, aby określić, kiedy nastąpi przeciąganie, a następnie <xref:System.Windows.DragDrop.DoDragDrop%2A> zainicjować operację przeciągania i upuszczania przez wywołanie metody. Zazwyczaj jest to, <xref:System.Windows.UIElement.MouseMove> gdy zdarzenie występuje nad elementem, który ma być przeciągany podczas naciskania przycisku myszy. W poniższym przykładzie pokazano, jak zainicjować operację <xref:System.Windows.UIElement.MouseMove> przeciągania <xref:System.Windows.Shapes.Ellipse> i upuszczania z obsługi zdarzeń elementu, aby uczynić go źródłem przeciągania. Przekazane dane są reprezentacją ciągu właściwości elipsy. <xref:System.Windows.Shapes.Shape.Fill%2A>  
  
 [!code-csharp[DragDropSnippets#DoDragDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dodragdrop)]
 [!code-vb[DragDropSnippets#DoDragDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dodragdrop)]  
  
 Wewnątrz programu <xref:System.Windows.UIElement.MouseMove> obsługi zdarzeń <xref:System.Windows.DragDrop.DoDragDrop%2A> wywołać metodę, aby zainicjować operację przeciągania i upuszczania. Metoda <xref:System.Windows.DragDrop.DoDragDrop%2A> przyjmuje trzy parametry:  
  
- `dragSource`– odwołanie do obiektu zależności, który jest źródłem przesyłanych danych; jest to zazwyczaj źródło <xref:System.Windows.UIElement.MouseMove> zdarzenia.  
  
- `data`- Obiekt, który zawiera przesłane dane, zawinięte w <xref:System.Windows.DataObject>plik .  
  
- `allowedEffects`- Jedna <xref:System.Windows.DragDropEffects> z wartości wyliczenia, która określa dozwolone efekty operacji przeciągania i upuszczania.  
  
 Dowolny obiekt serializowalny `data` może być przekazywany w parametrze. Jeśli dane nie są jeszcze <xref:System.Windows.DataObject>zawinięte w program , <xref:System.Windows.DataObject>zostaną automatycznie zawinięte w nowy plik . Aby przekazać wiele elementów danych, należy utworzyć <xref:System.Windows.DataObject> samodzielnie <xref:System.Windows.DragDrop.DoDragDrop%2A> i przekazać go do metody. Aby uzyskać więcej informacji, zobacz [Obiekty danych i danych](data-and-data-objects.md).  
  
 Parametr `allowedEffects` jest używany do określenia, co źródło przeciągania pozwoli miejsce docelowe upuszczania zrobić z przesyłanych danych. Wspólne wartości źródła przeciągania <xref:System.Windows.DragDropEffects.Move>to <xref:System.Windows.DragDropEffects.All> <xref:System.Windows.DragDropEffects.Copy>, i .  
  
> [!NOTE]
> Miejsce docelowe upuszczania jest również w stanie określić, jakie efekty zamierza w odpowiedzi na porzucone dane. Jeśli na przykład obiekt docelowy upuszczania nie rozpoznaje typu danych, który ma <xref:System.Windows.DragDropEffects.None>zostać upuszczony, może odrzucić dane, ustawiając dozwolone efekty na . Zazwyczaj robi to w <xref:System.Windows.DragDrop.DragOver> jego obsługi zdarzeń.  
  
 Źródło przeciągania może <xref:System.Windows.DragDrop.GiveFeedback> opcjonalnie obsługiwać zdarzenia i <xref:System.Windows.DragDrop.QueryContinueDrag> zdarzenia. Te zdarzenia mają domyślne programy obsługi, które są używane, chyba że oznaczysz zdarzenia jako obsługiwane. Zazwyczaj ignorujesz te zdarzenia, chyba że masz określoną potrzebę zmiany ich domyślnego zachowania.  
  
 Zdarzenie <xref:System.Windows.DragDrop.GiveFeedback> jest wywoływane w sposób ciągły podczas przeciągania źródła przeciągania. Domyślny program obsługi dla tego zdarzenia sprawdza, czy źródło przeciągania jest zaowidencjonować miejsce docelowe upuszczania. Jeśli tak jest, sprawdza dozwolone efekty docelowego upuszczania. Następnie przekazuje informacje zwrotne do użytkownika końcowego dotyczące dozwolonych efektów upuszczania. Zazwyczaj odbywa się to przez zmianę kursora myszy na kursor bez upuszczania, kopiowania lub przenoszenia. To zdarzenie należy obsługiwać tylko wtedy, gdy trzeba użyć kursorów niestandardowych, aby przekazać opinię do użytkownika. Jeśli obsługujesz to zdarzenie, należy oznaczyć go jako obsługiwane, tak aby domyślny program obsługi nie zastępuje obsługi.  
  
 Zdarzenie <xref:System.Windows.DragDrop.QueryContinueDrag> jest wywoływane w sposób ciągły podczas przeciągania źródła przeciągania. Można obsłużyć to zdarzenie, aby określić, jaka akcja kończy operację przeciągania i upuszczania na podstawie stanu klawiszy ESC, SHIFT, CTRL i ALT, a także stanu przycisków myszy. Domyślny program obsługi dla tego zdarzenia anuluje operację przeciągania i upuszczania, jeśli zostanie naciśnięty klawisz ESC, i upuszcza dane, jeśli zostanie zwolniony przycisk myszy.  
  
> [!CAUTION]
> Zdarzenia te są wywoływane w sposób ciągły podczas operacji przeciągania i upuszczania. W związku z tym należy unikać zadań intensywnie korzystających z zasobów w programach obsługi zdarzeń.  Na przykład użyj buforowanego kursora zamiast tworzenia nowego kursora za <xref:System.Windows.DragDrop.GiveFeedback> każdym razem, gdy zdarzenie jest wywoływane.  
  
### <a name="enabling-an-element-to-be-a-drop-target"></a>Włączanie elementu jako celu upuszczania  
 Obiekt, który jest celem upuszczania jest odpowiedzialny za:  
  
- Określanie, że jest to prawidłowy obiekt docelowy upuszczania.  
  
- Odpowiadanie na źródło przeciągania, gdy przeciąga się nad obiektem docelowym.  
  
- Sprawdzanie, czy przesłane dane są w formacie, który może odbierać.  
  
- Przetwarzanie porzuconych danych.  
  
 Aby określić, że element jest obiektem docelowym upuszczania, należy ustawić jego <xref:System.Windows.UIElement.AllowDrop%2A> właściwość na `true`. Zdarzenia docelowe upuszczania zostaną następnie podniesione na elemencie, dzięki czemu można je obsługiwać. Podczas operacji przeciągania i upuszczania na docelowym upuszczaniu występuje następująca sekwencja zdarzeń:  
  
1. <xref:System.Windows.DragDrop.DragEnter>  
  
2. <xref:System.Windows.DragDrop.DragOver>  
  
3. <xref:System.Windows.DragDrop.DragLeave> lub <xref:System.Windows.DragDrop.Drop>  
  
 Zdarzenie <xref:System.Windows.DragDrop.DragEnter> występuje, gdy dane są przeciągane do granicy docelowego upuszczania. Zazwyczaj obsługuje to zdarzenie, aby zapewnić podgląd efektów operacji przeciągania i upuszczania, jeśli jest to właściwe dla aplikacji. Nie należy <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> ustawiać <xref:System.Windows.DragDrop.DragEnter> właściwość w przypadku, ponieważ zostanie <xref:System.Windows.DragDrop.DragOver> ona zastąpiona w zdarzeniu.  
  
 W poniższym <xref:System.Windows.DragDrop.DragEnter> przykładzie pokazano <xref:System.Windows.Shapes.Ellipse> program obsługi zdarzeń dla elementu. Ten kod wyświetla podgląd efektów operacji przeciągania i <xref:System.Windows.Shapes.Shape.Fill%2A> upuszczania przez zapisanie bieżącego pędzla. Następnie używa metody, <xref:System.Windows.DataObject.GetDataPresent%2A> aby sprawdzić, <xref:System.Windows.DataObject> czy przeciągane przez elipsę zawiera dane ciągu, które można przekonwertować na <xref:System.Windows.Media.Brush>. Jeśli tak, dane są wyodrębniane przy użyciu <xref:System.Windows.DataObject.GetData%2A> metody. Następnie jest konwertowany na <xref:System.Windows.Media.Brush> i stosowany do elipsy. Zmiana jest przywracana <xref:System.Windows.DragDrop.DragLeave> w programie obsługi zdarzeń. Jeśli danych nie można przekonwertować na <xref:System.Windows.Media.Brush>, nie jest wykonywana żadna akcja.  
  
 [!code-csharp[DragDropSnippets#DragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragenter)]
 [!code-vb[DragDropSnippets#DragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragenter)]  
  
 Zdarzenie <xref:System.Windows.DragDrop.DragOver> występuje w sposób ciągły, gdy dane są przeciągane nad miejsce docelowe upuszczania. To zdarzenie jest sparowane ze zdarzeniem <xref:System.Windows.DragDrop.GiveFeedback> w źródle przeciągania. W <xref:System.Windows.DragDrop.DragOver> programie obsługi zdarzeń zazwyczaj <xref:System.Windows.DataObject.GetDataPresent%2A> używasz i <xref:System.Windows.DataObject.GetData%2A> metody, aby sprawdzić, czy przesyłane dane są w formacie, który można przetworzyć miejsce docelowe upuszczania. Można również sprawdzić, czy wszystkie klawisze modyfikatora są naciśnięte, które zazwyczaj wskazują, czy użytkownik zamierza przenieść lub skopiować akcję. Po wykonaniu tych kontroli, <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> należy ustawić właściwość, aby powiadomić źródło przeciągania, jaki efekt upuszczanie danych będzie miało. Źródło przeciągania odbiera <xref:System.Windows.DragDrop.GiveFeedback> te informacje w args zdarzenia i można ustawić odpowiedni kursor, aby przekazać opinię do użytkownika.  
  
 W poniższym <xref:System.Windows.DragDrop.DragOver> przykładzie pokazano <xref:System.Windows.Shapes.Ellipse> program obsługi zdarzeń dla elementu. Ten kod sprawdza, <xref:System.Windows.DataObject> czy przeciągane przez elipsę zawiera dane ciągu, <xref:System.Windows.Media.Brush>które można przekonwertować na . Jeśli tak, ustawia <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> właściwość na <xref:System.Windows.DragDropEffects.Copy>. Oznacza to dla źródła przeciągania, że dane mogą być kopiowane do elipsy. Jeśli danych nie można przekonwertować na <xref:System.Windows.Media.Brush>, właściwość jest ustawiona <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> na <xref:System.Windows.DragDropEffects.None>. Oznacza to źródło przeciągania, że elipsa nie jest prawidłowym celem upuszczania danych.  
  
 [!code-csharp[DragDropSnippets#DragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragover)]
 [!code-vb[DragDropSnippets#DragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragover)]  
  
 Zdarzenie <xref:System.Windows.DragDrop.DragLeave> występuje, gdy dane są przeciągane poza granicę obiektu docelowego bez porzucanych. Obsługi tego zdarzenia, aby cofnąć wszystko, co zostało zrobioną <xref:System.Windows.DragDrop.DragEnter> w programie obsługi zdarzeń.  
  
 W poniższym <xref:System.Windows.DragDrop.DragLeave> przykładzie pokazano <xref:System.Windows.Shapes.Ellipse> program obsługi zdarzeń dla elementu. Ten kod cofa podgląd wykonywane <xref:System.Windows.DragDrop.DragEnter> w programie obsługi zdarzeń, stosując zapisane <xref:System.Windows.Media.Brush> do elipsy.  
  
 [!code-csharp[DragDropSnippets#DragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragleave)]
 [!code-vb[DragDropSnippets#DragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragleave)]  
  
 Zdarzenie <xref:System.Windows.DragDrop.Drop> występuje, gdy dane są upuszczane nad celem upuszczania; domyślnie dzieje się tak po zwolnieniu przycisku myszy. W <xref:System.Windows.DragDrop.Drop> programie obsługi zdarzeń <xref:System.Windows.DataObject.GetData%2A> należy użyć metody wyodrębnić <xref:System.Windows.DataObject> przesłane dane z i wykonać wszelkie przetwarzanie danych, które wymaga aplikacji. Zdarzenie <xref:System.Windows.DragDrop.Drop> kończy operację przeciągania i upuszczania.  
  
 W poniższym <xref:System.Windows.DragDrop.Drop> przykładzie pokazano <xref:System.Windows.Shapes.Ellipse> program obsługi zdarzeń dla elementu. Ten kod stosuje skutki operacji przeciągania i upuszczania i jest <xref:System.Windows.DragDrop.DragEnter> podobny do kodu w programie obsługi zdarzeń. Sprawdza, czy <xref:System.Windows.DataObject> przeciągane przez elipsę zawiera dane ciągu, które można <xref:System.Windows.Media.Brush>przekonwertować na . Jeśli tak, <xref:System.Windows.Media.Brush> jest stosowany do elipsy. Jeśli danych nie można przekonwertować na <xref:System.Windows.Media.Brush>, nie jest wykonywana żadna akcja.  
  
 [!code-csharp[DragDropSnippets#Drop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#drop)]
 [!code-vb[DragDropSnippets#Drop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#drop)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Clipboard>
- [Przewodnik: włączanie przeciągania i upuszczania w kontrolce użytkownika](walkthrough-enabling-drag-and-drop-on-a-user-control.md)
- [Tematy in jakże](drag-and-drop-how-to-topics.md)
- [Przeciąganie i upuszczanie](drag-and-drop.md)
