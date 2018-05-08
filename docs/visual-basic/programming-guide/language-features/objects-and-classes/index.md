---
title: Obiekty i klasy w języku Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: 2917a698f9aa7828c201a048f443f5941797c704
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="objects-and-classes-in-visual-basic"></a>Obiekty i klasy w języku Visual Basic
*Obiektu* jest kombinacją kod i dane, które mogą być traktowane jako jednostka. Obiekt może być częścią aplikacji, takich jak formularz lub formant. Można także obiekt całej aplikacji.

Podczas tworzenia aplikacji w języku Visual Basic, stale Praca z obiektami. Można użyć obiekty dostarczane w Visual Basic, takich jak uzyskiwanie dostępu do obiektów formantów formularzy i danych. Umożliwia także obiekty z innych aplikacji w aplikacji Visual Basic. Można nawet utworzyć własny obiektów i określić dodatkowe właściwości i metody dla nich. Obiekty działać tak jak prefabrykowanych bloków konstrukcyjnych dla programów — pozwalają jednokrotny fragment kodu i użyć go ponownie samodzielnego.  
  
W tym temacie omówiono obiektów szczegółowo.  

## <a name="objects-and-classes"></a>Obiekty i klasy
Każdy obiekt w języku Visual Basic jest definiowana za pomocą *klasy*. Klasa opisuje zmiennych, właściwości, procedur i zdarzeń obiektu. Obiekty są wystąpieniami klasy; można utworzyć dowolną liczbę obiektów, których należy po zdefiniowaniu klasy.

Aby poznać relacja między obiektem i jego klasa, traktować zielonki pliku cookie i plików cookie. Krajarki plik cookie jest klasą. Definiuje właściwości każdego pliku cookie, na przykład wielkość i kształt. Klasa jest używana do tworzenia obiektów. Obiekty są pliki cookie.

Aby korzystać z jego elementów członkowskich należy utworzyć obiekt.  

#### <a name="to-create-an-object-from-a-class"></a>Aby utworzyć obiekt z klasy

1. Określ, z których klasy do utworzenia obiektu.  

2. Zapis [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) można utworzyć zmiennej, do której można przypisać do wystąpienia klasy. Zmienna powinna być typu odpowiednią klasę.

   ```vb
   Dim nextCustomer As customer
   ```

3. Dodaj [operatora New](../../../../visual-basic/language-reference/operators/new-operator.md) — słowo kluczowe można zainicjować zmiennej nowe wystąpienie klasy.

   ```vb
   Dim nextCustomer As New customer
   ```

4. Członkowie klasy można uzyskać dostęp za pośrednictwem zmiennej obiektu.  

   ```vb
   nextCustomer.accountNumber = lastAccountNumber + 1  
   ```

> [!NOTE]
>  Jeśli to możliwe, należy zadeklarować zmienną typu klasy, który chcesz przypisać do niej. Ta metoda jest wywoływana *wczesne wiązanie*. Jeśli nie znasz klasy, wpisz w czasie kompilacji, można wywołać *późne wiązanie* przez zadeklarowanie zmiennej za [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md). Jednak późne wiązanie można wprowadzić wydajność wolniejszej i ograniczyć dostęp do elementów członkowskich obiektu środowiska wykonawczego. Aby uzyskać więcej informacji, zobacz [deklaracja zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).

### <a name="multiple-instances"></a>Wiele wystąpień
Nowo utworzone z klasy obiektów często są identyczne ze sobą. Gdy istnieją jako pojedyncze obiekty, jednak ich właściwości i zmienne można zmienić niezależnie od innych wystąpień. Na przykład, jeśli dodasz trzy pola wyboru na formularzu, każdy obiekt pole wyboru jest wystąpieniem <xref:System.Windows.Forms.CheckBox> klasy. Poszczególne <xref:System.Windows.Forms.CheckBox> obiektów korzystają ze wspólnego zestawu właściwości i możliwości (właściwości, zmienne, procedur i zdarzeń), zdefiniowane przez klasę. Jednak każdy ma własną nazwę, oddzielnie włączone i wyłączone, a można umieścić w innym miejscu w formularzu.

