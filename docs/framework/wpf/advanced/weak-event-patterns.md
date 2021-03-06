---
title: Słabe wzorce zdarzeń
description: Dowiedz się więcej o Windows Presentation Foundation słabym wzorcu zdarzeń, który rozwiązuje problem niezniszczonych programów obsługi, unikając przecieków pamięci.
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: 75c6888c8ac20c41d13e3787005377c75248c5d9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168270"
---
# <a name="weak-event-patterns"></a>Słabe wzorce zdarzeń
W aplikacjach jest możliwe, że programy obsługi dołączone do źródeł zdarzeń nie zostaną zniszczone w koordynacji z obiektem odbiornika, który dołączył program obsługi do źródła. Ta sytuacja może prowadzić do przecieków pamięci. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]wprowadza Wzorzec projektowy, który może służyć do rozwiązywania tego problemu, dostarczając dedykowaną klasę Menedżera dla określonych zdarzeń i implementując interfejs w detektorach dla tego zdarzenia. Ten Wzorzec projektowy jest znany jako *słaby wzorzec zdarzeń*.  
  
## <a name="why-implement-the-weak-event-pattern"></a>Dlaczego warto zaimplementować słaby wzorzec zdarzeń?  
 Nasłuchiwanie zdarzeń może prowadzić do przecieków pamięci. Typową techniką nasłuchiwania zdarzeń jest użycie składni charakterystycznej dla języka, która dołącza procedurę obsługi do zdarzenia w źródle. Na przykład w języku C# składnia jest następująca: `source.SomeEvent += new SomeEventHandler(MyEventHandler)` .  
  
 Ta technika tworzy silne odwołanie ze źródła zdarzenia do odbiornika zdarzeń. Zwykle dołączenie obsługi zdarzeń dla odbiornika powoduje, że odbiornik ma czas istnienia obiektu, na który ma wpływ okres istnienia obiektu (chyba że program obsługi zdarzeń został jawnie usunięty). W pewnych okolicznościach może być konieczne, aby okres istnienia obiektu odbiornika był kontrolowany przez inne czynniki, na przykład czy należy on do drzewa wizualnego aplikacji, a nie przez okres istnienia źródła. Za każdym razem, gdy okres istnienia obiektu źródłowego wykracza poza okres istnienia obiektu odbiornika, normalny wzorzec zdarzenia prowadzi do przecieku pamięci: odbiornik działa dłużej niż zamierzone.  
  
 Niesłaby wzorzec zdarzeń został zaprojektowany w celu rozwiązania tego problemu przecieku pamięci. Wzorca zdarzeń słabych można użyć zawsze, gdy odbiornik musi zarejestrować się na potrzeby zdarzenia, ale odbiornik nie wie jawnie, kiedy należy wyrejestrować. Wzorca zdarzeń słabych można również użyć zawsze, gdy okres istnienia obiektu źródła przekracza użyteczny okres istnienia odbiornika. (W tym przypadku jest to *przydatne* przez użytkownika). Słaby wzorzec zdarzeń umożliwia odbiornikowi rejestrowanie i odbieranie zdarzenia bez wpływu na charakterystykę okresu istnienia obiektu odbiornika w jakikolwiek sposób. W efekcie odwołanie implikowane ze źródła nie określa, czy odbiornik kwalifikuje się do wyrzucania elementów bezużytecznych. Odwołanie to słabe odwołanie, w związku z czym nazwa słabego wzorca zdarzeń i powiązane interfejsy API. Odbiornik może być wyrzucony lub zniszczony w inny sposób, a źródło może kontynuować bez zachowywania odwołań niekolekcjonowanych do teraz zniszczonych obiektów.  
  
## <a name="who-should-implement-the-weak-event-pattern"></a>Kto powinien zaimplementować słaby wzorzec zdarzeń?  
 Implementacja niesłabego wzorca zdarzeń jest interesująca głównie dla autorów kontroli. Autorem kontrolki jest w dużym stopniu odpowiedzialny za zachowanie i zawieranie kontroli oraz wpływu na aplikacje, w których został wstawiony. Obejmuje to zachowanie okresu istnienia obiektu sterowania, w szczególności obsługę opisanego problemu przecieku pamięci.  
  
 Niektóre scenariusze polegają na wykorzystaniu samego wzorca zdarzenia słabego. Jeden taki scenariusz to powiązanie danych. W powiązaniu danych wspólne jest, aby obiekt źródłowy był całkowicie niezależny od obiektu odbiornika, który jest obiektem docelowym powiązania. Wiele aspektów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] powiązania danych ma już niesłaby wzorzec zdarzeń stosowany w sposobie implementacji zdarzeń.  
  
## <a name="how-to-implement-the-weak-event-pattern"></a>Jak zaimplementować wzorzec słabych zdarzeń  
 Istnieją trzy sposoby implementacji słabego wzorca zdarzeń. W poniższej tabeli wymieniono trzy podejścia i przedstawiono wskazówki dotyczące sytuacji, w których należy użyć każdego z nich.  
  
