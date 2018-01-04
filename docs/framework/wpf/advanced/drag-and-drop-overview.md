---
title: "Przegląd Przeciąganie i upuszczanie"
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
- drag-and-drop [WPF], implementing
- drag sources [WPF], drag-and-drop
- data transfer [WPF], drag-and-drop
- drag-and-drop [WPF], about
- drag-and-drop [WPF], events
- drop targets [WPF], drag-and-drop
ms.assetid: 1a5b27b0-0ac5-4cdf-86c0-86ac0271fa64
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b7a69a4dcd5fc39b700bf9c3404e70d581509ebc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="drag-and-drop-overview"></a>Przegląd Przeciąganie i upuszczanie
Ten temat zawiera omówienie Obsługa przeciągania i upuszczania w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji. Przeciągnij i upuść często odwołuje się do metody transferu danych, która obejmuje za pomocą myszy (lub innego urządzenia wskazującego) wybierz co najmniej jeden obiekt, przeciągając obiekty te przez niektóre odpowiednie miejsca docelowego w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]i ich usunięcie.  
  
  
<a name="Drag_and_Drop_Support"></a>   
## <a name="drag-and-drop-support-in-wpf"></a>Obsługa przeciągania i upuszczania na platformie WPF  
 Operacje przeciągania i upuszczania zwykle obejmują dwie strony: przeciągnij źródło, z którego pochodzi przeciąganego obiektu i miejsca docelowego, który odbiera upuszczony obiekt.  Element docelowy źródła i upuszczanie przeciągania może być elementy interfejsu użytkownika w tej samej aplikacji lub innej aplikacji.  
  
 Typ i liczbę obiektów, które można modyfikować za pomocą przeciągania i upuszczania jest całkowicie dowolnego. Na przykład pliki, foldery i opcje zawartości są niektóre obiekty częściej manipulować przy użyciu operacji przeciągania i upuszczania.  
  
 Określonej akcji wykonywanych podczas operacji przeciągania i upuszczania są aplikacji określonych i często określone przez kontekst.  Na przykład przeciąganie zaznaczone pliki z jednego folderu do innego na tym samym urządzeniu magazynującym przenosi pliki domyślnie, podczas gdy przeciąganie plików z [!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)] udziału do folderu lokalnego kopiuje pliki domyślnie.  
  
 Funkcji przeciągania i upuszczania podał [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mają być bardzo elastyczne i dostosowywanych do obsługi różnych scenariuszy przeciągania i upuszczania.  Obsługa przeciągania i upuszczania manipulowanie obiektów wewnątrz aplikacji lub między różnymi aplikacjami. Przeciąganie i upuszczanie między [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji i innych [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)] aplikacji jest także w pełni obsługiwane.  
  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]oraz <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement> mogą uczestniczyć w przeciągania i upuszczania. Zdarzenia i metody wymagane dla operacji przeciągania i upuszczania są zdefiniowane w <xref:System.Windows.DragDrop> klasy. <xref:System.Windows.UIElement> i <xref:System.Windows.ContentElement> klasy zawierać aliasy <xref:System.Windows.DragDrop> dołączone zdarzenia, dzięki czemu zdarzenia wyświetlane w klasie listy elementów członkowskich, gdy <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement> jest dziedziczona jako podstawowy element. Programy obsługi zdarzeń, które są dołączone do tych zdarzeń są dołączone do odpowiadającego <xref:System.Windows.DragDrop> dołączony zdarzeń i odbierać to samo wystąpienie danych zdarzenia. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.UIElement.Drop?displayProperty=nameWithType> zdarzeń.  
  
> [!IMPORTANT]
>  OLE przeciągania i upuszczania nie działa w strefie Internet.  
  