## <a name="object-members"></a>Elementów członkowskich obiektu
Element aplikacji jest obiekt reprezentujący *wystąpienia* klasy. Pola, metody, właściwości i zdarzenia są blokami konstrukcyjnymi obiektów i stanowią ich *członków*.

### <a name="member-access"></a>Dostęp do elementu członkowskiego
Dostęp do elementu członkowskiego obiektu, określając w kolejności, nazwa zmiennej obiektu okres (`.`), a nazwa elementu członkowskiego. W poniższym przykładzie <xref:System.Windows.Forms.Control.Text%2A> właściwość <xref:System.Windows.Forms.Label> obiektu.

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a>IntelliSense lista elementów członkowskich
Po wywołaniu jego opcja Lista składników, na przykład po wpisaniu okres, IntelliSense wyświetla elementy członkowskie klasy (`.`) jako operatora dostępu do elementu członkowskiego. Jeśli wpiszesz okres, po nazwie zmiennej zadeklarowanej jako wystąpienie tej klasy, IntelliSense wyświetla listę wszystkich elementów członkowskich wystąpień i żaden udostępniane elementy członkowskie. Jeśli wpiszesz okres, po nazwie klasy sam IntelliSense wyświetla wszystkie elementy członkowskie udostępnionego i żaden z elementów członkowskich wystąpień. Aby uzyskać więcej informacji, zobacz [za pomocą funkcji IntelliSense](/visualstudio/ide/using-intellisense).

### <a name="fields-and-properties"></a>Pola i właściwości
*Pola* i *właściwości* reprezentują informacje przechowywane w obiekcie. Pobierz i ustawienia ich wartości z instrukcji przypisania taki sam sposób pobrać i ustawić zmienne lokalne w procedurze. Poniższy przykład pobiera <xref:System.Windows.Forms.Control.Width%2A> właściwości i zestawy <xref:System.Windows.Forms.Control.ForeColor%2A> właściwość <xref:System.Windows.Forms.Label> obiektu.

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

Należy pamiętać, że pole jest również nazywany *zmiennej członkowskiej*.
  
Użyj procedur właściwości, gdy:

- Należy kontrolować, kiedy i jak wartość jest ustawiona lub pobrać.

- Właściwość ma dobrze zdefiniowanego zestawu wartości, które muszą być weryfikowane.

- Ustawienie tej wartości powoduje, że niektóre widocznych zmian w stan obiektu, takich jak `IsVisible` właściwości.

- Ustawienie właściwości powoduje zmian do innych zmiennych wewnętrznych lub wartości innych właściwości.

- Zestaw czynności należy wykonać przed właściwości można ustawić ani pobrać.

Użyj pola, gdy:  

- Wartość jest typu własnym sprawdzania poprawności. Na przykład błąd lub konwersji danych występuje, gdy wartość inną niż `True` lub `False` jest przypisany do `Boolean` zmiennej.

- Dowolna wartość zakresu obsługiwanego przez typ danych jest prawidłowy. Dotyczy to wielu właściwości typu `Single` lub `Double`.

- Ta właściwość jest `String` typu danych i nie ma żadnych ograniczenie rozmiaru lub wartość ciągu.

- Aby uzyskać więcej informacji, zobacz [procedury właściwości](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).

### <a name="methods"></a>Metody
A *metody* to operacja, którą można wykonać obiektu. Na przykład <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> jest metodą <xref:System.Windows.Forms.ComboBox> obiekt, który dodaje nowy wpis do pola kombi.

W poniższym przykładzie pokazano <xref:System.Windows.Forms.Timer.Start%2A> metody <xref:System.Windows.Forms.Timer> obiektu.

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

Należy pamiętać, że metoda jest po prostu *procedury* które będzie widoczne za pomocą obiektu.

Aby uzyskać więcej informacji, zobacz [procedury](../../../../visual-basic/programming-guide/language-features/procedures/index.md).

