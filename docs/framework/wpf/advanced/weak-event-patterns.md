---
title: Słabe wzorce zdarzeń
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: 039d25fb14ed2d29f21168267611d4f0d7f2d04f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367612"
---
# <a name="weak-event-patterns"></a>Słabe wzorce zdarzeń
W przypadku aplikacji jest możliwe, że programy obsługi, które są dołączone do źródła zdarzeń, nie jest niszczony w połączeniu z obiekt odbiornik, który jest dołączony program obsługi do źródła. Taka sytuacja może prowadzić do przecieków pamięci. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] wprowadzono szablon projektu, który może służyć do rozwiązania tego problemu, przesyłając klasy Menedżera dedykowane dla określonych zdarzeń i implementowania interfejsu na odbiorniki dla tego zdarzenia. Ten wzorzec projektowy jest znany jako *słaby wzorzec zdarzeń*.  
  
## <a name="why-implement-the-weak-event-pattern"></a>Dlaczego warto wdrażać słaby wzorzec zdarzeń?  
 Nasłuchiwanie zdarzeń może prowadzić do przecieków pamięci. Typowych technik w celu nasłuchiwania na zdarzenie jest należy użyć składni specyficzny dla języka, który dołącza obsługę do zdarzenia w źródle. Na przykład w C#, czy składnia jest: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.  
  
 Ta metoda tworzy silne odwołanie ze źródła zdarzeń do odbiornika zdarzeń. Zazwyczaj Dołączanie programu obsługi zdarzeń dla odbiornika powoduje, że odbiornika mieć okresu istnienia obiektu, który ma wpływ okres istnienia obiektu źródłowego (chyba że program obsługi zdarzeń jest jawnie usunięte). Jednak w pewnych okolicznościach może być okres istnienia obiektu nasłuchującego kontrolowany przez inne czynniki, takie jak aktualnie przynależność do drzewa wizualnego w aplikacji, a nie przez okres istnienia źródła. Po każdym okresie istnienia obiektu źródłowego wykracza poza okres istnienia obiektu odbiornika, wzorzec zdarzeń normalne prowadzi do przeciek pamięci: odbiornika jest życiu dłużej, niż planowano.  
  
 Słaby wzorzec zdarzeń zaprojektowano w celu rozwiązania tego problemu przeciek pamięci. Słaby wzorzec zdarzeń można zawsze wtedy, gdy odbiornik musi zarejestrować zdarzenie, ale odbiornik nie jawnie wiedział, kiedy można wyrejestrować. Słaby wzorzec zdarzeń można również zawsze wtedy, gdy okres istnienia obiektu źródła przekracza okres istnienia obiektu przydatne odbiornika. (W tym przypadku *przydatne* jest określany przez użytkownika.) Słaby wzorzec zdarzeń umożliwia odbiornika przeprowadzać rejestrację i otrzymają zdarzenie bez wywierania wpływu na właściwości okresu istnienia obiektu odbiornika w dowolny sposób. W efekcie odwołanie domniemane ze źródła nie określa, czy odbiornik kwalifikują się do wyrzucania elementów bezużytecznych. Odwołanie jest słabe odwołanie, w związku z tym nazewnictwa słaby wzorzec zdarzeń i powiązane [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]. Odbiornik może zostać usunięte zebrane lub w przeciwnym razie zniszczenia obiektu, a źródła można kontynuować bez zachowania noncollectible obsługi odwołań do obiektu teraz niszczone.  
  
## <a name="who-should-implement-the-weak-event-pattern"></a>Kto należy zaimplementować słaby wzorzec zdarzeń?  
 Implementacja wzorca zdarzeń słabych jest interesująca przede wszystkim dla autorów kontroli. Jako autor kontroli odpowiedzialność za stopniu zachowanie i zawierania kontroli nad oraz wpływ, znajdującymi się na aplikacjach, w których zostanie ona wstawiona. W tym kontroli zachowania okresu istnienia obiektu, w szczególności obsługi problem przeciek pamięci opisem.  
  
 Niektóre scenariusze natury nadają się do aplikacji słaby wzorzec zdarzeń. Taki scenariusz jest powiązanie danych. W powiązaniu danych to częsty problem w obiekcie źródłowym w celu całkowicie niezależne od obiektu odbiornika, który jest elementem docelowym powiązania. Wiele aspektów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] już powiązania danych mają słaby wzorzec zdarzeń stosowane w implementacji zdarzenia.  
  
## <a name="how-to-implement-the-weak-event-pattern"></a>Jak zaimplementować słaby wzorzec zdarzeń  
 Istnieją trzy sposoby, aby zaimplementować słaby wzorzec zdarzeń. Poniższa tabela zawiera trzy metody oraz zawiera pewne wskazówki dotyczące kiedy należy używać każdego.  
  
