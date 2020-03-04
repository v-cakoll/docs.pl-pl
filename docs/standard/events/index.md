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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159627"
---
# <a name="handling-and-raising-events"></a>Obsługa i wywoływanie zdarzeń

Zdarzenia w programie .NET są oparte na modelu delegata. Model delegata jest zgodny z [wzorcem projektowym obserwatora](observer-design-pattern.md), co umożliwia subskrybentowi zarejestrowanie się w usłudze i otrzymywanie powiadomień od dostawcy. Nadawca zdarzeń wypychanie powiadomienia o wystąpieniu zdarzenia, a odbiorca zdarzenia odbiera to powiadomienie i definiuje odpowiedź na nie. W tym artykule opisano główne składniki modelu delegata, sposób korzystania ze zdarzeń w aplikacjach oraz sposób implementacji zdarzeń w kodzie.  
  
 Aby uzyskać informacje na temat obsługi zdarzeń w aplikacjach ze sklepu Windows 8. x, zobacz [Omówienie zdarzeń i zdarzeń kierowanych](https://docs.microsoft.com/previous-versions/windows/apps/hh758286(v=win.10)).  
  
## <a name="events"></a>Zdarzenia

Zdarzenie jest wiadomością wysłaną przez obiekt, aby sygnalizować wystąpienie akcji. Akcja może być spowodowana przez interakcję użytkownika, taką jak kliknięcie przycisku, lub może wynikać z innej logiki programu, takiej jak zmiana wartości właściwości. Obiekt, który wywołuje zdarzenie, jest nazywany *nadawcą zdarzenia*. Nadawca zdarzenia nie wie, który obiekt lub metoda otrzyma (dojście) zdarzenia, które wywołuje. Zdarzenie jest zwykle członkiem nadawcy zdarzenia; na przykład zdarzenie <xref:System.Web.UI.WebControls.Button.Click> jest członkiem klasy <xref:System.Web.UI.WebControls.Button>, a zdarzenie <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> jest członkiem klasy implementującej interfejs <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
Aby zdefiniować zdarzenie, należy użyć C# słowa kluczowego [`event`](../../csharp/language-reference/keywords/event.md) lub Visual Basic [`Event`](../../visual-basic/language-reference/statements/event-statement.md) w sygnaturze klasy Event i określić typ delegata zdarzenia. Delegaty są opisane w następnej sekcji.  
  
Zwykle, aby zgłosić zdarzenie, należy dodać metodę, która jest oznaczona jako `protected` i `virtual` (in C#) lub `Protected` i `Overridable` (w Visual Basic). Nadaj nazwę tej metodzie `On`*EventName*; na przykład `OnDataReceived`. Metoda powinna przyjmować jeden parametr, który określa obiekt danych zdarzenia, który jest obiektem typu <xref:System.EventArgs> lub typem pochodnym. Ta metoda umożliwia włączenie klas pochodnych w celu zastąpienia logiki w celu podniesienia poziomu zdarzenia. Klasa pochodna zawsze powinna wywołać metodę `On`*EventName* klasy bazowej, aby upewnić się, że zarejestrowani delegowani odbiera zdarzenie.  

Poniższy przykład pokazuje, jak zadeklarować zdarzenie o nazwie `ThresholdReached`. Zdarzenie jest skojarzone z delegatem <xref:System.EventHandler> i wywoływane w metodzie o nazwie `OnThresholdReached`.  
  
 [!code-csharp[EventsOverview#1](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#1)]
 [!code-vb[EventsOverview#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#1)]  
  
## <a name="delegates"></a>Delegaty

Delegat jest typem, który przechowuje odwołanie do metody. Delegat jest zadeklarowany za pomocą podpisu, który pokazuje zwracany typ i parametry dla metod, do których się odwołuje, i może zawierać odwołania tylko do metod, które pasują do podpisu. Delegat jest analogiczny do wskaźnika funkcji bezpiecznego typu lub wywołania zwrotnego. Deklaracja delegata jest wystarczająca do zdefiniowania klasy delegata.  
  
Delegaty mają wiele użycia w programie .NET. W kontekście zdarzeń delegat jest pośrednim (lub mechanizmem podobnym do wskaźnika) między źródłem zdarzenia a kodem, który obsługuje zdarzenie. Można skojarzyć delegata ze zdarzeniem, dołączając typ delegata w deklaracji zdarzenia, jak pokazano w przykładzie w poprzedniej sekcji. Aby uzyskać więcej informacji na temat delegatów, zobacz Klasa <xref:System.Delegate>.  
  
Platforma .NET udostępnia delegatów <xref:System.EventHandler> i <xref:System.EventHandler%601> do obsługi większości scenariuszy zdarzeń. Dla wszystkich zdarzeń, które nie zawierają danych zdarzenia, należy użyć delegata <xref:System.EventHandler>. Użyj delegata <xref:System.EventHandler%601> dla zdarzeń, które zawierają dane dotyczące zdarzenia. Te Delegaty nie mają wartości zwracanego typu i przyjmują dwa parametry (obiekt dla źródła zdarzenia i obiekt dla danych zdarzenia).  
  
Delegaty są [multiemisją](xref:System.MulticastDelegate), co oznacza, że mogą przechowywać odwołania do więcej niż jednej metody obsługi zdarzeń. Aby uzyskać szczegółowe informacje, zobacz stronę referencyjną <xref:System.Delegate>. Delegaty zapewniają elastyczność i szczegółową kontrolę w obsłudze zdarzeń. Delegat działa jako Dyspozytor zdarzeń dla klasy, która wywołuje zdarzenie przez utrzymywanie listy zarejestrowanych programów obsługi zdarzeń dla zdarzenia.  
  
W scenariuszach, w których <xref:System.EventHandler> i <xref:System.EventHandler%601> delegatów nie działają, można zdefiniować delegata. Scenariusze, które wymagają zdefiniowania delegata, są bardzo rzadkimi, na przykład gdy trzeba współpracować z kodem, który nie rozpoznaje typów ogólnych. Delegat można oznaczyć za pomocą C# słowa kluczowego [`delegate`](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) i Visual Basic [`Delegate`](../../visual-basic/language-reference/statements/delegate-statement.md) w deklaracji. Poniższy przykład pokazuje, jak zadeklarować delegata o nazwie `ThresholdReachedEventHandler`.  
  
[!code-csharp[EventsOverview#4](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#4)]
[!code-vb[EventsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#4)]  
  
## <a name="event-data"></a>Dane zdarzenia

Dane skojarzone ze zdarzeniem mogą być dostarczane za pomocą klasy danych zdarzenia. Platforma .NET udostępnia wiele klas danych zdarzeń, których można używać w aplikacjach. Na przykład Klasa <xref:System.IO.Ports.SerialDataReceivedEventArgs> jest klasą danych zdarzenia dla zdarzenia <xref:System.IO.Ports.SerialPort.DataReceived?displayProperty=nameWithType>. .NET stosuje wzorzec nazewnictwa kończący wszystkie klasy danych zdarzeń z `EventArgs`. Należy określić, która Klasa danych zdarzenia jest skojarzona ze zdarzeniem, przeglądając delegata zdarzenia. Na przykład delegat <xref:System.IO.Ports.SerialDataReceivedEventHandler> zawiera klasę <xref:System.IO.Ports.SerialDataReceivedEventArgs> jako jeden z jej parametrów.  
  
Klasa <xref:System.EventArgs> jest typem podstawowym dla wszystkich klas danych zdarzeń. <xref:System.EventArgs> jest również klasą używaną, gdy do zdarzenia nie są skojarzone żadne dane. Podczas tworzenia zdarzenia, które jest przeznaczone tylko do powiadamiania innych klas, których coś dotyczy, i nie musi przekazywać żadnych danych, należy uwzględnić klasę <xref:System.EventArgs> jako drugi parametr w delegatze. Można przekazać wartość <xref:System.EventArgs.Empty?displayProperty=nameWithType>, gdy nie są dostarczane żadne dane. Delegat <xref:System.EventHandler> zawiera klasę <xref:System.EventArgs> jako parametr.  
  
Jeśli chcesz utworzyć dostosowaną klasę danych zdarzenia, Utwórz klasę pochodzącą z <xref:System.EventArgs>, a następnie podaj wszelkich członków, którzy będą musieli przekazać dane związane ze zdarzeniem. Zazwyczaj należy używać tego samego wzorca nazewnictwa jak .NET i kończyć nazwę klasy danych zdarzenia z `EventArgs`.  
  
Poniższy przykład pokazuje klasę danych zdarzenia o nazwie `ThresholdReachedEventArgs`. Zawiera właściwości, które są specyficzne dla wywoływanego zdarzenia.  
  
[!code-csharp[EventsOverview#3](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#3)]
[!code-vb[EventsOverview#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#3)]  
  
## <a name="event-handlers"></a>Procedury obsługi zdarzeń

Aby odpowiedzieć na zdarzenie, należy zdefiniować metodę obsługi zdarzeń w odbiorcy zdarzeń. Ta metoda musi być zgodna z sygnaturą delegata dla zdarzenia, które jest obsługiwane. W programie obsługi zdarzeń wykonywane są akcje, które są wymagane w przypadku zgłoszenia zdarzenia, takie jak zbieranie danych wejściowych przez użytkownika po kliknięciu przycisku. Aby otrzymywać powiadomienia, gdy wystąpi zdarzenie, metoda obsługi zdarzeń musi subskrybować zdarzenie.  
  
Poniższy przykład przedstawia metodę procedury obsługi zdarzeń o nazwie `c_ThresholdReached`, która pasuje do sygnatury <xref:System.EventHandler> delegata. Metoda subskrybuje zdarzenie `ThresholdReached`.  
  
[!code-csharp[EventsOverview#2](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#2)]
[!code-vb[EventsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#2)]  
  
## <a name="static-and-dynamic-event-handlers"></a>Procedury obsługi zdarzeń statycznych i dynamicznych  

Platforma .NET umożliwia subskrybentom rejestrację powiadomień o zdarzeniach statycznie lub dynamicznie. Procedury obsługi zdarzeń statycznych są stosowane dla całego okresu istnienia klasy, której zdarzenia obsługują. Procedury obsługi zdarzeń dynamicznych są jawnie uaktywniane i dezaktywowane podczas wykonywania programu, zazwyczaj w odpowiedzi na niektóre logiki programu warunkowego. Można na przykład użyć ich w przypadku, gdy powiadomienia o zdarzeniach są wymagane tylko w określonych warunkach lub jeśli aplikacja zawiera wiele programów obsługi zdarzeń, a warunki czasu wykonywania definiują odpowiednią wartość do użycia. W przykładzie w poprzedniej sekcji pokazano, jak dynamicznie dodać program obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [zdarzenia](../../visual-basic/programming-guide/language-features/events/index.md) (w Visual Basic) i [zdarzenia](../../csharp/programming-guide/events/index.md) ( C#w programie).  
  
## <a name="raising-multiple-events"></a>Wywoływanie wielu zdarzeń  
 Jeśli Klasa wywołuje wiele zdarzeń, kompilator generuje jedno pole na wystąpienie delegata zdarzenia. Jeśli liczba zdarzeń jest duża, koszt magazynowania jednego pola na delegata może nie być akceptowalny. W takich sytuacjach platforma .NET udostępnia właściwości zdarzeń, które mogą być używane z inną strukturą danych, która umożliwia przechowywanie delegatów zdarzeń.  
  
 Właściwości zdarzenia składają się z deklaracji zdarzeń, które towarzyszą metodom dostępu do zdarzeń. Metody dostępu zdarzeń są zdefiniowane w celu dodawania lub usuwania wystąpień delegatów zdarzeń ze struktury danych magazynu. Należy pamiętać, że właściwości zdarzeń są wolniejsze od pól zdarzeń, ponieważ każdy delegat zdarzenia musi zostać pobrany, aby można było go wywołać. Handel jest między pamięcią a szybkością. Jeśli klasa definiuje wiele zdarzeń, które są rzadko zgłaszane, należy zaimplementować właściwości zdarzenia. Aby uzyskać więcej informacji, zobacz [How to: obsługa wielu zdarzeń przy użyciu właściwości zdarzenia](how-to-handle-multiple-events-using-event-properties.md).  
  
## <a name="related-topics"></a>Powiązane tematy  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: Wywoływanie zdarzeń i korzystanie z nich](how-to-raise-and-consume-events.md)|Zawiera przykłady podnoszenia i zużywania zdarzeń.|  
|[Instrukcje: Obsługa wielu zdarzeń przy użyciu właściwości zdarzenia](how-to-handle-multiple-events-using-event-properties.md)|Pokazuje, jak używać właściwości zdarzenia do obsługi wielu zdarzeń.|  
|[Wzorzec projektowy obserwatora](observer-design-pattern.md)|Opisuje Wzorzec projektowy, który umożliwia subskrybentowi zarejestrowanie się w usłudze i otrzymywanie powiadomień od dostawcy.|  
|[Instrukcje: Korzystanie ze zdarzeń w aplikacjach formularzy internetowych](how-to-consume-events-in-a-web-forms-application.md)|Pokazuje, jak obsłużyć zdarzenie, które jest wywoływane przez formant formularzy sieci Web.|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.EventHandler>
- <xref:System.EventHandler%601>
- <xref:System.EventArgs>
- <xref:System.Delegate>
- [Zdarzenia (Visual Basic)](../../visual-basic/programming-guide/language-features/events/index.md)
- [Zdarzenia (C# Przewodnik programowania)](../../csharp/programming-guide/events/index.md)
- [Zdarzenia i zdarzenia kierowane — omówienie (platformy UWP Apps)](/windows/uwp/xaml-platform/events-and-routed-events-overview)