### <a name="events"></a>Zdarzenia
Zdarzenie jest Akcja rozpoznawana przez obiekt, takie jak kliknięcie myszą lub naciśnięcie klawisza i dla którego można napisać kod odpowiedzieć. Zdarzenia może wystąpić w wyniku akcji użytkownika lub kod programu, lub może być spowodowany przez system. Dociera do kodu, która sygnalizuje zdarzenie *podnieść* zdarzeń i kod, który odpowiada do niego jest nazywany *obsługi* go.

Można również tworzyć zdarzenia niestandardowe wywoływane przez obiekty i obsługiwane przez inne obiekty. Aby uzyskać więcej informacji, zobacz [zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md).

### <a name="instance-members-and-shared-members"></a>Elementy członkowskie wystąpień i udostępniane elementy członkowskie
Po utworzeniu obiektu z klasą wynik jest wystąpienie tej klasy. Elementy członkowskie, które nie są zadeklarowane z [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) — słowo kluczowe są *wystąpienia elementów członkowskich*, które należy ściśle określone wystąpienie. Elementu członkowskiego wystąpienia w jednym wystąpieniu zależy od tego samego elementu członkowskiego w innym wystąpieniu tego samego rodzaju. Wystąpienie zmiennej członkowskiej, na przykład może mieć różne wartości w różnych wystąpieniach.

Zadeklarowane elementy członkowskie z `Shared` — słowo kluczowe są *udostępniane elementy członkowskie*, które należą do klasy jako całości, a nie do dowolne wystąpienie. Udostępnionego elementu członkowskiego istnieje tylko raz, niezależnie od tego, jak wiele wystąpień klasy jej tworzenia lub nawet w przypadku tworzenia żadnych wystąpień. Na przykład udostępnionego elementu członkowskiego zmiennej, która ma tylko jedną wartość, która jest dostępna dla całego kodu, które mogą uzyskiwać dostęp do tej klasy.

#### <a name="accessing-nonshared-members"></a>Uzyskiwanie dostępu do członków udostępniana  

###### <a name="to-access-a-nonshared-member-of-an-object"></a>Aby uzyskiwanie dostępu do członka udostępniana obiektu

1. Upewnij się, że obiekt został utworzony po swojej klasie i przypisany do zmiennej obiektu.

   ```vb
   Dim secondForm As New System.Windows.Forms.Form  
   ```  

2. W instrukcji, która uzyskuje dostęp do elementu członkowskiego, postępuj zgodnie z nazwy zmiennej obiektu z *operatora dostępu do elementu członkowskiego* (`.`), a następnie nazwę elementu członkowskiego.

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a>Uzyskiwanie dostępu do udostępniane elementy członkowskie

###### <a name="to-access-a-shared-member-of-an-object"></a>Aby uzyskać dostępu do udostępnionego elementu członkowskiego obiektu

- Po nazwie klasy *operatora dostępu do elementu członkowskiego* (`.`), a następnie nazwę elementu członkowskiego. Należy zawsze dostęp do `Shared` element członkowski obiektu bezpośrednio za pomocą nazwy klasy.

   ```vb
   MsgBox("This computer is called " & Environment.MachineName)  
   ```

- Jeśli utworzono już obiekt z klasy, można też dostęp `Shared` elementu członkowskiego za pośrednictwem zmiennej obiektu.

### <a name="differences-between-classes-and-modules"></a>Różnice między klasami i modułów
Podstawowa różnica między klasy i moduły jest, że klasy można wdrożyć jako obiekty podczas standardowe moduły nie. Zmiana zmiennej publicznej w module standardowym jedną część programu jest tylko jedna kopia danych standardowy moduł, innych części programu pobiera tę samą wartość, jeśli następnie odczytuje tej zmiennej. Z kolei obiekt istnieją dane osobno dla poszczególnych wystąpień obiektu. Inna różnica polega na tym, w przeciwieństwie do standardowych moduły klasy mogą implementować interfejsów.

> [!NOTE]
> Gdy `Shared` modyfikator jest stosowana do elementu członkowskiego klasy, jest ona skojarzona z samej zamiast konkretnego wystąpienia klasy klasy. Element członkowski jest dostępny bezpośrednio za pomocą nazwy klasy, tych samych elementów członkowskich modułu sposób są dostępne.