<a name="Data_Transfer"></a>   
## <a name="data-transfer"></a>Transfer danych  
 Przeciągnij i upuść jest częścią obszaru bardziej ogólne transferu danych. Transfer danych obejmuje operacje przeciągania i upuszczania oraz kopiowania i wklejania. Operacja przeciągania i upuszczania jest odpowiednikiem operacji kopiowania i wklejania lub wycinanie i wklejanie, używany do przenoszenia danych z jednego obiektu lub aplikacji do innej przy użyciu schowka systemowego. Wymagaj oba typy działań:  
  
-   Obiekt źródłowy, który udostępnia dane.  
  
-   Sposób do tymczasowego przechowywania danych przeniesione.  
  
-   Obiekt docelowy, który odbiera dane.  
  
 W operacji kopiowania i wklejania Schowka systemu jest używana do tymczasowego przechowywania danych przekazanych; w ramach operacji przeciągania i upuszczania <xref:System.Windows.DataObject> służy do przechowywania danych. Koncepcyjnie, obiekt danych składa się z jednego lub więcej par <xref:System.Object> zawierający dane i odpowiedni identyfikator formatu danych.  
  
 Źródła przeciągania inicjuje operację przeciągania i upuszczania, wywołując statycznych <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> — metoda i przekazywanie danych przekazanych do niego. <xref:System.Windows.DragDrop.DoDragDrop%2A> Metoda będzie automatycznie zawijany dane w <xref:System.Windows.DataObject> w razie potrzeby. Aby uzyskać większą kontrolę nad format danych, może zawijać się dane w <xref:System.Windows.DataObject> przed przekazaniem go do <xref:System.Windows.DragDrop.DoDragDrop%2A> metody. Element docelowy upuszczania jest odpowiedzialny za wyodrębnianie danych z <xref:System.Windows.DataObject>. Aby uzyskać więcej informacji na temat pracy z obiektami danych, zobacz [danych i obiektów danych](../../../../docs/framework/wpf/advanced/data-and-data-objects.md).  
  
 Źródło i cel operacji przeciągnij i upuść są elementy interfejsu użytkownika; Jednak dane, które są rzeczywiście przesyłane zwykle nie ma wizualną reprezentację. Można napisać kod, aby zapewnić wizualną reprezentację danych, która zostanie przeciągnięty, takich jak występuje, gdy przeciąganie plików w Eksploratorze Windows. Domyślnie opinie są udostępniane użytkownikowi przez kursor do reprezentowania wpływu tego operacji przeciągania i upuszczania na dane, takie jak zmiana czy zostanie przeniesiona lub skopiować dane.  
  
### <a name="drag-and-drop-effects"></a>Efekty przeciągnij i upuść  
 Operacje przeciągania i upuszczania mogą mieć inny wpływ na przeniesionych danych. Na przykład można skopiować danych lub przenieść dane. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]definiuje <xref:System.Windows.DragDropEffects> wyliczenia, którego można użyć, aby określić wpływ operacji przeciągania i upuszczania. Ze źródła przeciągania, można określić efekty, które umożliwi źródła w <xref:System.Windows.DragDrop.DoDragDrop%2A> metody. W celu upuszczania, można określić wpływ, jaki element docelowy zamierza w <xref:System.Windows.DragEventArgs.Effects%2A> właściwość <xref:System.Windows.DragEventArgs> klasy. Jeśli element docelowy upuszczania określa zamierzonego skutku w <xref:System.Windows.DragDrop.DragOver> zdarzenia, które informacje są przekazywane z powrotem do źródła przeciągania w <xref:System.Windows.DragDrop.GiveFeedback> zdarzeń. Źródła przeciągania używa tych informacji, aby poinformować użytkownika wpływ, jaki ma element docelowy upuszczania zamierza na danych. Po upuszczeniu danych, element docelowy upuszczania określa jego rzeczywistego efekt <xref:System.Windows.DragDrop.Drop> zdarzeń. Czy informacje są przekazywane z powrotem do źródła przeciągania jako wartość zwracaną <xref:System.Windows.DragDrop.DoDragDrop%2A> metody. Jeśli element docelowy upuszczania zwraca efekt, który nie jest na liście źródeł przeciągania `allowedEffects`, anulowanie operacji przeciągania i upuszczania bez przekazywania danych wystąpienia.  
  
 Należy pamiętać, że w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.DragDropEffects> wartości są używane tylko w celu zapewnienia komunikacji między serwerem źródłowym przeciągania, a element docelowy upuszczania dotyczące wpływu operacji przeciągania i upuszczania. Rzeczywisty wynik operacji przeciągania i upuszczania jest zależna od napisać odpowiedni kod w aplikacji.  
  
 Na przykład miejsca docelowego może określić efekt porzucenie danych na nim przenoszenia danych. Jednak przenoszenia danych, musi być zarówno dodane do elementu docelowego i usunąć z elementu źródłowego. Source element może wskazywać umożliwia przenoszenie danych, że jeśli kod, aby usunąć z elementu źródła danych nie zostanie określona, wynik końcowy będzie czy dane są kopiowane i nie są przenoszone.  
  
