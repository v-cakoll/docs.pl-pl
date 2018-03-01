---
title: "Okres istnienia obiektów: w jaki sposób obiekty są tworzone i niszczone (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f985d6bf7b26ec22d6e533eae1f1d7ea0682e56c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="object-lifetime-how-objects-are-created-and-destroyed-visual-basic"></a>Okres istnienia obiektów: w jaki sposób obiekty są tworzone i niszczone (Visual Basic)
Wystąpienie klasy, obiektu, jest tworzona przy użyciu `New` — słowo kluczowe. Inicjowanie zadania często muszą być wykonywane na nowe obiekty zanim zostaną użyte. Typowe zadania inicjowania obejmują otwieranie plików, łączenie z bazami danych i odczytywania wartości kluczy rejestru. Visual Basic steruje inicjowania nowych obiektów za pomocą procedur o nazwie *konstruktorów* (specjalne metody umożliwiające kontrolę nad inicjowania).  
  
 Obiekt zwolnionego zakres jest wydane przez środowisko uruchomieniowe języka wspólnego (CLR). Visual Basic steruje zwolnienia zasobów systemowych przy użyciu procedury o nazwie *destruktory*. Razem konstruktory i destruktory obsługuje tworzenie bibliotek klas niezawodny i przewidywalne.  
  
## <a name="using-constructors-and-destructors"></a>Przy użyciu konstruktory i destruktory  
 Konstruktory i destruktory kontrolować tworzenie i likwidacja obiektów. `Sub New` i `Sub Finalize` procedury w Visual Basic, zainicjować i zniszcz obiektów; zastępują one `Class_Initialize` i `Class_Terminate` metody używane w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 6.0 i starsze wersje.  
  