Klasy i moduły również użyć różne zakresy ich elementy członkowskie. Elementów członkowskich zdefiniowanych w klasie ograniczone w ramach określonego wystąpienia klasy i istnieje tylko w przypadku istnienia obiektu. Aby uzyskać dostęp do elementów członkowskich klasy z poza klasą, należy użyć w pełni kwalifikowane nazwy w formacie *obiektu*. *Element członkowski*.

Z drugiej strony elementów członkowskich zadeklarowanych w module jest publicznie dostępny domyślnie i można uzyskać, sprawdzając dowolny kod, który można uzyskać dostęp do modułu. Oznacza to, że zmienne w module standardowym są zmienne globalne skutecznie, ponieważ są one widoczne z dowolnego miejsca w projekcie, a istnieją przez cały okres istnienia program.

## <a name="reusing-classes-and-objects"></a>Ponowne używanie klas i obiektów  
Obiekty umożliwiają zadeklarować zmienne i procedury raz i ponowne ich zawsze, gdy potrzebne. Na przykład jeśli chcesz dodać do aplikacji sprawdzania pisowni można zdefiniować wszystkie zmienne i obsługuje funkcje umożliwiają korzystanie z funkcji sprawdzania pisowni. Jeśli tworzysz Twojej sprawdzania pisowni jako klasa, można użyć w innych aplikacjach przez dodanie odwołania do zestawu skompilowanego. Jeszcze lepiej można zaoszczędzić niektórych pracy przy użyciu klasy sprawdzania pisowni, że ktoś inny już został utworzony.

