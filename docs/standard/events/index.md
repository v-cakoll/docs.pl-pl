---
title: Obsługa i wywoływanie zdarzeń
description: Dowiedz się, jak obsługiwać i zgłaszać zdarzenia platformy .NET, które są oparte na modelu delegata. Ten model umożliwia subskrybentom rejestrowanie się z dostawcami lub otrzymywanie z nich powiadomień.
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
ms.openlocfilehash: 8cf0ff323e9bf7305e3d9cbb6dabd8f685059e97
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447111"
---
# <a name="handling-and-raising-events"></a>Obsługa i wywoływanie zdarzeń

Zdarzenia w programie .NET są oparte na modelu delegata. Model delegata jest zgodny z [wzorcem projektowym obserwatora](observer-design-pattern.md), co umożliwia subskrybentowi zarejestrowanie się w usłudze i otrzymywanie powiadomień od dostawcy. Nadawca zdarzeń wypychanie powiadomienia o wystąpieniu zdarzenia, a odbiorca zdarzenia odbiera to powiadomienie i definiuje odpowiedź na nie. W tym artykule opisano główne składniki modelu delegata, sposób korzystania ze zdarzeń w aplikacjach oraz sposób implementacji zdarzeń w kodzie.  
  
 Aby uzyskać informacje na temat obsługi zdarzeń w aplikacjach ze sklepu Windows 8. x, zobacz [Omówienie zdarzeń i zdarzeń kierowanych](https://docs.microsoft.com/previous-versions/windows/apps/hh758286(v=win.10)).  
  
## <a name="events"></a>Zdarzenia

Zdarzenie jest wiadomością wysłaną przez obiekt, aby sygnalizować wystąpienie akcji. Akcja może być spowodowana przez interakcję użytkownika, taką jak kliknięcie przycisku, lub może wynikać z innej logiki programu, takiej jak zmiana wartości właściwości. Obiekt, który wywołuje zdarzenie, jest nazywany *nadawcą zdarzenia*. Nadawca zdarzenia nie wie, który obiekt lub metoda otrzyma (dojście) zdarzenia, które wywołuje. Zdarzenie jest zwykle członkiem nadawcy zdarzenia; na przykład <xref:System.Web.UI.WebControls.Button.Click> zdarzenie jest członkiem <xref:System.Web.UI.WebControls.Button> klasy, a <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> zdarzenie jest członkiem klasy, która implementuje <xref:System.ComponentModel.INotifyPropertyChanged> interfejs.  
  
Aby zdefiniować zdarzenie, należy użyć [`event`](../../csharp/language-reference/keywords/event.md) słowa kluczowego C# lub Visual Basic [`Event`](../../visual-basic/language-reference/statements/event-statement.md) w sygnaturze klasy Event i określić typ delegata zdarzenia. Delegaty są opisane w następnej sekcji.  
  
Zwykle, aby zgłosić zdarzenie, należy dodać metodę, która jest oznaczona jako `protected` i `virtual` (w języku C#) lub `Protected` i `Overridable` (w Visual Basic). Nadaj nazwę tej metodzie `On` *EventName*; na przykład `OnDataReceived` . Metoda powinna przyjmować jeden parametr, który określa obiekt danych zdarzenia, który jest obiektem typu <xref:System.EventArgs> lub typu pochodnego. Ta metoda umożliwia włączenie klas pochodnych w celu zastąpienia logiki w celu podniesienia poziomu zdarzenia. Klasa pochodna zawsze powinna wywołać metodę `On` *EventName* klasy bazowej, aby upewnić się, że zarejestrowani delegowani odbiera zdarzenie.  

Poniższy przykład pokazuje, jak zadeklarować zdarzenie o nazwie `ThresholdReached` . Zdarzenie jest skojarzone z <xref:System.EventHandler> delegatem i wywoływane w metodzie o nazwie `OnThresholdReached` .  
  
 [!code-csharp[EventsOverview#1](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#1)]
 [!code-vb[EventsOverview#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#1)]  
  
## <a name="delegates"></a>Delegaci

Delegat jest typem, który przechowuje odwołanie do metody. Delegat jest zadeklarowany za pomocą podpisu, który pokazuje zwracany typ i parametry dla metod, do których się odwołuje, i może zawierać odwołania tylko do metod, które pasują do podpisu. Delegat jest analogiczny do wskaźnika funkcji bezpiecznego typu lub wywołania zwrotnego. Deklaracja delegata jest wystarczająca do zdefiniowania klasy delegata.  
  
Delegaty mają wiele użycia w programie .NET. W kontekście zdarzeń delegat jest pośrednim (lub mechanizmem podobnym do wskaźnika) między źródłem zdarzenia a kodem, który obsługuje zdarzenie. Można skojarzyć delegata ze zdarzeniem, dołączając typ delegata w deklaracji zdarzenia, jak pokazano w przykładzie w poprzedniej sekcji. Aby uzyskać więcej informacji na temat delegatów, zobacz <xref:System.Delegate> Klasa.  
  
Platforma .NET udostępnia <xref:System.EventHandler> <xref:System.EventHandler%601> delegatów i umożliwia obsługę większości scenariuszy zdarzeń. Użyj <xref:System.EventHandler> delegata dla wszystkich zdarzeń, które nie zawierają danych zdarzenia. Użyj <xref:System.EventHandler%601> delegata dla zdarzeń, które zawierają dane dotyczące zdarzenia. Te Delegaty nie mają wartości zwracanego typu i przyjmują dwa parametry (obiekt dla źródła zdarzenia i obiekt dla danych zdarzenia).  
  
Delegaty są [multiemisją](xref:System.MulticastDelegate), co oznacza, że mogą przechowywać odwołania do więcej niż jednej metody obsługi zdarzeń. Aby uzyskać szczegółowe informacje, zobacz <xref:System.Delegate> stronę referencyjną. Delegaty zapewniają elastyczność i szczegółową kontrolę w obsłudze zdarzeń. Delegat działa jako Dyspozytor zdarzeń dla klasy, która wywołuje zdarzenie przez utrzymywanie listy zarejestrowanych programów obsługi zdarzeń dla zdarzenia.  
  
W przypadku scenariuszy, w których <xref:System.EventHandler> <xref:System.EventHandler%601> Delegaty nie działają, można zdefiniować delegata. Scenariusze, które wymagają zdefiniowania delegata, są bardzo rzadkimi, na przykład gdy trzeba współpracować z kodem, który nie rozpoznaje typów ogólnych. Obiekt delegowany jest oznaczany za pomocą [`delegate`](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) [`Delegate`](../../visual-basic/language-reference/statements/delegate-statement.md) słowa kluczowego C# i Visual Basic w deklaracji. Poniższy przykład pokazuje, jak zadeklarować delegata o nazwie `ThresholdReachedEventHandler` .  
  
[!code-csharp[EventsOverview#4](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#4)]
[!code-vb[EventsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#4)]  
  
## <a name="event-data"></a>Dane zdarzenia

Dane skojarzone ze zdarzeniem mogą być dostarczane za pomocą klasy danych zdarzenia. Platforma .NET udostępnia wiele klas danych zdarzeń, których można używać w aplikacjach. Na przykład <xref:System.IO.Ports.SerialDataReceivedEventArgs> Klasa jest klasą danych zdarzenia dla <xref:System.IO.Ports.SerialPort.DataReceived?displayProperty=nameWithType> zdarzenia. .NET stosuje wzorzec nazewnictwa kończący wszystkie klasy danych zdarzeń za pomocą `EventArgs` . Należy określić, która Klasa danych zdarzenia jest skojarzona ze zdarzeniem, przeglądając delegata zdarzenia. Na przykład <xref:System.IO.Ports.SerialDataReceivedEventHandler> Delegat zawiera <xref:System.IO.Ports.SerialDataReceivedEventArgs> klasę jako jeden z jej parametrów.  
  
<xref:System.EventArgs>Klasa jest typem podstawowym dla wszystkich klas danych zdarzeń. <xref:System.EventArgs>jest również klasą używaną, gdy do zdarzenia nie są skojarzone żadne dane. Podczas tworzenia zdarzenia, które jest przeznaczone tylko do powiadamiania innych klas, których coś dotyczy, i nie musi przekazywać żadnych danych, należy uwzględnić <xref:System.EventArgs> klasę jako drugi parametr w delegatze. Wartość można przekazać, <xref:System.EventArgs.Empty?displayProperty=nameWithType> gdy nie są dostarczane żadne dane. <xref:System.EventHandler>Delegat zawiera <xref:System.EventArgs> klasę jako parametr.  
  
Jeśli chcesz utworzyć dostosowaną klasę danych zdarzenia, Utwórz klasę, która pochodzi od <xref:System.EventArgs> , a następnie podaj wszelkich członków potrzebnych do przekazywania danych związanych ze zdarzeniem. Zazwyczaj należy używać tego samego wzorca nazewnictwa jak .NET i kończyć nazwę klasy danych zdarzenia za pomocą `EventArgs` .  
  
Poniższy przykład pokazuje klasę danych zdarzenia o nazwie `ThresholdReachedEventArgs` . Zawiera właściwości, które są specyficzne dla wywoływanego zdarzenia.  
  
[!code-csharp[EventsOverview#3](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#3)]
[!code-vb[EventsOverview#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#3)]  
  
## <a name="event-handlers"></a>Procedury obsługi zdarzeń

Aby odpowiedzieć na zdarzenie, należy zdefiniować metodę obsługi zdarzeń w odbiorcy zdarzeń. Ta metoda musi być zgodna z sygnaturą delegata dla zdarzenia, które jest obsługiwane. W programie obsługi zdarzeń wykonywane są akcje, które są wymagane w przypadku zgłoszenia zdarzenia, takie jak zbieranie danych wejściowych przez użytkownika po kliknięciu przycisku. Aby otrzymywać powiadomienia, gdy wystąpi zdarzenie, metoda obsługi zdarzeń musi subskrybować zdarzenie.  
  
Poniższy przykład pokazuje metodę procedury obsługi zdarzeń o nazwie `c_ThresholdReached` , która pasuje do sygnatury <xref:System.EventHandler> delegata. Metoda subskrybuje `ThresholdReached` zdarzenie.  
  
[!code-csharp[EventsOverview#2](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#2)]
[!code-vb[EventsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#2)]  
  
## <a name="static-and-dynamic-event-handlers"></a>Procedury obsługi zdarzeń statycznych i dynamicznych  

Platforma .NET umożliwia subskrybentom rejestrację powiadomień o zdarzeniach statycznie lub dynamicznie. Procedury obsługi zdarzeń statycznych są stosowane dla całego okresu istnienia klasy, której zdarzenia obsługują. Procedury obsługi zdarzeń dynamicznych są jawnie uaktywniane i dezaktywowane podczas wykonywania programu, zazwyczaj w odpowiedzi na niektóre logiki programu warunkowego. Można na przykład użyć ich w przypadku, gdy powiadomienia o zdarzeniach są wymagane tylko w określonych warunkach lub jeśli aplikacja zawiera wiele programów obsługi zdarzeń, a warunki czasu wykonywania definiują odpowiednią wartość do użycia. W przykładzie w poprzedniej sekcji pokazano, jak dynamicznie dodać program obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [zdarzenia](../../visual-basic/programming-guide/language-features/events/index.md) (w Visual Basic) i [zdarzenia](../../csharp/programming-guide/events/index.md) (w języku C#).  
  
## <a name="raising-multiple-events"></a>Wywoływanie wielu zdarzeń  
 Jeśli Klasa wywołuje wiele zdarzeń, kompilator generuje jedno pole na wystąpienie delegata zdarzenia. Jeśli liczba zdarzeń jest duża, koszt magazynowania jednego pola na delegata może nie być akceptowalny. W takich sytuacjach platforma .NET udostępnia właściwości zdarzeń, które mogą być używane z inną strukturą danych, która umożliwia przechowywanie delegatów zdarzeń.  
  
 Właściwości zdarzenia składają się z deklaracji zdarzeń, które towarzyszą metodom dostępu do zdarzeń. Metody dostępu zdarzeń są zdefiniowane w celu dodawania lub usuwania wystąpień delegatów zdarzeń ze struktury danych magazynu. Należy pamiętać, że właściwości zdarzeń są wolniejsze od pól zdarzeń, ponieważ każdy delegat zdarzenia musi zostać pobrany, aby można było go wywołać. Handel jest między pamięcią a szybkością. Jeśli klasa definiuje wiele zdarzeń, które są rzadko zgłaszane, należy zaimplementować właściwości zdarzenia. Aby uzyskać więcej informacji, zobacz [How to: obsługa wielu zdarzeń przy użyciu właściwości zdarzenia](how-to-handle-multiple-events-using-event-properties.md).  
  
## <a name="related-topics"></a>Powiązane tematy  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Porady: wywoływanie zdarzeń i korzystanie z nich](how-to-raise-and-consume-events.md)|Zawiera przykłady podnoszenia i zużywania zdarzeń.|  
|[Instrukcje: Obsługa wielu zdarzeń przy użyciu właściwości zdarzenia](how-to-handle-multiple-events-using-event-properties.md)|Pokazuje, jak używać właściwości zdarzenia do obsługi wielu zdarzeń.|  
|[Wzorzec projektowy obserwatora](observer-design-pattern.md)|Opisuje Wzorzec projektowy, który umożliwia subskrybentowi zarejestrowanie się w usłudze i otrzymywanie powiadomień od dostawcy.|  
|[Porady: korzystanie ze zdarzeń w aplikacjach formularzy sieci Web](how-to-consume-events-in-a-web-forms-application.md)|Pokazuje, jak obsłużyć zdarzenie, które jest wywoływane przez formant formularzy sieci Web.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.EventHandler>
- <xref:System.EventHandler%601>
- <xref:System.EventArgs>
- <xref:System.Delegate>
- [Zdarzenia (Visual Basic)](../../visual-basic/programming-guide/language-features/events/index.md)
- [Zdarzenia (Przewodnik programowania w języku C#)](../../csharp/programming-guide/events/index.md)
- [Zdarzenia i zdarzenia kierowane — omówienie (platformy UWP Apps)](/windows/uwp/xaml-platform/events-and-routed-events-overview)
