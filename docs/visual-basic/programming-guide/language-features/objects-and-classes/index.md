---
title: Obiekty i klasy w języku Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: 2917a698f9aa7828c201a048f443f5941797c704
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934293"
---
# <a name="objects-and-classes-in-visual-basic"></a>Obiekty i klasy w języku Visual Basic
*Obiektu* składa się z kodu i danych, które mogą być traktowane jako jednostka. Obiekt może być częścią aplikacji, takich jak formularz lub formant. Można także obiekt całej aplikacji.

Po utworzeniu aplikacji w języku Visual Basic stale pracy z obiektami. Możesz użyć obiekty dostarczane w języku Visual Basic, takich jak uzyskiwanie dostępu do obiektów formantów, formularzy i danych. Umożliwia także obiekty z innymi aplikacjami w swojej aplikacji Visual Basic. Można nawet tworzenia własnych obiektów i zdefiniować dodatkowe właściwości i metody dla nich. Obiekty zachowywać się jak prefabrykowanych bloków konstrukcyjnych dla programów — umożliwiają Napisz raz, fragment kodu i ponownie używać jej wielokrotnie.  
  
W tym temacie omówiono obiektów szczegółowo.  

## <a name="objects-and-classes"></a>Obiekty i klasy
Każdy obiekt w języku Visual Basic jest definiowany przez *klasy*. Klasa opisuje zmiennych, właściwości, procedur i zdarzeń obiektu. Obiekty są wystąpieniami klasy; można utworzyć dowolną liczbę obiektów, czego potrzebujesz, aby po zdefiniowaniu klasy.

Aby zrozumieć relację między obiektem i jego klasa, pomyśl o zielonki plików cookie i plików cookie. Krajarki plik cookie jest klasą. Definiuje właściwości poszczególnych plików cookie, na przykład rozmiar i kształt. Klasa jest używana do tworzenia obiektów. Obiekty są pliki cookie.

Aby korzystać z jej elementów członkowskich, należy utworzyć obiekt.  

#### <a name="to-create-an-object-from-a-class"></a>Aby utworzyć obiekt z klasy

1. Określ, z której klasy, którą chcesz utworzyć obiekt.  

2. Zapis [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) do utworzenia zmiennej, do której można przypisać wystąpienia klasy. Zmienna powinna być typu odpowiednią klasę.

   ```vb
   Dim nextCustomer As customer
   ```

3. Dodaj [operatora New](../../../../visual-basic/language-reference/operators/new-operator.md) — słowo kluczowe, aby zainicjalizować zmienną do nowego wystąpienia klasy.

   ```vb
   Dim nextCustomer As New customer
   ```

4. Elementy członkowskie klasy można teraz uzyskiwać dostęp za pośrednictwem zmiennej obiektu.  

   ```vb
   nextCustomer.accountNumber = lastAccountNumber + 1  
   ```

> [!NOTE]
>  Jeśli to możliwe, należy zadeklarować zmienną typu klasy, które chcesz przypisać do niej. Jest to nazywane *wczesne powiązania*. Jeśli nie znasz klasy typu w czasie kompilacji, można wywołać *późnym wiązaniu* przez zadeklarowanie zmiennej będzie [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md). Jednak późnym wiązaniu można wprowadzić wydajności wolniejszy i ograniczyć dostęp do elementów członkowskich w obiekcie środowiska wykonawczego. Aby uzyskać więcej informacji, zobacz [deklaracja zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).

### <a name="multiple-instances"></a>Wiele wystąpień
Obiekty nowo utworzone na podstawie klasy często są identyczne z siebie nawzajem. Gdy istnieją jako pojedyncze obiekty, jednak ich zmienne i właściwości można zmienić niezależnie od innych wystąpień. Na przykład jeśli dodasz trzy pola wyboru do formularza, każdy obiekt pole wyboru jest wystąpieniem <xref:System.Windows.Forms.CheckBox> klasy. Poszczególne <xref:System.Windows.Forms.CheckBox> obiekty współużytkują wspólny zbiór właściwości oraz możliwości (właściwości, zmienne, procedur i zdarzeń), zdefiniowane przez klasę. Jednak każdy ma własną nazwę, oddzielnie włączone i wyłączone, a można umieścić w innym miejscu w formularzu.

