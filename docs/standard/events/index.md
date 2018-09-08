---
title: Obsługa i wywoływanie zdarzeń
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- delegate model for events
- application development [.NET Framework], events
- events [.NET Framework]
ms.assetid: b6f65241-e0ad-4590-a99f-200ce741bb1f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5d106dd3b7b9a7a0aeedca86e63a6fccbb1cc27
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192487"
---
# <a name="handling-and-raising-events"></a>Obsługa i wywoływanie zdarzeń
Zdarzenia w .NET Framework są oparte na modelu delegata. Model delegata następuje po wzorcu projektowania obserwatora, który umożliwia subskrybentom zarejestrowanie i otrzymywanie powiadomienia od dostawcy. Nadawca wydarzenie wypycha powiadomienie, która miała miejsce zdarzenie, Odbiorca zdarzenia odbiera to powiadomienie i definiuje odpowiedź na to. W tym artykule opisano główne składniki modelu delegowanego, jak używać zdarzenia w aplikacjach i sposobie implementacji zdarzenia w kodzie.  
  
 Aby uzyskać informacje na temat obsługi zdarzeń w systemie Windows 8.x Store apps, zobacz [zdarzenia i przegląd zdarzeń trasowanych](https://docs.microsoft.com/previous-versions/windows/apps/hh758286(v=win.10)).  
  
## <a name="events"></a>Zdarzenia  
 Zdarzenie jest wiadomością wysłaną przez obiekt do sygnalizowania wystąpienia akcji. Akcja może być spowodowane przez interakcję użytkownika, takie jak kliknięcie przycisku lub może być zgłaszany przez jakiś innych logik programu, takiej jak zmiana wartości właściwości. Nosi nazwę obiektu, który wywołuje zdarzenie *nadawcy zdarzeń*. Nadawca zdarzeń nie może ustalić, które właściwości lub metody obiektu otrzymają (dojście) zdarzenia które podnosi. Zdarzenie jest zazwyczaj członkiem nadawcy zdarzeń; na przykład <xref:System.Web.UI.WebControls.Button.Click> zdarzenie jest członkiem <xref:System.Web.UI.WebControls.Button> klasy, a <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> zdarzenie jest członkiem klasy, która implementuje <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu.  
  
 Aby zdefiniować określone zdarzenie, należy użyć `event` (w języku C#) lub `Event` (w języku Visual Basic) słowa kluczowego w podpisie wydarzenia klasy i określić typ delegata zdarzenia. Delegaty są opisane w następnej sekcji.  
  
 Zazwyczaj aby wywołać zdarzenie, dodajesz metodę, która jest oznaczona jako `protected` i `virtual` (w języku C#) lub `Protected` i `Overridable` (w języku Visual Basic). Nazwij tę metodę `On` *EventName*, na przykład `OnDataReceived`. Metoda powinna podjąć jeden parametr, który określa obiekt danych zdarzenia. Możesz podać tę metodę, aby włączyć klasy pochodne zastąpić logikę dla podnoszonego zdarzenia. Klasa pochodna zawsze powinna wywołać `On` *EventName* metody klasy bazowej, aby upewnić się, że zarejestrowani delegaci otrzymają zdarzenie.  
  
 Poniższy przykład pokazuje, jak zadeklarować wydarzenie nazwane `ThresholdReached`. Zdarzenie jest skojarzone z <xref:System.EventHandler> delegatem i podnoszone w metodę o nazwie `OnThresholdReached`.  
  
 [!code-csharp[EventsOverview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#1)]
 [!code-vb[EventsOverview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#1)]  
  
## <a name="delegates"></a>Delegaty  
 Delegat to typ, który zawiera odwołanie do metody. Delegat jest zadeklarowany za pomocą podpisu, który pokazuje zwracany typ i parametry metody odwołuje i może zawierać odniesienia tylko do metod, które pasują do jego podpisu. Delegat to ten sposób równoważny wskaźnikowi funkcji bezpiecznego typu lub wywołania zwrotnego. Deklaracja delegata jest wystarczająca do zdefiniowania klasy delegata.  
  
 Delegaty mają wiele zastosowań w .NET Framework. W kontekście wydarzeń, delegat jest pośrednikiem (lub mechanizmem podobnym do wskaźnika) między źródłem zdarzeń i kod, który obsługuje zdarzenia. Można skojarzyć pełnomocnika ze zdarzeniem, łącznie z typem obiektu delegowanego w zgłoszeniu zdarzenia, jak pokazano w przykładzie w poprzedniej sekcji. Aby uzyskać więcej informacji na temat obiektów delegowanych, zobacz <xref:System.Delegate> klasy.  
  
 Program .NET Framework oferuje <xref:System.EventHandler> i <xref:System.EventHandler%601> delegatów do obsługi większości scenariuszy zdarzenia. Użyj <xref:System.EventHandler> delegata dla wszystkich zdarzeń, które nie zawierają danych zdarzenia. Użyj <xref:System.EventHandler%601> delegata dla wszystkich zdarzeń, które zawierają dane o zdarzeniu. Ci delegaci nie mają żadnej zwracanej wartości i przyjmują dwa parametry (obiekt dla źródła zdarzenia) i obiekt danych zdarzenia.  
  
 Delegaty mają charakter multiemisyjny, co oznacza, że mogą posiadać odniesienia do więcej niż jednej metody obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz <xref:System.Delegate> odwołania do stron. Delegaty zapewniają elastyczność i szczegółową kontrolę w obsłudze zdarzeń. Delegat działa jako wysyłający zdarzenia dla klasy, która wywołuje zdarzenie Utrzymując listę zarejestrowanych obsług zdarzeń dla zdarzenia.  
  
 W scenariuszach gdzie <xref:System.EventHandler> i <xref:System.EventHandler%601> delegatów nie działają, można zdefiniować delegata. Scenariusze wymagające umożliwia zdefiniowanie pełnomocnika są bardzo rzadkie, np gdy musisz pracować z kodem, który nie rozpoznaje typów ogólnych. Oznaczasz pełnomocnika z `delegate` w (C#) i `Delegate` (w języku Visual Basic) słowa kluczowego w zgłoszeniu. Poniższy przykład pokazuje, jak zadeklarować delegatów nazwanych `ThresholdReachedEventHandler`.  
  
 [!code-csharp[EventsOverview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#4)]
 [!code-vb[EventsOverview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#4)]  
  
## <a name="event-data"></a>Dane opisujące zdarzenie  
 Dane, które są skojarzone ze zdarzeniem mogą być dostarczone przez klasę danych zdarzenia. .NET Framework zawiera wiele klas danych zdarzeń, których można używać w aplikacjach. Na przykład <xref:System.IO.Ports.SerialDataReceivedEventArgs> klasa jest klasą danych zdarzeń dla <xref:System.IO.Ports.SerialPort.DataReceived?displayProperty=nameWithType> zdarzeń. .NET Framework śledzi wzorzec nazewnictwa zakończenia wszystkich klas danych zdarzeń za pomocą `EventArgs`. Należy określić klas danych zdarzenia, które jest skojarzone ze zdarzeniem patrząc na obiekt delegowany dla zdarzenia. Na przykład <xref:System.IO.Ports.SerialDataReceivedEventHandler> delegat obejmuje <xref:System.IO.Ports.SerialDataReceivedEventArgs> klasy jako jeden z jego parametrów.  
  
 <xref:System.EventArgs> Klasa jest typem podstawowym dla wszystkich klas danych zdarzeń. <xref:System.EventArgs> jest również klasą, używaną, gdy zdarzenie nie ma żadnych skojarzonych z nim danych. Podczas tworzenia zdarzenia jest przeznaczone wyłącznie do powiadamiania innych klas, które coś się stało i nie trzeba przekazywać żadnych danych, obejmują <xref:System.EventArgs> klasa jako drugi parametr w delegacie. Możesz przekazać <xref:System.EventArgs.Empty?displayProperty=nameWithType> wartości w przypadku braku danych. <xref:System.EventHandler> Delegat obejmuje <xref:System.EventArgs> klasy jako parametr.  
  
 Jeśli chcesz utworzyć klasę danych zdarzenia niestandardowego należy utworzyć klasę, która pochodzi od klasy <xref:System.EventArgs>, a następnie podaj wszelkie elementy potrzebne do przekazywania danych, które jest związane ze zdarzeniem. Zazwyczaj należy używać tego samego wzorca nazw jako .NET Framework i zakończenia Nazwa klasy danych zdarzenia, tak z `EventArgs`.  
  
 Poniższy przykład pokazuje klasę danych zdarzenia o nazwie `ThresholdReachedEventArgs`. Zawiera właściwości, które są specyficzne dla wywoływanego zdarzenia.  
  
 [!code-csharp[EventsOverview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#3)]
 [!code-vb[EventsOverview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#3)]  
  
## <a name="event-handlers"></a>Programy obsługi zdarzeń  
 Aby odpowiedzieć na zdarzenie, należy zdefiniować metodę programu obsługi zdarzeń w naczyniu zbierającym zdarzenia. Ta metoda musi odpowiadać podpisowi delegata zdarzenia, które obsługujesz. W przypadku obsługi, możesz wykonać akcje, które są wymagane, gdy zdarzenie jest wywoływane, takich jak zbieranie danych wejściowych użytkownika, po kliknięciu przycisku. Aby otrzymywać powiadomienia, gdy wystąpi zdarzenie, Twoja metoda programu obsługi zdarzeń musi subskrybować zdarzenia.  
  
 W poniższym przykładzie przedstawiono metodę programu obsługi zdarzeń o nazwie `c_ThresholdReached` które odpowiadają podpisowi dla <xref:System.EventHandler> delegować. Metoda subskrybuje `ThresholdReached` zdarzeń.  
  
 [!code-csharp[EventsOverview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#2)]
 [!code-vb[EventsOverview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#2)]  
  
## <a name="static-and-dynamic-event-handlers"></a>Programy obsługi zdarzeń statycznych i dynamicznych  
 .NET Framework umożliwia subskrybentom zarejestrowanie powiadomień o zdarzeniach statycznie lub dynamicznie. Programy obsługi zdarzeń statycznych działają przez całe życie klasy, której zdarzenie obsługują. Programy obsługi zdarzeń dynamicznych są jawnie aktywowane i dezaktywowane podczas wykonywania programu, zwykle w odpowiedzi na niektóre warunkowe logiki programu. Mogą one na przykład używane, jeśli powiadomienia zdarzeń są potrzebne tylko w określonych warunkach lub aplikacja zapewnia wiele procedur obsługi zdarzeń, a warunki uruchomieniowe określają odpowiedni do użycia. W przykładzie w poprzedniej sekcji pokazano, jak dynamicznie dodać program obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [zdarzenia](../../visual-basic/programming-guide/language-features/events/index.md) i [zdarzenia](../../csharp/programming-guide/events/index.md).  
  
## <a name="raising-multiple-events"></a>Podjęcie wielu zdarzeń  
 Jeśli klasa wywołuje wiele zdarzeń, kompilator generuje jedno pole na wystąpienie delegata zdarzenia. Jeśli liczba zdarzeń jest duża, koszt magazynowania jednego pola przypadającego na delegata może nie być akceptowane. W tych sytuacjach program .NET Framework dostarcza właściwości zdarzeń służące z inną wybraną strukturą danych do przechowywania delegatów zdarzeń.  
  
 Właściwości zdarzenia składają się z deklaracji zdarzeń, którym towarzyszą metody dostępu zdarzeń. Metody dostępu zdarzeń są metodami zdefiniowanymi przez użytkownika do dodawania lub usuwania wystąpień delegata zdarzenia ze struktury przechowywania danych. Należy pamiętać, że właściwości zdarzeń są wolniejsze od pól zdarzeń, ponieważ każdy delegat zdarzenia musi zostać pobrany zanim może być wywołana. Jest to kompromis między pamięcią i szybkością. Jeśli klasa definiuje wiele zdarzeń, które rzadko są wywoływane, można zaimplementować właściwości zdarzenia. Aby uzyskać więcej informacji, zobacz [porady: Obsługa wielu zdarzeń przy użyciu właściwości zdarzenia](../../../docs/standard/events/how-to-handle-multiple-events-using-event-properties.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: Wywoływanie zdarzeń i korzystanie z nich](../../../docs/standard/events/how-to-raise-and-consume-events.md)|Zawiera Przykłady podnoszenia i zużywania zdarzeń.|  
|[Instrukcje: Obsługa wielu zdarzeń przy użyciu właściwości zdarzenia](../../../docs/standard/events/how-to-handle-multiple-events-using-event-properties.md)|Pokazuje, jak używać właściwości zdarzenia do obsługi wielu zdarzeń.|  
|[Wzorzec projektowy obserwatora](../../../docs/standard/events/observer-design-pattern.md)|Opisuje szablon projektu, który umożliwia subskrybentom zarejestrowanie i otrzymywanie powiadomienia od dostawcy.|  
|[Instrukcje: Korzystanie ze zdarzeń w aplikacjach formularzy internetowych](../../../docs/standard/events/how-to-consume-events-in-a-web-forms-application.md)|Pokazuje, jak obsługiwać zdarzenia wywoływane przez formant formularzy sieci Web.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.EventHandler>  
- <xref:System.EventHandler%601>  
- <xref:System.EventArgs>  
- <xref:System.Delegate>  
- [Zdarzenia i przegląd zdarzeń trasowanych (aplikacje platformy uniwersalnej systemu Windows)](/windows/uwp/xaml-platform/events-and-routed-events-overview)  
- [Zdarzenia (Visual Basic)](../../visual-basic/programming-guide/language-features/events/index.md)  
- [Zdarzenia (C# Programming Guide)](../../csharp/programming-guide/events/index.md)
