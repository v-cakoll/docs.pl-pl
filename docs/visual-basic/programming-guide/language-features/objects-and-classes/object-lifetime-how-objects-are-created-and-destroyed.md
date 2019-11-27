---
title: 'Okres istnienia obiektów: w jaki sposób obiekty są tworzone i niszczone'
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
ms.openlocfilehash: 8d9647fa490077f9f6ef82f30eccc4d5ee271985
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346106"
---
# <a name="object-lifetime-how-objects-are-created-and-destroyed-visual-basic"></a>Okres istnienia obiektów: w jaki sposób obiekty są tworzone i niszczone (Visual Basic)

Wystąpienie klasy, obiektu jest tworzone za pomocą słowa kluczowego `New`. Zadania inicjowania często należy wykonać na nowych obiektach przed ich użyciem. Typowe zadania inicjowania obejmują otwieranie plików, łączenie z bazami danych i odczytywanie wartości kluczy rejestru. Visual Basic steruje inicjalizacją nowych obiektów przy użyciu procedur nazywanych *konstruktorami* (specjalne metody, które zezwalają na kontrolę nad inicjalizacją).

Gdy obiekt zostanie pozostawiony, zostanie on opublikowany przez środowisko uruchomieniowe języka wspólnego (CLR). Visual Basic kontroluje wydawanie zasobów systemowych przy użyciu procedur nazywanych *destruktorami*. Razem konstruktory i destruktory obsługują tworzenie niezawodnych i przewidywalnych bibliotek klas.

## <a name="using-constructors-and-destructors"></a>Używanie konstruktorów i destruktorów

Konstruktory i destruktory kontrolują tworzenie i niszczenie obiektów. Procedury `Sub New` i `Sub Finalize` w Visual Basic zainicjować i zniszczyć obiekty; zastępują one `Class_Initialize` i `Class_Terminate` metody używane w Visual Basic 6,0 i wcześniejszych wersjach.

### <a name="sub-new"></a>Sub New

Konstruktor `Sub New` można uruchomić tylko raz podczas tworzenia klasy. Nie można go wywołać jawnie wszędzie poza pierwszym wierszem kodu innego konstruktora z tej samej klasy lub z klasy pochodnej. Ponadto kod w metodzie `Sub New` zawsze jest uruchamiany przed jakimkolwiek innym kodem w klasie. Visual Basic niejawnie tworzy konstruktora `Sub New` w czasie wykonywania, jeśli nie określisz jawnie procedury `Sub New` dla klasy.

Aby utworzyć konstruktora dla klasy, należy utworzyć procedurę o nazwie `Sub New` gdziekolwiek w definicji klasy. Aby utworzyć sparametryzowany Konstruktor, określ nazwy i typy danych argumentów do `Sub New` tak samo jak w przypadku określenia argumentów dla każdej innej procedury, jak w poniższym kodzie:

