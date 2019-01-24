---
title: 'Okres istnienia obiektów: Jak obiekty są tworzone i niszczone (Visual Basic)'
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
ms.openlocfilehash: 319d606bcd19397932c05f1d5b808f2f5d8923ff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610334"
---
# <a name="object-lifetime-how-objects-are-created-and-destroyed-visual-basic"></a>Okres istnienia obiektów: Jak obiekty są tworzone i niszczone (Visual Basic)
Wystąpienie klasy, obiektu, jest tworzona przy użyciu `New` — słowo kluczowe. Inicjowanie zadania często muszą być wykonywane na nowe obiekty zanim zostaną użyte. Typowe zadania inicjowania obejmują otwierania plików, łączenie z bazami danych i odczytywania wartości kluczy rejestru. Visual Basic kontroluje inicjowania nowych obiektów za pomocą procedur o nazwie *konstruktory* (specjalne metody, które umożliwiają kontrolę nad inicjowania).  
  
 Obiekt zwolnionego zakres jest on zwalniany przez środowisko uruchomieniowe języka wspólnego (CLR). Visual Basic kontroluje zwolnienia zasobów systemowych za pomocą procedur o nazwie *destruktory*. Razem konstruktory i destruktory obsługuje tworzenie bibliotek klas niezawodne i przewidywalne.  
  
## <a name="using-constructors-and-destructors"></a>Za pomocą konstruktorów i destruktorów  
 Konstruktory i destruktory kontrolować, tworzenie i niszczenie obiektów. `Sub New` i `Sub Finalize` procedury w Visual Basic, zainicjować i niszczy obiektów; zastępują one `Class_Initialize` i `Class_Terminate` metod używanych w Visual Basic 6.0 i starszych wersji.  
  
