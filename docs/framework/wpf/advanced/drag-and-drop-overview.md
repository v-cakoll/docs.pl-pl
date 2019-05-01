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
ms.openlocfilehash: 2b76c8fd3e2c6961b6ebdddc9b7ff9649f5196f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051640"
---
# <a name="drag-and-drop-overview"></a>Przegląd Przeciąganie i upuszczanie
Ten temat zawiera omówienie obsługi przeciągania i upuszczania w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji. Przeciągnij i upuść często odnosi się do metody transferu danych, która polega na użyciu myszy (lub inne urządzenie wskazujące) zaznacz jeden lub więcej obiektów, przeciągając obiekty za pośrednictwem niektórych żądanego miejsca docelowego w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]i upuszczając je.  

<a name="Drag_and_Drop_Support"></a>   
## <a name="drag-and-drop-support-in-wpf"></a>Obsługa przeciągania i upuszczania w WPF  
 Operacji przeciągania i upuszczania zwykle obejmują dwie strony: przeciągnij źródło, z której pochodzi przeciągany obiekt i miejsca docelowego, który odbiera upuszczony obiekt.  Docelowy przeciągania źródłowej i docelowej mogą być elementy interfejsu użytkownika w tej samej aplikacji lub innej aplikacji.  
  
 Typ i liczbę obiektów, które mogą być zmieniane za pomocą przeciągania i upuszczania jest całkowicie dowolnego. Na przykład pliki, foldery i opcje zawartości są niektórych obiektów częściej manipulować przy użyciu operacji przeciągania i upuszczania.  
  
 Określonej akcji wykonywanych podczas operacji przeciągania i upuszczania są aplikacji określonych i często określone przez kontekst.  Na przykład przeciągając zaznaczone pliki z jednego folderu do innego na tym samym urządzeniu magazynującym przenosi pliki domyślnie, natomiast przeciąganie plików z [!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)] udziału do folderu lokalnego kopiuje pliki domyślnie.  
  
 Funkcji przeciągania i upuszczania, dostarczone przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są przeznaczone do wysoce elastyczny i możliwe do dostosowania do obsługi szerokiej gamy scenariuszy przeciągania i upuszczania.  Obsługa przeciągania i upuszczania, manipulowania obiektami w ramach jednej aplikacji lub między różnymi aplikacjami. Przeciąganie i upuszczanie między [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji i innych aplikacji Windows jest również w pełni obsługiwane.  
  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], any <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement> mogą brać udział w przeciągania i upuszczania. Zdarzenia i metody wymagane dla operacji przeciągania i upuszczania są zdefiniowane w <xref:System.Windows.DragDrop> klasy. <xref:System.Windows.UIElement> i <xref:System.Windows.ContentElement> klasy zawierają aliasów <xref:System.Windows.DragDrop> dołączone zdarzenia, tak aby zdarzenia wyświetlane w klasie listy elementów członkowskich, gdy <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement> jest dziedziczone jako podstawowy element. Programy obsługi zdarzeń, które są dołączone do tych zdarzeń są dołączone do podstawowej <xref:System.Windows.DragDrop> dołączone zdarzenie i odbierać to samo wystąpienie danych zdarzeń. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.UIElement.Drop?displayProperty=nameWithType> zdarzeń.  
  
> [!IMPORTANT]
>  OLE przeciągania i upuszczania nie działa w strefie Internet.  
  
<a name="Data_Transfer"></a>   
## <a name="data-transfer"></a>Transfer danych  
 Przeciągnij i upuść jest częścią obszaru bardziej ogólnych transferu danych. Transfer danych obejmuje operacje przeciągania i upuszczania oraz kopiowania i wklejania. Operacja przeciągania i upuszczania jest analogiczne do operacji kopiowania i wklejania lub Wytnij i Wklej, używany do przesyłania danych z jednego obiektu lub aplikacji do innej przy użyciu schowka systemowego. Wymagaj oba rodzaje operacji:  
  
