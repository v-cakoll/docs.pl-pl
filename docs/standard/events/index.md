---
title: Obsługa i wywoływanie zdarzeń
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- delegate model for events
- application development [.NET], events
- application development [.NET Framework], events
- application development [.NET Core], events
- events [.NET]
- events [.NET Core]
- events [.NET Framework]
ms.assetid: b6f65241-e0ad-4590-a99f-200ce741bb1f
ms.openlocfilehash: b8ed028bc1edabf14d7b2dd67d94b28d574d2eb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159627"
---
# <a name="handling-and-raising-events"></a>Obsługa i podnoszenie zdarzeń

Zdarzenia w .NET są oparte na modelu delegata. Model delegata następuje [wzorca projektu obserwatora](observer-design-pattern.md), który umożliwia subskrybentowi rejestrowanie się i odbieranie powiadomień od dostawcy. Nadawca zdarzenia wypycha powiadomienie, że zdarzenie miało miejsce, a odbiorca zdarzenia odbiera to powiadomienie i definiuje odpowiedź na nie. W tym artykule opisano główne składniki modelu delegata, jak używać zdarzeń w aplikacjach i jak zaimplementować zdarzenia w kodzie.  
  
 Aby uzyskać informacje dotyczące obsługi zdarzeń w aplikacjach ze Sklepu Windows 8.x, zobacz [Omówienie zdarzeń i zdarzeń trasowanych](https://docs.microsoft.com/previous-versions/windows/apps/hh758286(v=win.10)).  
  
## <a name="events"></a>Zdarzenia

Zdarzenie to wiadomość wysłana przez obiekt w celu zasygnalizowania wystąpienia akcji. Akcja może być spowodowana przez interakcję z użytkownikiem, takich jak kliknięcie przycisku lub może wynikać z innej logiki programu, takich jak zmiana wartości właściwości. Obiekt, który wywołuje zdarzenie jest nazywany *nadawcą zdarzenia*. Nadawca zdarzenia nie wie, który obiekt lub metoda otrzyma (doobsługi) zdarzenia, które wywołuje. Zdarzenie jest zazwyczaj członkiem nadawcy wydarzenia; na przykład <xref:System.Web.UI.WebControls.Button.Click> zdarzenie jest członkiem <xref:System.Web.UI.WebControls.Button> klasy, a <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> zdarzenie jest członkiem klasy, która <xref:System.ComponentModel.INotifyPropertyChanged> implementuje interfejs.  
  
Aby zdefiniować zdarzenie, należy użyć [`event`](../../csharp/language-reference/keywords/event.md) C# [`Event`](../../visual-basic/language-reference/statements/event-statement.md) lub Visual Basic słowa kluczowego w podpisie klasy zdarzenia i określić typ delegata dla zdarzenia. Delegaci są opisane w następnej sekcji.  
  
Zazwyczaj, aby podnieść zdarzenie, należy dodać metodę, `protected` `virtual` która jest oznaczona jako i (w języku C#) lub `Protected` (w `Overridable` języku Visual Basic). Nazwij `On`tę metodę *Nazwa zdarzenia;* na przykład `OnDataReceived`. Metoda powinna podjąć jeden parametr, który określa obiekt danych zdarzenia, który jest obiektem typu <xref:System.EventArgs> lub typu pochodnego. Ta metoda umożliwia klasy pochodne, aby zastąpić logikę do podnoszenia zdarzenia. Klasa pochodna powinna zawsze `On`wywołać *EventName* metody klasy podstawowej, aby upewnić się, że zarejestrowani delegaci odbierają zdarzenie.  

W poniższym przykładzie pokazano, `ThresholdReached`jak zadeklarować zdarzenie o nazwie . Zdarzenie jest skojarzone z pełnomocnikiem <xref:System.EventHandler> i `OnThresholdReached`wywoływane w metodzie o nazwie .  
  
 [!code-csharp[EventsOverview#1](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#1)]
 [!code-vb[EventsOverview#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#1)]  
  
## <a name="delegates"></a>Delegaty

Delegat jest typem, który zawiera odwołanie do metody. Delegat jest zadeklarowany z podpisem, który pokazuje typ zwracany i parametry dla metod, do których się odwołuje, i może przechowywać odwołania tylko do metod, które pasują do jego podpisu. Delegat jest zatem odpowiednikiem wskaźnika funkcji bezpiecznego typu lub wywołania wywołania odgłosowego. Deklaracja delegata jest wystarczająca do zdefiniowania klasy delegata.  
  
Pełnomocnicy mają wiele zastosowań w .NET. W kontekście zdarzeń delegat jest pośrednikiem (lub mechanizmem przypominającym wskaźnik) między źródłem zdarzenia a kodem, który obsługuje zdarzenie. Pełnomocnika można skojarzyć ze zdarzeniem, dołączając typ pełnomocnika do deklaracji zdarzenia, jak pokazano w przykładzie w poprzedniej sekcji. Aby uzyskać więcej informacji <xref:System.Delegate> na temat delegatów, zobacz klasę.  
  
.NET udostępnia <xref:System.EventHandler> <xref:System.EventHandler%601> i delegatów do obsługi większości scenariuszy zdarzeń. Użyj <xref:System.EventHandler> pełnomocnika dla wszystkich zdarzeń, które nie zawierają danych zdarzeń. Pełnomocnika <xref:System.EventHandler%601> służy do zdarzeń, które zawierają dane o zdarzeniu. Te delegatów nie mają wartości typu zwracanego i podjąć dwa parametry (obiekt dla źródła zdarzenia i obiekt dla danych zdarzenia).  
  
Delegaci są [multiemisji](xref:System.MulticastDelegate), co oznacza, że mogą posiadać odwołania do więcej niż jednej metody obsługi zdarzeń. Szczegółowe informacje można <xref:System.Delegate> znaleźć na stronie referencyjnej. Delegaci zapewniają elastyczność i precyzyjną kontrolę w obsłudze zdarzeń. Delegowany działa jako dyspozytor zdarzeń dla klasy, która wywołuje zdarzenie, utrzymując listę zarejestrowanych programów obsługi zdarzeń dla zdarzenia.  
  
W przypadku scenariuszy, w <xref:System.EventHandler> których i <xref:System.EventHandler%601> delegatów nie działają, można zdefiniować pełnomocnika. Scenariusze, które wymagają zdefiniowania delegata są bardzo rzadkie, na przykład, gdy trzeba pracować z kodem, który nie rozpoznaje typów ogólnych. W deklaracji oznacza się pełnomocnika słowem kluczowym C# [`delegate`](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) i Visual Basic. [`Delegate`](../../visual-basic/language-reference/statements/delegate-statement.md) W poniższym przykładzie pokazano, `ThresholdReachedEventHandler`jak zadeklarować pełnomocnika o nazwie .  
  
[!code-csharp[EventsOverview#4](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#4)]
[!code-vb[EventsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#4)]  
  
## <a name="event-data"></a>Dane zdarzenia

Dane skojarzone ze zdarzeniem mogą być dostarczane za pośrednictwem klasy danych zdarzenia. .NET udostępnia wiele klas danych zdarzeń, których można używać w aplikacjach. Na przykład <xref:System.IO.Ports.SerialDataReceivedEventArgs> klasa jest klasą danych <xref:System.IO.Ports.SerialPort.DataReceived?displayProperty=nameWithType> zdarzenia dla zdarzenia. .NET następuje wzorzec nazewnictwa zakończenia `EventArgs`wszystkich klas danych zdarzeń z . Można określić, która klasa danych zdarzenia jest skojarzona ze zdarzeniem, patrząc na pełnomocnika zdarzenia. Na przykład <xref:System.IO.Ports.SerialDataReceivedEventHandler> delegat zawiera <xref:System.IO.Ports.SerialDataReceivedEventArgs> klasę jako jeden z jej parametrów.  
  
Klasa <xref:System.EventArgs> jest typem podstawowym dla wszystkich klas danych zdarzeń. <xref:System.EventArgs>jest również klasą, której używasz, gdy zdarzenie nie ma żadnych danych skojarzonych z nim. Podczas tworzenia zdarzenia, które ma tylko powiadomić inne klasy, że coś się <xref:System.EventArgs> stało i nie trzeba przekazywać żadnych danych, należy uwzględnić klasę jako drugi parametr w pełnomocnika. Można przekazać <xref:System.EventArgs.Empty?displayProperty=nameWithType> wartość, gdy nie podano żadnych danych. Delegat <xref:System.EventHandler> zawiera <xref:System.EventArgs> klasę jako parametr.  
  
Aby utworzyć dostosowaną klasę danych zdarzenia, należy utworzyć <xref:System.EventArgs>klasę, która pochodzi z , a następnie podać wszystkie elementy członkowskie potrzebne do przekazywania danych, które są związane ze zdarzeniem. Zazwyczaj należy użyć tego samego wzorca nazewnictwa jako .NET i `EventArgs`zakończyć nazwę klasy danych zdarzenia za pomocą .  
  
W poniższym przykładzie przedstawiono `ThresholdReachedEventArgs`klasę danych zdarzenia o nazwie . Zawiera właściwości, które są specyficzne dla zdarzenia wywoływane.  
  
[!code-csharp[EventsOverview#3](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#3)]
[!code-vb[EventsOverview#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#3)]  
  
## <a name="event-handlers"></a>Procedury obsługi zdarzeń

Aby odpowiedzieć na zdarzenie, należy zdefiniować metodę obsługi zdarzeń w odbiorniku zdarzeń. Ta metoda musi odpowiadać podpisowi pełnomocnika dla zdarzenia, które obsługujesz. W programie obsługi zdarzeń można wykonać akcje, które są wymagane, gdy zdarzenie jest wywoływane, takich jak zbieranie danych wejściowych użytkownika po kliknięciu przycisku przez użytkownika. Aby otrzymywać powiadomienia po wystąpieniu zdarzenia, metoda obsługi zdarzeń musi subskrybować zdarzenie.  
  
W poniższym przykładzie przedstawiono `c_ThresholdReached` metodę obsługi zdarzeń <xref:System.EventHandler> o nazwie, która pasuje do podpisu pełnomocnika. Metoda subskrybuje `ThresholdReached` zdarzenie.  
  
[!code-csharp[EventsOverview#2](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#2)]
[!code-vb[EventsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#2)]  
  
## <a name="static-and-dynamic-event-handlers"></a>Statyczne i dynamiczne programy obsługi zdarzeń  

.NET umożliwia subskrybentom rejestrowanie powiadomień o zdarzeniach statycznie lub dynamicznie. Statyczne programy obsługi zdarzeń są w mocy dla całego życia klasy, których zdarzenia obsługują. Dynamiczne programy obsługi zdarzeń są jawnie aktywowane i dezaktywowane podczas wykonywania programu, zwykle w odpowiedzi na logikę programu warunkowego. Na przykład można użyć, jeśli powiadomienia o zdarzeniach są potrzebne tylko pod pewnymi warunkami lub jeśli aplikacja zapewnia wiele programów obsługi zdarzeń i warunki czasu wykonywania zdefiniować odpowiedni do użycia. W przykładzie w poprzedniej sekcji pokazano, jak dynamicznie dodawać program obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [Zdarzenia](../../visual-basic/programming-guide/language-features/events/index.md) (w języku Visual Basic) i [Zdarzenia](../../csharp/programming-guide/events/index.md) (w języku C#).  
  
## <a name="raising-multiple-events"></a>Podnoszenie wielu zdarzeń  
 Jeśli klasa wywołuje wiele zdarzeń, kompilator generuje jedno pole na wystąpienie delegata zdarzenia. Jeśli liczba zdarzeń jest duża, koszt magazynowania jednego pola na delegata może nie być do przyjęcia. W takich sytuacjach .NET udostępnia właściwości zdarzeń, których można używać z inną strukturą danych do przechowywania delegatów zdarzeń.  
  
 Właściwości zdarzenia składają się z deklaracji zdarzeń wraz z akcesorami zdarzeń. Akcesory zdarzeń to metody zdefiniowane w celu dodania lub usunięcia wystąpień delegatów zdarzeń ze struktury danych magazynu. Należy zauważyć, że właściwości zdarzenia są wolniejsze niż pola zdarzeń, ponieważ każdy pełnomocnik zdarzenia musi zostać pobrany, zanim będzie można wywołać. Kompromis jest między pamięcią a szybkością. Jeśli klasa definiuje wiele zdarzeń, które są rzadko wywoływane, należy zaimplementować właściwości zdarzenia. Aby uzyskać więcej informacji, zobacz [Jak: Obsługiwać wiele zdarzeń przy użyciu właściwości zdarzeń](how-to-handle-multiple-events-using-event-properties.md).  
  
## <a name="related-topics"></a>Powiązane tematy  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Porady: wywoływanie zdarzeń i korzystanie z nich](how-to-raise-and-consume-events.md)|Zawiera przykłady zdarzeń pozyskiwania i używania.|  
|[Instrukcje: Obsługa wielu zdarzeń przy użyciu właściwości zdarzenia](how-to-handle-multiple-events-using-event-properties.md)|Pokazuje, jak używać właściwości zdarzeń do obsługi wielu zdarzeń.|  
|[Wzorzec projektowy obserwatora](observer-design-pattern.md)|W tym artykule opisano wzorzec projektu, który umożliwia subskrybentowi zarejestrować się i otrzymywać powiadomienia od dostawcy.|  
|[Porady: korzystanie ze zdarzeń w aplikacjach formularzy sieci Web](how-to-consume-events-in-a-web-forms-application.md)|Pokazuje, jak obsługiwać zdarzenie wywoływane przez formant formularzy sieci Web.|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.EventHandler>
- <xref:System.EventHandler%601>
- <xref:System.EventArgs>
- <xref:System.Delegate>
- [Zdarzenia (Visual Basic)](../../visual-basic/programming-guide/language-features/events/index.md)
- [Zdarzenia (Przewodnik programowania w języku C#)](../../csharp/programming-guide/events/index.md)
- [Omówienie zdarzeń i zdarzeń trasowanych (aplikacje usługi Windows)](/windows/uwp/xaml-platform/events-and-routed-events-overview)
