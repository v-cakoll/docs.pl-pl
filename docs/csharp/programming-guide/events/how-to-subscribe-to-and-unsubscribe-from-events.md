---
title: Jak subskrybować i anulować subskrypcję wydarzeń - Przewodnik programowania języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: 0a9e2cc64da56c376445efce32e8da36ba9b6cdc
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738233"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a>Jak subskrybować i anulować subskrypcję wydarzeń (Przewodnik programowania języka C#)
Subskrybujesz zdarzenie, które jest publikowane przez inną klasę, gdy chcesz napisać kod niestandardowy, który jest wywoływany, gdy to zdarzenie jest wywoływane. Na przykład można subskrybować `click` zdarzenie przycisku, aby aplikacja zrobić coś przydatne, gdy użytkownik kliknie przycisk.  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a>Aby subskrybować zdarzenia przy użyciu środowiska IDE programu Visual Studio  
  
1. Jeśli nie widać okna **Właściwości,** w widoku **Projekt** kliknij prawym przyciskiem myszy formularz lub formant, dla którego chcesz utworzyć program obsługi zdarzeń, a następnie wybierz polecenie **Właściwości**.  
  
2. Na górze okna **Właściwości** kliknij ikonę **Zdarzenia.**  
  
3. Kliknij dwukrotnie zdarzenie, które chcesz utworzyć, `Load` na przykład zdarzenie.  
  
     Visual C# tworzy metodę obsługi pustych zdarzeń i dodaje go do kodu. Alternatywnie można dodać kod ręcznie w widoku **kod.** Na przykład następujące wiersze kodu zadeklarować metodę obsługi zdarzeń, która zostanie wywołana, gdy `Form` klasa wywołuje `Load` zdarzenie.  
  
     [!code-csharp[csProgGuideEvents#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#11)]  
  
     Wiersz kodu, który jest wymagany do subskrybowania zdarzenia jest `InitializeComponent` również automatycznie generowany w metodzie w pliku Form1.Designer.cs w projekcie. Przypomina to:  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a>Aby zasubskrybować wydarzenia programowo  
  
1. Zdefiniuj metodę obsługi zdarzeń, której podpis pasuje do podpisu pełnomocnika dla zdarzenia. Na przykład jeśli zdarzenie jest <xref:System.EventHandler> oparte na typ delegata, następujący kod reprezentuje skrót metody:  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2. Operator przypisania dodawania (`+=`), aby dołączyć program obsługi zdarzeń do zdarzenia. W poniższym przykładzie załóżmy, że obiekt o nazwie `publisher` ma zdarzenie o nazwie `RaiseCustomEvent`. Należy zauważyć, że klasa subskrybenta wymaga odwołania do klasy wydawcy, aby subskrybować jego zdarzenia.  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     Należy zauważyć, że poprzednia składnia jest nowa w języku C# 2.0. Jest dokładnie odpowiednikiem składni C# 1.0, w której delegat hermetyzacji musi być `new` jawnie utworzony przy użyciu słowa kluczowego:  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     Można również użyć [wyrażenia lambda,](../statements-expressions-operators/lambda-expressions.md) aby określić program obsługi zdarzeń:
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        this.Click += (s,e) =>
            {
                MessageBox.Show(((MouseEventArgs)e).Location.ToString());
            };
    }  
    ```  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a>Aby subskrybować zdarzenia przy użyciu metody anonimowej  
  
- Jeśli nie będziesz musiał później anulować subskrypcji zdarzenia, możesz użyć operatora przypisania dodawania (`+=`) do dołączenia do zdarzenia metody anonimowej. W poniższym przykładzie załóżmy, że obiekt o nazwie `publisher` ma zdarzenie o nazwie `RaiseCustomEvent` i że `CustomEventArgs` klasa została również zdefiniowana do przenoszenia pewnego rodzaju informacji o zdarzeniach specjalistycznych. Należy zauważyć, że klasa subskrybenta `publisher` wymaga odwołania do w celu subskrybowania jego zdarzeń.  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     Ważne jest, aby zauważyć, że nie można łatwo zrezygnować z subskrypcji zdarzenia, jeśli używasz funkcji anonimowej, aby go subskrybować. Aby anulować subskrypcję w tym scenariuszu, należy wrócić do kodu, w którym subskrybujesz zdarzenie, przechowywać metodę anonimową w zmiennej delegata, a następnie dodać pełnomocnika do zdarzenia. Ogólnie rzecz biorąc zaleca się, aby nie używać funkcji anonimowych do subskrybowania zdarzeń, jeśli będziesz musiał zrezygnować z wydarzenia w późniejszym momencie kodu. Aby uzyskać więcej informacji na temat funkcji anonimowych, zobacz [Funkcje anonimowe](../statements-expressions-operators/anonymous-functions.md).  
  
## <a name="unsubscribing"></a>Anulowanie subskrypcji  
 Aby zapobiec wywoływaniu programu obsługi zdarzeń, gdy zdarzenie jest wywoływane, wypisuj się z tego zdarzenia. Aby zapobiec wyciekom zasobów, należy anulować subskrypcję zdarzeń przed usunięciem obiektu subskrybenta. Dopóki nie anulusz subskrypcję zdarzenia, pełnomocnik multiemisji, który stanowi podstawę zdarzenia w obiekcie publikowania, ma odwołanie do pełnomocnika, który hermetyzuje program obsługi zdarzeń subskrybenta. Tak długo, jak obiekt publikowania posiada tego odwołania, wyrzucania elementów bezużytecznych nie będzie usuwać obiektu subskrybenta.  
  
#### <a name="to-unsubscribe-from-an-event"></a>Aby anulować subskrypcję wydarzenia  
  
- Użyj operatora przypisania odejmowania (`-=`) , aby anulować subskrypcję zdarzenia:  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     Gdy wszyscy subskrybenci mają anulować subskrypcję zdarzenia, wystąpienie zdarzenia `null`w klasie wydawcy jest ustawione na .  
  
## <a name="see-also"></a>Zobacz też

- [Zdarzenia](./index.md)
- [Zdarzenie](../../language-reference/keywords/event.md)
- [Publikowanie zdarzeń zgodnych ze wskazówkami dotyczącymi .NET Framework](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [- i -= operatorzy](../../language-reference/operators/subtraction-operator.md)
- [+ i += operatorzy](../../language-reference/operators/addition-operator.md)