## <a name="object-members"></a>Elementach członkowskich obiektu
Obiekt jest elementem aplikacji, reprezentująca *wystąpienia* klasy. Pola, właściwości, metody i zdarzenia są blokami konstrukcyjnymi obiektów i stanowią ich *członków*.

### <a name="member-access"></a>Dostęp do elementu członkowskiego
Możesz uzyskać dostęp do członka obiektu, określając w kolejności, nazwa zmiennej obiektu okres (`.`) i nazwę elementu członkowskiego. Poniższy przykład ustawia <xref:System.Windows.Forms.Control.Text%2A> właściwość <xref:System.Windows.Forms.Label> obiektu.

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a>Funkcja IntelliSense listę elementów członkowskich
Funkcja IntelliSense wyświetla elementy członkowskie klasy po wywołaniu jego opcji listę elementów członkowskich, na przykład gdy wpiszesz kropkę (`.`) jako operatora dostępu do elementu członkowskiego. Jeśli wpiszesz okres, po nazwie zmiennej zadeklarowanej jako wystąpienie tej klasy, funkcja IntelliSense wyświetla wszystkie składowe wystąpienia i żaden z udostępnionych elementów członkowskich. Jeśli wpiszesz okresie następującym sama nazwa klasy, funkcja IntelliSense wyświetla wszystkie udostępnione elementy członkowskie i żaden z elementów członkowskich wystąpienia. Aby uzyskać więcej informacji, zobacz [za pomocą funkcji IntelliSense](/visualstudio/ide/using-intellisense).

### <a name="fields-and-properties"></a>Pola i właściwości
*Pola* i *właściwości* przedstawiania informacji przechowywanych w obiekcie. Pobierz i ustaw ich wartości za pomocą instrukcji przypisania taki sam sposób pobierania i ustawiania zmiennych lokalnych w procedurze. Poniższy przykład pobiera <xref:System.Windows.Forms.Control.Width%2A> właściwość i zestawach <xref:System.Windows.Forms.Control.ForeColor%2A> właściwość <xref:System.Windows.Forms.Label> obiektu.

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

Należy pamiętać, że pole jest również nazywany *zmiennej składowej*.
  
Użyj procedur właściwości, gdy:

- Wymagane jest sterowanie, kiedy i jak wartość jest ustawiona lub pobrać.

- Właściwość ma dobrze zdefiniowanego zestawu wartości, które muszą być weryfikowane.

- Ustawienie tej wartości powoduje, że niektóre widocznych zmian w stan obiektu, takie jak `IsVisible` właściwości.

- Ustawianie właściwości powoduje, że zmiany do innych wewnętrznych zmiennych lub wartości innych właściwości.

- Zestaw kroków należy wykonać, zanim właściwość można ustawić lub pobrać.

Użyj pola, gdy:  

- Wartość jest typu własnym sprawdzania poprawności. Na przykład komunikat o błędzie lub konwersja danych automatycznego występuje, gdy wartość inną niż `True` lub `False` jest przypisany do `Boolean` zmiennej.

- Dowolna wartość poza zasięgiem obsługiwanym przez typ danych jest prawidłowy. Ta zasada obowiązuje wielu właściwości typu `Single` lub `Double`.

- Właściwość jest `String` typu danych i brak ograniczeń dotyczących rozmiaru lub wartość ciągu.

- Aby uzyskać więcej informacji, zobacz [procedury właściwości](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).

### <a name="methods"></a>Metody
A *metoda* to działanie, którą obiekt może wykonywać. Na przykład <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> to metoda <xref:System.Windows.Forms.ComboBox> obiektu, który dodaje nowy wpis do pola kombi.

W poniższym przykładzie pokazano <xref:System.Windows.Forms.Timer.Start%2A> metody <xref:System.Windows.Forms.Timer> obiektu.

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

Należy zauważyć, że metoda jest po prostu *procedury* , jest uwidaczniany za pomocą obiektu.