[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Przykłady wiele składników, które są dostępne do użycia. W poniższym przykładzie użyto <xref:System.TimeZone> klasy w <xref:System> przestrzeni nazw. <xref:System.TimeZone> zapewnia to członkom, dzięki którym można pobrać informacji o strefie czasowej bieżącego systemu komputera.

```vb
Public Sub examineTimeZone()
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone
    Dim s As String = "Current time zone is "
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "
    s &= "different from UTC (coordinated universal time)"
    s &= vbCrLf & "and is currently "
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "
    s &= "on ""summer time""."
    MsgBox(s)
End Sub
```

W powyższym przykładzie pierwszy [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) deklaruje zmienną obiektu typu <xref:System.TimeZone> i przypisuje jej <xref:System.TimeZone> obiektu zwróconego przez <xref:System.TimeZone.CurrentTimeZone%2A> właściwości.

## <a name="relationships-among-objects"></a>Relacje między obiektami  
Obiekty może być powiązane ze sobą na kilka sposobów. Główne rodzaje relacji są *hierarchiczna* i *zawierania*.

### <a name="hierarchical-relationship"></a>Hierarchiczna relacja
Klasy pochodne klasy więcej podstawowych, są one określane jako ma *hierarchiczną relację*. Klasy hierarchie są przydatne podczas opisywania elementów, które są podtypu bardziej ogólne klasy.

W poniższym przykładzie załóżmy, że chcesz zdefiniować specjalny rodzaj <xref:System.Windows.Forms.Button> czy działa jak zwykłym <xref:System.Windows.Forms.Button> , ale także opisuje metodę Odwraca kolory pierwszego planu i tła.

##### <a name="to-define-a-class-is-derived-from-an-already-existing-class"></a>Aby zdefiniować klasę jest pochodną klasy już istniejącej

1. Użyj [Class — instrukcja](../../../../visual-basic/language-reference/statements/class-statement.md) do klasy, z którego można utworzyć obiektu, należy zdefiniować.

   ```vb
   Public Class reversibleButton
   ```

   Upewnij się, `End Class` instrukcji następuje ostatniego wiersza kodu w klasie. Domyślnie automatycznie generuje zintegrowane środowisko programistyczne (IDE) `End Class` po wprowadzeniu `Class` instrukcji.

2. Postępuj zgodnie z `Class` instrukcji bezpośrednio z [dziedziczy instrukcję](../../../../visual-basic/language-reference/statements/inherits-statement.md). Określ klasę, z którego pochodzi nowej klasy.  
  
   ```vb
   Inherits System.Windows.Forms.Button
   ```

  Nowej klasy dziedziczy wszystkich elementów członkowskich zdefiniowanych przez klasę podstawową.

3. Dodaj kod dla dodatkowych członków ujawnia z klasy pochodnej. Na przykład można dodać `reverseColors` — metoda i klasy pochodne mogą wyglądać w następujący sposób:

   ```vb
   Public Class reversibleButton
       Inherits System.Windows.Forms.Button
           Public Sub reverseColors()
               Dim saveColor As System.Drawing.Color = Me.BackColor
               Me.BackColor = Me.ForeColor
               Me.ForeColor = saveColor
          End Sub
   End Class
   ```

   W przypadku utworzenia obiektu z `reversibleButton` klasy, będzie miał dostęp do wszystkich członków <xref:System.Windows.Forms.Button> klasy, jak również `reverseColors` — metoda i innych nowych członków, należy zdefiniować na `reversibleButton`.

Klasy pochodne dziedziczyć elementów członkowskich klasy, które bazują na, co umożliwia dodawanie w czasie złożoność w hierarchii klasy. Aby uzyskać więcej informacji, zobacz [podstawowe informacje o dziedziczeniu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).

#### <a name="compiling-the-code"></a>Kompilowanie kodu
Upewnij się, że kompilator mogą uzyskiwać dostęp do tej klasy, z którego mają pochodzić nowej klasy. Może to oznaczać pełni kwalifikujących się jego nazwę, tak jak w poprzednim przykładzie, lub jego przestrzeni nazw w identyfikacji [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md). Klasa znajduje się w innym projekcie, może być konieczne Dodaj odwołanie do tego projektu. Aby uzyskać więcej informacji, zobacz [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project).

### <a name="containment-relationship"></a>Relacja zawierania
Innym sposobem obiekty mogą być powiązane jest *relacji zawierania*. Obiekty kontenera hermetyzować logicznie inne obiekty. Na przykład <xref:System.OperatingSystem> obiekt logicznie zawiera <xref:System.Version> obiektu, który zwraca za pośrednictwem jego <xref:System.OperatingSystem.Version%2A> właściwości. Należy pamiętać, że obiekt kontenera nie fizycznie zawiera inny obiekt.

#### <a name="collections"></a>Kolekcje
Jednego określonego typu obiektu zawierania jest reprezentowana przez *kolekcji*. Kolekcje są podobne obiekty, które mogą być wyliczane grup. Visual Basic obsługuje określonej składni w [For Each... Następna instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) umożliwiająca iterację elementów w kolekcji. Ponadto kolekcji często umożliwiają używanie <xref:Microsoft.VisualBasic.Collection.Item%2A> można pobrać elementów według ich indeksu lub skojarzyć je z unikatowym ciągiem. Kolekcje można łatwiej używać niż tablic, ponieważ umożliwiają dodawanie lub usuwanie elementów bez użycia indeksów. Ze względu na ich łatwość użycia kolekcje są często używane do przechowywania formularzy i kontrolek.

## <a name="related-topics"></a>Tematy pokrewne  
 [Przewodnik: definiowanie klas](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)  
 Krok po kroku opisano sposób tworzenia klasy.  

 [Przeciążone właściwości i metody](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)  
 Przeciążone właściwości i metody  

 [Podstawowe informacje o dziedziczeniu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 Obejmuje Modyfikatory dziedziczenia, zastępowanie metody i właściwości, MyClass i MyBase.  

 [Okres istnienia obiektów: w jaki sposób obiekty są tworzone i niszczone](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 W tym artykule omówiono tworzenie i usuwanie wystąpienia klas.  

 [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 Opisuje sposób tworzenia i używania typy anonimowe, które umożliwiają tworzenie obiektów bez pisania definicji klasy dla typu danych.  

 [Inicjatory obiektów: typy nazwane i anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 W tym artykule omówiono inicjatory obiektów, które są używane do tworzenia wystąpień typów nazwane i anonimowe przy użyciu jedno wyrażenie.  

 [Instrukcje: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 Wyjaśniono, jak wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego. Zawiera przykłady wnioskowania zakończone powodzeniem i niepowodzeniem.
