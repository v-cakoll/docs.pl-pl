---
title: "Obsługa i wywoływanie zdarzeń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- delegate model for events
- application development [.NET Framework], events
- events [.NET Framework]
ms.assetid: b6f65241-e0ad-4590-a99f-200ce741bb1f
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 49355c4271efc37a40c025c0f8275ec42e13723e
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="handling-and-raising-events"></a>Obsługa i wywoływanie zdarzeń
Zdarzenia w programie .NET Framework są oparte na modelu obiektu delegowanego. Model obiektu delegowanego następuje wzorzec projektowy obserwatora, który umożliwia subskrybenta do rejestrowania i odbierania powiadomień od dostawcy. Nadawca zdarzeń wypycha powiadomienie, które miało miejsce zdarzenie, a odbiorca zdarzenia otrzymuje powiadomienia i definiuje odpowiedzi na to. W tym artykule opisano głównych składników modelu delegata, jak korzystanie ze zdarzeń w aplikacjach i implementowania zdarzenia w kodzie.  
  
 Aby uzyskać informacje na temat obsługi zdarzeń w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, zobacz [zdarzenia i przegląd kierowane zdarzenia (aplikacje ze Sklepu Windows)](http://go.microsoft.com/fwlink/p/?LinkId=261485).  
  
## <a name="events"></a>Zdarzenia  
 Zdarzenia jest wiadomość wysłana przez obiekt sygnalizują wystąpienia akcji. Akcja może być spowodowana przez użytkownika, takich jak kliknij przycisk lub może być wywoływane przez inne logikę programów, takich jak zmiana wartości właściwości. Obiekt, który wywołuje zdarzenie jest nazywany *zdarzenia*. Zdarzenia nie może ustalić, które obiekt lub metoda otrzymają (dojście) uruchamia zdarzenia. Zdarzenie jest zwykle członkiem nadawcy zdarzeń; na przykład <xref:System.Web.UI.WebControls.Button.Click> zdarzeń jest elementem członkowskim <xref:System.Web.UI.WebControls.Button> klasy i <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> zdarzeń jest elementem członkowskim klasy, która implementuje <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu.  
  
 Aby zdefiniować zdarzenia, należy użyć `event` (w języku C#) lub `Event` (w języku Visual Basic) — słowo kluczowe w podpisie zdarzenie klasy, a następnie określ typ delegata zdarzenia. Obiekty delegowane są opisane w następnej sekcji.  
  
 Zazwyczaj, aby zgłosić zdarzenie, dodaje metodę, która jest oznaczona jako `protected` i `virtual` (w języku C#) lub `Protected` i `Overridable` (w języku Visual Basic). Nazwa tej metody `On` *EventName*, na przykład `OnDataReceived`. Metoda powinna przyjmować jeden parametr, który określa obiekt danych zdarzenia. Musisz podać tę metodę, aby włączyć klasy pochodne zastąpić logikę wywołaniem zdarzenia. Klasa pochodna zawsze powinny wywoływać `On` *EventName* metody klasy podstawowej, aby upewnić się, że zarejestrowanych delegatów odbierać zdarzenia.  
  
 Poniższy przykład przedstawia sposób zadeklarować zdarzenia o nazwie `ThresholdReached`. Zdarzenie jest skojarzony z <xref:System.EventHandler> delegować i zgłoszono metodę o nazwie `OnThresholdReached`.  
  
 [!code-csharp[EventsOverview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#1)]
 [!code-vb[EventsOverview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#1)]  
  
## <a name="delegates"></a>Delegaty  
 Delegat jest typem, który zawiera odwołanie do metody. Delegat jest zadeklarowany za pomocą podpisu, który pokazuje zwracany typ i parametry dla metody odwołuje się i może zawierać odwołania tylko do metod, które odpowiada jego sygnatura. Delegat w związku z tym jest odpowiednikiem wskaźnika funkcji bezpieczny lub wywołania zwrotnego. Deklaracji obiektu delegowanego jest wystarczające, aby zdefiniować klasę obiektu delegowanego.  
  
 Obiekty delegowane mają wiele zastosowań w programie .NET Framework. W kontekście zdarzeń, delegat jest pośrednik (lub podobny wskaźnika mechanizm) między źródłem zdarzeń i kod obsługujący zdarzenia. Należy powiązać delegata ze zdarzeniem przy tym typ delegata w deklaracji zdarzenia, jak pokazano w przykładzie w poprzedniej sekcji. Aby uzyskać więcej informacji na temat delegatów, zobacz <xref:System.Delegate> klasy.  
  
 Platforma .NET Framework zapewnia <xref:System.EventHandler> i <xref:System.EventHandler%601> delegatów, aby obsługiwać większość scenariuszy zdarzeń. Użyj <xref:System.EventHandler> delegowanie dla wszystkich zdarzeń, które nie zawierają danych zdarzenia. Użyj <xref:System.EventHandler%601> delegowanie dla zdarzenia, które zawierają dane o zdarzeniu. Te obiekty delegowane niezawierające wartości zwracany typ i mieć dwa parametry (obiekt źródła zdarzenia) oraz obiekt danych zdarzenia.  
  
 Obiekty delegowane są multiemisji, co oznacza, że zostały zablokowane odwołania do więcej niż jednej metody obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz <xref:System.Delegate> strony odwołania. Obiekty delegowane zapewniają elastyczność i szczegółową kontrolę w obsłudze zdarzeń. Delegat działa jako dyspozytora zdarzeń klasy, która wywołuje zdarzenie Utrzymując listę programów obsługi zdarzeń zarejestrowane zdarzenia.  
  
 W scenariuszach, gdzie <xref:System.EventHandler> i <xref:System.EventHandler%601> delegatów nie działają, można zdefiniować delegata. Scenariusze wymagające zdefiniowanie delegata są bardzo rzadko, takie jak kiedy należy skontaktować się z kodu, który nie rozpoznaje typów ogólnych. Oznacz delegata z `delegate` w (C#) i `Delegate` (w języku Visual Basic) — słowo kluczowe w deklaracji. Poniższy przykład przedstawia sposób deklaruje delegata o nazwie `ThresholdReachedEventHandler`.  
  
 [!code-csharp[EventsOverview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#4)]
 [!code-vb[EventsOverview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#4)]  
  
## <a name="event-data"></a>Dane opisujące zdarzenie  
 Dane skojarzone ze zdarzeniem mogą być dostarczane za pośrednictwem klasą danych zdarzenia. .NET Framework zapewnia wiele zdarzeń klas danych używanych w aplikacjach. Na przykład <xref:System.IO.Ports.SerialDataReceivedEventArgs> klasa jest klasą danych zdarzeń dla <xref:System.IO.Ports.SerialPort.DataReceived?displayProperty=nameWithType> zdarzeń. .NET Framework następuje wzorzec nazewnictwa kończenia wszystkich klas dane zdarzeń z `EventArgs`. Należy określić, która klasa danych zdarzenia jest skojarzony ze zdarzeniem analizując delegowanie dla zdarzenia. Na przykład <xref:System.IO.Ports.SerialDataReceivedEventHandler> zawiera delegata <xref:System.IO.Ports.SerialDataReceivedEventArgs> klasy jako jeden z jego parametrów.  
  
 <xref:System.EventArgs> Klasy jest typem podstawowym dla wszystkich klas danych zdarzenia. <xref:System.EventArgs>jest również używanych podczas zdarzenie nie ma wszelkie dane skojarzone z nią klasy. Podczas tworzenia zdarzeń jest przeznaczone tylko do powiadamiania innych klas, które coś się stało i nie trzeba przekazać wszystkie dane, obejmują <xref:System.EventArgs> klasy jako drugiego parametru w obiekt delegowany. Można przekazać <xref:System.EventArgs.Empty?displayProperty=nameWithType> wartość, gdy jest dostępne żadne dane. <xref:System.EventHandler> Zawiera delegata <xref:System.EventArgs> klasy jako parametr.  
  
 Jeśli chcesz utworzyć klasę danych niestandardowych zdarzeń, Utwórz klasę, która pochodzi z <xref:System.EventArgs>, a następnie podaj żadnych elementów członkowskich potrzebne do przekazywania danych, który jest powiązany ze zdarzeniem. Zwykle należy używać tego samego wzorca nazewnictwa jako programu .NET Framework i kończyć na nazwę klasy dane zdarzeń z `EventArgs`.  
  
 W poniższym przykładzie przedstawiono klasę danych zdarzenia o nazwie `ThresholdReachedEventArgs`. Zawiera właściwości, które są specyficzne dla zdarzenia są zgłaszane.  
  
 [!code-csharp[EventsOverview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#3)]
 [!code-vb[EventsOverview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#3)]  
  
## <a name="event-handlers"></a>Programy obsługi zdarzeń  
 Aby odpowiedzieć na zdarzenie, definiowania metoda obsługi zdarzeń odbiorcy zdarzeń. Ta metoda musi być zgodna podpis delegata zdarzenia, które są obsługi. W przypadku obsługi, możesz wykonać akcje, które są wymagane, gdy zdarzenie jest zgłaszane, takich jak zbieranie danych wejściowych użytkownika, po kliknięciu przycisku. Aby otrzymywać powiadomienia, gdy wystąpi zdarzenie, Twoje metoda obsługi zdarzeń musi subskrybować zdarzenia.  
  
 W poniższym przykładzie przedstawiono metoda obsługi zdarzeń o nazwie `c_ThresholdReached` odpowiadającego podpis dla <xref:System.EventHandler> delegowanie. Metoda subskrybuje `ThresholdReached` zdarzeń.  
  
 [!code-csharp[EventsOverview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#2)]
 [!code-vb[EventsOverview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#2)]  
  
## <a name="static-and-dynamic-event-handlers"></a>Programy obsługi zdarzeń statycznych i dynamicznych  
 .NET Framework umożliwia subskrybentów zarejestrować powiadomienia o zdarzeniach statycznie lub dynamicznie. Programy obsługi zdarzeń statycznych działają dla całego okresu klasa zdarzenia, których obsługują. Programy obsługi zdarzeń dynamiczne są jawnie aktywowana i wyłączone podczas wykonywania programu, zazwyczaj w odpowiedzi na niektóre logikę warunkową program. Na przykład użyciem czy powiadomienia o zdarzeniach są wymagane tylko w pewnych warunkach, czy aplikacja zawiera wielu obsług zdarzeń i warunków środowiska wykonawczego zdefiniować odpowiednie do użycia. W przykładzie w poprzedniej sekcji przedstawiono sposób dynamiczne dodawanie obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [zdarzenia](../../visual-basic/programming-guide/language-features/events/index.md) i [zdarzenia](../../csharp/programming-guide/events/index.md).  
  
## <a name="raising-multiple-events"></a>Podjęcie wielu zdarzeń  
 Jeśli klasa wywołuje wiele zdarzeń, kompilator generuje jedno pole na wystąpienie obiektu delegowanego zdarzenia. W przypadku dużej liczby zdarzeń koszt magazynowania na delegata jednego pola nie może być akceptowane. W tych sytuacjach .NET Framework zapewnia właściwości zdarzenia której można z inną strukturę danych wybranych do przechowywania obiektów delegowanych zdarzeń.  
  
 Właściwości zdarzenia składają się z wraz z metod dostępu zdarzeń deklaracje zdarzeń. Metod dostępu zdarzeń są metody definiujące można dodać ani usunąć wystąpienia delegata zdarzenia ze struktury magazynu danych. Należy zauważyć, że właściwości zdarzenia wolniej niż pola zdarzenie, ponieważ każdy delegata zdarzenia musi zostać pobrany przed może być wywoływany. Jest kompromis między pamięci i szybkości. Klasa definiuje wiele zdarzeń, które są rzadko zgłoszone, należy zaimplementować właściwości zdarzenia. Aby uzyskać więcej informacji, zobacz [porady: Obsługa wielu zdarzeń przy użyciu właściwości zdarzenia](../../../docs/standard/events/how-to-handle-multiple-events-using-event-properties.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: Wywoływanie zdarzeń i korzystanie z nich](../../../docs/standard/events/how-to-raise-and-consume-events.md)|Zawiera przykłady wywoływanie i przetwarzanie zdarzeń.|  
|[Instrukcje: Obsługa wielu zdarzeń przy użyciu właściwości zdarzenia](../../../docs/standard/events/how-to-handle-multiple-events-using-event-properties.md)|Przedstawia sposób użycia właściwości zdarzenia do obsługi wielu zdarzeń.|  
|[Wzorzec projektowy obserwatora](../../../docs/standard/events/observer-design-pattern.md)|W tym artykule opisano wzorzec projektowania, który umożliwia subskrybenta do rejestrowania i odbierania powiadomień od dostawcy.|  
|[Instrukcje: Korzystanie ze zdarzeń w aplikacjach formularzy internetowych](../../../docs/standard/events/how-to-consume-events-in-a-web-forms-application.md)|Pokazuje sposób obsługi zdarzeń, które jest wywoływane przez formant formularzy sieci Web.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.EventHandler>  
 <xref:System.EventHandler%601>  
 <xref:System.EventArgs>  
 <xref:System.Delegate>  
 [Zdarzenia i przegląd kierowane zdarzenia (aplikacji platformy uniwersalnej systemu Windows)](/windows/uwp/xaml-platform/events-and-routed-events-overview)  
 [Zdarzenia (Visual Basic)](../../visual-basic/programming-guide/language-features/events/index.md)  
 [Zdarzenia (C# przewodnik programowania w języku)](../../csharp/programming-guide/events/index.md)
