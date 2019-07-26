---
title: 'Okres istnienia obiektu: Jak obiekty są tworzone i niszczone (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.Constructor
helpviewer_keywords:
- destructors, object lifetime
- Sub Finalize destructor
- objects [Visual Basic], destroying
- lifetime [Visual Basic], objects
- Sub New constructor, object lifetime
- Finalize method [Visual Basic], object lifetime
- objects [Visual Basic], creating
- Class_Terminate
- Dispose method [Visual Basic], object lifetime
- Class_Initialize
- object creation [Visual Basic], object lifetime
- parameterized constructors
- objects [Visual Basic], lifetime
- objects [Visual Basic], garbage collection
- constructors [Visual Basic], object lifetime
- Sub Dispose destructor
- garbage collection [Visual Basic], Visual Basic
ms.assetid: f1ee8458-b156-44e0-9a8a-5dd171648cd8
ms.openlocfilehash: 5b092f50ddff5c432fbd6396b5fedafe7a6acba0
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512841"
---
# <a name="object-lifetime-how-objects-are-created-and-destroyed-visual-basic"></a>Okres istnienia obiektu: Jak obiekty są tworzone i niszczone (Visual Basic)

Wystąpienie klasy, obiektu jest tworzone za pomocą `New` słowa kluczowego. Zadania inicjowania często należy wykonać na nowych obiektach przed ich użyciem. Typowe zadania inicjowania obejmują otwieranie plików, łączenie z bazami danych i odczytywanie wartości kluczy rejestru. Visual Basic steruje inicjalizacją nowych obiektów przy użyciu procedur  nazywanych konstruktorami (specjalne metody, które zezwalają na kontrolę nad inicjalizacją).

Gdy obiekt zostanie pozostawiony, zostanie on opublikowany przez środowisko uruchomieniowe języka wspólnego (CLR). Visual Basic kontroluje wydawanie zasobów systemowych przy użyciu procedur nazywanych *destruktorami*. Razem konstruktory i destruktory obsługują tworzenie niezawodnych i przewidywalnych bibliotek klas.

## <a name="using-constructors-and-destructors"></a>Używanie konstruktorów i destruktorów

Konstruktory i destruktory kontrolują tworzenie i niszczenie obiektów. `Class_Initialize` `Class_Terminate` Procedury i w`Sub Finalize` Visual Basic zainicjować i zniszczyć obiekty; zastępują metody i używane w Visual Basic 6,0 i wcześniejszych wersjach. `Sub New`

### <a name="sub-new"></a>Sub New

`Sub New` Konstruktor można uruchomić tylko raz podczas tworzenia klasy. Nie można go wywołać jawnie wszędzie poza pierwszym wierszem kodu innego konstruktora z tej samej klasy lub z klasy pochodnej. Ponadto kod w `Sub New` metodzie zawsze jest uruchamiany przed jakimkolwiek innym kodem w klasie. Visual Basic i nowsze wersje niejawnie tworzą `Sub New` konstruktora w czasie wykonywania, jeśli nie `Sub New` określisz jawnie procedury dla klasy.

Aby utworzyć konstruktora dla klasy, należy utworzyć procedurę o nazwie `Sub New` gdziekolwiek w definicji klasy. Aby utworzyć sparametryzowany Konstruktor, określ nazwy i typy danych argumentów `Sub New` tak samo jak w przypadku określenia argumentów dla każdej innej procedury, jak w poniższym kodzie:

[!code-vb[VbVbalrOOP#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/WhidbeyStuff.vb#42)]

Konstruktory są często przeciążone, tak jak w poniższym kodzie:

[!code-vb[VbVbalrOOP#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/WhidbeyStuff.vb#116)]

Podczas definiowania klasy pochodnej z innej klasy, pierwszy wiersz konstruktora musi być wywołaniem konstruktora klasy bazowej, chyba że klasa bazowa ma dostępnego konstruktora, który nie przyjmuje żadnych parametrów. Na przykład `MyBase.New(s)`wywołanie klasy bazowej zawierającej powyższy Konstruktor. W przeciwnym razie jest opcjonalne, a środowisko uruchomieniowe Visual Basic wywołuje je niejawnie. `MyBase.New`

Po napisaniu kodu w celu wywołania konstruktora obiektu nadrzędnego można dodać do `Sub New` procedury dodatkowy kod inicjalizacji. `Sub New`można akceptować argumenty, gdy są wywoływane jako Konstruktor sparametryzowane. Te parametry są przesyłane z procedury wywołującej Konstruktor, na przykład `Dim AnObject As New ThisClass(X)`.

### <a name="sub-finalize"></a>Podfinalize

Przed zwolnieniem obiektów CLR automatycznie wywołuje `Finalize` metodę dla obiektów, które `Sub Finalize` definiują procedurę. `Finalize` Metoda może zawierać kod, który musi być wykonywany tuż przed zniszczeniem obiektu, taki jak kod zamykania plików i zapisywania informacji o stanie. Istnieje niewielki spadek wydajności dla wykonywania `Sub Finalize`, dlatego należy `Sub Finalize` zdefiniować metodę tylko wtedy, gdy trzeba będzie jawnie zwolnić obiekty.

> [!NOTE]
> Moduł wyrzucania elementów bezużytecznych w środowisku CLR nie (i nie może) usuwania *obiektów niezarządzanych*, obiektów, które system operacyjny wykonuje bezpośrednio, poza środowiskiem CLR. Wynika to z faktu, że różne obiekty niezarządzane muszą zostać usunięte na różne sposoby. Te informacje nie są bezpośrednio skojarzone z obiektem niezarządzanym; należy ją znaleźć w dokumentacji dla obiektu. Klasa, która korzysta z obiektów niezarządzanych, musi usunąć je `Finalize` w swojej metodzie.

`Finalize` Destruktor jest metodą chronioną, która może być wywoływana tylko z klasy, do której należy, lub z klas pochodnych. System automatycznie wywołuje `Finalize` , gdy obiekt jest niszczony, dlatego nie należy jawnie wywołać `Finalize` z zewnątrz `Finalize` implementacji klasy pochodnej.

W przeciwieństwie `Class_Terminate`do, które jest wykonywane zaraz, gdy tylko obiekt jest ustawiony na wartość Nothing, zazwyczaj opóźnienie między obiektem traci zakres i kiedy Visual Basic `Finalize` wywołuje destruktor. Visual Basic i nowsze wersje umożliwiają użycie drugiego rodzaju destruktora, <xref:System.IDisposable.Dispose%2A>który można jawnie wywołać w dowolnym momencie, aby natychmiast zwolnić zasoby.

> [!NOTE]
> `Finalize` Destruktor nie powinien zgłaszać wyjątków, ponieważ nie mogą być obsługiwane przez aplikację i może spowodować przerwanie działania aplikacji.

### <a name="how-new-and-finalize-methods-work-in-a-class-hierarchy"></a>Jak metody New i Finalize działają w hierarchii klas

Za każdym razem, gdy tworzone jest wystąpienie klasy, środowisko uruchomieniowe języka wspólnego (CLR) próbuje wykonać procedurę `New`o nazwie, jeśli istnieje w tym obiekcie. `New`jest typem procedury o nazwie `constructor` , która jest używana do inicjowania nowych obiektów przed wykonaniem dowolnego innego kodu w obiekcie. `New` Konstruktor może służyć do otwierania plików, łączenia z bazami danych, inicjowania zmiennych i ponoszenia innych zadań, które należy wykonać, aby można było użyć obiektu.

Gdy tworzone jest wystąpienie klasy pochodnej, `Sub New` Konstruktor klasy bazowej jest wykonywany jako pierwszy, a następnie konstruktory w klasach pochodnych. Dzieje się tak, ponieważ pierwszy wiersz kodu w `Sub New` konstruktorze używa składni `MyBase.New()`do wywołania konstruktora klasy bezpośrednio powyżej w hierarchii klas. `Sub New` Konstruktor jest następnie wywoływany dla każdej klasy w hierarchii klas do momentu osiągnięcia konstruktora dla klasy bazowej. W tym momencie kod w konstruktorze klasy bazowej jest wykonywany, po którym następuje kod w każdym konstruktorze we wszystkich klasach pochodnych i kod w większości klas pochodnych jest wykonywany jako ostatni.

![Zrzut ekranu przedstawiający konstruktory hierarchii klas i dziedziczenie.](./media/object-lifetime-how-objects-are-created-and-destroyed/subnew-constructor-inheritance.gif)

Gdy obiekt nie jest już wymagany, środowisko CLR wywołuje <xref:System.Object.Finalize%2A> metodę dla tego obiektu przed zwolnieniem jego pamięci. Metoda jest wywoływana a `destructor` ponieważ wykonuje zadania oczyszczania, takie jak zapisywanie informacji o stanie, zamykanie plików i połączeń z bazami danych oraz inne zadania, które należy wykonać przed zwolnieniem obiektu. <xref:System.Object.Finalize%2A>

![Zrzut ekranu przedstawiający destruktor metody Finalize.](./media/object-lifetime-how-objects-are-created-and-destroyed/finalize-method-destructor.gif)

## <a name="idisposable-interface"></a>Interfejs IDisposable

Wystąpienia klas często kontrolują zasoby, które nie są zarządzane przez środowisko CLR, takie jak uchwyty systemu Windows i połączenia bazy danych. Te zasoby muszą zostać usunięte `Finalize` z metody klasy, aby były zwalniane, gdy obiekt zostanie zniszczony przez moduł wyrzucania elementów bezużytecznych. Jednak Moduł wyrzucania elementów bezużytecznych niszczy obiekty tylko wtedy, gdy środowisko CLR wymaga więcej wolnej pamięci. Oznacza to, że zasoby mogą nie być uwalniane aż do momentu, gdy obiekt wykracza poza zakres.

Aby uzupełniać odzyskiwanie pamięci, klasy mogą być mechanizmem do aktywnego zarządzania zasobami systemu, jeśli implementują <xref:System.IDisposable> interfejs. <xref:System.IDisposable>ma jedną metodę, <xref:System.IDisposable.Dispose%2A>która powinna być wywoływana przez klientów po zakończeniu korzystania z obiektu. Możesz użyć <xref:System.IDisposable.Dispose%2A> metody, aby natychmiast zwolnić zasoby i wykonać zadania, takie jak zamykanie plików i połączeń z bazą danych. `Finalize` W<xref:System.IDisposable.Dispose%2A> przeciwieństwie do destruktora Metoda nie jest wywoływana automatycznie. Klienci klasy muszą jawnie wywołać <xref:System.IDisposable.Dispose%2A> , gdy chcesz natychmiast zwolnić zasoby.

### <a name="implementing-idisposable"></a>Implementowanie interfejsu IDisposable

Klasa implementująca <xref:System.IDisposable> interfejs powinna zawierać następujące sekcje kodu:

- Pole do śledzenia, czy obiekt został usunięty:

  ```vb
  Protected disposed As Boolean = False
  ```

- Przeciążenie <xref:System.IDisposable.Dispose%2A> zwalniające zasoby klasy. Ta metoda powinna być wywoływana przez <xref:System.IDisposable.Dispose%2A> metody i `Finalize` klasy bazowej:

  ```vb
  Protected Overridable Sub Dispose(ByVal disposing As Boolean)
      If Not Me.disposed Then
          If disposing Then
              ' Insert code to free managed resources.
          End If
          ' Insert code to free unmanaged resources.
      End If
      Me.disposed = True
  End Sub
  ```

- Implementacja programu <xref:System.IDisposable.Dispose%2A> , która zawiera tylko następujący kod:

  ```vb
  Public Sub Dispose() Implements IDisposable.Dispose
      Dispose(True)
      GC.SuppressFinalize(Me)
  End Sub
  ```

- Przesłonięcie `Finalize` metody, która zawiera tylko następujący kod:

  ```vb
  Protected Overrides Sub Finalize()
      Dispose(False)
      MyBase.Finalize()
  End Sub
  ```

### <a name="deriving-from-a-class-that-implements-idisposable"></a>Wyprowadzanie z klasy implementującej interfejs IDisposable

Klasa, która dziedziczy z klasy bazowej implementującej <xref:System.IDisposable> interfejs, nie musi przesłonić żadnej z metod podstawowych, chyba że używa dodatkowych zasobów, które muszą zostać usunięte. W takiej sytuacji Klasa pochodna powinna zastąpić `Dispose(disposing)` metodę klasy bazowej, aby usunąć zasoby klasy pochodnej. To zastąpienie musi wywoływać `Dispose(disposing)` metodę klasy bazowej.

```vb
Protected Overrides Sub Dispose(ByVal disposing As Boolean)
    If Not Me.disposed Then
        If disposing Then
            ' Insert code to free managed resources.
        End If
        ' Insert code to free unmanaged resources.
    End If
    MyBase.Dispose(disposing)
End Sub
```

Klasa pochodna nie powinna przesłaniać metod klasy <xref:System.IDisposable.Dispose%2A> bazowej i. `Finalize` Gdy te metody są wywoływane z wystąpienia klasy pochodnej, implementacja klasy bazowej `Dispose(disposing)` metoda wywołuje zastąpienie metody klasy pochodnej.

## <a name="garbage-collection-and-the-finalize-destructor"></a>Odzyskiwanie pamięci i destruktor finalizatora

.NET Framework używa systemu wyrzucania *elementów bezużytecznych śledzenia odwołań* do okresowego zwalniania nieużywanych zasobów. Visual Basic 6,0 i wcześniejsze wersje używają innego systemu zwanego *zliczaniem odwołań* do zarządzania zasobami. Chociaż obie systemy wykonują tę samą funkcję automatycznie, istnieje kilka istotnych różnic.

Środowisko CLR okresowo niszczy obiekty, gdy system ustali, że takie obiekty nie są już potrzebne. Obiekty są uwalniane szybciej, gdy zasoby systemu są w krótkim dostawie i rzadziej w inny sposób. Opóźnienie między momentem, gdy obiekt traci zakres i kiedy środowisko CLR wykryje, że, w przeciwieństwie do obiektów w Visual Basic 6,0 i wcześniejszych wersjach, nie można określić dokładnie, gdy obiekt zostanie zniszczony. W takiej sytuacji obiekty są określane jako Niedeterministyczny *okres istnienia*. W większości przypadków okres istnienia Niedeterministyczny nie zmienia sposobu pisania aplikacji, o ile pamiętasz, że `Finalize` destruktor może nie zostać natychmiast wykonany, gdy obiekt utraci zakres.

Inna różnica między systemami zbierania elementów bezużytecznych polega na użyciu `Nothing`programu. Aby skorzystać z zliczania odwołań w Visual Basic 6,0 i wcześniejszych wersjach, programiści czasami są `Nothing` przypisani do zmiennych obiektów w celu zwolnienia odwołań do tych zmiennych. Jeśli zmienna posiadała ostatnie odwołanie do obiektu, zasoby obiektu zostały wydane od razu. W nowszych wersjach Visual Basic, chociaż mogą wystąpić przypadki, w których ta procedura jest nadal cenna, wykonanie nigdy nie powoduje, że obiekt, do którego istnieje odwołanie, natychmiast zwolni swoje zasoby. Aby natychmiast zwolnić zasoby, użyj <xref:System.IDisposable.Dispose%2A> metody obiektu, jeśli jest dostępna. Jedynym momentem, w którym należy ustawić zmienną `Nothing` , jest to, kiedy jego okres istnienia jest długi względem czasu, gdy moduł zbierający elementy bezużyteczne wykrywa obiekty oddzielone.

## <a name="see-also"></a>Zobacz także

- <xref:System.IDisposable.Dispose%2A>
- [Inicjowanie i kończenie działania składników](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ws9dc6t6(v=vs.120))
- [New, operator](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Oczyszczanie zasobów niezarządzanych](../../../../standard/garbage-collection/unmanaged.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
