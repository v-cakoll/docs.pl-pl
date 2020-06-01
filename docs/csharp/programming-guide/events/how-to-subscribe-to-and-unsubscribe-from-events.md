---
title: Jak subskrybować i anulować subskrypcję zdarzeń — Przewodnik programowania w języku C#
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: d917ea097cf9253a65c1907efdca71a640df9497
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240671"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a>Subskrybowanie i anulowanie subskrypcji zdarzeń (Przewodnik programowania w języku C#)
Zasubskrybujesz zdarzenie, które jest publikowane przez inną klasę, gdy chcesz napisać niestandardowy kod, który jest wywoływany, gdy zdarzenie jest zgłaszane. Na przykład można subskrybować zdarzenie przycisku, `click` Aby aplikacja była przydatna, gdy użytkownik kliknie przycisk.  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a>Aby subskrybować zdarzenia za pomocą środowiska IDE programu Visual Studio  
  
1. Jeśli nie widzisz okna **Właściwości** , w widoku **projektu** kliknij prawym przyciskiem myszy formularz lub kontrolkę, dla której chcesz utworzyć procedurę obsługi zdarzeń, a następnie wybierz polecenie **Właściwości**.  
  
2. W górnej części okna **Właściwości** kliknij ikonę **zdarzenia** .  
  
3. Kliknij dwukrotnie zdarzenie, które chcesz utworzyć, na przykład `Load` zdarzenie.  
  
     Visual C# tworzy pustą metodę obsługi zdarzeń i dodaje ją do kodu. Alternatywnie możesz dodać kod ręcznie w widoku **kodu** . Na przykład następujące wiersze kodu deklarują metodę procedury obsługi zdarzeń, która zostanie wywołana, gdy `Form` Klasa zgłasza `Load` zdarzenie.  
  
     [!code-csharp[csProgGuideEvents#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#11)]  
  
     Wiersz kodu, który jest wymagany do subskrybowania zdarzenia, jest również generowany automatycznie w `InitializeComponent` metodzie w pliku Form1.Designer.cs w projekcie. Przypomina to:  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a>Aby programowo subskrybować zdarzenia  
  
1. Zdefiniuj metodę procedury obsługi zdarzeń, której sygnatura pasuje do sygnatury delegata zdarzenia. Na przykład, jeśli zdarzenie jest oparte na <xref:System.EventHandler> typie delegata, poniższy kod reprezentuje element zastępczy metody:  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2. Użyj operatora przypisania dodawania ( `+=` ), aby dołączyć procedurę obsługi zdarzeń do zdarzenia. W poniższym przykładzie Załóżmy, że obiekt o nazwie `publisher` ma zdarzenie o nazwie `RaiseCustomEvent` . Należy zauważyć, że Klasa subskrybenta wymaga odwołania do klasy wydawcy w celu subskrybowania jego zdarzeń.  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     Należy zauważyć, że poprzednia składnia jest nowa w języku C# 2,0. Jest to dokładnie równoważne składni języka C# 1,0, w której delegata hermetyzowania musi być jawnie utworzona przy użyciu `new` słowa kluczowego:  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     Można również użyć [wyrażenia lambda](../statements-expressions-operators/lambda-expressions.md) do określenia programu obsługi zdarzeń:
  
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
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a>Aby subskrybować zdarzenia za pomocą metody anonimowej  
  
- Jeśli nie musisz anulować subskrybowania zdarzenia później, możesz użyć operatora przypisania dodawania ( `+=` ) w celu dołączenia anonimowej metody do zdarzenia. W poniższym przykładzie Załóżmy, że obiekt o nazwie `publisher` ma zdarzenie o nazwie `RaiseCustomEvent` i że `CustomEventArgs` Klasa została również zdefiniowana w taki sposób, aby wykonywała wyspecjalizowane informacje o zdarzeniu. Należy zauważyć, że Klasa subskrybenta wymaga odwołania do, aby `publisher` subskrybować jego zdarzenia.  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     Należy pamiętać, że nie można łatwo anulować subskrypcji zdarzenia, jeśli użyto anonimowej funkcji do subskrybowania. Aby anulować subskrypcję w tym scenariuszu, należy wrócić do kodu, w którym subskrybujesz zdarzenie, zapisać metodę anonimową w zmiennej delegata, a następnie dodać delegata do zdarzenia. Ogólnie rzecz biorąc, firma Microsoft zaleca, aby nie używać funkcji anonimowych do subskrybowania zdarzeń, jeśli będzie konieczne anulowanie subskrypcji zdarzenia w pewnym momencie w kodzie. Aby uzyskać więcej informacji na temat funkcji anonimowych, zobacz [funkcje anonimowe](../statements-expressions-operators/anonymous-functions.md).  
  
## <a name="unsubscribing"></a>Anulowanie subskrypcji  
 Aby uniemożliwić wywoływanie programu obsługi zdarzeń po podniesieniu zdarzenia, Anuluj subskrypcję zdarzenia. Aby zapobiec przeciekom zasobów, należy anulować subskrypcję zdarzeń przed usunięciem obiektu subskrybenta. Dopóki nie subskrybujesz zdarzenia, delegat multiemisji, który opiera się na zdarzeniu w obiekcie do publikowania, ma odwołanie do delegata, który hermetyzuje procedurę obsługi zdarzeń subskrybenta. Tak długo, jak obiekt publikacji przechowuje to odwołanie, wyrzucanie elementów bezużytecznych nie usunie obiektu subskrybenta.  
  
#### <a name="to-unsubscribe-from-an-event"></a>Aby anulować subskrypcję zdarzenia  
  
- Użyj operatora przypisywania odejmowania ( `-=` ), aby anulować subskrypcję zdarzenia:  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     Gdy Wszyscy subskrybenci nie subskrybują zdarzenia, wystąpienie zdarzenia w klasie wydawcy jest ustawione na `null` .  
  
## <a name="see-also"></a>Zobacz też

- [Zdarzenia](./index.md)
- [wydarzen](../../language-reference/keywords/event.md)
- [Jak opublikować zdarzenia zgodne z zaleceniami dotyczącymi platformy .NET](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [Operatory-and-=](../../language-reference/operators/subtraction-operator.md)
- [Operatory + i + =](../../language-reference/operators/addition-operator.md)