- Obiekt źródłowy, który zawiera dane.  
  
- Sposób do tymczasowego przechowywania przeniesionych danych.  
  
- Obiekt docelowy, który odbiera dane.  
  
 W ramach operacji kopiowania i wklejania schowka systemowego jest używana do tymczasowego przechowywania przeniesionych danych; w ramach operacji przeciągania i upuszczania <xref:System.Windows.DataObject> służy do przechowywania danych. Model obiektu danych składa się z jednego lub więcej par <xref:System.Object> zawiera dane rzeczywiste i odpowiedni identyfikator format danych.  
  
 Elementem źródłowym przeciągania inicjuje operację przeciągania i upuszczania, przez wywołanie statycznego <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> metody i przekazywanie danych przekazywanych do niego. <xref:System.Windows.DragDrop.DoDragDrop%2A> Metoda będzie automatycznie zawijany dane w <xref:System.Windows.DataObject> w razie potrzeby. Aby uzyskać większą kontrolę nad formatem danych może zawijać się dane w <xref:System.Windows.DataObject> przed przekazaniem go do <xref:System.Windows.DragDrop.DoDragDrop%2A> metody. Element docelowy upuszczania jest odpowiedzialny za wyodrębnienie danych z <xref:System.Windows.DataObject>. Aby uzyskać więcej informacji na temat pracy z obiektami danych, zobacz [dane i obiekty danych](data-and-data-objects.md).  
  
 Źródłowy i docelowy operacji przeciągania i upuszczania elementów interfejsu użytkownika; dane, które są faktycznie przesyłane zwykle nie ma jednak wizualnej reprezentacji. Można napisać kod, aby zapewnić wizualną reprezentację danych, które zostanie przeciągnięty, takich jak występuje podczas przeciągania pliki w Eksploratorze Windows. Domyślnie opinii jest udostępniany użytkownikowi, zmieniając kursor do reprezentowania efekt tego operacji przeciągania i upuszczania na dane, takie jak czy zostanie przeniesiona lub skopiować dane.  
  
### <a name="drag-and-drop-effects"></a>Drag-and-Drop Effects  
 Operacje przeciągania i upuszczania może mieć inny wpływ na przeniesione dane. Na przykład możesz skopiować dane, lub można przenieść dane. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definiuje <xref:System.Windows.DragDropEffects> wyliczenie, które można użyć, aby określić wpływ operacji przeciągania i upuszczania. Źródła przeciągania można określić efekty, które pozwoli źródła w <xref:System.Windows.DragDrop.DoDragDrop%2A> metody. W celu upuszczania można określić wpływ, jaki element docelowy zamierza w <xref:System.Windows.DragEventArgs.Effects%2A> właściwość <xref:System.Windows.DragEventArgs> klasy. Gdy element docelowy upuszczania określa jego zamierzony efekt w <xref:System.Windows.DragDrop.DragOver> zdarzenia, które informacje jest przekazywany z powrotem do źródła przeciągania w <xref:System.Windows.DragDrop.GiveFeedback> zdarzeń. Elementem źródłowym przeciągania używa tych informacji, aby poinformować użytkownika wpływ, jaki element docelowy upuszczania zamierza na danych. Gdy danych zostało porzucone, element docelowy upuszczania określa jego rzeczywisty wpływ w <xref:System.Windows.DragDrop.Drop> zdarzeń. Czy informacje są przekazywane do źródła przeciągania jako wartość zwracaną <xref:System.Windows.DragDrop.DoDragDrop%2A> metody. Jeśli element docelowy upuszczania zwraca efektu, który nie jest na liście źródła przeciągania `allowedEffects`, przeciągnij i upuść operacja została anulowana, bez przekazywania danych pojawiają się.  
  
 Należy pamiętać, że w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.DragDropEffects> wartości są używane tylko w celu zapewnienia komunikacji między elementem źródłowym przeciągania i element docelowy upuszczania dotyczące wpływu operacji przeciągania i upuszczania. Rzeczywisty wynik operacji przeciągania i upuszczania zależy od napisać odpowiedni kod w aplikacji.  
  
 Element docelowy upuszczania może na przykład określić, czy usunięcie danych na nim powoduje przenoszenia danych. Jednak do przenoszenia danych, musi być zarówno dodawane do elementu docelowego i usunięta z elementu źródłowego. Element źródłowy może wskazywać, że umożliwia przenoszenie danych, ale jeśli nie podasz kod, aby usunąć dane z elementu źródłowego, wynik końcowy będzie czy dane są kopiowane i nieruchomy.  
  