|Podejście|Kiedy należy zaimplementować|  
|--------------|-----------------------|  
|Użyj istniejącej klasy słabego Menedżera zdarzeń|Jeśli zdarzenie, które chcesz subskrybować, ma odpowiednie <xref:System.Windows.WeakEventManager> użycie, użyj istniejącego słabego Menedżera zdarzeń. Aby zapoznać się z listą słabych menedżerów zdarzeń, które są dołączone do platformy WPF, zobacz Hierarchia dziedziczenia w <xref:System.Windows.WeakEventManager> klasie. Ze względu na to, że wliczone Menedżery zdarzeń słabych są ograniczone, prawdopodobnie trzeba będzie wybrać jedną z innych metod.|  
|Użyj generycznej słabej klasy Menedżera zdarzeń|Użyj generycznej <xref:System.Windows.WeakEventManager%602> , gdy istniejąca <xref:System.Windows.WeakEventManager> jest niedostępna, chcesz ułatwić wdrożenie i nie ma żadnych informacji o wydajności. Wartość ogólna <xref:System.Windows.WeakEventManager%602> jest mniej wydajna niż istniejący lub niestandardowy słaby Menedżer zdarzeń. Na przykład Klasa generyczna wykonuje więcej odbicia w celu odnalezienia zdarzenia uwzględniającego nazwę zdarzenia. Ponadto kod, aby zarejestrować zdarzenie przy użyciu generycznego, <xref:System.Windows.WeakEventManager%602> jest bardziej pełny niż użycie istniejącej lub niestandardowej <xref:System.Windows.WeakEventManager> .|  
|Utwórz niestandardową klasę słabego Menedżera zdarzeń|Utwórz niestandardową, <xref:System.Windows.WeakEventManager> gdy istniejąca <xref:System.Windows.WeakEventManager> jest niedostępna, i potrzebujesz najlepszej wydajności. Użycie niestandardowego <xref:System.Windows.WeakEventManager> do subskrybowania zdarzenia będzie bardziej wydajne, ale powiąże się to z kosztem napisania większej ilości kodu na początku.|  
|Korzystanie z niesłabego Menedżera zdarzeń innej firmy|Pakiet NuGet ma [kilku słabych menedżerów zdarzeń](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) , a wiele struktur WPF obsługuje również wzorzec (na przykład zobacz [dokumentację biblioteki Prism na temat luźno powiązanej subskrypcji zdarzeń](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/legacy/Communication.md#subscribing-to-events)).|

 W poniższych sekcjach opisano sposób implementacji słabego wzorca zdarzeń.  Na potrzeby tej dyskusji wydarzenie subskrybowane ma następujące cechy.  
  
- Nazwa zdarzenia to `SomeEvent` .  
  
- Zdarzenie jest zgłaszane przez `EventSource` klasę.  
  
- Program obsługi zdarzeń ma typ: `SomeEventEventHandler` (lub `EventHandler<SomeEventEventArgs>` ).  
  
- Zdarzenie przekazuje parametr typu `SomeEventEventArgs` do programów obsługi zdarzeń.  
  
### <a name="using-an-existing-weak-event-manager-class"></a>Używanie istniejącej słabej klasy Menedżera zdarzeń  
  
1. Znajdź istniejący słaby Menedżer zdarzeń.  
  
     Aby zapoznać się z listą słabych menedżerów zdarzeń, które są dołączone do platformy WPF, zobacz Hierarchia dziedziczenia w <xref:System.Windows.WeakEventManager> klasie.  
  
2. Użyj nowego słabego Menedżera zdarzeń zamiast normalnego podłączenie zdarzeń.  
  
     Na przykład jeśli kod używa następującego wzorca do subskrybowania zdarzenia:  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Zmień go na następujący wzorzec:  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     Podobnie, jeśli kod używa następującego wzorca, aby anulować subskrypcję zdarzenia:  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Zmień go na następujący wzorzec:  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a>Korzystanie z ogólnej słabej klasy Menedżera zdarzeń  
  
1. Użyj klasy generycznej <xref:System.Windows.WeakEventManager%602> zamiast normalnej podłączenie zdarzeń.  
  
     W przypadku korzystania <xref:System.Windows.WeakEventManager%602> z programu do rejestrowania detektorów zdarzeń należy podać Źródło zdarzenia i <xref:System.EventArgs> Typ jako parametry typu klasy i wywołania, <xref:System.Windows.WeakEventManager%602.AddHandler%2A> jak pokazano w poniższym kodzie:  
  
    ```csharp  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a>Tworzenie niestandardowej słabej klasy Menedżera zdarzeń  
  
1. Skopiuj następujący szablon klasy do projektu.  
  
     Ta klasa dziedziczy z <xref:System.Windows.WeakEventManager> klasy.  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. Zastąp `SomeEventWeakEventManager` nazwę własną nazwą.  
  
3. Zastąp trzy nazwy opisane wcześniej odpowiednimi nazwami dla zdarzenia. ( `SomeEvent` , `EventSource` i `SomeEventEventArgs` )  
  
4. Ustaw widoczność (Public/Internal/Private) słabej klasy Menedżera zdarzeń w taki sam sposób jak zdarzenie, które zarządza.  
  
5. Użyj nowego słabego Menedżera zdarzeń zamiast normalnego podłączenie zdarzeń.  
  
     Na przykład jeśli kod używa następującego wzorca do subskrybowania zdarzenia:  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Zmień go na następujący wzorzec:  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     Podobnie, jeśli kod używa następującego wzorca, aby anulować subskrypcję zdarzenia:  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     Zmień go na następujący wzorzec:  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [Przegląd Zdarzenia trasowane](routed-events-overview.md)
- [Przegląd powiązań danych](../../../desktop-wpf/data/data-binding-overview.md)