Aby uzyskać więcej informacji, zobacz [procedury](../../../../visual-basic/programming-guide/language-features/procedures/index.md).

### <a name="events"></a>Zdarzenia
Zdarzenie jest Akcja rozpoznawana przez obiekt, takie jak kliknięcie myszą lub naciskając klawisz i dla którego można napisać kod odpowiedzi. Zdarzenia może wystąpić w wyniku akcji przez użytkownika lub kod programu, lub może być spowodowane przez system. Kod, który sygnalizuje zdarzenie jest nazywany *podnieść* zdarzeń i kod, który odpowiada do niego jest nazywany *obsługi* go.

Możesz również tworzyć niestandardowe zdarzenia wygenerowane przez obiekty i obsługiwane przez inne obiekty. Aby uzyskać więcej informacji, zobacz [zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md).

### <a name="instance-members-and-shared-members"></a>Elementy członkowskie wystąpień i udostępniane elementy członkowskie
Podczas tworzenia obiektu z klasą, wynik jest wystąpieniem tej klasy. Elementy członkowskie, które nie są zadeklarowane za pomocą [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) — słowo kluczowe są *wystąpieniami elementów członkowskich*, które należą wyłącznie do tego konkretnego wystąpienia. W jednym wystąpieniu elementu członkowskiego wystąpienia jest niezależna od jednego elementu członkowskiego w innym wystąpieniu tej samej klasy. Zmienną elementu członkowskiego, na przykład mogą mieć różne wartości w różnych wystąpieniach.

Elementy członkowskie są zadeklarowane za pomocą `Shared` — słowo kluczowe są *udostępniane elementy członkowskie*, które należą do klasy jako całości, a nie dowolne wystąpienie. Składnik współużytkowany istnieje tylko raz, niezależnie od tego, ile wystąpień klasy można tworzyć lub nawet wtedy, gdy tworzysz żadnych wystąpień. Zmienną członkowską udostępnionej, na przykład ma tylko jedną wartość, która jest dostępna dla całego kodu, które mogą uzyskiwać dostęp do tej klasy.

#### <a name="accessing-nonshared-members"></a>Uzyskiwanie dostępu do elementów nieudostępnionych  

###### <a name="to-access-a-nonshared-member-of-an-object"></a>Do uzyskania dostępu do członka nieudostępnionych obiektu

1. Upewnij się, że obiekt został utworzony od swojej klasy i przypisane do zmiennej obiektu.

   ```vb
   Dim secondForm As New System.Windows.Forms.Form  
   ```  

2. W instrukcji, która uzyskuje dostęp do elementu członkowskiego, postępuj zgodnie z obiektu nazwą zmiennej *operator dostępu do elementu członkowskiego* (`.`) i następnie nazwę elementu członkowskiego.

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a>Uzyskiwanie dostępu do udostępnionych elementów członkowskich

###### <a name="to-access-a-shared-member-of-an-object"></a>Do uzyskania dostępu do członka udostępnionego obiektu

- Postępuj zgodnie z nazwą klasy *operator dostępu do elementu członkowskiego* (`.`) i następnie nazwę elementu członkowskiego. Należy zawsze dostęp do `Shared` członka obiektu bezpośrednio za pomocą nazwy klasy.

   ```vb
   MsgBox("This computer is called " & Environment.MachineName)  
   ```

- Jeśli utworzono już obiekt z klasy, możesz również uzyskać dostęp `Shared` elementu członkowskiego za pośrednictwem zmiennej obiektu.

### <a name="differences-between-classes-and-modules"></a>Różnice między klasami i modułów
Główną różnicą między klasami i modułów jest, że klasy mogą być utworzone jako obiekty podczas standardowych modułów nie. Ponieważ istnieje tylko jedną kopię standardowego modułu danych zmiennej publicznej w module standardowym zmianie jednej części programu, innych części programu pobiera tę samą wartość, jeśli następnie odczytuje tę zmienną. Z kolei obiekt istnieją dane osobno dla poszczególnych wystąpień obiektu. Inny różnica polega na tym, że w przeciwieństwie do standardowych modułów klasy mogą implementować interfejsy.