<a name="Drag_and_Drop_Events"></a>   
## <a name="drag-and-drop-events"></a>Przeciągnij i upuść zdarzenia  
 Operacje przeciągania i upuszczania obsługuje model oparte na zdarzeniach.  Elementem źródłowym przeciągania i element docelowy upuszczania Użyj standardowy zestaw zdarzeń, do obsługi operacji przeciągania i upuszczania.  W poniższych tabelach zestawiono standardowych zdarzeń przeciągania i upuszczania. Zdarzenia dołączone znajdują się na <xref:System.Windows.DragDrop> klasy. Aby uzyskać więcej informacji na temat zdarzenia dołączone zobacz [Przegląd zdarzeń dołączonych](attached-events-overview.md).  
  
### <a name="drag-source-events"></a>Przeciągnij źródła zdarzeń  
  
|Zdarzenie|Podsumowanie|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.GiveFeedback>|To zdarzenie występuje stale podczas operacji przeciągania i upuszczania, a także umożliwia miejsca źródłowego oferowanie formularza opinii użytkownika. To często zwrotnych, zmieniając wygląd wskaźnik myszy do wskazania efekty dozwolone przez element docelowy upuszczania.  Jest to zdarzenie propagacji.|  
|<xref:System.Windows.DragDrop.QueryContinueDrag>|To zdarzenie występuje, gdy nie nastąpiła zmiana w klawiatury lub przycisku myszy stany podczas operacji przeciągania i upuszczania i umożliwia miejsca źródłowego anulować operację przeciągania i upuszczania w zależności od Państwa przycisk/klucz. Jest to zdarzenie propagacji.|  
|<xref:System.Windows.DragDrop.PreviewGiveFeedback>|Wersja tunelowania <xref:System.Windows.DragDrop.GiveFeedback>.|  
|<xref:System.Windows.DragDrop.PreviewQueryContinueDrag>|Wersja tunelowania <xref:System.Windows.DragDrop.QueryContinueDrag>.|  
  
### <a name="drop-target-events"></a>Docelowy upuszczania.  
  
