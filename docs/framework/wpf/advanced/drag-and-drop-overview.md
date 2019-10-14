---
title: Przegląd przeciągania i upuszczania
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
ms.openlocfilehash: 72dc443e5653b9871c3f67b003bd1af0536d5993
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291477"
---
# <a name="drag-and-drop-overview"></a>Przegląd przeciągania i upuszczania
Ten temat zawiera omówienie obsługi przeciągania i upuszczania w aplikacjach [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Przeciąganie i upuszczanie często odnosi się do metody transferu danych, która polega na użyciu myszy (lub innego urządzenia wskazującego) do wybrania jednego lub większej liczby obiektów, przeciąganie tych obiektów na niewłaściwy element docelowy w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] i upuszczenie ich.  

<a name="Drag_and_Drop_Support"></a>   
## <a name="drag-and-drop-support-in-wpf"></a>Obsługa przeciągania i upuszczania w programie WPF  
 Operacje przeciągania i upuszczania zwykle obejmują dwie strony: Źródło przeciągane, z którego pochodzi przeciągany obiekt, oraz miejsce docelowe upuszczania, które odbiera usunięty obiekt.  Obiekt docelowy przeciągania i upuszczania może być elementami interfejsu użytkownika w tej samej aplikacji lub innej aplikacji.  
  
 Typ i liczba obiektów, które mogą być manipulowane za pomocą przeciągania i upuszczania, są całkowicie arbitralne. Na przykład pliki, foldery i zaznaczenia zawartości to niektóre z bardziej popularnych obiektów manipulowanych przez operacje przeciągania i upuszczania.  
  
 Określone akcje wykonywane podczas operacji przeciągania i upuszczania są specyficzne dla aplikacji i często określane przez kontekstu.  Na przykład przeciąganie zaznaczenia plików z jednego folderu do drugiego na tym samym urządzeniu magazynującym powoduje przeniesienie plików domyślnie, podczas gdy przeciąganie plików z udziału Universal Naming Convention (UNC) do folderu lokalnego kopiuje pliki domyślnie.  
  
 Urządzenia przeciągające i upuść udostępniane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są zaprojektowane tak, aby były wysoce elastyczne i dostosowywalne w celu obsługi szerokiej gamy scenariuszy typu "przeciągnij i upuść".  Przeciąganie i upuszczanie obsługuje manipulowanie obiektami w ramach jednej aplikacji lub między różnymi aplikacjami. Przeciąganie i upuszczanie między aplikacjami [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i innymi aplikacjami systemu Windows również jest w pełni obsługiwane.  
  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wszystkie <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement> mogą uczestniczyć w przeciąganiu i upuszczaniu. Zdarzenia i metody wymagane dla operacji przeciągania i upuszczania są zdefiniowane w klasie <xref:System.Windows.DragDrop>. Klasy <xref:System.Windows.UIElement> i <xref:System.Windows.ContentElement> zawierają aliasy dla załączonych zdarzeń <xref:System.Windows.DragDrop>, dzięki czemu zdarzenia są wyświetlane na liście składowych klasy, gdy <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement> są dziedziczone jako element podstawowy. Programy obsługi zdarzeń, które są dołączone do tych zdarzeń, są dołączane do powiązanego zdarzenia <xref:System.Windows.DragDrop> i odbierają to samo wystąpienie danych zdarzenia. Aby uzyskać więcej informacji, zobacz zdarzenie <xref:System.Windows.UIElement.Drop?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
> Przeciąganie i upuszczanie OLE nie działa w strefie Internet.  
  
<a name="Data_Transfer"></a>   
## <a name="data-transfer"></a>Transfer danych  
 Przeciąganie i upuszczanie jest częścią bardziej ogólnego obszaru transferu danych. Transfer danych obejmuje operacje przeciągania i upuszczania oraz kopiowania i wklejania. Operacja przeciągania i upuszczania jest analogiczna do operacji kopiowania i wklejania lub wycinania i wklejania, która jest używana do transferowania danych z jednego obiektu lub aplikacji do innego przy użyciu schowka systemowego. Oba typy operacji wymagają:  
  
- Obiekt źródłowy, który udostępnia dane.  
  
- Sposób tymczasowego przechowywania przesłanych danych.  
  
- Obiekt docelowy, który odbiera dane.  
  
 W operacji kopiowania i wklejania do tymczasowego przechowywania transferowanych danych używany jest schowek systemowy. w operacji przeciągania i upuszczania jest używana <xref:System.Windows.DataObject> do przechowywania danych. Koncepcyjnie obiekt danych składa się z co najmniej jednej pary <xref:System.Object>, która zawiera rzeczywiste dane, oraz odpowiadającego im identyfikatora formatu danych.  
  
 Źródło przeciągania Inicjuje operację przeciągania i upuszczania przez wywołanie statycznej metody <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> i przekazanie do niej przesłanych danych. Metoda <xref:System.Windows.DragDrop.DoDragDrop%2A> automatycznie zawija dane w <xref:System.Windows.DataObject>, jeśli będzie to konieczne. Aby uzyskać większą kontrolę nad formatem danych, można otoczyć dane w <xref:System.Windows.DataObject> przed przekazaniem ich do metody <xref:System.Windows.DragDrop.DoDragDrop%2A>. Element docelowy upuszczania jest odpowiedzialny za wyodrębnienie danych z <xref:System.Windows.DataObject>. Aby uzyskać więcej informacji na temat pracy z obiektami danych, zobacz [dane i obiekty danych](data-and-data-objects.md).  
  
 Źródłem i elementem docelowym operacji przeciągania i upuszczania są elementy interfejsu użytkownika; Jednak dane, które faktycznie są transferowane zazwyczaj nie mają wizualnej reprezentacji. Można napisać kod, aby zapewnić wizualną reprezentację przeciąganych danych, na przykład podczas przeciągania plików w Eksploratorze Windows. Domyślnie informacje zwrotne są przekazywane użytkownikowi przez zmianę kursora w celu reprezentowania efektu operacji przeciągania i upuszczania na danych, na przykład czy dane zostaną przeniesione lub skopiowane.  
  
### <a name="drag-and-drop-effects"></a>Efekty przeciągania i upuszczania  
 Operacje przeciągania i upuszczania mogą mieć różny wpływ na przesyłane dane. Można na przykład skopiować dane lub przenieść dane. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definiuje wyliczenie <xref:System.Windows.DragDropEffects>, za pomocą którego można określić efekt operacji przeciągania i upuszczania. W źródle przeciągnij możesz określić efekty, które będą dozwolone przez źródło w metodzie <xref:System.Windows.DragDrop.DoDragDrop%2A>. W miejscu docelowym upuść Możesz określić wpływ, jaki ma obiekt docelowy na Właściwość <xref:System.Windows.DragEventArgs.Effects%2A> klasy <xref:System.Windows.DragEventArgs>. Gdy element docelowy upuszczania określa zamierzony efekt w zdarzeniu <xref:System.Windows.DragDrop.DragOver>, te informacje są przesyłane z powrotem do źródła przeciągania w zdarzeniu <xref:System.Windows.DragDrop.GiveFeedback>. Źródło przeciągania używa tych informacji do informowania użytkownika o tym, że obiekt docelowy upuszczania ma wpływ na dane. Gdy dane zostaną usunięte, cel upuszczania określa swój rzeczywisty efekt w zdarzeniu <xref:System.Windows.DragDrop.Drop>. Te informacje są przesyłane z powrotem do źródła przeciągania jako wartość zwracana metody <xref:System.Windows.DragDrop.DoDragDrop%2A>. Jeśli obiekt docelowy upuszczania zwróci efekt, który nie znajduje się na liście "przeciągnij źródła" `allowedEffects`, operacja przeciągania i upuszczania zostanie anulowana bez jakiegokolwiek transferu danych.  
  
 Należy pamiętać, że w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wartości <xref:System.Windows.DragDropEffects> są używane tylko w celu zapewnienia komunikacji między źródłem przeciągania a elementem docelowym upuszczania związanym z efektami operacji przeciągania i upuszczania. Rzeczywisty efekt operacji przeciągania i upuszczania zależy od tego, w jaki sposób napisać odpowiedni kod w aplikacji.  
  
 Na przykład obiekt docelowy upuszczania może określać, że efektem upuszczania danych jest przeniesienie danych. Jednak aby przenieść dane, należy je dodać do elementu docelowego i usunąć z elementu źródłowego. Element źródłowy może wskazywać, że umożliwia przenoszenie danych, ale jeśli nie podasz kodu, aby usunąć dane z elementu źródłowego, wynik końcowy będzie kopiowany i nie przenoszony.  
  
<a name="Drag_and_Drop_Events"></a>   
## <a name="drag-and-drop-events"></a>Zdarzenia przeciągania i upuszczania  
 Operacje przeciągania i upuszczania obsługują model oparty na zdarzeniach.  Zarówno źródło Przeciągnij, jak i miejsce docelowe umożliwiają użycie standardowego zestawu zdarzeń do obsługi operacji przeciągania i upuszczania.  W poniższej tabeli zestawiono standardowe zdarzenia przeciągania i upuszczania. Są to dołączone zdarzenia w klasie <xref:System.Windows.DragDrop>. Aby uzyskać więcej informacji o załączonych zdarzeniach, zobacz [Omówienie załączonych zdarzeń](attached-events-overview.md).  
  
### <a name="drag-source-events"></a>Przeciągnij zdarzenia źródłowe  
  
|Wydarzenie|Podsumowanie|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.GiveFeedback>|To zdarzenie występuje w sposób ciągły podczas operacji przeciągania i upuszczania oraz umożliwia źródło informacji zwrotnych dla użytkownika. Ta opinia jest zwykle wyrażana przez zmianę wyglądu wskaźnika myszy w celu wskazania efektów dozwolonych przez element docelowy upuszczania.  Jest to zdarzenie propagacji.|  
|<xref:System.Windows.DragDrop.QueryContinueDrag>|To zdarzenie występuje w przypadku zmiany stanu przycisku klawiatury lub myszy podczas operacji przeciągania i upuszczania, a następnie umożliwienie źródłowej operacji przeciągania i upuszczania w zależności od Stanów klawiszy/przycisków. Jest to zdarzenie propagacji.|  
|<xref:System.Windows.DragDrop.PreviewGiveFeedback>|Tunelowanie wersji <xref:System.Windows.DragDrop.GiveFeedback>.|  
|<xref:System.Windows.DragDrop.PreviewQueryContinueDrag>|Tunelowanie wersji <xref:System.Windows.DragDrop.QueryContinueDrag>.|  
  
### <a name="drop-target-events"></a>Upuść zdarzenia docelowe  
  
|Wydarzenie|Podsumowanie|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.DragEnter>|To zdarzenie występuje, gdy obiekt zostanie przeciągnięty do granicy elementu docelowego upuszczania. Jest to zdarzenie propagacji.|  
|<xref:System.Windows.DragDrop.DragLeave>|To zdarzenie występuje, gdy obiekt zostanie przeciągnięty z granicy elementu docelowego upuszczania.  Jest to zdarzenie propagacji.|  
|<xref:System.Windows.DragDrop.DragOver>|To zdarzenie występuje w sposób ciągły, gdy obiekt zostanie przeciągnięty (przeniesiony) w obrębie granicy elementu docelowego upuszczania. Jest to zdarzenie propagacji.|  
|<xref:System.Windows.DragDrop.Drop>|To zdarzenie występuje, gdy obiekt zostanie usunięty z elementu docelowego upuszczania.  Jest to zdarzenie propagacji.|  
|<xref:System.Windows.DragDrop.PreviewDragEnter>|Tunelowanie wersji <xref:System.Windows.DragDrop.DragEnter>.|  
|<xref:System.Windows.DragDrop.PreviewDragLeave>|Tunelowanie wersji <xref:System.Windows.DragDrop.DragLeave>.|  
|<xref:System.Windows.DragDrop.PreviewDragOver>|Tunelowanie wersji <xref:System.Windows.DragDrop.DragOver>.|  
|<xref:System.Windows.DragDrop.PreviewDrop>|Tunelowanie wersji <xref:System.Windows.DragDrop.Drop>.|  
  
 Aby obsłużyć zdarzenia przeciągania i upuszczania dla wystąpień obiektu, należy dodać procedury obsługi dla zdarzeń wymienionych w poprzednich tabelach. Aby obsłużyć zdarzenia przeciągane i upuszczane na poziomie klasy, Zastąp odpowiednie wirtualne zdarzenie * i w metodach @ no__t-0PreviewEvent. Aby uzyskać więcej informacji, zobacz temat [Obsługa zdarzeń kierowanych przez klasy bazowe formantów](marking-routed-events-as-handled-and-class-handling.md#Class_Handling_of_Routed_Events).  
  
<a name="Implementing_Drag_And_Drop"></a>   
## <a name="implementing-drag-and-drop"></a>Implementowanie przeciągania i upuszczania  
 Element interfejsu użytkownika może być źródłem przeciągania, elementem docelowym upuszczania lub jednocześnie. Aby zaimplementować podstawowe przeciąganie i upuszczanie, napisz kod w celu zainicjowania operacji przeciągania i upuszczania oraz przetworzenia porzuconych danych. Możesz ulepszyć środowisko przeciągania i upuszczania, obsługując opcjonalne zdarzenia przeciągania i upuszczania.  
  
 Aby zaimplementować podstawowe przeciąganie i upuszczanie, należy wykonać następujące zadania:  
  
- Zidentyfikuj element, który będzie źródłem przeciągania. Źródłem przeciągania może być <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement>.  
  
- Utwórz procedurę obsługi zdarzeń dla źródła przeciągania, które będzie inicjować operację przeciągania i upuszczania. Zdarzenie jest zazwyczaj zdarzeniem <xref:System.Windows.UIElement.MouseMove>.  
  
- W procedurze obsługi zdarzeń źródła przeciągnij Wywołaj metodę <xref:System.Windows.DragDrop.DoDragDrop%2A> w celu zainicjowania operacji przeciągania i upuszczania. W wywołaniu <xref:System.Windows.DragDrop.DoDragDrop%2A> Określ źródło przeciągania, dane, które mają być transferowane oraz dozwolone efekty.  
  
- Określ element, który będzie elementem docelowym upuszczania. Obiekt docelowy upuszczania może być <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement>.  
  
- W miejscu docelowym upuść ustaw właściwość <xref:System.Windows.UIElement.AllowDrop%2A> na `true`.  
  
- W miejscu docelowym upuść Utwórz procedurę obsługi zdarzeń <xref:System.Windows.DragDrop.Drop>, aby przetworzyć usunięte dane.  
  
- W obsłudze zdarzeń <xref:System.Windows.DragDrop.Drop> Wyodrębnij dane z <xref:System.Windows.DragEventArgs> przy użyciu metod <xref:System.Windows.DataObject.GetDataPresent%2A> i <xref:System.Windows.DataObject.GetData%2A>.  
  
- W obsłudze zdarzeń <xref:System.Windows.DragDrop.Drop> użyj danych do wykonania odpowiedniej operacji przeciągania i upuszczania.  
  
 Możesz udoskonalić implementację typu "przeciągnij i upuść", tworząc niestandardową <xref:System.Windows.DataObject> i obsługując opcjonalne zdarzenia przeciągania źródła i upuszczania, jak pokazano w następujących zadaniach:  
  
- Aby przesłać dane niestandardowe lub wiele elementów danych, należy utworzyć <xref:System.Windows.DataObject> do przekazania do metody <xref:System.Windows.DragDrop.DoDragDrop%2A>.  
  
- Aby wykonać dodatkowe akcje podczas przeciągania, obsługuj zdarzenia <xref:System.Windows.DragDrop.DragEnter>, <xref:System.Windows.DragDrop.DragOver> i <xref:System.Windows.DragDrop.DragLeave> w miejscu docelowym upuszczania.  
  
- Aby zmienić wygląd wskaźnika myszy, obsłuż zdarzenie <xref:System.Windows.DragDrop.GiveFeedback> na źródle przeciągania.  
  
- Aby zmienić sposób anulowania operacji przeciągania i upuszczania, obsłuż zdarzenie <xref:System.Windows.DragDrop.QueryContinueDrag> na źródle przeciągania.  
  
<a name="Drag_And_Drop_Example"></a>   
## <a name="drag-and-drop-example"></a>Przykład przeciągania i upuszczania  
 W tej sekcji opisano, jak zaimplementować przeciąganie i upuszczanie dla elementu <xref:System.Windows.Shapes.Ellipse>. @No__t-0 to zarówno źródło Przeciągnij, jak i element docelowy upuszczania. Przesyłane dane są reprezentacją ciągu <xref:System.Windows.Shapes.Shape.Fill%2A> właściwości wielokropka. Poniższy kod XAML pokazuje element <xref:System.Windows.Shapes.Ellipse> i zdarzenia związane z przeciąganiem i upuszczaniem, które obsługuje. Aby dowiedzieć się, jak zaimplementować przeciąganie i upuszczanie, zobacz [Przewodnik: włączanie przeciągania i upuszczania w kontrolce użytkownika](walkthrough-enabling-drag-and-drop-on-a-user-control.md).  
  
 [!code-xaml[DragDropSnippets#EllipseXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#ellipsexaml)]  
  
### <a name="enabling-an-element-to-be-a-drag-source"></a>Włączanie elementu jako źródła przeciągania  
 Obiekt, który jest źródłem przeciągania, jest odpowiedzialny za:  
  
- Identyfikowanie, kiedy nastąpi przeciągnięcie.  
  
- Inicjowanie operacji przeciągania i upuszczania.  
  
- Identyfikowanie danych do przeniesienia.  
  
- Określanie wpływu operacji przeciągania i upuszczania na transferowane dane.  
  
 Źródło przeciągania może również przekazać użytkownikowi informacje zwrotne dotyczące dozwolonych akcji (przenoszenia, kopiowania, braku) i umożliwia anulowanie operacji przeciągania i upuszczania na podstawie dodatkowych danych wejściowych użytkownika, takich jak naciśnięcie klawisza ESC podczas przeciągania.  
  
 Jest odpowiedzialna za aplikację, aby określić, kiedy nastąpi przeciąganie, a następnie zainicjować operację przeciągania i upuszczania przez wywołanie metody <xref:System.Windows.DragDrop.DoDragDrop%2A>. Zwykle jest to spowodowane tym, że zdarzenie <xref:System.Windows.UIElement.MouseMove> dotyczy elementu, który ma być przeciągany podczas naciskania przycisku myszy. Poniższy przykład pokazuje, jak zainicjować operację przeciągania i upuszczania z programu obsługi zdarzeń <xref:System.Windows.UIElement.MouseMove> elementu <xref:System.Windows.Shapes.Ellipse>, aby uczynić go źródłem przeciągania. Przesyłane dane są reprezentacją ciągu <xref:System.Windows.Shapes.Shape.Fill%2A> właściwości wielokropka.  
  
 [!code-csharp[DragDropSnippets#DoDragDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dodragdrop)]
 [!code-vb[DragDropSnippets#DoDragDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dodragdrop)]  
  
 Wewnątrz procedury obsługi zdarzeń <xref:System.Windows.UIElement.MouseMove> Wywołaj metodę <xref:System.Windows.DragDrop.DoDragDrop%2A> w celu zainicjowania operacji przeciągania i upuszczania. Metoda <xref:System.Windows.DragDrop.DoDragDrop%2A> przyjmuje trzy parametry:  
  
- `dragSource` — odwołanie do obiektu zależności, który jest źródłem przesłanych danych; jest to zazwyczaj źródłem zdarzenia <xref:System.Windows.UIElement.MouseMove>.  
  
- `data`-obiekt, który zawiera przesyłane dane, opakowany w <xref:System.Windows.DataObject>.  
  
- `allowedEffects` — jedna z wartości wyliczenia <xref:System.Windows.DragDropEffects>, która określa dozwolone skutki operacji przeciągania i upuszczania.  
  
 Dowolny możliwy do serializacji obiekt można przesłać w parametrze `data`. Jeśli dane nie są jeszcze opakowane w <xref:System.Windows.DataObject>, zostanie automatycznie opakowane w nową <xref:System.Windows.DataObject>. Aby przekazać wiele elementów danych, należy samodzielnie utworzyć <xref:System.Windows.DataObject> i przekazać go do metody <xref:System.Windows.DragDrop.DoDragDrop%2A>. Aby uzyskać więcej informacji, zobacz [obiekty danych i danych](data-and-data-objects.md).  
  
 Parametr `allowedEffects` służy do określenia, jakie źródło przeciągania będzie zezwalać na miejsce docelowe upuszczania z transferowanymi danymi. Typowe wartości dla źródła przeciągania to <xref:System.Windows.DragDropEffects.Copy>, <xref:System.Windows.DragDropEffects.Move> i <xref:System.Windows.DragDropEffects.All>.  
  
> [!NOTE]
> Obiekt docelowy upuszczania umożliwia również określenie, jakie skutki ma w odpowiedzi na porzucone dane. Na przykład jeśli element docelowy upuszczania nie rozpoznaje typu danych, który ma zostać porzucony, może odmówić danych przez ustawienie jego dozwolonych efektów do <xref:System.Windows.DragDropEffects.None>. Zwykle jest to wykonywane w ramach obsługi zdarzeń <xref:System.Windows.DragDrop.DragOver>.  
  
 Źródło przeciągania może opcjonalnie obsłużyć zdarzenia <xref:System.Windows.DragDrop.GiveFeedback> i <xref:System.Windows.DragDrop.QueryContinueDrag>. Te zdarzenia mają domyślne programy obsługi, które są używane, chyba że zostaną oznaczone zdarzenia jako obsłużone. Te zdarzenia są zwykle ignorowane, chyba że użytkownik ma konkretną potrzebę zmiany domyślnego zachowania.  
  
 Zdarzenie <xref:System.Windows.DragDrop.GiveFeedback> jest stale zgłaszane podczas przeciągania źródła przeciągania. Domyślne procedury obsługi dla tego zdarzenia sprawdzają, czy źródło przeciągania znajduje się w poprawnym elemencie docelowym upuszczania. Jeśli tak jest, sprawdza dozwolone efekty elementu docelowego upuszczania. Następnie przekazuje użytkownikowi końcowemu opinię na temat dozwolonych efektów upuszczania. Jest to zwykle wykonywane przez zmianę kursora myszy na kursor nie upuszczany, Kopiuj lub Przenieś. To zdarzenie należy obsłużyć tylko wtedy, gdy musisz użyć niestandardowych kursorów, aby przekazać użytkownikom informacje zwrotne. W przypadku obsługi tego zdarzenia Pamiętaj, aby oznaczyć je jako obsłużone, tak aby domyślna procedura obsługi nie przesłaniał programu obsługi.  
  
 Zdarzenie <xref:System.Windows.DragDrop.QueryContinueDrag> jest stale zgłaszane podczas przeciągania źródła przeciągania. Możesz obsłużyć to zdarzenie, aby określić, jaka akcja powoduje zakończenie operacji przeciągania i upuszczania na podstawie stanu klawiszy ESC, SHIFT, CTRL i ALT, jak również stanu przycisków myszy. Domyślna procedura obsługi dla tego zdarzenia powoduje anulowanie operacji przeciągania i upuszczania w przypadku naciśnięcia klawisza ESC i odrzucenie danych po udostępnieniu przycisku myszy.  
  
> [!CAUTION]
> Te zdarzenia są stale zgłaszane podczas operacji przeciągania i upuszczania. W związku z tym należy unikać zadań intensywnie korzystających z zasobów w programach obsługi zdarzeń.  Na przykład użyj buforowanego kursora zamiast tworzenia nowego kursora za każdym razem, gdy zostanie zgłoszone zdarzenie <xref:System.Windows.DragDrop.GiveFeedback>.  
  
### <a name="enabling-an-element-to-be-a-drop-target"></a>Włączanie elementu jako miejsca docelowego upuszczania  
 Obiekt, który jest obiektem docelowym upuszczania, jest odpowiedzialny za:  
  
- Określanie, że jest to prawidłowy element docelowy upuszczania.  
  
- Odpowiadanie na źródło przeciągania, gdy jest ono przeciągane względem obiektu docelowego.  
  
- Sprawdzanie, czy transferowane dane są w formacie, który może zostać odebrany.  
  
- Przetwarzanie porzuconych danych.  
  
 Aby określić, że element jest obiektem docelowym, ustaw jego właściwość <xref:System.Windows.UIElement.AllowDrop%2A> na `true`. Zdarzenia Drop Target zostaną następnie zgłoszone dla elementu, aby można było je obsłużyć. Podczas operacji przeciągania i upuszczania występuje następująca sekwencja zdarzeń w miejscu docelowym upuszczania:  
  
1. <xref:System.Windows.DragDrop.DragEnter>  
  
2. <xref:System.Windows.DragDrop.DragOver>  
  
3. <xref:System.Windows.DragDrop.DragLeave> lub <xref:System.Windows.DragDrop.Drop>  
  
 Zdarzenie <xref:System.Windows.DragDrop.DragEnter> występuje, gdy dane są przeciągane do granicy elementu docelowego upuszczania. To zdarzenie jest zwykle obsługiwane, aby zapewnić podgląd efektów operacji przeciągania i upuszczania, jeśli jest to odpowiednie dla aplikacji. Nie ustawiaj właściwości <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> w zdarzeniu <xref:System.Windows.DragDrop.DragEnter>, ponieważ zostanie ona zapisywana w zdarzeniu <xref:System.Windows.DragDrop.DragOver>.  
  
 Poniższy przykład pokazuje procedurę obsługi zdarzeń <xref:System.Windows.DragDrop.DragEnter> dla elementu <xref:System.Windows.Shapes.Ellipse>. Ten kod umożliwia wyświetlenie podglądu efektów operacji przeciągania i upuszczania przez zapisanie bieżącego pędzla <xref:System.Windows.Shapes.Shape.Fill%2A>. Następnie używa metody <xref:System.Windows.DataObject.GetDataPresent%2A>, aby sprawdzić, czy <xref:System.Windows.DataObject>, który jest przeciągany przez wielokropek, zawiera dane ciągu, które można przekonwertować na <xref:System.Windows.Media.Brush>. Jeśli tak, dane są wyodrębniane przy użyciu metody <xref:System.Windows.DataObject.GetData%2A>. Następnie jest konwertowany na <xref:System.Windows.Media.Brush> i stosowany do elipsy. Zmiana zostanie przywrócona w obsłudze zdarzeń <xref:System.Windows.DragDrop.DragLeave>. Jeśli nie można przekonwertować danych na <xref:System.Windows.Media.Brush>, nie jest wykonywana żadna akcja.  
  
 [!code-csharp[DragDropSnippets#DragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragenter)]
 [!code-vb[DragDropSnippets#DragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragenter)]  
  
 Zdarzenie <xref:System.Windows.DragDrop.DragOver> odbywa się w sposób ciągły, gdy dane są przeciągane nad elementem docelowym upuszczania. To zdarzenie jest sparowane ze zdarzeniem <xref:System.Windows.DragDrop.GiveFeedback> na źródle przeciągania. W obsłudze zdarzeń <xref:System.Windows.DragDrop.DragOver> są zwykle używane metody <xref:System.Windows.DataObject.GetDataPresent%2A> i <xref:System.Windows.DataObject.GetData%2A>, aby sprawdzić, czy transferowane dane są w formacie, który może przetwarzać element docelowy upuszczania. Możesz również sprawdzić, czy zostały naciśnięte jakiekolwiek klawisze modyfikujące, które zwykle wskazują, czy użytkownik zamierza wykonać akcję przenoszenia lub kopiowania. Po wykonaniu tych testów należy ustawić właściwość <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType>, aby powiadomić Źródło przeciągania o tym, jaki efekt spowoduje porzucenie danych. Źródło przeciągania odbiera te informacje w argumentych zdarzeń <xref:System.Windows.DragDrop.GiveFeedback> i może ustawić odpowiedni kursor, aby przekazać użytkownikowi opinię.  
  
 Poniższy przykład pokazuje procedurę obsługi zdarzeń <xref:System.Windows.DragDrop.DragOver> dla elementu <xref:System.Windows.Shapes.Ellipse>. Ten kod sprawdza, czy <xref:System.Windows.DataObject> jest przeciągany przez wielokropek, zawiera dane ciągu, które można przekonwertować na <xref:System.Windows.Media.Brush>. Jeśli tak, ustawia właściwość <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> na <xref:System.Windows.DragDropEffects.Copy>. Wskazuje źródło przeciągania, które można skopiować dane na elipsę. Jeśli nie można przekonwertować danych na <xref:System.Windows.Media.Brush>, właściwość <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> ma wartość <xref:System.Windows.DragDropEffects.None>. Wskazuje to na źródło przeciągania, którego Elipsa nie jest prawidłowym obiektem docelowym upuszczania dla danych.  
  
 [!code-csharp[DragDropSnippets#DragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragover)]
 [!code-vb[DragDropSnippets#DragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragover)]  
  
 Zdarzenie <xref:System.Windows.DragDrop.DragLeave> występuje, gdy dane są przeciągane poza granicę elementu docelowego bez porzucenia. To zdarzenie jest obsługiwane w celu cofnięcia wszystkich elementów, które zostały wykonane w obsłudze zdarzeń <xref:System.Windows.DragDrop.DragEnter>.  
  
 Poniższy przykład pokazuje procedurę obsługi zdarzeń <xref:System.Windows.DragDrop.DragLeave> dla elementu <xref:System.Windows.Shapes.Ellipse>. Ten kod wycofał Podgląd wykonany w obsłudze zdarzeń <xref:System.Windows.DragDrop.DragEnter>, stosując zapisany <xref:System.Windows.Media.Brush> do elipsy.  
  
 [!code-csharp[DragDropSnippets#DragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragleave)]
 [!code-vb[DragDropSnippets#DragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragleave)]  
  
 Zdarzenie <xref:System.Windows.DragDrop.Drop> występuje, gdy dane są opuszczane przez element docelowy upuszczania; Domyślnie dzieje się tak po wydaniu przycisku myszy. W obsłudze zdarzeń <xref:System.Windows.DragDrop.Drop> należy użyć metody <xref:System.Windows.DataObject.GetData%2A> do wyodrębnienia przesłanych danych z <xref:System.Windows.DataObject> i wykonania dowolnego przetwarzania danych wymaganego przez aplikację. Zdarzenie <xref:System.Windows.DragDrop.Drop> spowoduje zakończenie operacji przeciągania i upuszczania.  
  
 Poniższy przykład pokazuje procedurę obsługi zdarzeń <xref:System.Windows.DragDrop.Drop> dla elementu <xref:System.Windows.Shapes.Ellipse>. Ten kod stosuje efekty operacji przeciągania i upuszczania oraz jest podobny do kodu w obsłudze zdarzeń <xref:System.Windows.DragDrop.DragEnter>. Sprawdza, czy <xref:System.Windows.DataObject> jest przeciągany przez wielokropek, zawiera dane ciągu, które można przekonwertować na <xref:System.Windows.Media.Brush>. W takim przypadku <xref:System.Windows.Media.Brush> jest stosowany do elipsy. Jeśli nie można przekonwertować danych na <xref:System.Windows.Media.Brush>, nie jest wykonywana żadna akcja.  
  
 [!code-csharp[DragDropSnippets#Drop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#drop)]
 [!code-vb[DragDropSnippets#Drop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#drop)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Clipboard>
- [Przewodnik: włączanie przeciągania i upuszczania w kontrolce użytkownika](walkthrough-enabling-drag-and-drop-on-a-user-control.md)
- [Tematy porad](drag-and-drop-how-to-topics.md)
- [Przeciągnij i upuść](drag-and-drop.md)
