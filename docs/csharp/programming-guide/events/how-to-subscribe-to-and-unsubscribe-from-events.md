---
title: Jak subskrybować i wypisać się ze zdarzeń - Przewodnik po programowaniu C#
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: 3df357cb15f7f77cefbf360dd9615ce246afe2ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705330"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a>Jak subskrybować i anulować subskrypcję zdarzeń (C# Programming Guide)
Subskrybujesz zdarzenie, które jest publikowane przez inną klasę, gdy chcesz napisać kod niestandardowy, który jest wywoływany, gdy to zdarzenie jest wywoływane. Na przykład można zapisać się do `click` zdarzenia przycisku w celu aplikacji zrobić coś pożytecznego, gdy użytkownik kliknie przycisk.  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a>Aby subskrybować zdarzenia przy użyciu ide programu Visual Studio  
  
1. Jeśli nie widzisz okna **Właściwości,** w **widoku projektowym** kliknij prawym przyciskiem myszy formularz lub formant, dla którego chcesz utworzyć program obsługi zdarzeń, a następnie wybierz pozycję **Właściwości**.  
  
2. Na górze okna **Właściwości** kliknij ikonę **Zdarzenia.**  
  
3. Kliknij dwukrotnie zdarzenie, które chcesz utworzyć, `Load` na przykład zdarzenie.  
  
     Visual C# tworzy metodę obsługi zdarzeń puste i dodaje go do kodu. Alternatywnie można dodać kod ręcznie w **widoku kod.** Na przykład następujące wiersze kodu deklarują metodę obsługi zdarzeń, która zostanie wywołana, `Form` gdy klasa wywołuje `Load` zdarzenie.  
  
     [!code-csharp[csProgGuideEvents#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#11)]  
  
     Wiersz kodu, który jest wymagany do subskrybowania zdarzenia `InitializeComponent` jest również automatycznie generowany w metodzie w pliku Form1.Designer.cs w projekcie. Przypomina to:  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a>Aby programowo subskrybować zdarzenia  
  
1. Zdefiniuj metodę obsługi zdarzeń, której podpis pasuje do podpisu delegata dla zdarzenia. Na przykład jeśli zdarzenie jest <xref:System.EventHandler> oparte na typie delegata, następujący kod reprezentuje wycinek metody:  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2. Użyj operatora przypisania`+=`dodawania ( ) do dołączenia programu obsługi zdarzeń do zdarzenia. W poniższym przykładzie załóżmy, że obiekt o nazwie `publisher` ma zdarzenie o nazwie `RaiseCustomEvent`. Należy zauważyć, że klasa subskrybenta wymaga odwołania do klasy wydawcy, aby subskrybować jego zdarzenia.  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     Należy zauważyć, że poprzednia składnia jest nowa w języku C# 2.0. Jest to dokładnie odpowiednik składni C# 1.0, w którym encapsulating delegata `new` muszą być jawnie utworzone przy użyciu słowa kluczowego:  
  
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
  
- Jeśli nie będziesz musiał zrezygnować z subskrypcji zdarzenia później, możesz`+=`użyć operatora przypisania dodawania ( ) aby dołączyć do zdarzenia metodę anonimową. W poniższym przykładzie załóżmy, że obiekt o nazwie `publisher` ma zdarzenie o nazwie `RaiseCustomEvent` i że `CustomEventArgs` klasa została również zdefiniowana do przenoszenia jakiegoś specjalistycznego informacji o zdarzeniach. Należy zauważyć, że klasa subskrybenta wymaga odwołania do, `publisher` aby zapisać się do jego zdarzeń.  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     Ważne jest, aby zauważyć, że nie można łatwo zrezygnować z subskrypcji zdarzenia, jeśli używasz funkcji anonimowej, aby go zapisać. Aby anulować subskrypcję w tym scenariuszu, należy wrócić do kodu, w którym subskrybujesz zdarzenie, przechowuj metodę anonimową w zmiennej delegata, a następnie dodaj pełnomocnika do zdarzenia. Ogólnie rzecz biorąc, zaleca się, aby nie używać funkcji anonimowych do subskrybowania zdarzeń, jeśli będziesz musiał zrezygnować z subskrypcji zdarzenia w późniejszym momencie w kodzie. Aby uzyskać więcej informacji na temat funkcji anonimowych, zobacz [Funkcje anonimowe](../statements-expressions-operators/anonymous-functions.md).  
  
## <a name="unsubscribing"></a>Anulowanie subskrypcji  
 Aby zapobiec wywoływaniu programu obsługi zdarzeń po wywołaniu zdarzenia, anuluj subskrypcję ze zdarzenia. Aby zapobiec wyciekom zasobów, należy anulować subskrypcję ze zdarzeń przed utylizacji obiektu subskrybenta. Dopóki nie anulujesz subskrypcji zdarzenia, delegat multiemisji, który leży u podstaw zdarzenia w obiekcie publikowania, ma odwołanie do pełnomocnika, który hermetyzuje program obsługi zdarzeń subskrybenta. Tak długo, jak obiekt publikowania przechowuje tego odwołania, wyrzucanie elementów bezużytecznych nie spowoduje usunięcia obiektu subskrybenta.  
  
#### <a name="to-unsubscribe-from-an-event"></a>Aby anulować subskrypcję wydarzenia  
  
- Użyj operatora przypisania`-=`odejmowania ( ) aby anulować subskrypcję zdarzenia:  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     Gdy wszyscy subskrybenci zrezygnowali z subskrypcji `null`zdarzenia, wystąpienie zdarzenia w klasie wydawcy jest ustawione na .  
  
## <a name="see-also"></a>Zobacz też

- [Zdarzenia](./index.md)
- [Zdarzenie](../../language-reference/keywords/event.md)
- [Publikowanie zdarzeń zgodnych ze wskazówkami dotyczącymi .NET Framework](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [- i -= operatory](../../language-reference/operators/subtraction-operator.md)
- [+ i += operatory](../../language-reference/operators/addition-operator.md)