|Zdarzenie|Podsumowanie|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.DragEnter>|To zdarzenie występuje, gdy obiekt zostanie przeciągnięty do granic miejsca docelowego. Jest to zdarzenie propagacji.|  
|<xref:System.Windows.DragDrop.DragLeave>|To zdarzenie występuje, gdy obiekt zostanie przeciągnięty poza granicą miejsca docelowego.  Jest to zdarzenie propagacji.|  
|<xref:System.Windows.DragDrop.DragOver>|To zdarzenie występuje stale, gdy obiekt zostanie przeciągnięty (przeniesione) w obrębie granicy miejsca docelowego. Jest to zdarzenie propagacji.|  
|<xref:System.Windows.DragDrop.Drop>|To zdarzenie występuje, gdy obiekt został upuszczony na element docelowy upuszczania.  Jest to zdarzenie propagacji.|  
|<xref:System.Windows.DragDrop.PreviewDragEnter>|Wersja tunelowania <xref:System.Windows.DragDrop.DragEnter>.|  
|<xref:System.Windows.DragDrop.PreviewDragLeave>|Wersja tunelowania <xref:System.Windows.DragDrop.DragLeave>.|  
|<xref:System.Windows.DragDrop.PreviewDragOver>|Wersja tunelowania <xref:System.Windows.DragDrop.DragOver>.|  
|<xref:System.Windows.DragDrop.PreviewDrop>|Wersja tunelowania <xref:System.Windows.DragDrop.Drop>.|  
  
 Do obsługi zdarzeń przeciągania i upuszczania dla wystąpień obiektu, dodawanie obsługi zdarzeń wymienionych w poprzednich tabelach. Do obsługi przeciągania i upuszczania zdarzeń na poziomie klasy, należy zastąpić, odpowiedni wirtualny na * zdarzeń i\*PreviewEvent metody. Aby uzyskać więcej informacji, zobacz [klasy obsługi dla zdarzeń trasowanych przez klasy podstawowej kontroli](marking-routed-events-as-handled-and-class-handling.md#Class_Handling_of_Routed_Events).  
  
<a name="Implementing_Drag_And_Drop"></a>   
## <a name="implementing-drag-and-drop"></a>Implementowanie przeciągania i upuszczania  
 Element interfejsu użytkownika może być źródła przeciągania i/lub miejsca docelowego. Aby zaimplementować podstawowe przeciągania i upuszczania, pisania kodu, można zainicjować operacji przeciągania i upuszczania oraz do przetwarzania elementów usuniętych danych. Dzięki obsłudze opcjonalne zdarzenia przeciągania i upuszczania, możesz zwiększyć obsługi przeciągania i upuszczania.  
  
 Aby zaimplementować podstawowe przeciągania i upuszczania, wykonasz następujące zadania:  
  
- Określ element, który ma być źródła przeciągania. Źródła przeciągania może być <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement>.  
  
- Utwórz procedurę obsługi zdarzeń na elementem źródłowym przeciągania, która zainicjuje operację przeciągania i upuszczania. Zdarzenie jest zazwyczaj <xref:System.Windows.UIElement.MouseMove> zdarzeń.  
  
- W obsłudze zdarzeń źródła przeciągania, należy wywołać <xref:System.Windows.DragDrop.DoDragDrop%2A> metodę, aby zainicjować operację przeciągania i upuszczania. W <xref:System.Windows.DragDrop.DoDragDrop%2A> wywołań, określ źródła przeciągania, transfer danych i dozwolone efekty.  
  
- Określ element, który ma być miejsca docelowego. Miejsca docelowego może być <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement>.  
  
- Na element docelowy upuszczania ustaw <xref:System.Windows.UIElement.AllowDrop%2A> właściwość `true`.  
  
- Element docelowy upuszczania tworzenia <xref:System.Windows.DragDrop.Drop> program obsługi zdarzeń do przetwarzania elementów usuniętych danych.  
  
- W <xref:System.Windows.DragDrop.Drop> procedura obsługi zdarzeń, wyodrębnianie danych z <xref:System.Windows.DragEventArgs> przy użyciu <xref:System.Windows.DataObject.GetDataPresent%2A> i <xref:System.Windows.DataObject.GetData%2A> metody.  
  
- W <xref:System.Windows.DragDrop.Drop> procedura obsługi zdarzeń, korzystać z danych można wykonać żądanej operacji przeciągania i upuszczania.  
  
 Możesz zwiększyć implementacji przeciągania i upuszczania, tworząc niestandardowe <xref:System.Windows.DataObject> i obsługi opcjonalne przeciągnij źródłowej i docelowej zdarzenia docelowy, jak pokazano w następujących zadań:  
  
- Transfer danych niestandardowych lub wielu elementów danych, należy utworzyć <xref:System.Windows.DataObject> do przekazania do <xref:System.Windows.DragDrop.DoDragDrop%2A> metody.  
  
- Aby wykonać dodatkowe akcje podczas przeciągania, obsługi <xref:System.Windows.DragDrop.DragEnter>, <xref:System.Windows.DragDrop.DragOver>, i <xref:System.Windows.DragDrop.DragLeave> zdarzenia na element docelowy upuszczania.  
  
- Aby zmienić wygląd wskaźnika myszy, obsługi <xref:System.Windows.DragDrop.GiveFeedback> zdarzenie w systemie źródłowym przeciągania.  
  
- Aby zmienić sposób operacji przeciągania i upuszczania zostanie anulowane, obsługi <xref:System.Windows.DragDrop.QueryContinueDrag> zdarzenie w systemie źródłowym przeciągania.  
  
<a name="Drag_And_Drop_Example"></a>   
## <a name="drag-and-drop-example"></a>Przykład przeciągnij i upuść  
 W tej sekcji opisano sposób implementacji przeciągania i upuszczania dla <xref:System.Windows.Shapes.Ellipse> elementu. <xref:System.Windows.Shapes.Ellipse> Źródła przeciągania i miejsca docelowego. Przeniesione dane jest reprezentacją ciągu elipsy <xref:System.Windows.Shapes.Shape.Fill%2A> właściwości. Pokazano w poniższym XAML <xref:System.Windows.Shapes.Ellipse> elementu i przeciągnij i upuść zdarzenia powiązane, które obsługuje. Aby uzyskać pełne instrukcje dotyczące sposobu implementacji przeciągania i upuszczania, zobacz [instruktażu: Włączanie przeciągania i upuszczania w kontrolce użytkownika](walkthrough-enabling-drag-and-drop-on-a-user-control.md).  
  
 [!code-xaml[DragDropSnippets#EllipseXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#ellipsexaml)]  
  
### <a name="enabling-an-element-to-be-a-drag-source"></a>Włączanie element jako Element źródłowy przeciągania  
 Obiekt, który jest źródłem przeciągania jest odpowiedzialny za:  
  
- Identyfikowanie sytuacji przeciągania.  
  
- Inicjowanie operacji przeciągania i upuszczania.  
  
- Identyfikowanie przekazywanych danych.  
  
- Określanie efekty, które może mieć na przeniesione dane operacji przeciągania i upuszczania.  
  
 Elementem źródłowym przeciągania może również dawać opinie użytkowników dotyczące dozwolonych akcji (przenieść, skopiuj none) i anulować operację przeciągania i upuszczania, na podstawie danych wejściowych użytkownika dodatkowe, takie jak naciśnięcie klawisza ESC podczas przeciągania.  
  
 Jest odpowiedzialny za aplikację, aby określić, gdy wystąpi przeciągnij, a następnie zainicjuj przeciąganie i upuszczanie działania, wywołując <xref:System.Windows.DragDrop.DoDragDrop%2A> metody. Zazwyczaj jest to kiedy <xref:System.Windows.UIElement.MouseMove> zdarzeń odbywa się za pośrednictwem elementu, który ma być przeciągane naciśnięciu przycisku myszy. Poniższy przykład pokazuje, jak zainicjować operację przeciągania i upuszczania z <xref:System.Windows.UIElement.MouseMove> program obsługi zdarzeń <xref:System.Windows.Shapes.Ellipse> element, aby stał się źródłom przeciągania. Przeniesione dane jest reprezentacją ciągu elipsy <xref:System.Windows.Shapes.Shape.Fill%2A> właściwości.  
  
 [!code-csharp[DragDropSnippets#DoDragDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dodragdrop)]
 [!code-vb[DragDropSnippets#DoDragDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dodragdrop)]  
  
 Wewnątrz <xref:System.Windows.UIElement.MouseMove> programu obsługi zdarzeń, wywołanie <xref:System.Windows.DragDrop.DoDragDrop%2A> metodę, aby zainicjować operację przeciągania i upuszczania. <xref:System.Windows.DragDrop.DoDragDrop%2A> Metoda przyjmuje trzy parametry:  
  
- `dragSource` — Odwołanie do obiektu zależności, który jest źródłem przeniesionych danych. Zazwyczaj jest to źródło <xref:System.Windows.UIElement.MouseMove> zdarzeń.  
  
- `data` -Obiekt, który zawiera przeniesione dane, zapakowane w <xref:System.Windows.DataObject>.  
  
- `allowedEffects` -Jedno z <xref:System.Windows.DragDropEffects> wartości wyliczenia, które określa dozwolone efekty operacji przeciągania i upuszczania.  
  
 Mogą być przekazywane dowolnego obiektu podlegającego serializacji `data` parametru. Jeśli dane nie jest już opakowana w <xref:System.Windows.DataObject>, zostanie zawinięta automatycznie w nowym <xref:System.Windows.DataObject>. Aby przekazać wiele elementów danych, należy utworzyć <xref:System.Windows.DataObject> samodzielnie i przekazać ją do <xref:System.Windows.DragDrop.DoDragDrop%2A> metody. Aby uzyskać więcej informacji, zobacz [dane i obiekty danych](data-and-data-objects.md).  
  
 `allowedEffects` Parametr jest używany do określenia, jakie źródła przeciągania umożliwi miejsca docelowego wykonać za pomocą przeniesione dane. Typowe wartości dla źródła przeciągania <xref:System.Windows.DragDropEffects.Copy>, <xref:System.Windows.DragDropEffects.Move>, i <xref:System.Windows.DragDropEffects.All>.  
  
> [!NOTE]
>  Element docelowy upuszczania jest również mogą określić, jakie skutki zamierza w odpowiedzi na dane porzucone. Na przykład, jeśli element docelowy upuszczania nie rozpoznaje typ danych ma zostać przerwane, można odmówić dane, ustawiając jego dozwolone efekty <xref:System.Windows.DragDropEffects.None>. Dzieje się tak zwykle jego <xref:System.Windows.DragDrop.DragOver> programu obsługi zdarzeń.  
  
 Źródła przeciągania może opcjonalnie obsługiwać <xref:System.Windows.DragDrop.GiveFeedback> i <xref:System.Windows.DragDrop.QueryContinueDrag> zdarzenia. Zdarzenia te mają obsługi domyślne, które są używane, chyba że oznaczenia zdarzeń jako obsługiwane. Zwykle będzie ignorować te zdarzenia, chyba że istnieje konkretna potrzeba zmieniać swojego zachowania domyślnego.  
  
 <xref:System.Windows.DragDrop.GiveFeedback> Zdarzenie jest zgłaszane w stale, podczas przeciągania elementem źródłowym przeciągania. Domyślny program obsługi dla tego zdarzenia sprawdza, czy elementem źródłowym przeciągania za pośrednictwem prawidłowe miejsca docelowego. Jeśli tak jest, sprawdza dozwolone efekty miejsca docelowego. Następnie przekazuje opinie do użytkownika końcowego dotyczące wpływu listy dozwolonych. To jest zazwyczaj wykonywane przez zmianę kursor myszy na nieupuszczalny, kopiowania, ani nie przenoś kursora. To zdarzenie powinna obsługiwać tylko, jeśli należy użyć niestandardowych kursorów, aby przekazać opinię do użytkownika. Możesz obsługiwać to zdarzenie, należy oznaczyć go jako obsłużony, tak aby domyślny program obsługi nie zastępuje programu obsługi.  
  
 <xref:System.Windows.DragDrop.QueryContinueDrag> Zdarzenie jest zgłaszane w stale, podczas przeciągania elementem źródłowym przeciągania. Może obsługiwać to zdarzenie, aby określić, jaką akcję kończy operację przeciągania i upuszczania, oparte na stanie ESC, SHIFT, CTRL i ALT — klawisze, a także stan przycisku myszy. Domyślny program obsługi dla tego zdarzenia anuluje operację przeciągania i upuszczania, jeśli klawisz ESC naciśnięciu i umieszcza dane, jeśli zwolnieniu przycisku myszy.  
  
> [!CAUTION]
>  Te zdarzenia są wywoływane podczas operacji przeciągania i upuszczania. W związku z tym należy unikać zadania intensywnie obciążające w procedurze obsługi zdarzeń.  Na przykład użyć kursora pamięci podręcznej, zamiast tworzyć nowy kursor każdorazowo <xref:System.Windows.DragDrop.GiveFeedback> zdarzenie jest wywoływane.  
  
### <a name="enabling-an-element-to-be-a-drop-target"></a>Włączanie element jako Element docelowy upuszczania  
 Obiekt, który jest miejsca docelowego jest odpowiedzialny za:  
  
- Określenie, czy jest prawidłowe miejsca docelowego.  
  
- Podczas przeciągania go przez przez element docelowy i odpowiada do źródła przeciągania.  
  
- Sprawdzanie, czy przeniesionych danych jest w formacie, który może zostać wyświetlony.  
  
- Przetwarzanie danych porzucone.  
  
 Aby określić, czy element jest miejsca docelowego, możesz ustawić jej <xref:System.Windows.UIElement.AllowDrop%2A> właściwość `true`. Docelowego upuszczania następnie zostanie wygenerowany w elemencie, tak aby mógł je obsłużyć. Podczas operacji przeciągania i upuszczania w element docelowy upuszczania ma miejsce następująca sekwencja zdarzeń:  
  
1. <xref:System.Windows.DragDrop.DragEnter>  
  
2. <xref:System.Windows.DragDrop.DragOver>  
  
3. <xref:System.Windows.DragDrop.DragLeave> lub <xref:System.Windows.DragDrop.Drop>  
  
 <xref:System.Windows.DragDrop.DragEnter> Zdarzenie występuje, gdy dane zostanie przeciągnięty do granic miejsca docelowego. To zdarzenie do podglądu skutków operacji przeciągania i upuszczania, zwykle obsłużyć, jeśli jest to odpowiedni dla aplikacji. Nie należy ustawiać <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> właściwość <xref:System.Windows.DragDrop.DragEnter> zdarzenie, ponieważ zostaną zastąpione w <xref:System.Windows.DragDrop.DragOver> zdarzeń.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.DragDrop.DragEnter> program obsługi zdarzeń dla <xref:System.Windows.Shapes.Ellipse> elementu. Ten kod wyświetla podgląd skutków operacji przeciągania i upuszczania, zapisując bieżącego <xref:System.Windows.Shapes.Shape.Fill%2A> pędzla. Następnie używa <xref:System.Windows.DataObject.GetDataPresent%2A> metodę sprawdzania, czy <xref:System.Windows.DataObject> Przeciąganie kursorem na wielokropek zawiera dane ciągów, które mogą być konwertowane na <xref:System.Windows.Media.Brush>. Jeśli tak, dane są wyodrębniane, za pomocą <xref:System.Windows.DataObject.GetData%2A> metody. Następnie jest konwertowany na <xref:System.Windows.Media.Brush> i zastosowane do elipsy. Zmiana zostanie wycofana w <xref:System.Windows.DragDrop.DragLeave> programu obsługi zdarzeń. Jeśli nie można przekonwertować danych <xref:System.Windows.Media.Brush>, jest wykonywana żadna akcja.  
  
 [!code-csharp[DragDropSnippets#DragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragenter)]
 [!code-vb[DragDropSnippets#DragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragenter)]  
  
 <xref:System.Windows.DragDrop.DragOver> Wystąpi zdarzenie ciągle w przypadku, gdy dane jest przeciągany nad element docelowy upuszczania. To zdarzenie jest powiązany z <xref:System.Windows.DragDrop.GiveFeedback> zdarzenie w systemie źródłowym przeciągania. W <xref:System.Windows.DragDrop.DragOver> procedura obsługi zdarzeń, zazwyczaj używa się <xref:System.Windows.DataObject.GetDataPresent%2A> i <xref:System.Windows.DataObject.GetData%2A> metody, aby sprawdzić, czy przeniesione dane w formacie, który może przetwarzać miejsca docelowego. Można również sprawdzić, czy wszystkie klawisze modyfikujące naciśnięciu, które będą zwykle wskazywać, czy użytkownik zamierza akcji przenosić ani kopiować. Po te testy są wykonywane, możesz ustawić <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> właściwości, aby powiadomić przeciągania źródła, będzie miał wpływ, jaki usunięcie danych. Elementem źródłowym przeciągania otrzymuje te informacje w <xref:System.Windows.DragDrop.GiveFeedback> argumenty zdarzenia i ustawić odpowiednie kursora, aby przesłać opinię dla użytkownika.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.DragDrop.DragOver> program obsługi zdarzeń dla <xref:System.Windows.Shapes.Ellipse> elementu. Ten kod sprawdza, czy <xref:System.Windows.DataObject> Przeciąganie kursorem na wielokropek zawiera dane ciągów, które mogą być konwertowane na <xref:System.Windows.Media.Brush>. Jeśli tak, ustawia <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> właściwość <xref:System.Windows.DragDropEffects.Copy>. Wskazuje elementem źródłowym przeciągania, można skopiować danych do elipsy. Jeśli nie można przekonwertować danych <xref:System.Windows.Media.Brush>, <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> właściwość jest ustawiona na <xref:System.Windows.DragDropEffects.None>. Wskazuje elementem źródłowym przeciągania czy elipsy nie jest prawidłową miejsca docelowego dla danych.  
  
 [!code-csharp[DragDropSnippets#DragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragover)]
 [!code-vb[DragDropSnippets#DragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragover)]  
  
 <xref:System.Windows.DragDrop.DragLeave> Zdarzenie występuje, gdy dane jest przeciągnąć poza granicą elementu docelowego bez porzucana. Obsługa tego zdarzenia, aby cofnąć wszystkie elementy, które zostały w <xref:System.Windows.DragDrop.DragEnter> programu obsługi zdarzeń.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.DragDrop.DragLeave> program obsługi zdarzeń dla <xref:System.Windows.Shapes.Ellipse> elementu. Ten kod cofa wykonywane w wersji zapoznawczej <xref:System.Windows.DragDrop.DragEnter> programu obsługi zdarzeń, stosując zapisane <xref:System.Windows.Media.Brush> do elipsy.  
  
 [!code-csharp[DragDropSnippets#DragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragleave)]
 [!code-vb[DragDropSnippets#DragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragleave)]  
  
 <xref:System.Windows.DragDrop.Drop> Zdarzenie występuje, gdy dane jest przenoszony przez element docelowy upuszczania; domyślnie tak się stanie po zwolnieniu przycisku myszy. W <xref:System.Windows.DragDrop.Drop> procedura obsługi zdarzeń, możesz użyć <xref:System.Windows.DataObject.GetData%2A> metodę, aby wyodrębnić przeniesione dane z <xref:System.Windows.DataObject> i wykonywać żadnego przetwarzania danych wymaganych przez aplikację. <xref:System.Windows.DragDrop.Drop> Niezrealizowane operacji przeciągania i upuszczania.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.DragDrop.Drop> program obsługi zdarzeń dla <xref:System.Windows.Shapes.Ellipse> elementu. Ten kod ma zastosowanie efektów operacji przeciągania i upuszczania i jest podobna do kodu w <xref:System.Windows.DragDrop.DragEnter> programu obsługi zdarzeń. Sprawdza, czy <xref:System.Windows.DataObject> Przeciąganie kursorem na wielokropek zawiera dane ciągów, które mogą być konwertowane na <xref:System.Windows.Media.Brush>. Jeśli tak, <xref:System.Windows.Media.Brush> jest stosowany do elipsy. Jeśli nie można przekonwertować danych <xref:System.Windows.Media.Brush>, jest wykonywana żadna akcja.  
  
 [!code-csharp[DragDropSnippets#Drop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#drop)]
 [!code-vb[DragDropSnippets#Drop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#drop)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Clipboard>
- [Przewodnik: Włączanie przeciągania i upuszczania w kontrolce użytkownika](walkthrough-enabling-drag-and-drop-on-a-user-control.md)
- [Tematy z instrukcjami](drag-and-drop-how-to-topics.md)
- [Przeciąganie i upuszczanie](drag-and-drop.md)
