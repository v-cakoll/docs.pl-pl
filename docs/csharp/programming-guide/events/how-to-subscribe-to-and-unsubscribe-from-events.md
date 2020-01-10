---
title: Jak subskrybować i anulować subskrypcję zdarzeń — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: 3df357cb15f7f77cefbf360dd9615ce246afe2ea
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705330"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a>Subskrybowanie i anulowanie subskrypcji zdarzeń (C# Przewodnik programowania)
Zasubskrybujesz zdarzenie, które jest publikowane przez inną klasę, gdy chcesz napisać niestandardowy kod, który jest wywoływany, gdy zdarzenie jest zgłaszane. Na przykład możesz subskrybować zdarzenie `click` przycisku, aby aplikacja była przydatna, gdy użytkownik kliknie przycisk.  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a>Aby subskrybować zdarzenia za pomocą środowiska IDE programu Visual Studio  
  
1. Jeśli nie widzisz okna **Właściwości** , w widoku **projektu** kliknij prawym przyciskiem myszy formularz lub kontrolkę, dla której chcesz utworzyć procedurę obsługi zdarzeń, a następnie wybierz polecenie **Właściwości**.  
  
2. W górnej części okna **Właściwości** kliknij ikonę **zdarzenia** .  
  
3. Kliknij dwukrotnie zdarzenie, które chcesz utworzyć, na przykład zdarzenie `Load`.  
  
     Wizualizacja C# tworzy pustą metodę obsługi zdarzeń i dodaje ją do kodu. Alternatywnie możesz dodać kod ręcznie w widoku **kodu** . Na przykład następujące wiersze kodu deklarują metodę procedury obsługi zdarzeń, która zostanie wywołana, gdy Klasa `Form` zgłasza zdarzenie `Load`.  
  
     [!code-csharp[csProgGuideEvents#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#11)]  
  
     Wiersz kodu, który jest wymagany do subskrybowania zdarzenia jest również automatycznie generowany w metodzie `InitializeComponent` w pliku Form1.Designer.cs w projekcie. Przypomina to:  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a>Aby programowo subskrybować zdarzenia  
  
1. Zdefiniuj metodę procedury obsługi zdarzeń, której sygnatura pasuje do sygnatury delegata zdarzenia. Na przykład, jeśli zdarzenie jest oparte na typie delegata <xref:System.EventHandler>, poniższy kod reprezentuje element zastępczy metody:  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2. Użyj operatora przypisania dodawania (`+=`), aby dołączyć procedurę obsługi zdarzeń do zdarzenia. W poniższym przykładzie Załóżmy, że obiekt o nazwie `publisher` ma zdarzenie o nazwie `RaiseCustomEvent`. Należy zauważyć, że Klasa subskrybenta wymaga odwołania do klasy wydawcy w celu subskrybowania jego zdarzeń.  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     Należy pamiętać, że poprzednia składnia C# jest nowa w 2,0. Jest to dokładnie równoważne składni C# 1,0, w której delegata hermetyzowania musi być jawnie utworzona za pomocą słowa kluczowego `new`:  
  
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
  
- Jeśli nie musisz anulować subskrybowania zdarzenia później, możesz użyć operatora przypisania dodawania (`+=`) do dołączenia anonimowej metody do zdarzenia. W poniższym przykładzie Załóżmy, że obiekt o nazwie `publisher` ma zdarzenie o nazwie `RaiseCustomEvent` i że Klasa `CustomEventArgs` została również zdefiniowana do przeprowadzenia pewnego rodzaju specjalistycznych informacji o zdarzeniu. Należy zauważyć, że Klasa subskrybenta wymaga odwołania do `publisher`, aby subskrybować jego zdarzenia.  
  
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
  
- Użyj operatora przypisywania odejmowania (`-=`), aby anulować subskrypcję zdarzenia:  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     Gdy Wszyscy subskrybenci nie subskrybują zdarzenia, wystąpienie zdarzenia w klasie wydawcy jest ustawione na `null`.  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia](./index.md)
- [event](../../language-reference/keywords/event.md)
- [Jak opublikować zdarzenia zgodne z wytycznymi .NET Framework](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [Operatory-and-=](../../language-reference/operators/subtraction-operator.md)
- [Operatory + i + =](../../language-reference/operators/addition-operator.md)
