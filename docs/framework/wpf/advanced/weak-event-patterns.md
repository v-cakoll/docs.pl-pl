---
title: "Słabe wzorce zdarzeń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f024ae77740c596d8646b10a036428e2342d084
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2017
---
# <a name="weak-event-patterns"></a>Słabe wzorce zdarzeń
W aplikacjach istnieje możliwość, że programy obsługi, które są dołączone do źródła zdarzeń nie zostaną usunięte w połączeniu z obiektu odbiornika, który dołączyć program obsługi do źródła. Taka sytuacja może prowadzić do przecieki pamięci. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]wprowadza wzorzec projektowania, który może służyć do rozwiązania tego problemu, zapewniając klasy Menedżera dedykowane dla konkretnego zdarzenia i implementowanie interfejsu na odbiorników dla tego zdarzenia. Ten wzorzec projektowy nosi nazwę *wzorzec słabe zdarzeń*.  
  
## <a name="why-implement-the-weak-event-pattern"></a>Dlaczego implementują wzorzec słabe zdarzenia?  
 Nasłuchiwanie zdarzeń może prowadzić do przecieki pamięci. Typowe techniki do nasłuchiwania zdarzeń jest należy użyć składni specyficzny dla języka, łączący program obsługi zdarzeń w źródle. Na przykład w [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)], że składnia jest: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.  
  
 Ta metoda tworzy silne odwołanie ze źródła zdarzeń dla odbiornika zdarzeń. Zwykle dołączanie program obsługi zdarzeń dla odbiornika powoduje, że odbiornika mają okres istnienia obiektu, który ma wpływ okres istnienia obiektu źródłowego (chyba że obsługi zdarzeń jest jawnie usunięte). Jednak w pewnych okolicznościach może być okres istnienia obiektu nasłuchującego kontrolowany przez inne czynniki, takie jak obecnie przynależność do drzewa wizualnego aplikacji, a nie przez okres istnienia źródła. Zawsze, gdy okres istnienia obiektu źródłowego wykracza poza okres istnienia obiektu odbiornika, ze wzorcem normalnego zdarzeń prowadzi do przeciek pamięci: odbiornika jest utrzymywane dłużej niż zamierzony.  
  
 Wzorzec słabe zdarzeń zaprojektowano w celu rozwiązania tego problemu przeciek pamięci. Wzorzec słabe zdarzeń można zawsze, gdy odbiornik musi zarejestrować zdarzenie, ale odbiornika nie może jawnie określić kiedy wyrejestrować. Wzorzec słabe zdarzenia można również zawsze, gdy okres istnienia obiektu źródła przekracza okres istnienia obiektu przydatne odbiornika. (W tym przypadku *przydatne* jest określany przez użytkownika.) Wzorzec słabe zdarzeń umożliwia odbiornika, aby zarejestrować i odbierać zdarzenia bez wpływu na właściwości okres istnienia obiektu nasłuchującego w dowolny sposób. W efekcie domniemanych odwołania ze źródła nie określa, czy odbiornik kwalifikuje się do pamięci. Odwołanie jest słabe odwołanie, w związku z tym nazewnictwa wzorzec słabe zdarzeń i powiązanych [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]. Odbiornik można odzyskiwanie zebrane lub w przeciwnym razie zniszczone i źródła można kontynuować bez zachowania noncollectible obsługi odwołania do obiektu teraz niszczone.  
  
## <a name="who-should-implement-the-weak-event-pattern"></a>Kto powinien implementować wzorzec słabe zdarzenia?  
 Implementacja wzorca słabe zdarzeń jest ciekawe głównie dla autorów formantu. Jako autor kontroli jesteś przede wszystkim odpowiedzialne za działanie i zawierania formantu i wpływu, jaki ma w przypadku aplikacji, w których zostanie on włożony. W tym zachowanie okresu istnienia obiektu kontrolki, w szczególności obsługi problem przeciek pamięci opisem.  
  
 Niektóre scenariusze z założenia nadają się do aplikacji wzorzec słabe zdarzeń. Taki scenariusz jest powiązanie danych. W powiązaniu danych jest typowe dla obiekt źródłowy, być całkowicie niezależna od obiektu odbiornika, który jest elementem docelowym powiązania. Wiele aspektów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] już powiązania danych mają wzorzec słabe zdarzeń w implementowania zdarzenia.  
  
## <a name="how-to-implement-the-weak-event-pattern"></a>Jak zaimplementować wzorzec słabe zdarzeń  
 Istnieją trzy sposoby implementacji klienta wzorca słabe zdarzeń. Poniższa tabela zawiera listę trzech metod i zawiera pewne wskazówki dotyczące kiedy należy używać każdego.  
  