[!code-vb[VbVbalrOOP#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/WhidbeyStuff.vb#42)]

Konstruktory są często przeciążone, tak jak w poniższym kodzie:

[!code-vb[VbVbalrOOP#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/WhidbeyStuff.vb#116)]

Podczas definiowania klasy pochodnej z innej klasy, pierwszy wiersz konstruktora musi być wywołaniem konstruktora klasy bazowej, chyba że klasa bazowa ma dostępnego konstruktora, który nie przyjmuje żadnych parametrów. Na przykład wywołanie klasy bazowej zawierającej powyższy Konstruktor może być `MyBase.New(s)`. W przeciwnym razie `MyBase.New` jest opcjonalne, a środowisko uruchomieniowe Visual Basic wywołuje je niejawnie.

Po napisaniu kodu w celu wywołania konstruktora obiektu nadrzędnego można dodać dowolny dodatkowy kod inicjujący do procedury `Sub New`. `Sub New` może akceptować argumenty, gdy są wywoływane jako Konstruktor sparametryzowane. Te parametry są przesyłane z procedury wywołującej konstruktora, na przykład `Dim AnObject As New ThisClass(X)`.

### <a name="sub-finalize"></a>Podfinalize

Przed zwolnieniem obiektów CLR automatycznie wywołuje metodę `Finalize` dla obiektów, które definiują procedurę `Sub Finalize`. Metoda `Finalize` może zawierać kod, który musi być wykonywany tuż przed zniszczeniem obiektu, taki jak kod zamykania plików i zapisywania informacji o stanie. Istnieje niewielki spadek wydajności dla wykonywania `Sub Finalize`, dlatego należy zdefiniować metodę `Sub Finalize` tylko wtedy, gdy trzeba będzie jawnie zwolnić obiekty.

> [!NOTE]
> Moduł wyrzucania elementów bezużytecznych w środowisku CLR nie (i nie może) usuwania *obiektów niezarządzanych*, obiektów, które system operacyjny wykonuje bezpośrednio, poza środowiskiem CLR. Wynika to z faktu, że różne obiekty niezarządzane muszą zostać usunięte na różne sposoby. Te informacje nie są bezpośrednio skojarzone z obiektem niezarządzanym; należy ją znaleźć w dokumentacji dla obiektu. Klasa, która korzysta z obiektów niezarządzanych, musi usunąć je w swojej metodzie `Finalize`.

Destruktor `Finalize` jest metodą chronioną, która może być wywoływana tylko z klasy, do której należy, lub z klas pochodnych. System wywołuje `Finalize` automatycznie, gdy obiekt jest niszczony, dlatego nie należy jawnie wywołać `Finalize` spoza implementacji `Finalize` klasy pochodnej.

W przeciwieństwie do `Class_Terminate`, które jest wykonywane zaraz, gdy tylko obiekt jest ustawiony na wartość Nothing, zazwyczaj opóźnienie między obiektem traci zakres i gdy Visual Basic wywołuje destruktor `Finalize`. Visual Basic .NET umożliwia korzystanie z drugiego rodzaju destruktora, <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>, który można jawnie wywołać w dowolnym momencie w celu natychmiastowego zwolnienia zasobów.

> [!NOTE]
> Destruktor `Finalize` nie powinien zgłaszać wyjątków, ponieważ nie mogą być obsługiwane przez aplikację i może spowodować przerwanie działania aplikacji.

### <a name="how-new-and-finalize-methods-work-in-a-class-hierarchy"></a>Jak metody New i Finalize działają w hierarchii klas

Za każdym razem, gdy tworzone jest wystąpienie klasy, środowisko uruchomieniowe języka wspólnego (CLR) próbuje wykonać procedurę o nazwie `New`, jeśli istnieje w tym obiekcie. `New` jest typem procedury nazywanej `constructor`, który jest używany do inicjowania nowych obiektów przed wykonaniem dowolnego innego kodu w obiekcie. Konstruktor `New` może służyć do otwierania plików, łączenia z bazami danych, inicjowania zmiennych i ponoszenia innych zadań, które należy wykonać, aby można było użyć obiektu.

Po utworzeniu wystąpienia klasy pochodnej, Konstruktor `Sub New` klasy bazowej jest wykonywany jako pierwszy, a następnie konstruktory w klasach pochodnych. Dzieje się tak, ponieważ pierwszy wiersz kodu w konstruktorze `Sub New` używa składni `MyBase.New()`do wywołania konstruktora klasy bezpośrednio powyżej w hierarchii klas. Konstruktor `Sub New` jest następnie wywoływany dla każdej klasy w hierarchii klas do momentu osiągnięcia konstruktora dla klasy bazowej. W tym momencie kod w konstruktorze klasy bazowej jest wykonywany, po którym następuje kod w każdym konstruktorze we wszystkich klasach pochodnych i kod w większości klas pochodnych jest wykonywany jako ostatni.

![Zrzut ekranu przedstawiający konstruktory hierarchii klas i dziedziczenie.](./media/object-lifetime-how-objects-are-created-and-destroyed/subnew-constructor-inheritance.gif)

Gdy obiekt nie jest już wymagany, środowisko CLR wywołuje metodę <xref:System.Object.Finalize%2A> dla tego obiektu przed zwolnieniem jego pamięci. Metoda <xref:System.Object.Finalize%2A> jest nazywana `destructor`, ponieważ wykonuje zadania oczyszczania, takie jak zapisywanie informacji o stanie, zamykanie plików i połączeń z bazami danych oraz inne zadania, które należy wykonać przed zwolnieniem obiektu.

![Zrzut ekranu przedstawiający destruktor metody Finalize.](./media/object-lifetime-how-objects-are-created-and-destroyed/finalize-method-destructor.gif)

## <a name="idisposable-interface"></a>Interfejs IDisposable

Wystąpienia klas często kontrolują zasoby, które nie są zarządzane przez środowisko CLR, takie jak uchwyty systemu Windows i połączenia bazy danych. Te zasoby muszą zostać usunięte w metodzie `Finalize` klasy, dzięki czemu zostaną wydane, gdy obiekt zostanie zniszczony przez moduł wyrzucania elementów bezużytecznych. Jednak Moduł wyrzucania elementów bezużytecznych niszczy obiekty tylko wtedy, gdy środowisko CLR wymaga więcej wolnej pamięci. Oznacza to, że zasoby mogą nie być uwalniane aż do momentu, gdy obiekt wykracza poza zakres.

Aby uzupełniać odzyskiwanie pamięci, klasy mogą udostępniać mechanizm aktywnego zarządzania zasobami systemu, jeśli implementują interfejs <xref:System.IDisposable>. <xref:System.IDisposable> ma jedną metodę, <xref:System.IDisposable.Dispose%2A>, która powinna być wywoływana przez klientów po zakończeniu korzystania z obiektu. Za pomocą metody <xref:System.IDisposable.Dispose%2A> można natychmiast zwolnić zasoby i wykonać zadania, takie jak zamykanie plików i połączeń z bazami danych. W przeciwieństwie do destruktora `Finalize` Metoda <xref:System.IDisposable.Dispose%2A> nie jest wywoływana automatycznie. Klienci klasy muszą jawnie wywołać <xref:System.IDisposable.Dispose%2A>, gdy chcesz natychmiast zwolnić zasoby.

### <a name="implementing-idisposable"></a>Implementowanie interfejsu IDisposable

Klasa implementująca interfejs <xref:System.IDisposable> powinna zawierać następujące sekcje kodu:

- Pole do śledzenia, czy obiekt został usunięty:

  ```vb
  Protected disposed As Boolean = False
  ```

- Przeciążenie <xref:System.IDisposable.Dispose%2A>, które zwalnia zasoby klasy. Ta metoda powinna być wywoływana przez <xref:System.IDisposable.Dispose%2A> i `Finalize` metody klasy bazowej:

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

- Implementacja <xref:System.IDisposable.Dispose%2A>, która zawiera tylko następujący kod:

  ```vb
  Public Sub Dispose() Implements IDisposable.Dispose
      Dispose(True)
      GC.SuppressFinalize(Me)
  End Sub
  ```

- Zastąpienie metody `Finalize`, która zawiera tylko następujący kod:

  ```vb
  Protected Overrides Sub Finalize()
      Dispose(False)
      MyBase.Finalize()
  End Sub
  ```

### <a name="deriving-from-a-class-that-implements-idisposable"></a>Wyprowadzanie z klasy implementującej interfejs IDisposable

Klasa, która dziedziczy z klasy bazowej implementującej interfejs <xref:System.IDisposable> nie musi przesłoniać żadnej z metod podstawowych, chyba że używa dodatkowych zasobów, które muszą zostać usunięte. W takiej sytuacji Klasa pochodna powinna zastąpić metodę `Dispose(disposing)` klasy bazowej, aby usunąć zasoby klasy pochodnej. To zastąpienie musi wywoływać metodę `Dispose(disposing)` klasy bazowej.

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

Klasa pochodna nie powinna przesłaniać <xref:System.IDisposable.Dispose%2A> i `Finalize` metod klasy bazowej. Gdy te metody są wywoływane z wystąpienia klasy pochodnej, implementacja klasy bazowej metoda wywołuje zastąpienie klasy pochodnej metody `Dispose(disposing)`.

## <a name="garbage-collection-and-the-finalize-destructor"></a>Odzyskiwanie pamięci i destruktor finalizatora

.NET Framework używa systemu *wyrzucania elementów bezużytecznych śledzenia odwołań* do okresowego zwalniania nieużywanych zasobów. Visual Basic 6,0 i wcześniejsze wersje używają innego systemu zwanego *zliczaniem odwołań* do zarządzania zasobami. Chociaż obie systemy wykonują tę samą funkcję automatycznie, istnieje kilka istotnych różnic.

Środowisko CLR okresowo niszczy obiekty, gdy system ustali, że takie obiekty nie są już potrzebne. Obiekty są uwalniane szybciej, gdy zasoby systemu są w krótkim dostawie i rzadziej w inny sposób. Opóźnienie między momentem, gdy obiekt traci zakres i kiedy środowisko CLR wykryje, że, w przeciwieństwie do obiektów w Visual Basic 6,0 i wcześniejszych wersjach, nie można określić dokładnie, gdy obiekt zostanie zniszczony. W takiej sytuacji obiekty są określane jako *Niedeterministyczny okres istnienia*. W większości przypadków okres istnienia Niedeterministyczny nie zmienia sposobu pisania aplikacji, o ile pamiętasz, że destruktor `Finalize` może nie zostać natychmiast wykonany, gdy obiekt utraci zakres.

Inna różnica między systemami zbierania elementów bezużytecznych polega na użyciu `Nothing`. Aby skorzystać z zliczania odwołań w Visual Basic 6,0 i wcześniejszych wersjach, programiści czasami przypisuje `Nothing` do zmiennych obiektów w celu zwolnienia odwołań do tych zmiennych. Jeśli zmienna posiadała ostatnie odwołanie do obiektu, zasoby obiektu zostały wydane od razu. W nowszych wersjach Visual Basic, chociaż mogą wystąpić przypadki, w których ta procedura jest nadal cenna, wykonanie nigdy nie powoduje, że obiekt, do którego istnieje odwołanie, natychmiast zwolni swoje zasoby. Aby natychmiast zwolnić zasoby, użyj metody <xref:System.IDisposable.Dispose%2A> obiektu, jeśli jest dostępna. Jedynym warunkiem, dla którego należy ustawić zmienną `Nothing`, jest to, że okres istnienia jest długi względem czasu, gdy moduł zbierający elementy bezużyteczne wykrywa obiekty oddzielone.

## <a name="see-also"></a>Zobacz także

- <xref:System.IDisposable.Dispose%2A>
- [Inicjowanie i kończenie działania składników](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ws9dc6t6(v=vs.120))
- [Operator New](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Oczyszczanie zasobów niezarządzanych](../../../../standard/garbage-collection/unmanaged.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
