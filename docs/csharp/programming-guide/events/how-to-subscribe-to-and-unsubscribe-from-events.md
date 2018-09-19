---
title: 'Porady: subskrybowanie i anulowanie subskrypcji zdarzeń (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: e27473ca34f634f4a3125a2e87e6d0ef918a6f9d
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "45999143"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a>Porady: subskrybowanie i anulowanie subskrypcji zdarzeń (Przewodnik programowania w języku C#)
Subskrybowanie zdarzenia, które jest opublikowane przez inną klasę napisać kod niestandardowy, który jest wywoływana, gdy zdarzenie jest zgłaszane. Na przykład może subskrybować przycisku `click` zdarzeń, aby zapewnić aplikacji zrobić coś, co jest przydatne, gdy użytkownik kliknie przycisk.  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a>Aby subskrybować zdarzenia przy użyciu programu Visual Studio IDE  
  
1.  Jeśli nie widzisz **właściwości** okna w **projektowania** wyświetlić, kliknij prawym przyciskiem myszy formularza lub kontrolki, dla której chcesz utworzyć program obsługi zdarzeń, a następnie wybierz pozycję **właściwości**.  
  
2.  W górnej części **właściwości** okna, kliknij przycisk **zdarzenia** ikony.  
  
3.  Kliknij dwukrotnie zdarzenie, które chcesz utworzyć, na przykład `Load` zdarzeń.  
  
     Visual C# tworzy metodę programu obsługi zdarzeń pusty i dodaje go do kodu. Alternatywnie można dodać kod ręcznie w **kodu** widoku. Na przykład następujące wiersze kodu Zadeklaruj metodę programu obsługi zdarzeń, która zostanie wywołana kiedy `Form` klasy wywołuje `Load` zdarzeń.  
  
     [!code-csharp[csProgGuideEvents#11](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-subscribe-to-and-unsubscribe-from-events_1.cs)]  
  
     Wiersz kodu, który jest wymagany do subskrybowania zdarzenia jest automatycznie generowany w `InitializeComponent` metody w pliku Form1.Designer.cs w projekcie. Przypomina to:  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a>Aby subskrybować zdarzenia programowe  
  
1.  Zdefiniuj metodę programu obsługi zdarzeń, którego podpis odpowiadają podpisowi delegata zdarzenia. Na przykład, jeśli zdarzenie jest oparty na <xref:System.EventHandler> typ delegata, poniższy kod przedstawia szkieletu metody:  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2.  Użyj operator przypisania dodawania (`+=`) do dołączenia programu obsługi zdarzeń do zdarzenia. W poniższym przykładzie przyjęto założenie, że obiekt o nazwie `publisher` posiada zdarzenie o nazwie `RaiseCustomEvent`. Należy pamiętać, że klasy subskrybenta wymaga odwołania do klasy wydawcy Aby subskrybować ze zdarzeniami.  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     Należy pamiętać, że składnia poprzednich jest nowego w języku C# w wersji 2.0. Jest to równoważne dokładnie składni języka C# 1.0, w którym hermetyzowany delegata należy jawnie utworzyć przy użyciu `new` — słowo kluczowe:  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     Program obsługi zdarzeń mogą być również dodawane za pomocą wyrażenia lambda:  
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
        this.Click += (s,e) => { MessageBox.Show(  
           ((MouseEventArgs)e).Location.ToString());};  
    }  
    ```  
  
     Aby uzyskać więcej informacji, zobacz [porady: użycie Lambda wyrażenia poza LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a>Aby subskrybować zdarzenia przy użyciu metody anonimowej  
  
-   Jeśli nie trzeba będzie później anulować subskrypcję zdarzenia, można użyć operator przypisania dodawania (`+=`) można dołączyć metodę anonimową na zdarzenie. W poniższym przykładzie przyjęto założenie, że obiekt o nazwie `publisher` posiada zdarzenie o nazwie `RaiseCustomEvent` i `CustomEventArgs` klasy została zdefiniowana również przeprowadzenie pewnego rodzaju informacji o zdarzeniach specjalne. Należy pamiętać, że klasa subskrybenta wymaga odwołania do `publisher` Aby subskrybować ze zdarzeniami.  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     Należy zauważyć, że nie można łatwo anulować zdarzenie Jeśli funkcja anonimowa jest używany do subskrybowania. Aby anulować subskrypcję, w tym scenariuszu, należy przejść do kodu, gdzie możesz subskrybować zdarzenie, Zapisz metody anonimowej w zmiennej delegata, a następnie dodaj delegata zdarzenia. Ogólnie rzecz biorąc zaleca się, że nie należy używać funkcji anonimowych do subskrybowania zdarzenia, jeśli będzie konieczne anulowanie subskrypcji zdarzeń w pewnym momencie później w kodzie. Aby uzyskać więcej informacji na temat funkcji anonimowych zobacz [funkcjami anonimowymi](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="unsubscribing"></a>Anulowanie subskrypcji  
 Aby zapobiec sytuacji, w której obsługi zdarzenia są wywoływane, gdy zdarzenie jest wywoływane, Anuluj subskrypcję zdarzenia. Aby zapobiec przeciekom zasobów, anulujesz subskrypcję zdarzeń przed usunięcia obiektu subskrybenta. Dopóki nie można anulować subskrypcję zdarzenia, delegatów multiemisji, źródłową zdarzeń w obiekcie publikowania odwołuje się do delegata, który hermetyzuje programu obsługi zdarzeń subskrybenta. Tak długo, jak obiekt publikowania zawiera odwołanie do tego, wyrzucanie elementów bezużytecznych nie spowoduje usunięcia obiektu subskrybenta.  
  
#### <a name="to-unsubscribe-from-an-event"></a>Aby anulować subskrypcję zdarzenia  
  
-   Użyj operator przypisania odejmowania (`-=`), aby anulować subskrypcję zdarzenia:  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     Gdy wszyscy subskrybenci została anulowana zdarzenie, wystąpienie zdarzenia w klasie wydawca jest ustawiona na `null`.  
  
## <a name="see-also"></a>Zobacz też

- [Zdarzenia](../../../csharp/programming-guide/events/index.md)  
- [event](../../../csharp/language-reference/keywords/event.md)  
- [Instrukcje: publikowanie zdarzeń zgodnych ze wskazówkami dotyczącymi platformy .NET Framework](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
- [-= — Operator (odwołanie w C#)](../../language-reference/operators/subtraction-assignment-operator.md)  
- [+=, operator](../../../csharp/language-reference/operators/addition-assignment-operator.md)