|Podejście|Kiedy należy zaimplementować|  
|--------------|-----------------------|  
|Użyj istniejącej klasy Menedżera słabe zdarzeń|Jeśli chcesz subskrybować zdarzenie ma odpowiadające mu <xref:System.Windows.WeakEventManager>, użyj istniejącego menedżera słabe zdarzeń. Aby uzyskać listę menedżerów słabe zdarzeń, które są dołączone do WPF, zobacz w hierarchii dziedziczenia <xref:System.Windows.WeakEventManager> klasy. Należy jednak pamiętać, że są względnie mało menedżerów słabe zdarzeń dołączonych WPF, dzięki czemu prawdopodobnie trzeba wybrać jeden z innych metod.|  
|Używanie klasy Menedżera ogólnego słabe zdarzeń|Użyj ogólnego <xref:System.Windows.WeakEventManager%602> kiedy istniejący <xref:System.Windows.WeakEventManager> jest nie jest dostępny, chcesz w prosty sposób wdrożenia, które nie mają danych o wydajności. Ogólnego <xref:System.Windows.WeakEventManager%602> jest mniej wydajne niż Menedżer zdarzeń słabe istniejących lub niestandardowy. Na przykład klasa ogólna ma więcej odbicia do odnajdywania zdarzenie otrzymuje nazwę zdarzenia. Ponadto kod, aby zarejestrować zdarzenia przy użyciu ogólnej <xref:System.Windows.WeakEventManager%602> jest bardziej pełne niż przy użyciu istniejącej lub niestandardowych <xref:System.Windows.WeakEventManager>.|  
|Utwórz klasę Menedżera słabe zdarzenie niestandardowe|Utworzenie niestandardowego <xref:System.Windows.WeakEventManager> kiedy istniejący <xref:System.Windows.WeakEventManager> nie jest dostępna i ma najlepszą wydajność. Przy użyciu niestandardowego <xref:System.Windows.WeakEventManager> Aby subskrybować zdarzenia będą bardziej wydajne, ale ponoszenia kosztów więcej kod na początku.|  
  
 W poniższych sekcjach opisano sposobu implementacji wzorca słabe zdarzeń.  Dla celów tej dyskusji Aby subskrybować zdarzenia o następujących cechach.  
  
-   Nazwa zdarzenia `SomeEvent`.  
  
-   Zdarzenie jest zgłaszane przez `EventSource` klasy.  
  
-   Program obsługi zdarzeń ma typ: `SomeEventEventHandler` (lub `EventHandler<SomeEventEventArgs>`).  
  
-   Parametr typu przekazuje zdarzenia `SomeEventEventArgs` do obsługi zdarzeń.  
  
### <a name="using-an-existing-weak-event-manager-class"></a>Przy użyciu istniejącej klasy słabe Menedżer zdarzeń  
  
1.  Znajdź zdarzenia słabe istniejącego menedżera.  
  
     Aby uzyskać listę menedżerów słabe zdarzeń, które są dołączone do WPF, zobacz w hierarchii dziedziczenia <xref:System.Windows.WeakEventManager> klasy.  
  
2.  Użyj nowego Menedżera słabe zdarzeń zamiast podłączenie zdarzenia normalnego.  
  
     Jeśli na przykład następujący wzór używa Twój kod, aby subskrybować zdarzenia:  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Zmień go na następujący wzór:  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     Podobnie jeśli kod używa następującego wzorca do anulowania subskrypcji na zdarzenie:  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     Zmień go na następujący wzór:  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a>Przy użyciu klasy ogólnej słabe Menedżer zdarzeń  
  
1.  Użyj ogólnych <xref:System.Windows.WeakEventManager%602> klasy zamiast podłączenie zdarzenia normalnego.  
  
     Jeśli używasz <xref:System.Windows.WeakEventManager%602> zarejestrować odbiorników zdarzeń, podać źródło zdarzenia i <xref:System.EventArgs> typu jako parametrów typu klasy i wywołanie <xref:System.Windows.WeakEventManager%602.AddHandler%2A> zgodnie z poniższym kodem:  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a>Tworzenie niestandardowych słabe klasy Menedżer zdarzeń  
  
1.  Skopiuj następujący szablon klasy do projektu.  
  
     Ta klasa dziedziczy <xref:System.Windows.WeakEventManager> klasy.  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2.  Zastąp `SomeEventWeakEventManager` nazwa z własnej nazwy.  
  
3.  Zamień nazwy trzech opisanych wcześniej odpowiadają nazwom wydarzenia. (`SomeEvent`, `EventSource`, i `SomeEventEventArgs`)  
  
4.  Ustawić widoczność (publiczne / wewnętrzne / prywatnej) klasy słabe zdarzeń Menedżera taką samą widoczność jak zdarzenia, którymi zarządza.  
  
5.  Użyj nowego Menedżera słabe zdarzeń zamiast podłączenie zdarzenia normalnego.  
  
     Jeśli na przykład następujący wzór używa Twój kod, aby subskrybować zdarzenia:  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Zmień go na następujący wzór:  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     Podobnie jeśli kod używa następującego wzorca do anulowania subskrypcji na zdarzenie:  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     Zmień go na następujący wzór:  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.WeakEventManager>  
 <xref:System.Windows.IWeakEventListener>  
 [Przegląd zdarzeń trasowanych](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)