|Podejście|O czasie implementacji|  
|--------------|-----------------------|  
|Użyj istniejącej klasy menedżera zdarzeń słabych|Jeśli zdarzenie, aby subskrybować ma odpowiadające mu <xref:System.Windows.WeakEventManager>, przy użyciu istniejącego menedżera zdarzeń słabych. Listę menedżerów zdarzeń słabych, które są uwzględniane przy użyciu platformy WPF, na ten temat można znaleźć w hierarchii dziedziczenia w <xref:System.Windows.WeakEventManager> klasy. Ponieważ menedżerów zdarzeń słabych uwzględniane są ograniczone, prawdopodobnie musisz wybrać jedną z innych metod.|  
|Używanie klasy menedżera zdarzeń słabych generycznych|Korzystają z ogólnego <xref:System.Windows.WeakEventManager%602> kiedy istniejący <xref:System.Windows.WeakEventManager> nie jest dostępny, chcesz, aby łatwo wdrożyć, a nie są faktycznie zajmuje się wydajność. Ogólny <xref:System.Windows.WeakEventManager%602> jest mniej wydajne niż do istniejącego lub niestandardowego Menedżera zdarzeń słabych. Na przykład klasy generycznej jest więcej odbicia, aby odnaleźć zdarzenie otrzymuje nazwę zdarzenia. Ponadto kod, aby rejestrować zdarzenia za pomocą ogólnego <xref:System.Windows.WeakEventManager%602> jest bardziej pełne niż korzystanie z istniejących lub niestandardowych <xref:System.Windows.WeakEventManager>.|  
|Utwórz klasę Menedżera niestandardowych zdarzeń słabych|Utwórz niestandardową <xref:System.Windows.WeakEventManager> kiedy istniejący <xref:System.Windows.WeakEventManager> nie jest dostępna i uzyskania najlepszej wydajności. Za pomocą niestandardowego <xref:System.Windows.WeakEventManager> do subskrybowania zdarzenia będzie bardziej wydajne, ale wiąże się koszt pisania więcej kodu na początku.|  
|Korzystanie z Menedżera zdarzeń słabych innych firm|NuGet ma [kilka zdarzeń słabych menedżerów](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) i wiele struktur WPF obsługuje również wzorca (na przykład zobacz [firmy pryzmat dokumentację dotyczącą subskrypcji luźno powiązanych zdarzeń](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).|

 Poniżej opisano sposób implementacji słaby wzorzec zdarzeń.  Dla celów tej dyskusji zdarzenia, aby zasubskrybować ma następujące cechy.  
  
-   Nazwa zdarzenia jest `SomeEvent`.  
  
-   Zdarzenie jest wywoływane przez `EventSource` klasy.  
  
-   Program obsługi zdarzeń ma typ: `SomeEventEventHandler` (lub `EventHandler<SomeEventEventArgs>`).  
  
-   Zdarzenie przekazuje parametr typu `SomeEventEventArgs` do obsługi zdarzeń.  
  
### <a name="using-an-existing-weak-event-manager-class"></a>Przy użyciu istniejącej klasy Menedżer zdarzeń słabych  
  
1.  Znajdowanie istniejącego zdarzenia słabe menedżera.  
  
     Listę menedżerów zdarzeń słabych, które są uwzględniane przy użyciu platformy WPF, na ten temat można znaleźć w hierarchii dziedziczenia w <xref:System.Windows.WeakEventManager> klasy.  
  
2.  Użyj nowego menedżera zdarzeń słabych zamiast zaczep zdarzenia normalny.  
  
     Na przykład, jeśli kod używa następującego wzorca do subskrybowania zdarzenia:  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Zmień go na następujący wzór:  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     Podobnie jeśli kod używa następującego wzorca, aby anulować subskrypcję zdarzenia:  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     Zmień go na następujący wzór:  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a>Za pomocą klasy ogólnej słabe Menedżer zdarzeń  
  
1.  Używać ogólnych <xref:System.Windows.WeakEventManager%602> klasy zamiast zaczep zdarzenia normalny.  
  
     Kiedy używać <xref:System.Windows.WeakEventManager%602> rejestrowanie detektorów zdarzeń, podaj źródło zdarzenia i <xref:System.EventArgs> typu jako parametrów typu klasy i wywołania <xref:System.Windows.WeakEventManager%602.AddHandler%2A> jak pokazano w poniższym kodzie:  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a>Tworzenie niestandardowych słabe klasy Menedżer zdarzeń  
  
1.  Skopiuj następujący szablon klasy do projektu.  
  
     Ta klasa dziedziczy <xref:System.Windows.WeakEventManager> klasy.  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2.  Zastąp `SomeEventWeakEventManager` nazwa własną nazwą.  
  
3.  Zastąp te trzy nazwy opisane wcześniej przy użyciu odpowiadających im nazw do zdarzenia. (`SomeEvent`, `EventSource`, i `SomeEventEventArgs`)  
  
4.  Ustaw widoczność (publiczne / wewnętrzne / prywatne) klasy menedżera zdarzeń słabych na taką samą widoczność jak zdarzenia, którymi zarządza.  
  
5.  Użyj nowego menedżera zdarzeń słabych zamiast zaczep zdarzenia normalny.  
  
     Na przykład, jeśli kod używa następującego wzorca do subskrybowania zdarzenia:  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Zmień go na następujący wzór:  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     Podobnie jeśli kod używa następującego wzorca, aby anulować subskrypcję zdarzenia:  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     Zmień go na następujący wzór:  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [Przegląd zdarzeń trasowanych](routed-events-overview.md)
- [Powiązanie danych — omówienie](../data/data-binding-overview.md)