<a name="Drag_and_Drop_Events"></a>   
## <a name="drag-and-drop-events"></a>Przeciągnij i upuść zdarzenia  
 Operacje przeciągania i upuszczania obsługuje model zdarzeniami.  Źródłowym przeciągania i element docelowy upuszczania używa standardowego zbioru zdarzeń do obsługi operacji przeciągania i upuszczania.  W poniższej tabeli podsumowano standardowych zdarzeń przeciągania i upuszczania. Dołączone zdarzenia znajdują się na <xref:System.Windows.DragDrop> klasy. Aby uzyskać więcej informacji na temat dołączone zdarzenia, zobacz [dołączony Przegląd zdarzeń](../../../../docs/framework/wpf/advanced/attached-events-overview.md).  
  
### <a name="drag-source-events"></a>Przeciągnij źródła zdarzeń  
  
|Zdarzenie|Podsumowanie|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.GiveFeedback>|To zdarzenie występuje podczas operacji przeciągania i upuszczania i umożliwia miejsca źródłowego przekazać opinię informacje użytkownika. To powszechnie zwrotnych, zmieniając wygląd wskaźnika myszy wskazująca efekty dozwolone przez element docelowy upuszczania.  To jest zdarzenie propagacji.|  
|<xref:System.Windows.DragDrop.QueryContinueDrag>|To zdarzenie występuje, gdy nastąpiła zmiana w klawiatury lub myszy stany podczas operacji przeciągania i upuszczania, a umożliwia miejsca źródłowego anulować operację przeciągania i upuszczania w zależności od stanów przycisk/klucz. To jest zdarzenie propagacji.|  
|<xref:System.Windows.DragDrop.PreviewGiveFeedback>|Wersja tunelowania <xref:System.Windows.DragDrop.GiveFeedback>.|  
|<xref:System.Windows.DragDrop.PreviewQueryContinueDrag>|Wersja tunelowania <xref:System.Windows.DragDrop.QueryContinueDrag>.|  
  
### <a name="drop-target-events"></a>Docelowy upuszczania.  
  
