---
title: "Porady: subskrybowanie i anulowanie subskrypcji zdarzeń (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: deeed6f6b572e04780f0eda1e7e42f1dd6233567
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a>Porady: subskrybowanie i anulowanie subskrypcji zdarzeń (Przewodnik programowania w języku C#)
Subskrybować zdarzenia, które są publikowane przez inną klasę, umożliwia pisanie kodu niestandardowego, który jest wywoływany, gdy zdarzenie jest wywoływane. Na przykład może subskrybować przycisk `click` zdarzeń, aby zwiększyć bezpieczeństwo aplikacji Zrób coś, które są przydatne, gdy użytkownik kliknie przycisk.  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a>Aby subskrybować zdarzenia za pomocą środowiska IDE programu Visual Studio  
  
1.  Jeśli nie widzisz **właściwości** okna w **projekt** wyświetlić, kliknij prawym przyciskiem myszy formularz lub formant, dla którego chcesz utworzyć program obsługi zdarzeń, a następnie wybierz **właściwości**.  
  
2.  Nad **właściwości** okna, kliknij przycisk **zdarzenia** ikony.  
  
3.  Kliknij dwukrotnie zdarzenie, które chcesz utworzyć, na przykład `Load` zdarzeń.  
  
     [!INCLUDE[csprcs](~/includes/csprcs-md.md)]Tworzy metoda obsługi zdarzeń pusty i dodaje go do kodu. Alternatywnie można dodać ręcznie w kodzie **kod** widoku. Na przykład następujące wiersze kodu zadeklarować metoda obsługi zdarzeń, która zostanie wywołana podczas `Form` klasy zgłasza `Load` zdarzeń.  
  
     [!code-csharp[csProgGuideEvents#11](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-subscribe-to-and-unsubscribe-from-events_1.cs)]  
  
     Wiersz kodu, który jest wymagany, aby subskrybować zdarzenia jest automatycznie generowany w `InitializeComponent` metody w pliku Form1.Designer.cs w projekcie. Przypomina to:  
  
    ```  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a>Aby subskrybować zdarzenia programowo  
  
1.  Zdefiniuj metoda obsługi zdarzeń, których Podpis pasuje do podpisu delegata zdarzenia. Na przykład, jeśli zdarzenie jest oparta na <xref:System.EventHandler> typ delegata, poniższy kod przedstawia szkieletu metody:  
  
    ```  
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2.  Użyj operator przypisania dodawania (`+=`) można dołączyć obsługi zdarzenia do zdarzenia. W poniższym przykładzie założono, że obiekt o nazwie `publisher` ma zdarzenia o nazwie `RaiseCustomEvent`. Należy pamiętać, że klasa subskrybenta wymaga odwołania do klasy wydawcy, aby subskrybować jego zdarzeń.  
  
    ```  
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     Należy pamiętać, że składnia poprzedniej nowego w języku C# 2.0. Jest dokładnym odpowiednikiem składni 1.0 C#, w której hermetyzowany delegata musi jawnie utworzone za pomocą `new` — słowo kluczowe:  
  
    ```  
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     Program obsługi zdarzeń można również dodać za pomocą wyrażenia lambda:  
  
    ```  
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
        this.Click += (s,e) => { MessageBox.Show(  
           ((MouseEventArgs)e).Location.ToString());};  
    }  
    ```  
  
     Aby uzyskać więcej informacji, zobacz [porady: użycie Lambda wyrażenia poza LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a>Aby subskrybować zdarzenia za pomocą metody anonimowej  
  
-   Jeśli nie musisz anulować subskrypcję później na zdarzenie, można użyć operator przypisania dodawania (`+=`) można dołączyć do zdarzenia metody anonimowej. W poniższym przykładzie założono, że obiekt o nazwie `publisher` ma zdarzenia o nazwie `RaiseCustomEvent` oraz że `CustomEventArgs` klasa została zdefiniowana również do przenoszenia określonego rodzaju informacje dotyczące specjalnych zdarzenia. Należy pamiętać, że klasa subskrybenta wymaga odwołania do `publisher` Aby subskrybować jego zdarzenia.  
  
    ```  
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     Należy zauważyć, że nie można łatwo anulować zdarzenie użycie funkcji anonimowej jego subskrypcji. Aby anulować subskrypcję, w tym scenariuszu, należy go z powrotem do kodu, w którym subskrybować zdarzenia, metodą anonimową należy przechowywać w zmiennej obiektu delegowanego, a następnie dodaj delegata zdarzenia. Ogólnie rzecz biorąc zaleca się, że nie należy używać funkcji anonimowych Aby subskrybować zdarzenia, jeśli konieczne będzie anulowanie subskrypcji zdarzeń w pewnym momencie nowsze w kodzie. Aby uzyskać więcej informacji na temat funkcji anonimowych zobacz [funkcje anonimowe](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="unsubscribing"></a>Anulowanie  
 Aby zapobiec obsługi zdarzenia jest wywoływane, gdy zdarzenie jest zgłaszane, subskrypcję zdarzenia. Aby zapobiec przecieków zasobów, anulujesz subskrypcję zdarzenia przed usunięcia obiektu subskrybenta. Dopóki subskrypcję zdarzeń, delegat multiemisji źródłową zdarzeń w obiekcie publikowania odwołuje się do delegata, który hermetyzuje abonenta obsługi zdarzeń. Tak długo, jak obiekt publikowania zawiera odwołanie do tego, wyrzucanie elementów bezużytecznych nie spowoduje usunięcia obiektu subskrybenta.  
  
#### <a name="to-unsubscribe-from-an-event"></a>Aby anulować subskrypcję zdarzenia  
  
-   Użyj operator przypisania odejmowania (`-=`) na anulowanie subskrypcji zdarzeń:  
  
    ```  
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     Po wszystkich subskrybentów została anulowana zdarzenia, wystąpienie zdarzenia w klasie wydawcy jest ustawiany na `null`.  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia](../../../csharp/programming-guide/events/index.md)  
 [zdarzenia](../../../csharp/language-reference/keywords/event.md)  
 [Porady: publikowanie zdarzeń zgodnych ze wskazówkami dotyczącymi .NET Framework](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
 [-= — Operator (odwołanie w C#)](../../language-reference/operators/subtraction-assignment-operator.md)  
 [+= — Operator](../../../csharp/language-reference/operators/addition-assignment-operator.md)