### <a name="sub-new"></a>Nowe podrzędne  
 `Sub New` Konstruktor można uruchomić tylko raz, po utworzeniu klasy. Nie można wywołać w jawnie w dowolnym miejscu innym niż w pierwszym wierszu kodu innego konstruktora z tej samej klasie lub klasie pochodnej. Ponadto kod w `Sub New` metody jest zawsze uruchamiany przed innymi kodami w klasie. [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)] i nowszych wersjach niejawnie Utwórz `Sub New` konstruktora w czasie wykonywania, jeżeli nie zdefiniujesz jawnie `Sub New` procedury dla klasy.  
  
 Aby utworzyć konstruktor dla klasy, należy utworzyć procedurę o nazwie `Sub New` w dowolnym miejscu definicji klasy. Aby utworzyć sparametryzowania konstruktora, określ nazwy i typy danych argumentów `Sub New` tak samo jak należy określić argumenty dla innej procedury, zgodnie z poniższym kodem:  
  
 [!code-vb[VbVbalrOOP#42](../../../../visual-basic/misc/codesnippet/VisualBasic/object-lifetime-how-objects-are-created-and-destroyed_1.vb)]  
  
 Konstruktory często są przeciążone, zgodnie z poniższym kodem:  
  
 [!code-vb[VbVbalrOOP#116](../../../../visual-basic/misc/codesnippet/VisualBasic/object-lifetime-how-objects-are-created-and-destroyed_2.vb)]  
  
 Podczas definiowania klasy pochodzącej od innej klasy w pierwszym wierszu konstruktora musi być wywołaniem do konstruktora klasy bazowej, chyba że klasa bazowa ma dostępny konstruktor, który nie przyjmuje żadnych parametrów. Wywołania do klasy bazowej, zawierający powyżej konstruktora, na przykład będzie `MyBase.New(s)`. W przeciwnym razie `MyBase.New` jest opcjonalna, i wywołuje ona niejawnie środowiska uruchomieniowego języka Visual Basic.  
  
 Po napisaniu kodu, aby wywołać konstruktora obiektu nadrzędnego, można dodać kodu inicjowania dodatkowe `Sub New` procedury. `Sub New` można zaakceptować argumenty wywołanego jako sparametryzowania konstruktora. Te parametry są przekazywane z procedury wywołanie konstruktora, na przykład `Dim AnObject As New ThisClass(X)`.  
  
### <a name="sub-finalize"></a>Sub Finalize  
 Przed wydaniem obiektów, automatycznie wywołuje środowisko CLR `Finalize` metody dla obiektów, które definiują `Sub Finalize` procedury. `Finalize` Metoda może zawierać kod, który trzeba wykonać przed obiekt jest niszczony, takie jak kod zamykanie plików i zapisywanie informacji o stanie. Zwłoka niewielkim wzroście wydajności do wykonywania `Sub Finalize`, więc należy zdefiniować `Sub Finalize` metody tylko wtedy, gdy trzeba jawnie zwolnić obiektów.  
  
> [!NOTE]
>  Moduł zbierający elementy bezużyteczne w CLR nie jest i nie mogą usuwanie *niezarządzanych obiektów*, obiekty, które system operacyjny wykonuje bezpośrednio, poza środowiskiem CLR. Jest to spowodowane różnych obiektów niezarządzanych musi zostać usunięty z na różne sposoby. Informacje nie są bezpośrednio związane z obiektem niezarządzane; musi zostać znaleziony w dokumentacji dla obiektu. Klasa, która używa niezarządzane obiekty muszą usunięcia go w jego `Finalize` metody.  
  
 `Finalize` Destruktor jest metodą chronionych, który można wywołać tylko z klasy należy ona do lub z klas pochodnych. Wywołania systemowe `Finalize` automatycznie kiedy obiekt jest niszczony, więc nie należy jawnie wywołać `Finalize` z poza klasy pochodnej `Finalize` implementacji.  
  
 W odróżnieniu od `Class_Terminate`, które wykonuje, gdy tylko obiekt jest ustawiony na wartość nothing, jest zwykle opóźnienia między kiedy obiekt traci zakresu i kiedy wywołuje języka Visual Basic `Finalize` destruktora. [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)] i nowsze wersje umożliwiają drugi rodzaj destruktora, <xref:System.IDisposable.Dispose%2A>, której można jawnie wywołać w dowolnym momencie, aby od razu zwolnić zasoby.  
  
> [!NOTE]
>  A `Finalize` destruktor nie powinna zgłaszać wyjątków, ponieważ nie mogą być obsługiwane przez aplikację i może spowodować nieplanowane zamknięcie aplikacji.  
  
### <a name="how-new-and-finalize-methods-work-in-a-class-hierarchy"></a>Jak nowe i zakończyć metody działają w hierarchii klas  
 Zawsze, gdy tworzone jest wystąpienie klasy, środowisko uruchomieniowe języka wspólnego (CLR) próbuje wykonać procedurę o nazwie `New`, jeśli taki istnieje w tym obiekcie. `New` rodzaj procedury o nazwie `constructor` używany do zainicjowania nowych obiektów, przed wykonaniem każdy inny kod w obiekcie. A `New` Konstruktor może służyć do otwierania plików, połączenie z bazami danych, zainicjować zmienne i zajmie się inne zadania, które należy wykonać, zanim obiekt może być używany.  
  
 Po utworzeniu wystąpienia klasy pochodnej `Sub New` wykonaniem konstruktora klasy bazowej, najpierw następuje konstruktory w klasach pochodnych. Zdarza się to pierwszy wiersz kodu w `Sub New` Konstruktor używa składni `MyBase.New()`wywołać konstruktora klasy bezpośrednio nad sama w hierarchii klas. `Sub New` Konstruktor jest następnie wywoływana dla każdej klasy w hierarchii klas do konstruktora dla klasy bazowej zostanie osiągnięty. W tym momencie kod w Konstruktorze dla klasy bazowej jest wykonywana, a następnie kod w każdym konstruktora dla wszystkich klas pochodnych, a ostatnia wykonywany jest kod w najbardziej pochodnej klasy.  
  
 ![Konstruktory i dziedziczenie](../../../../visual-basic/programming-guide/language-features/objects-and-classes/media/vaconstructorsinheritance.gif "vaConstructorsInheritance")  
  
 Gdy obiekt nie jest już potrzebny, środowisko CLR wywołuje <xref:System.Object.Finalize%2A> metodę dla tego obiektu, przed zwolnieniem pamięci. <xref:System.Object.Finalize%2A> Wywoływana jest metoda `destructor` ponieważ wykonuje zadania oczyszczania, takie jak zapisywanie informacji o stanie, zamykanie plików i połączenia z bazami danych i innych zadań, które muszą być wykonane przed zwolnieniem obiektu.  
  
 ![Dziedziczenie konstruktorów 2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/media/vaconstructorsinheritance_2.gif "vaConstructorsInheritance_2")  
  
## <a name="idisposable-interface"></a>Interfejs IDisposable  
 Wystąpienia klasy często kontrolować zasoby, które nie są zarządzane przez środowisko CLR, takich jak Windows obsługuje i połączenia z bazą danych. Te zasoby muszą być usuwane w `Finalize` metody klasy, tak aby ich zwolniony, kiedy niszczony jest obiekt przez moduł odśmiecania pamięci. Jednak moduł odśmiecania pamięci niszczy obiektów tylko wtedy, gdy środowisko CLR wymaga więcej pamięci. Oznacza to, że zasoby mogą nie być dostępne aż do czasu, po obiekt wykracza poza zakres.  
  
 Aby uzupełnić wyrzucania elementów bezużytecznych, Twoich zajęciach zapewnia mechanizm aktywnie zarządzać zasobami systemu, jeśli implementują <xref:System.IDisposable> interfejsu. <xref:System.IDisposable> zawiera jedną metodę <xref:System.IDisposable.Dispose%2A>, klientów, którzy powinny wywoływać po zakończeniu używania obiektu. Możesz użyć <xref:System.IDisposable.Dispose%2A> metodę, aby natychmiast zwolnienia zasobów i wykonywania zadań takich jak zamykanie plików i połączenia z bazą danych. W odróżnieniu od `Finalize` destruktora, <xref:System.IDisposable.Dispose%2A> metoda nie jest wywoływana automatycznie. Klienci klasy należy jawnie wywołać <xref:System.IDisposable.Dispose%2A> kiedy chcesz od razu zwolnić zasoby.  
  
### <a name="implementing-idisposable"></a>Implementowanie interfejsu IDisposable  
 Klasa, która implementuje <xref:System.IDisposable> interfejsu powinny zawierać te sekcje kodu:  
  
-   Pole do śledzenia czy obiekt został usunięty:  
  
    ```  
    Protected disposed As Boolean = False  
    ```  
  
-   Przeciążenia <xref:System.IDisposable.Dispose%2A> , zwalnia zasoby klasy. Ta metoda powinna być wywoływana przez <xref:System.IDisposable.Dispose%2A> i `Finalize` metody klasy bazowej:  
  
    ```  
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
  
-   Implementacja <xref:System.IDisposable.Dispose%2A> zawierający następujący kod:  
  
    ```  
    Public Sub Dispose() Implements IDisposable.Dispose  
        Dispose(True)  
        GC.SuppressFinalize(Me)  
    End Sub  
    ```  
  
-   Zastępowanie `Finalize` metodę, która zawiera następujący kod:  
  
    ```  
    Protected Overrides Sub Finalize()  
        Dispose(False)  
        MyBase.Finalize()  
    End Sub  
    ```  
  
### <a name="deriving-from-a-class-that-implements-idisposable"></a>Wyprowadzanie z klas, w którym zaimplementowano interfejs IDisposable  
 Klasa, która pochodzi z klasy bazowej, która implementuje <xref:System.IDisposable> interfejsu nie jest konieczne przesłonić metod bazowych, chyba że używa dodatkowe zasoby, które muszą zostać usunięte. W takiej sytuacji klasy pochodne powinny przesłaniać klasy bazowej `Dispose(disposing)` metody do usuwania zasobów klasy pochodnej. To zastąpienie musi wywołać klasy bazowej `Dispose(disposing)` metody.  
  
```  
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
  
 Klasa pochodna nie powinien przesłonić klasy bazowej <xref:System.IDisposable.Dispose%2A> i `Finalize` metody. Gdy te metody są wywoływane z wystąpienia klasy pochodnej, klasa bazowa implementacji tych metod wywołania zastąpienie klasy pochodnej z `Dispose(disposing)` metody.  
  
## <a name="garbage-collection-and-the-finalize-destructor"></a>Wyrzucanie elementów bezużytecznych i finalizowanie — destruktor  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Używa *odwołania śledzenia wyrzucania elementów bezużytecznych* systemu, aby okresowo wersji nieużywane zasoby. Visual Basic 6.0 i starsze wersje należy użyć innego systemu o nazwie *zliczanie odwołań* do zarządzania zasobami. Mimo że oba systemy, które automatycznie pełnią taką samą funkcję, istnieje kilka istotnych różnic.  
  
 Środowisko CLR okresowo niszczy obiekty, gdy system określi, że takie obiekty nie są już potrzebne. Obiekty są zwalniane szybciej, gdy wszystkie zasoby systemu są w przeciwnym razie podaż i rzadziej. Opóźnienie między kiedy obiekt traci zakresu i gdy środowisko CLR zwalnia go oznacza, że w przeciwieństwie do obiektów w Visual Basic 6.0 i starszych wersjach, nie można ustalić dokładnie gdy obiekt jest niszczony. W takiej sytuacji obiektów mówi się, że masz *niedeterministyczne okres istnienia*. W większości przypadków niedeterministyczne okresu istnienia nie zmienia sposobu pisania aplikacji, tak długo, jak należy pamiętać, że `Finalize` destruktor nie może być od razu wykonywane gdy obiekt traci zakresu.  
  
 Inna różnica między systemami wyrzucania elementów bezużytecznych obejmuje użycie `Nothing`. Z zalet zliczanie w Visual Basic 6.0 i starszych wersjach, programiści czasami przypisane `Nothing` do obiektu zmiennych, aby zwolnić odwołań tych zmiennych przechowywanych. Jeśli zmienna przechowywane ostatnie odwołanie do obiektu, obiekt zasoby zostały wydane natychmiast. W nowszych wersjach programu Visual Basic gdy można wykluczyć sytuacji, w których ta procedura jest bardzo przydatna wykonywanie jej nigdy nie powoduje, że przywoływanego obiektu zwolnić jego zasoby, od razu. Aby zwolnić zasoby natychmiast, użyj obiektu <xref:System.IDisposable.Dispose%2A> metody, jeśli jest dostępny. Tylko wtedy należy ustawić zmienną `Nothing` jest, gdy czas względem czasu, moduł odśmiecania pamięci ma wykryć obiekty oddzielone cały okres ich istnienia.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.IDisposable.Dispose%2A>
- [Inicjowanie i kończenie działania składników](https://msdn.microsoft.com/library/58444076-a9d2-4c91-b3f6-0e180dc0695d)
- [New, operator](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Oczyszczanie zasobów niezarządzanych](../../../../standard/garbage-collection/unmanaged.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