> [!NOTE]
> Gdy `Shared` modyfikator jest stosowany do składowej klasy, jest skojarzony z klasą sama zamiast konkretnego wystąpienia klasy. Element członkowski odbywa się bezpośrednio przy użyciu nazwy klasy, są używane te same elementy członkowskie modułu sposób.

Klasy i moduły także użyć różnych zakresów dla swoich elementów członkowskich. Elementy członkowskie zdefiniowane w obrębie klasy są ograniczone w ramach określonego wystąpienia klasy i istnieje tylko w przypadku istnienia obiektu. Aby uzyskać dostęp do członków klasy z poza klasą, należy użyć w pełni kwalifikowane nazwy w formacie *obiektu*. *Element członkowski*.

Z drugiej strony elementów członkowskich zadeklarowanych w module są dostępne publicznie domyślnie i może zostać oceniony przez każdy kod, który można uzyskać dostęp do modułu. Oznacza to, że zmienne w module standardowym są zmienne globalne skutecznie, ponieważ są one widoczne w dowolnym miejscu w projekcie, a istnieją przez cały okres istnienia programu.

## <a name="reusing-classes-and-objects"></a>Ponowne używanie klas i obiektów  
Obiekty umożliwiają deklarowanie zmiennych i procedur raz i korzystać z nich je zawsze, gdy potrzebne. Na przykład jeśli chcesz dodać sprawdzania pisowni do aplikacji można zdefiniować wszystkie zmienne i obsługują funkcje umożliwiają korzystanie z funkcji sprawdzania pisowni. Jeśli tworzysz swoje sprawdzania pisowni, jako klasę, możesz użyć w innych aplikacjach, dodając odwołanie do zestawu skompilowanego. Można jeszcze lepiej, możesz zaoszczędzić pewnej pracy za pomocą klasy modułu sprawdzania pisowni, że ktoś już został opracowany.