|Zdarzenie|Podsumowanie|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.DragEnter>|To zdarzenie występuje, gdy obiekt zostanie przeciągnięty do granicy miejsca docelowego. To jest zdarzenie propagacji.|  
|<xref:System.Windows.DragDrop.DragLeave>|To zdarzenie występuje, gdy obiekt zostanie przeciągnięty poza granice miejsca docelowego.  To jest zdarzenie propagacji.|  
|<xref:System.Windows.DragDrop.DragOver>|To zdarzenie występuje stale, gdy obiekt zostanie przeciągnięty (przenoszonych) w obrębie granicy miejsca docelowego. To jest zdarzenie propagacji.|  
|<xref:System.Windows.DragDrop.Drop>|To zdarzenie występuje, gdy obiekt jest przerywane na element docelowy upuszczania.  To jest zdarzenie propagacji.|  
|<xref:System.Windows.DragDrop.PreviewDragEnter>|Wersja tunelowania <xref:System.Windows.DragDrop.DragEnter>.|  
|<xref:System.Windows.DragDrop.PreviewDragLeave>|Wersja tunelowania <xref:System.Windows.DragDrop.DragLeave>.|  
|<xref:System.Windows.DragDrop.PreviewDragOver>|Wersja tunelowania <xref:System.Windows.DragDrop.DragOver>.|  
|<xref:System.Windows.DragDrop.PreviewDrop>|Wersja tunelowania <xref:System.Windows.DragDrop.Drop>.|  
  
 Do obsługi przeciągania i upuszczania do wystąpień obiektu Dodaj programy obsługi dla zdarzenia wymienione w powyższej tabeli. Do obsługi przeciągania i upuszczania zdarzeń na poziomie klasy, Zastąp odpowiadającą jej wirtualny na * zdarzeń i na\*PreviewEvent metody. Aby uzyskać więcej informacji, zobacz [klasy obsługi z kierowane zdarzenia według klasy podstawowej formantów](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md#Class_Handling_of_Routed_Events).  
  
<a name="Implementing_Drag_And_Drop"></a>   
## <a name="implementing-drag-and-drop"></a>Implementowanie przeciągnij i upuść  
 Element interfejsu użytkownika może być źródłem przeciągania i/lub miejsca docelowego. Aby zaimplementować podstawowe przeciągania i upuszczania, pisania kodu Inicjowanie operacji przeciągania i upuszczania oraz przetwarzania danych porzucone. Udoskonalenie przeciągania i upuszczania dzięki obsłudze opcjonalne zdarzenia przeciągania i upuszczania.  
  
 Aby zaimplementować podstawowe przeciągania i upuszczania, zakończy się następujące zadania:  
  
-   Określ element, który ma być źródła przeciągania. Może być źródłem przeciągania <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement>.  
  
-   Tworzenie procedury obsługi zdarzeń o źródle przeciągania, dla którego zostanie zainicjowana operacja przeciągania i upuszczania. Zdarzenie jest zwykle <xref:System.Windows.UIElement.MouseMove> zdarzeń.  
  
-   W obsłudze zdarzeń źródła przeciągania, wywołaj <xref:System.Windows.DragDrop.DoDragDrop%2A> metodę, aby zainicjować operację przeciągania i upuszczania. W <xref:System.Windows.DragDrop.DoDragDrop%2A> wywołać, określ źródła przeciągania, przekazywanych danych i dozwolone efekty.  
  
-   Określ element, który ma być miejsca docelowego. Miejsca docelowego może być <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement>.  
  
-   Dla obiektu docelowego upuszczania, ustaw <xref:System.Windows.UIElement.AllowDrop%2A> właściwości `true`.  
  
-   W celu upuszczania, Utwórz <xref:System.Windows.DragDrop.Drop> program obsługi zdarzeń do przetwarzania danych porzucone.  
  
-   W <xref:System.Windows.DragDrop.Drop> program obsługi zdarzeń, wyodrębniania danych z <xref:System.Windows.DragEventArgs> za pomocą <xref:System.Windows.DataObject.GetDataPresent%2A> i <xref:System.Windows.DataObject.GetData%2A> metody.  
  
-   W <xref:System.Windows.DragDrop.Drop> program obsługi zdarzeń, użyj danych do wykonania żądanej operacji przeciągania i upuszczania.  
  
 Można zwiększyć implementacji przeciągania i upuszczania, tworząc niestandardowe <xref:System.Windows.DataObject> i obsługa opcjonalne przeciągnij zdarzenia docelowego źródła i upuszczania, jak pokazano w następujących zadań:  
  
-   Transfer danych niestandardowych lub wielu elementów danych, należy utworzyć <xref:System.Windows.DataObject> do przekazania do <xref:System.Windows.DragDrop.DoDragDrop%2A> metody.  
  
-   Aby wykonać dodatkowe czynności podczas przeciągania, obsługi <xref:System.Windows.DragDrop.DragEnter>, <xref:System.Windows.DragDrop.DragOver>, i <xref:System.Windows.DragDrop.DragLeave> zdarzenia na element docelowy upuszczania.  
  
-   Aby zmienić wygląd wskaźnika myszy, obsługi <xref:System.Windows.DragDrop.GiveFeedback> zdarzenia w źródła przeciągania.  
  
-   Aby zmienić sposób operacji przeciągania i upuszczania zostało anulowane, obsługi <xref:System.Windows.DragDrop.QueryContinueDrag> zdarzenia w źródła przeciągania.  
  
<a name="Drag_And_Drop_Example"></a>   
## <a name="drag-and-drop-example"></a>Przykład przeciągania i upuszczania  
 W tej sekcji opisano sposób implementacji przeciągania i upuszczania dla <xref:System.Windows.Shapes.Ellipse> elementu. <xref:System.Windows.Shapes.Ellipse> Jest źródłowym przeciągania i miejsca docelowego. Reprezentacja ciągu elipsy jest przeniesione dane <xref:System.Windows.Shapes.Shape.Fill%2A> właściwości. Poniżej przedstawiono XAML <xref:System.Windows.Shapes.Ellipse> elementu i zdarzenia powiązane przeciągania i upuszczania, który go obsługuje. Aby wykonać kroki implementowania przeciągania i upuszczania, zobacz [wskazówki: Włączanie przeciąganie i upuszczanie w formancie użytkownika](../../../../docs/framework/wpf/advanced/walkthrough-enabling-drag-and-drop-on-a-user-control.md).  
  
 [!code-xaml[DragDropSnippets#EllipseXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#ellipsexaml)]  
  
### <a name="enabling-an-element-to-be-a-drag-source"></a>Włączanie element jako Element źródłowy przeciągania  
 Obiekt, który jest źródłem przeciągania jest odpowiedzialny za:  
  
-   Identyfikowanie podczas przeciągania.  
  
-   Inicjowanie operacji przeciągania i upuszczania.  
  
-   Identyfikowanie przekazywanych danych.  
  
-   Określanie efekty, których może mieć na przeniesionych danych operacji przeciągania i upuszczania.  
  
 Źródła przeciągania może również wydać opinii dotyczących dozwolone akcje użytkownika (przenieść, skopiować, none) i anulować operację przeciągania i upuszczania, oparte na danych wejściowych użytkownika dodatkowe, takie jak naciśnięcie klawisza ESC podczas przeciągania.  
  
 Jest odpowiedzialny za ustalenie, kiedy występuje przeciągnij aplikacji, a następnie operacji przeciągania i upuszczania inicjowania przez wywołanie metody <xref:System.Windows.DragDrop.DoDragDrop%2A> metody. Zazwyczaj jest to kiedy <xref:System.Windows.UIElement.MouseMove> zdarzeń odbywa się za pośrednictwem elementu, aby przeciągnąć, gdy zostanie naciśnięty przycisk myszy. Poniższy przykład pokazuje, jak zainicjować operację przeciągania i upuszczania z <xref:System.Windows.UIElement.MouseMove> obsługi zdarzeń <xref:System.Windows.Shapes.Ellipse> element, aby była źródła przeciągania. Reprezentacja ciągu elipsy jest przeniesione dane <xref:System.Windows.Shapes.Shape.Fill%2A> właściwości.  
  
 [!code-csharp[DragDropSnippets#DoDragDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dodragdrop)]
 [!code-vb[DragDropSnippets#DoDragDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dodragdrop)]  
  
 Wewnątrz <xref:System.Windows.UIElement.MouseMove> obsługi zdarzeń, wywołaj <xref:System.Windows.DragDrop.DoDragDrop%2A> metodę, aby zainicjować operację przeciągania i upuszczania. <xref:System.Windows.DragDrop.DoDragDrop%2A> Metoda przyjmuje trzy parametry:  
  
-   `dragSource`— Odwołanie do obiektu zależności, który jest źródłem danych przekazanych; Zazwyczaj jest to źródło <xref:System.Windows.UIElement.MouseMove> zdarzeń.  
  
-   `data`-Obiekt, który zawiera przeniesione dane w <xref:System.Windows.DataObject>.  
  
-   `allowedEffects`-Jedno z <xref:System.Windows.DragDropEffects> wartości wyliczenia, które określa dozwolone efekty operacji przeciągania i upuszczania.  
  
 Przekazano dowolnego obiektu podlegającego serializacji `data` parametru. Jeśli dane nie jest już opakowana w <xref:System.Windows.DataObject>, zostanie on automatycznie zawijany w nowym <xref:System.Windows.DataObject>. Aby przekazać wielu elementów danych, należy utworzyć <xref:System.Windows.DataObject> samodzielnie i przekaż go do <xref:System.Windows.DragDrop.DoDragDrop%2A> metody. Aby uzyskać więcej informacji, zobacz [danych i obiektów danych](../../../../docs/framework/wpf/advanced/data-and-data-objects.md).  
  
 `allowedEffects` Parametr jest używany do określenia, jakie źródła przeciągania umożliwi element docelowy upuszczania z przeniesionych danych. Typowe wartości źródła przeciągania są <xref:System.Windows.DragDropEffects.Copy>, <xref:System.Windows.DragDropEffects.Move>, i <xref:System.Windows.DragDropEffects.All>.  
  
> [!NOTE]
>  Element docelowy upuszczania może się także do określenia wpływu, jaki zamierza w odpowiedzi na porzuconych danych. Na przykład, jeśli element docelowy upuszczania nie rozpoznaje typu danych ma być przerwane, można odmówić danych przez ustawienie jej dozwolone efekty <xref:System.Windows.DragDropEffects.None>. Zazwyczaj dzieje się tak jego <xref:System.Windows.DragDrop.DragOver> obsługi zdarzeń.  
  
 Opcjonalnie można obsługiwać źródła przeciągania <xref:System.Windows.DragDrop.GiveFeedback> i <xref:System.Windows.DragDrop.QueryContinueDrag> zdarzenia. Te zdarzenia mają obsługi domyślne, które są używane, chyba że oznaczenia zdarzeń jako obsługi. Zwykle będzie ignorować te zdarzenia, chyba że istnieje konkretna potrzeba zmiany ich zachowanie domyślne.  
  
 <xref:System.Windows.DragDrop.GiveFeedback> Zdarzenie jest zgłaszane w sposób ciągły podczas przeciągania źródła przeciągania. Domyślny program obsługi dla tego zdarzenia sprawdza, czy źródła przeciągania za pośrednictwem prawidłowy miejsca docelowego. Jeśli tak jest, sprawdza dozwolone efekty miejsca docelowego. Następnie udostępnia informacje zwrotne dla użytkownika końcowego dotyczące wpływu listy dozwolonych. To jest zazwyczaj wykonywane przez zmianę kursor myszy na nie upuść, kopiowania, ani nie przenoś kursora. To zdarzenie powinna obsługiwać tylko, jeśli należy użyć niestandardowych kursorów w celu otrzymania opinii dla użytkownika. Obsługa tego zdarzenia, należy oznaczyć go jako obsłużone tak, aby domyślny program obsługi nie przesłania programu obsługi.  
  
 <xref:System.Windows.DragDrop.QueryContinueDrag> Zdarzenie jest zgłaszane w sposób ciągły podczas przeciągania źródła przeciągania. Może obsłużyć tego zdarzenia w celu określenia, jaką akcję kończy operację przeciągania i upuszczania, oparte na stanie ESC, SHIFT, CTRL i ALT — klawisze, a także stan przycisku myszy. Domyślny program obsługi dla tego zdarzenia anuluje operację przeciągania i upuszczania, jeśli zostanie naciśnięty klawisz ESC i spadnie danych, gdy przycisk myszy zostanie zwolniony.  
  
> [!CAUTION]
>  Te zdarzenia są generowane podczas operacji przeciągania i upuszczania. W związku z tym należy unikać obciążający zasoby zadań w programie obsługi zdarzeń.  Na przykład użyć buforowanych kursora zamiast tworzyć nowy kursor zawsze <xref:System.Windows.DragDrop.GiveFeedback> zdarzenia.  
  
### <a name="enabling-an-element-to-be-a-drop-target"></a>Włączanie element jako Element docelowy upuszczania  
 Obiekt będący miejsca docelowego jest odpowiedzialny za:  
  
-   Określanie, czy jest prawidłową miejsca docelowego.  
  
-   Odpowiada na źródła przeciągania, gdy jego przeciągnięty nad elementem docelowym.  
  
-   Sprawdzanie, czy przeniesionych danych jest w formacie, który może odbierać.  
  
-   Przetwarzanie danych porzucone.  
  
 Aby określić, czy element to element docelowy upuszczania, musisz ustawić jej <xref:System.Windows.UIElement.AllowDrop%2A> właściwości `true`. Docelowy upuszczania następnie zostanie wygenerowany w elemencie, dzięki czemu można obsługiwać. Podczas operacji przeciągania i upuszczania występuje następująca sekwencja zdarzeń, w celu porzucenia:  
  
1.  <xref:System.Windows.DragDrop.DragEnter>  
  
2.  <xref:System.Windows.DragDrop.DragOver>  
  
3.  <xref:System.Windows.DragDrop.DragLeave>lub<xref:System.Windows.DragDrop.Drop>  
  
 <xref:System.Windows.DragDrop.DragEnter> Zdarzenie przeciągnięte danych do granicy miejsca docelowego. To zdarzenie do podglądu skutków operacji przeciągania i upuszczania jest zwykle obsługi, jeśli jest to odpowiedni dla twojej aplikacji. Nie ustawiaj <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> właściwości w <xref:System.Windows.DragDrop.DragEnter> zdarzeń, które zostaną zastąpione w <xref:System.Windows.DragDrop.DragOver> zdarzeń.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.DragDrop.DragEnter> programu obsługi zdarzeń dla <xref:System.Windows.Shapes.Ellipse> elementu. Ten kod wyświetla podgląd skutków operacji przeciągania i upuszczania przez zapisanie bieżącego <xref:System.Windows.Shapes.Shape.Fill%2A> pędzla. Następnie używa <xref:System.Windows.DataObject.GetDataPresent%2A> , aby sprawdzić, czy <xref:System.Windows.DataObject> przeciągany nad elipsy zawiera dane ciągu można przekonwertować na <xref:System.Windows.Media.Brush>. Jeśli tak, dane są wyodrębniane przy użyciu <xref:System.Windows.DataObject.GetData%2A> metody. Następnie jest konwertowana na <xref:System.Windows.Media.Brush> i zastosowane do elipsy. Zmiana zostanie przywrócony w <xref:System.Windows.DragDrop.DragLeave> obsługi zdarzeń. Jeśli nie można przekonwertować danych na <xref:System.Windows.Media.Brush>, nie wykonano żadnej akcji.  
  
 [!code-csharp[DragDropSnippets#DragEnter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragenter)]
 [!code-vb[DragDropSnippets#DragEnter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragenter)]  
  
 <xref:System.Windows.DragDrop.DragOver> Zdarzenie stale, gdy dane zostanie przeciągnięta nad element docelowy upuszczania. To zdarzenie jest łączyć się z <xref:System.Windows.DragDrop.GiveFeedback> zdarzenia w źródła przeciągania. W <xref:System.Windows.DragDrop.DragOver> program obsługi zdarzeń, zazwyczaj używa się <xref:System.Windows.DataObject.GetDataPresent%2A> i <xref:System.Windows.DataObject.GetData%2A> metody, aby sprawdzić, czy przeniesionych danych jest w formacie, który może przetwarzać miejsca docelowego. Można również sprawdzić, czy wszystkie klawisze modyfikujące naciśnięciu, które będą zwykle wskazywać, czy użytkownik zamierza akcji przenoszenia lub kopiowania. Po te są sprawdzane <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> właściwości powiadomiono przeciągania źródła będą miały wpływ, jaki usunięcie danych. Te informacje w odbiera źródła przeciągania <xref:System.Windows.DragDrop.GiveFeedback> argumentów zdarzenia i ustawić odpowiednie kursora, aby przekazać opinię do użytkownika.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.DragDrop.DragOver> programu obsługi zdarzeń dla <xref:System.Windows.Shapes.Ellipse> elementu. Ten kod sprawdza, czy <xref:System.Windows.DataObject> przeciągany nad elipsy zawiera dane ciągu można przekonwertować na <xref:System.Windows.Media.Brush>. Jeśli tak, ustawia <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> właściwości <xref:System.Windows.DragDropEffects.Copy>. Wskazuje źródła przeciągania czy danych może zostać skopiowana elipsy. Jeśli nie można przekonwertować danych na <xref:System.Windows.Media.Brush>, <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> właściwość jest ustawiona na <xref:System.Windows.DragDropEffects.None>. Wskazuje źródła przeciągania czy elipsy nie jest prawidłową miejsca docelowego dla danych.  
  
 [!code-csharp[DragDropSnippets#DragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragover)]
 [!code-vb[DragDropSnippets#DragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragover)]  
  
 <xref:System.Windows.DragDrop.DragLeave> Zdarzenie wystąpi, gdy dane zostanie przeciągnięty poza granice elementu docelowego bez usuwane. Obsługa tego zdarzenia, aby cofnąć wszystkie elementy, które zostały w <xref:System.Windows.DragDrop.DragEnter> obsługi zdarzeń.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.DragDrop.DragLeave> programu obsługi zdarzeń dla <xref:System.Windows.Shapes.Ellipse> elementu. Ten kod cofa wykonywane w wersji zapoznawczej <xref:System.Windows.DragDrop.DragEnter> obsługi zdarzeń, stosując zapisanego <xref:System.Windows.Media.Brush> do elipsy.  
  
 [!code-csharp[DragDropSnippets#DragLeave](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragleave)]
 [!code-vb[DragDropSnippets#DragLeave](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragleave)]  
  
 <xref:System.Windows.DragDrop.Drop> Zdarzenie po upuszczeniu danych przez element docelowy upuszczania; domyślnie ten następuje po zwolnieniu przycisku myszy. W <xref:System.Windows.DragDrop.Drop> program obsługi zdarzeń, użyj <xref:System.Windows.DataObject.GetData%2A> metodę, aby wyodrębnić dane przesyłane z <xref:System.Windows.DataObject> i wykonywać żadnych przetwarzania danych wymaganych przez aplikację. <xref:System.Windows.DragDrop.Drop> Zdarzeń kończy operację przeciągania i upuszczania.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.DragDrop.Drop> programu obsługi zdarzeń dla <xref:System.Windows.Shapes.Ellipse> elementu. Ten kod stosuje skutków operacji przeciągania i upuszczania, a jest podobny do kodu w <xref:System.Windows.DragDrop.DragEnter> obsługi zdarzeń. Sprawdza, czy <xref:System.Windows.DataObject> przeciągany nad elipsy zawiera dane ciągu można przekonwertować na <xref:System.Windows.Media.Brush>. Jeśli tak, <xref:System.Windows.Media.Brush> jest stosowany do elipsy. Jeśli nie można przekonwertować danych na <xref:System.Windows.Media.Brush>, nie wykonano żadnej akcji.  
  
 [!code-csharp[DragDropSnippets#Drop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#drop)]
 [!code-vb[DragDropSnippets#Drop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#drop)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Clipboard>  
 [Przewodnik: włączanie przeciągania i upuszczania w kontrolce użytkownika](../../../../docs/framework/wpf/advanced/walkthrough-enabling-drag-and-drop-on-a-user-control.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/advanced/drag-and-drop-how-to-topics.md)  
 [Przeciąganie i upuszczanie](../../../../docs/framework/wpf/advanced/drag-and-drop.md)