### <a name="sub-new"></a>Nowe podrzędne  
 `Sub New` Konstruktora można uruchomić tylko raz, podczas tworzenia klasy. Nie można wywołać w jawnie w dowolnym miejscu innym niż w pierwszym wierszu kodu innego konstruktora z tej samej klasy lub z klasy pochodnej. Ponadto kod w `Sub New` metoda zawsze jest uruchamiana przed innymi kod w klasie. [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)]i nowszych wersjach niejawnie Utwórz `Sub New` konstruktora w czasie wykonywania, jeśli nie zostanie jawnie zdefiniowana `Sub New` procedury dla klasy.  
  
 Aby utworzyć konstruktor dla klasy, Utwórz procedurę o nazwie `Sub New` w dowolnym miejscu definicji klasy. Aby utworzyć sparametryzowanym konstruktorze, określ nazwy i dane typy argumentów `Sub New` tylko należy określić argumenty dla innej procedury, zgodnie z poniższym kodem:  
  
 [!code-vb[VbVbalrOOP#42](../../../../visual-basic/misc/codesnippet/VisualBasic/object-lifetime-how-objects-are-created-and-destroyed_1.vb)]  
  
 Konstruktory są często przeciążone zgodnie z poniższym kodem:  
  
 [!code-vb[VbVbalrOOP#116](../../../../visual-basic/misc/codesnippet/VisualBasic/object-lifetime-how-objects-are-created-and-destroyed_2.vb)]  
  
 Po zdefiniowaniu klasy pochodnej z innej klasy pierwszy wiersz konstruktora musi być wywołanie konstruktora klasy podstawowej, chyba że klasę podstawową był dostępny konstruktor, który nie przyjmuje żadnych parametrów. Byłoby wywołania do klasy podstawowej, zawierający powyżej konstruktora, na przykład `MyBase.New(s)`. W przeciwnym razie `MyBase.New` jest opcjonalny i [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] środowisko urchomieniowe wywołuje go niejawnie.  
  
 Po napisaniu kod, aby wywołać konstruktora obiektu nadrzędnego, można dodać dowolny kod inicjujący dodatkowe do `Sub New` procedury. `Sub New`mogą akceptować argumenty wywołanego jako sparametryzowanym konstruktorze. Te parametry są przekazywane z procedury wywoływania konstruktora, na przykład `Dim AnObject As New ThisClass(X)`.  
  
### <a name="sub-finalize"></a>Sub Finalize  
 Przed wydaniem obiektów, automatycznie wywołuje CLR `Finalize` metody dla obiektów, które definiują `Sub Finalize` procedury. `Finalize` Metody może zawierać kod, który można wykonać tylko przed obiektu, takie jak kod zamykanie plików i zapisywanie informacji o stanie. Jest zmniejszenie wydajności nieznaczne wykonywania `Sub Finalize`, więc należy zdefiniować `Sub Finalize` metody tylko wtedy, gdy trzeba jawnie wersji obiektów.  
  
> [!NOTE]
>  Moduł garbage collector środowiska CLR nie i nie może usuwa *niezarządzane obiekty*, obiekty, które system operacyjny jest wykonywana bezpośrednio, poza środowiskiem CLR. Jest to spowodowane różnych niezarządzane obiekty musi zostać usunięty z na różne sposoby. Informacje nie są bezpośrednio związane z niezarządzanego obiektu; musi zostać znaleziony w dokumentacji dla obiekt. Klasa, która używa niezarządzane obiekty musi dysponować je w jego `Finalize` metody.  
  
 `Finalize` Destruktora jest metoda chroniona, który można wywołać tylko z należy do klasy lub klas pochodnych. Wywołania systemowe `Finalize` automatycznie gdy obiekt zostanie zniszczony, dlatego nie należy bezpośrednio wywoływać `Finalize` z poza klasy pochodnej `Finalize` implementacji.  
  
 W odróżnieniu od `Class_Terminate`, który wykonuje się, gdy obiekt jest ustawiony na wartość nothing, jest zwykle opóźnienia między po obiektu utraci zakresu i gdy wywołuje Visual Basic `Finalize` destruktora. [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)]i nowszych wersjach umożliwiają drugi rodzaj destruktor, <xref:System.IDisposable.Dispose%2A>, której można jawnie wywołać w dowolnej chwili, aby natychmiast zwolnić zasoby.  
  
> [!NOTE]
>  A `Finalize` destruktor nie powinien zgłosić wyjątkami, ponieważ nie mogą być obsługiwane przez aplikację i może spowodować zamknięcie aplikacji.  
  
### <a name="how-new-and-finalize-methods-work-in-a-class-hierarchy"></a>Jak nowy i zakończenia pracy metod w hierarchii klas  
 Zawsze, gdy tworzone jest wystąpienie klasy, środowisko uruchomieniowe języka wspólnego (CLR) próbuje wykonać procedurę o nazwie `New`, jeśli istnieje w tym obiekcie. `New`rodzaj procedury o nazwie `constructor` używany zainicjować nowe obiekty przed wykonaniem innego kodu w obiekcie. A `New` Konstruktor może służyć do otwierania plików, połączenie z bazami danych zainicjować zmienne i zajmie się inne zadania, które trzeba wykonać te czynności przed użyciem obiektu.  
  
 Gdy tworzone jest wystąpienie klasy pochodnej, `Sub New` konstruktora klasy podstawowej wykonuje najpierw następuje konstruktorów w klasach pochodnych. Zdarza się to pierwszy wiersz kodu w `Sub New` Konstruktor używa składni `MyBase.New()`można wywołać konstruktora klasy bezpośrednio nad sama w hierarchii klasy. `Sub New` Konstruktor jest następnie wywoływana dla każdej klasy w hierarchii klasy do konstruktora dla klasy podstawowej zostanie osiągnięty. W tym momencie kodu w Konstruktorze dla klasy podstawowej wykonuje, następuje kod w każdym konstruktora dla wszystkich klas pochodnych i ostatnio wykonywany jest kod w najdalszych pochodnych klas.  
  
 ![Konstruktory i dziedziczenie](../../../../visual-basic/programming-guide/language-features/objects-and-classes/media/vaconstructorsinheritance.gif "vaConstructorsInheritance")  
  
 Gdy obiekt nie jest już potrzebne, wywołuje CLR <xref:System.Object.Finalize%2A> metody dla tego obiektu przed zwalnianie pamięci. <xref:System.Object.Finalize%2A> Wywoływana jest metoda `destructor` ponieważ wykonuje zadania oczyszczania, takie jak zapisywanie informacji o stanie, zamykanie plików i połączenia z bazami danych i innych zadań, które muszą być wykonane przed zwolnieniem obiektu.  
  
 ![Dziedziczenie konstruktorów 2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/media/vaconstructorsinheritance_2.gif "vaConstructorsInheritance_2")  
  
## <a name="idisposable-interface"></a>Interfejs IDisposable  
 Wystąpienia klas kontrolować często zasobów nie są zarządzane przez środowisko CLR, takie jak uchwyty okien i połączenia z bazą danych. Te zasoby muszą być usuwane w `Finalize` metody klasy, dzięki czemu będzie można zwolnić, gdy obiekt zostanie zniszczony przez moduł garbage collector. Jednak moduł garbage collector niszczy obiektów tylko wtedy, gdy środowisko CLR wymaga więcej pamięci. Oznacza to, że zasoby nie można zwolnić dopiero, gdy obiekt wykracza poza zakres.  
  
 Uzupełnienie wyrzucanie elementów bezużytecznych, klas zapewniają mechanizm aktywnie zarządzać zasobami systemu, jeśli wdrażają <xref:System.IDisposable> interfejsu. <xref:System.IDisposable>zawiera jedną metodę <xref:System.IDisposable.Dispose%2A>, których klienci powinny wywoływać przy kończyły się przy użyciu obiektu. Można użyć <xref:System.IDisposable.Dispose%2A> metody natychmiast zwolnić zasoby i wykonywać zadania, takie jak zamykanie plików i połączenia z bazą danych. W odróżnieniu od `Finalize` destruktor, <xref:System.IDisposable.Dispose%2A> metoda nie jest wywoływana automatycznie. Klienci klasy musi jawnie wywołać <xref:System.IDisposable.Dispose%2A> Jeśli chcesz natychmiast zwolnić zasoby.  
  
### <a name="implementing-idisposable"></a>Implementacja interfejsu IDisposable  
 Klasa, która implementuje <xref:System.IDisposable> interfejsu powinny zawierać tych fragmentów kodu:  
  
-   Pole w celu śledzenia czy obiekt został usunięty:  
  
    ```  
    Protected disposed As Boolean = False  
    ```  
  
-   Przeciążenie <xref:System.IDisposable.Dispose%2A> który zwalnia zasoby tej klasy. Ta metoda powinna być wywoływana <xref:System.IDisposable.Dispose%2A> i `Finalize` metody klasy podstawowej:  
  
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
  
-   Implementacja interfejsu <xref:System.IDisposable.Dispose%2A> zawierający następujący kod:  
  
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
  
### <a name="deriving-from-a-class-that-implements-idisposable"></a>Wyprowadzanie z klasy, która implementuje interfejs IDisposable  
 Klasa, która pochodzi z klasy podstawowej, która implementuje <xref:System.IDisposable> interfejsu nie należy do przesłonięcia żadnej z metod bazowych, chyba że używa dodatkowe zasoby, które muszą zostać usunięte. W takiej sytuacji klasy pochodne powinny przesłaniać klasy podstawowej `Dispose(disposing)` metodę dispose klasy pochodnej zasobów. To zastąpienie musi wywołać klasy podstawowej `Dispose(disposing)` metody.  
  
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
  
 Klasa pochodna nie powinien przesłonić klasy podstawowej <xref:System.IDisposable.Dispose%2A> i `Finalize` metody. Jeśli te metody są wywoływane z wystąpienia klasy pochodnej, implementacji klasy podstawowej z tych metod wywołania zastąpienie klasy pochodnej z `Dispose(disposing)` metody.  
  
## <a name="garbage-collection-and-the-finalize-destructor"></a>Wyrzucanie elementów bezużytecznych i zakończenia — destruktor  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Używa *odwołanie śledzenia wyrzucanie elementów bezużytecznych* systemu, aby okresowo zwolnić zasoby nieużywane. Visual Basic 6.0 i starszych wersji użyć innego systemu o nazwie *liczenie odwołań w* do zarządzania zasobami. Mimo że obu systemów automatycznie wykonywać tę samą funkcję, istnieje kilka istotnych różnic.  
  
 Środowisko CLR niszczy obiektów okresowo, gdy system sprawdza, czy takie obiekty nie są już potrzebne. Obiekty są zwalniane szybciej, gdy zasoby systemowe są w przeciwnym razie Podaj krótki, a rzadziej. Opóźnienie między po obiektu utraci zakresu i kiedy CLR zwolnieniem oznacza, że w przeciwieństwie do obiektów w Visual Basic 6.0 i starszych wersji, nie można określić dokładnie gdy obiekt zostanie zniszczona. W takiej sytuacji obiekty są określane jako ma *deterministyczna istnienia*. W większości przypadków deterministyczna istnienia nie zmienia sposobu pisania aplikacji, tak długo, jak należy pamiętać, że `Finalize` destruktor nie może od razu wykonany, gdy obiekt utraci zakresu.  
  
 Inna różnica między systemami wyrzucanie elementów bezużytecznych wymaga stosowania `Nothing`. Aby skorzystać z zliczanie w Visual Basic 6.0 i starszych wersjach, czasami przypisane programistów `Nothing` do obiektu zmienne do zwolnienia odwołania tych zmiennych przechowywanych. Jeśli zmienna przechowywać ostatnie odwołanie do obiektu, obiektu zasoby zostały wydane od razu. W nowszych wersjach programu Visual Basic może być przypadki, w których jest wciąż obsługiwane w tej procedurze wykonywania go nigdy nie powoduje, że przywoływanego obiektu natychmiast zwolnienia zasobów. Aby zwolnić zasoby natychmiast, użyj obiektu <xref:System.IDisposable.Dispose%2A> metody, jeśli jest dostępna. Tylko wtedy można ustawić zmiennej `Nothing` przypadku długo względnym w stosunku do modułu zbierającego elementy bezużyteczne czasie wykryć obiekty oddzielone jego okres istnienia.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IDisposable.Dispose%2A>  
 [Inicjowanie i kończenie działania składników](http://msdn.microsoft.com/library/58444076-a9d2-4c91-b3f6-0e180dc0695d)  
 [New — Operator](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [Oczyszczanie zasobów niezarządzanych](../../../../standard/garbage-collection/unmanaged.md)  
 [Nothing](../../../../visual-basic/language-reference/nothing.md)