[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Zawiera przykłady wiele składników, które są dostępne do użycia. W poniższym przykładzie użyto <xref:System.TimeZone> klasy w <xref:System> przestrzeni nazw. <xref:System.TimeZone> zawiera elementy członkowskie, które umożliwiają pobieranie informacji o strefie czasowej bieżącego systemu komputera.

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

W powyższym przykładzie pierwsze [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) deklaruje zmienną obiektu typu <xref:System.TimeZone> i przypisuje do niego <xref:System.TimeZone> obiektu zwróconego przez <xref:System.TimeZone.CurrentTimeZone%2A> właściwości.

## <a name="relationships-among-objects"></a>Relacje między obiektami  
Obiekty mogą być powiązane ze sobą na kilka sposobów. Główne rodzaje relacji są *hierarchiczne* i *zawierania*.

### <a name="hierarchical-relationship"></a>Hierarchiczna relacja
Klasy pochodne więcej podstawowe klasy, są one określane jako mają *hierarchiczną relację*. Hierarchie klasy są przydatne podczas opisywania elementy, które są podtypem bardziej ogólnej klasy.

W poniższym przykładzie załóżmy, że chcesz zdefiniować specjalny rodzaj <xref:System.Windows.Forms.Button> czy działa jak normalne <xref:System.Windows.Forms.Button> , ale udostępnia również metody, która Odwraca kolory pierwszego planu i tła.

##### <a name="to-define-a-class-is-derived-from-an-already-existing-class"></a>Aby zdefiniować klasę jest tworzony na podstawie już istniejącej klasy

1. Użyj [Class — instrukcja](../../../../visual-basic/language-reference/statements/class-statement.md) Aby zdefiniować klasę, z którego można utworzyć obiektu potrzebny.

   ```vb
   Public Class reversibleButton
   ```

   Upewnij się, `End Class` instrukcji następuje ostatni wiersz kodu w klasie. Domyślnie automatycznie generuje zintegrowanego środowiska programistycznego (IDE) `End Class` po wprowadzeniu `Class` instrukcji.

2. Postępuj zgodnie z `Class` instrukcją natychmiast [dziedziczy instrukcję](../../../../visual-basic/language-reference/statements/inherits-statement.md). Określ klasę, z którego pochodzi nowej klasie.  
  
   ```vb
   Inherits System.Windows.Forms.Button
   ```

  Twoja nowa klasa dziedziczy wszystkie elementy członkowskie zdefiniowane przez klasę bazową.

3. Dodaj kod, aby uzyskać dodatkowe elementy członkowskie ujawnia swojej klasy pochodnej. Na przykład można dodać `reverseColors` metoda i Klasa pochodna może wyglądać w następujący sposób:

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

   Jeśli tworzysz obiekt z `reversibleButton` klasy, będzie miał dostęp do wszystkich członków <xref:System.Windows.Forms.Button> klasy, jak również `reverseColors` metody i innych nowych członków, należy zdefiniować na `reversibleButton`.

Klasy pochodne dziedziczy członków klasy, które są one oparte na, dzięki czemu możesz do zwiększenia złożoności jak postępy w hierarchii klas. Aby uzyskać więcej informacji, zobacz [podstawowe informacje o dziedziczeniu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).

#### <a name="compiling-the-code"></a>Kompilowanie kodu
Upewnij się, że kompilator mogą uzyskiwać dostęp do klasy, z którego mają pochodzić nowej klasie. Może to oznaczać pełni kwalifikujących się jego nazwę, jak w poprzednim przykładzie lub identyfikowanie jego przestrzeń nazw w [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md). Klasa znajduje się w innym projekcie, może być konieczne Dodaj odwołanie do tego projektu. Aby uzyskać więcej informacji, zobacz [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project).

### <a name="containment-relationship"></a>Relacja zawierania
Innym sposobem może być powiązanych obiektów jest *relacji zawierania*. Obiekty kontenera hermetyzować logicznie innych obiektów. Na przykład <xref:System.OperatingSystem> obiekt logicznie zawiera <xref:System.Version> obiektu, który zwraca za pośrednictwem jego <xref:System.OperatingSystem.Version%2A> właściwości. Należy pamiętać, że obiekt kontenera nie zawiera fizycznie jakiegokolwiek innego obiektu.

#### <a name="collections"></a>Kolekcje
Jeden typ określonego obiektu zawierania jest reprezentowany przez *kolekcje*. Kolekcje są grupami podobnymi obiektami, które mogą być wyliczane. Visual Basic obsługuje określonej składni w [For Each... Następna instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) pozwala do iteracji przez elementy kolekcji. Ponadto kolekcji często umożliwiają używanie <xref:Microsoft.VisualBasic.Collection.Item%2A> można pobrać elementów za pomocą ich indeksu lub przez skojarzenie ich z unikatowym ciągiem. Kolekcje mogą być łatwiejszy w obsłudze niż tablice, ponieważ umożliwiają dodawanie lub usuwanie elementów bez używania indeksów. Ze względu na ich łatwość użycia kolekcje są często używane do przechowywania formularzy i kontrolek.

## <a name="related-topics"></a>Tematy pokrewne  
 [Przewodnik: definiowanie klas](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)  
 Instrukcje krok po kroku opisano sposób tworzenia klasy.  

 [Przeciążone właściwości i metody](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)  
 Przeciążone właściwości i metody  

 [Podstawowe informacje o dziedziczeniu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 Obejmuje modyfikatorów dziedziczenie, zastępowanie metod "i" właściwości "," MyClass "i" MyBase.  

 [Okres istnienia obiektów: w jaki sposób obiekty są tworzone i niszczone](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 W tym artykule omówiono tworzenie i usuwanie wystąpień klas.  

 [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 Opisuje sposób tworzenia i używania typów anonimowych, które umożliwiają tworzenie obiektów bez konieczności pisania definicji klasy dla typu danych.  

 [Inicjatory obiektów: typy nazwane i anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 W tym artykule omówiono inicjatorów obiektów, które są używane do tworzenia wystąpień nazwanych i anonimowych typów przy użyciu pojedynczego wyrażenia.  

 [Instrukcje: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 Wyjaśnia, jak wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego. Zawiera przykłady wnioskowania zakończone powodzeniem i niepowodzeniem.
