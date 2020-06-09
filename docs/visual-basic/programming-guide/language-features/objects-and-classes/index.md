---
title: Obiekty i klasy
ms.date: 05/26/2020
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: 9e3cf262ef617a1ae5ee92bcc3d6fd5c691602f9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600415"
---
# <a name="objects-and-classes-in-visual-basic"></a>Obiekty i klasy w Visual Basic

*Obiekt* jest kombinacją kodu i danych, który może być traktowany jako jednostka. Obiekt może być częścią aplikacji, taką jak kontrolka lub formularz. Cała aplikacja może być również obiektem.

Podczas tworzenia aplikacji w Visual Basic, pracujesz z obiektami. Można używać obiektów dostarczonych przez Visual Basic, takich jak kontrolki, formularze i obiekty dostępu do danych. Możesz również używać obiektów z innych aplikacji w aplikacji Visual Basic. Można nawet utworzyć własne obiekty i zdefiniować dla nich dodatkowe właściwości i metody. Obiekty takie jak prefabrykowane bloki konstrukcyjne dla programów — umożliwiają pisanie fragmentu kodu raz i wielokrotne używanie go.

W tym temacie omówiono obiekty szczegółowo.

## <a name="objects-and-classes"></a>Obiekty i klasy

Każdy obiekt w Visual Basic jest zdefiniowany przez *klasę*. Klasa opisuje zmienne, właściwości, procedury i zdarzenia obiektu. Obiekty są wystąpieniami klas; można utworzyć dowolną liczbę obiektów, które są potrzebne po zdefiniowaniu klasy.

Aby zrozumieć relacje między obiektem a jego klasą, należy wziąć pod uwagę, że pliki cookie są odcięciami i plikami cookie. Wykrajarki plik cookie jest klasą. Definiuje on cechy poszczególnych plików cookie, na przykład rozmiar i kształt. Klasa jest używana do tworzenia obiektów. Obiekty są plikami cookie.

Należy utworzyć obiekt, aby można było uzyskać dostęp do jego członków, z wyjątkiem [`Shared`](../../../language-reference/modifiers/shared.md) elementów członkowskich, do których można uzyskać dostęp bez obiektu klasy.

### <a name="create-an-object-from-a-class"></a>Utwórz obiekt z klasy

1. Ustal, z której klasy chcesz utworzyć obiekt, lub Zdefiniuj własną klasę. Przykład:

   ```vb
   Public Class Customer
       Public Property AccountNumber As Integer
   End Class
   ```

2. Napisz [instrukcję Dim](../../../language-reference/statements/dim-statement.md) , aby utworzyć zmienną, do której można przypisać wystąpienie klasy. Zmienna powinna być typu żądanej klasy.

   ```vb
   Dim nextCustomer As Customer
   ```

3. Dodaj słowo kluczowe [new operatora](../../../language-reference/operators/new-operator.md) , aby zainicjować zmienną do nowego wystąpienia klasy.

   ```vb
   Dim nextCustomer As New Customer
   ```

4. Teraz możesz uzyskiwać dostęp do elementów członkowskich klasy za pomocą zmiennej obiektu.

   ```vb
   nextCustomer.AccountNumber = lastAccountNumber + 1
   ```

> [!NOTE]
> Jeśli to możliwe, należy zadeklarować zmienną jako typ klasy, która ma zostać przypisana do niej. Nazywa się to *wczesnym wiązaniem*. Jeśli nie znasz typu klasy w czasie kompilacji, możesz wywołać *późne wiązanie* przez zadeklarowanie zmiennej jako [typu danych obiektu](../../../language-reference/data-types/object-data-type.md). Jednak późne wiązanie może zwiększyć wydajność i ograniczyć dostęp do elementów członkowskich obiektu czasu wykonywania. Aby uzyskać więcej informacji, zobacz [Deklaracja zmiennej obiektu](../variables/object-variable-declaration.md).

### <a name="multiple-instances"></a>Wiele wystąpień

Obiekty nowo utworzone na podstawie klasy są często takie same. Gdy istnieją one jako pojedyncze obiekty, można jednak zmienić ich zmienne i właściwości niezależnie od innych wystąpień. Na przykład jeśli dodasz trzy pola wyboru do formularza, każdy obiekt pola wyboru jest wystąpieniem <xref:System.Windows.Forms.CheckBox> klasy. Poszczególne <xref:System.Windows.Forms.CheckBox> obiekty mają wspólny zestaw cech i funkcji (właściwości, zmienne, procedury i zdarzenia) zdefiniowane przez klasę. Jednak każda z nich ma własną nazwę, może być oddzielnie włączona i wyłączona i może być umieszczona w innej lokalizacji w formularzu.

## <a name="object-members"></a>Elementy członkowskie obiektów

Obiekt jest elementem aplikacji, reprezentującym *wystąpienie* klasy. Pola, właściwości, metody i zdarzenia są blokami konstrukcyjnymi obiektów i stanowią ich *składowe*.

### <a name="member-access"></a>Dostęp do elementu członkowskiego

Użytkownik uzyskuje dostęp do elementu członkowskiego obiektu przez określenie w kolejności nazwy zmiennej obiektu, kropki ( `.` ) i nazwy elementu członkowskiego. Poniższy przykład ustawia <xref:System.Windows.Forms.Control.Text%2A> Właściwość <xref:System.Windows.Forms.Label> obiektu.

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a>Lista elementów członkowskich IntelliSense

Funkcja IntelliSense wyświetla listę elementów członkowskich klasy po wywołaniu opcji członków listy, na przykład podczas wpisywania kropki ( `.` ) jako operatora dostępu do elementów członkowskich. Jeśli wpiszesz kropkę po nazwie zmiennej zadeklarowanej jako wystąpienie tej klasy, IntelliSense wyświetla wszystkie elementy członkowskie wystąpienia i żaden z udostępnionych elementów członkowskich. Jeśli wpiszesz kropkę po samej nazwie klasy, IntelliSense wyświetla wszystkie udostępnione elementy członkowskie i żaden z elementów członkowskich wystąpienia. Aby uzyskać więcej informacji, zobacz [Korzystanie z funkcji IntelliSense](/visualstudio/ide/using-intellisense).

### <a name="fields-and-properties"></a>Pola i właściwości

*Pola* i *Właściwości* reprezentują informacje przechowywane w obiekcie. Pobieranie i ustawianie wartości przy użyciu instrukcji przypisania w taki sam sposób, jak pobieranie i Ustawianie zmiennych lokalnych w procedurze. Poniższy przykład pobiera <xref:System.Windows.Forms.Control.Width%2A> Właściwość i ustawia <xref:System.Windows.Forms.Control.ForeColor%2A> Właściwość <xref:System.Windows.Forms.Label> obiektu.

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

Należy zauważyć, że pole jest również nazywane *zmienną członkowską*.

Użyj procedur właściwości, gdy:

- Należy określić, kiedy i w jaki sposób ma być ustawiona lub pobrana wartość.

- Właściwość zawiera dobrze zdefiniowany zestaw wartości, które muszą zostać sprawdzone.

- Ustawienie wartości powoduje pewne zauważalne zmiany stanu obiektu, takie jak `IsVisible` Właściwość.

- Ustawienie właściwości powoduje zmianę innych zmiennych wewnętrznych lub wartości innych właściwości.

- Przed ustawieniem lub pobraniem właściwości należy wykonać zestaw kroków.

Użyj pól w przypadku:

- Wartość jest typu samowalidacji. Na przykład błąd lub Automatyczna konwersja danych występuje, jeśli wartość inna niż `True` lub `False` jest przypisana do `Boolean` zmiennej.

- Dowolna wartość z zakresu obsługiwanego przez typ danych jest prawidłowa. Jest to prawdziwe w przypadku wielu właściwości typu `Single` lub `Double` .

- Właściwość jest `String` typem danych i nie ma żadnego ograniczenia dotyczącego rozmiaru lub wartości ciągu.

- Aby uzyskać więcej informacji, zobacz [procedury właściwości](../procedures/property-procedures.md).

> [!TIP]
> Zawsze zachowuj prywatne pola niestałe. Jeśli chcesz, aby był on publiczny, zamiast tego użyj właściwości.

### <a name="methods"></a>Metody

*Metoda* jest akcją, którą obiekt może wykonać. Na przykład, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> jest metodą <xref:System.Windows.Forms.ComboBox> obiektu, który dodaje nowy wpis do pola kombi.

Poniższy przykład ilustruje <xref:System.Windows.Forms.Timer.Start%2A> metodę <xref:System.Windows.Forms.Timer> obiektu.

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

Należy pamiętać, że metoda jest po prostu *procedurą* , która jest udostępniana przez obiekt.

Aby uzyskać więcej informacji, zobacz [procedur](../procedures/index.md).

### <a name="events"></a>Zdarzenia

Zdarzenie jest akcją rozpoznawaną przez obiekt, taką jak kliknięcie myszą lub naciśnięcie klawisza, dla którego można napisać kod, aby odpowiedzieć. Zdarzenia mogą wystąpić w wyniku działania użytkownika lub kodu programu albo mogą być spowodowane przez system. Kod, który sygnalizuje zdarzenie, jest wywoływany *w celu* *podniesienia* zdarzenia, a kod, który odpowiada na ten komunikat, jest nazywany.

Możesz również opracować własne zdarzenia niestandardowe, które mają być zgłaszane przez obiekty i obsługiwane przez inne obiekty. Aby uzyskać więcej informacji, zobacz [zdarzenia](../events/index.md).

### <a name="instance-members-and-shared-members"></a>Elementy członkowskie wystąpienia i udostępnione elementy członkowskie

Gdy tworzysz obiekt z klasy, wynikiem jest wystąpienie tej klasy. Elementy członkowskie, które nie są zadeklarowane za pomocą słowa kluczowego [Shared](../../../language-reference/modifiers/shared.md) , są *elementami członkowskimi wystąpień*, które należą do tego konkretnego wystąpienia. Element członkowski wystąpienia w jednym wystąpieniu jest niezależny od tego samego elementu członkowskiego w innym wystąpieniu tej samej klasy. Zmienna elementu członkowskiego wystąpienia może na przykład mieć różne wartości w różnych wystąpieniach.

Składowe zadeklarowane za pomocą `Shared` słowa kluczowego są *udostępnionymi elementami członkowskimi*, które należą do klasy jako całości, a nie do żadnego konkretnego wystąpienia. Współużytkowany element członkowski istnieje tylko raz, niezależnie od tego, ile wystąpień klasy tworzysz, lub nawet wtedy, gdy nie utworzysz żadnych wystąpień. Współdzielona zmienna członkowska na przykład ma tylko jedną wartość, która jest dostępna dla wszystkich kodów, które mogą uzyskać dostęp do klasy.

#### <a name="accessing-non-shared-members"></a>Uzyskiwanie dostępu do nieudostępnionych elementów członkowskich

1. Upewnij się, że obiekt został utworzony z klasy i przypisany do zmiennej obiektu.

   ```vb
   Dim secondForm As New System.Windows.Forms.Form
   ```

2. W instrukcji, która uzyskuje dostęp do elementu członkowskiego, postępuj według nazwy zmiennej obiektu z *operatorem dostępu do elementu członkowskiego* ( `.` ), a następnie nazwą elementu członkowskiego.

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a>Uzyskiwanie dostępu do udostępnionych członków

- Postępuj według nazwy klasy z *operatorem dostępu do elementów członkowskich* ( `.` ), a następnie nazwą elementu członkowskiego. Zawsze należy uzyskiwać dostęp do `Shared` elementu członkowskiego obiektu bezpośrednio za pomocą nazwy klasy.

   ```vb
   Console.WriteLine("This computer is called " & Environment.MachineName)
   ```

- Jeśli utworzono już obiekt z klasy, możesz alternatywnie uzyskać dostęp do `Shared` elementu członkowskiego za pośrednictwem zmiennej obiektu.

### <a name="differences-between-classes-and-modules"></a>Różnice między klasami i modułami

Główną różnicą między klasami i modułami jest to, że klasy mogą być tworzone jako obiekty, gdy nie mogą być używane w standardowym module. Ponieważ istnieje tylko jedna kopia danych modułu standardowego, gdy jedna część programu zmienia zmienną publiczną w module standardowym, każda inna część programu pobiera tę samą wartość, jeśli następnie odczytuje tę zmienną. Z kolei dane obiektów istnieją osobno dla każdego obiektu, który tworzy wystąpienie. Kolejną różnicą jest to, że w przeciwieństwie do modułów standardowych klasy mogą implementować interfejsy. Jeśli klasa jest oznaczona za pomocą modyfikatora [MustInherit](../../../language-reference/modifiers/mustinherit.md) , nie można jej utworzyć bezpośrednio. Jednak nadal różni się od modułu, ponieważ może być dziedziczony, podczas gdy moduły nie mogą być dziedziczone.

> [!NOTE]
> Gdy `Shared` modyfikator zostanie zastosowany do elementu członkowskiego klasy, jest on kojarzony z samą klasą, a nie z konkretnym wystąpieniem klasy. Dostęp do elementu członkowskiego uzyskuje się bezpośrednio przy użyciu nazwy klasy, w taki sam sposób, jak członkowie modułów są dostępni.

Klasy i moduły również używają różnych zakresów dla ich członków. Elementy członkowskie zdefiniowane w klasie są objęte zakresem określonego wystąpienia klasy i istnieją tylko dla okresu istnienia obiektu. Aby uzyskać dostęp do składowych klasy spoza klasy, należy użyć w pełni kwalifikowanych nazw w formacie *obiektu*. *Element członkowski*.

Z drugiej strony członkowie zadeklarowani w module są publicznie dostępni domyślnie i dostęp do niego można uzyskać za pomocą dowolnego kodu, który może uzyskać dostęp do modułu. Oznacza to, że zmienne w module standardowym są efektywnie zmiennymi globalnymi, ponieważ są widoczne z dowolnego miejsca w projekcie i istnieją w okresie istnienia programu.

## <a name="reusing-classes-and-objects"></a>Używanie klas i obiektów

Obiekty umożliwiają deklarowanie zmiennych i procedur jednokrotnie, a następnie ponowne używanie ich w razie konieczności. Na przykład, jeśli chcesz dodać do aplikacji moduł sprawdzania pisowni, możesz zdefiniować wszystkie zmienne i funkcje obsługi, aby zapewnić funkcje sprawdzania pisowni. Jeśli tworzysz moduł sprawdzania pisowni jako klasę, możesz użyć go ponownie w innych aplikacjach przez dodanie odwołania do skompilowanego zestawu. Jeszcze lepszym rozwiązaniem może być Oszczędność pracy przy użyciu klasy sprawdzania pisowni, która została już opracowana przez kogoś innego.

Platforma .NET zawiera wiele przykładów składników, które są dostępne do użycia. Poniższy przykład używa <xref:System.TimeZone> klasy w <xref:System> przestrzeni nazw. <xref:System.TimeZone>zawiera elementy członkowskie, które umożliwiają pobieranie informacji o strefie czasowej bieżącego systemu komputerowego.

```vb
Public Sub ExamineTimeZone()
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone
    Dim s As String = "Current time zone is "
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "
    s &= "different from UTC (coordinated universal time)"
    s &= vbCrLf & "and is currently "
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "
    s &= "on ""summer time""."
    Console.WriteLine(s)
End Sub
```

W poprzednim przykładzie, pierwsza [instrukcja Dim](../../../language-reference/statements/dim-statement.md) deklaruje zmienną obiektu typu <xref:System.TimeZone> i przypisuje do niego <xref:System.TimeZone> obiekt zwracany przez <xref:System.TimeZone.CurrentTimeZone%2A> Właściwość.

## <a name="relationships-among-objects"></a>Relacje między obiektami

Obiekty mogą być ze sobą powiązane na kilka sposobów. Główne rodzaje relacji są *hierarchiczne* i *zawiera*.

### <a name="hierarchical-relationship"></a>Relacja hierarchiczna

Gdy klasy są wyprowadzane z bardziej podstawowych klas, są one określane jako *relacje hierarchiczne*. Hierarchie klas są przydatne podczas opisywania elementów będących podtypem klasy bardziej ogólnej.

W poniższym przykładzie Załóżmy, że chcesz zdefiniować specjalny rodzaj <xref:System.Windows.Forms.Button> , który działa jak normalny, <xref:System.Windows.Forms.Button> ale również udostępnia metodę, która odwraca kolory pierwszego planu i tła.

#### <a name="define-a-class-that-is-derived-from-an-already-existing-class"></a>Zdefiniuj klasę pochodną już istniejącej klasy

1. Użyj [instrukcji klasy](../../../language-reference/statements/class-statement.md) , aby zdefiniować klasę, z której ma być tworzony obiekt.

   ```vb
   Public Class ReversibleButton
   ```

   Upewnij się, że `End Class` instrukcja jest zgodna z ostatnim wierszem kodu w klasie. Domyślnie zintegrowane środowisko programistyczne (IDE) automatycznie generuje `End Class` po wprowadzeniu `Class` instrukcji.

2. Wykonaj `Class` instrukcję natychmiast, używając [instrukcji Inherits](../../../language-reference/statements/inherits-statement.md). Określ klasę, z której pochodzi nowa klasa.

   ```vb
   Inherits System.Windows.Forms.Button
   ```

   Nowa klasa dziedziczy wszystkie elementy członkowskie zdefiniowane przez klasę bazową.

3. Dodaj kod dla dodatkowych elementów członkowskich udostępnianej przez klasę pochodną. Na przykład możesz dodać `ReverseColors` metodę, a Klasa pochodna może wyglądać następująco:

   ```vb
   Public Class ReversibleButton
       Inherits System.Windows.Forms.Button
           Public Sub ReverseColors()
               Dim saveColor As System.Drawing.Color = Me.BackColor
               Me.BackColor = Me.ForeColor
               Me.ForeColor = saveColor
          End Sub
   End Class
   ```

   Jeśli utworzysz obiekt z `ReversibleButton` klasy, będzie on miał dostęp do wszystkich elementów członkowskich <xref:System.Windows.Forms.Button> klasy, a także do `ReverseColors` metody i innych nowych elementów członkowskich, które definiujesz w `ReversibleButton` .

Klasy pochodne dziedziczą elementy członkowskie z klasy, na której bazują, co pozwala na dodawanie złożoności w miarę postępu w hierarchii klas. Aby uzyskać więcej informacji, zobacz podstawowe informacje o [dziedziczeniu](inheritance-basics.md).

### <a name="compile-the-code"></a>Kompiluj kod

Upewnij się, że kompilator ma dostęp do klasy, z której zamierzasz utworzyć nową klasę. Może to oznaczać, że w pełni kwalifikuje swoją nazwę, tak jak w poprzednim przykładzie, lub identyfikując jej przestrzeń nazw w [instrukcji Imports (przestrzeń nazw i typ platformy .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md). Jeśli Klasa znajduje się w innym projekcie, może być konieczne dodanie odwołania do tego projektu. Aby uzyskać więcej informacji, zobacz [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project).

### <a name="containment-relationship"></a>Relacja zawierania

Innym sposobem, w jaki obiekty mogą być powiązane, jest *relacja zawierania*. Obiekty kontenera logicznie hermetyzują inne obiekty. Na przykład <xref:System.OperatingSystem> obiekt logicznie zawiera <xref:System.Version> obiekt, który zwraca za pomocą jego <xref:System.OperatingSystem.Version%2A> właściwości. Należy zauważyć, że obiekt kontenera nie zawiera fizycznie żadnego innego obiektu.

#### <a name="collections"></a>Kolekcje

Jeden określony typ obiektu jest reprezentowany przez *kolekcje*. Kolekcje są grupami podobnych obiektów, które można wyliczyć. Visual Basic obsługuje określoną składnię w instrukcji [for each... Następna instrukcja](../../../language-reference/statements/for-each-next-statement.md) , która pozwala na iterację elementów kolekcji. Ponadto kolekcje często umożliwiają <xref:Microsoft.VisualBasic.Collection.Item%2A> Pobieranie elementów według ich indeksu lub kojarzenie ich z unikatowym ciągiem. Kolekcje mogą być łatwiejsze w użyciu niż tablice, ponieważ umożliwiają dodawanie lub usuwanie elementów bez użycia indeksów. Ze względu na łatwość użytkowania kolekcje są często używane do przechowywania formularzy i kontrolek.

## <a name="related-topics"></a>Powiązane tematy

[Wskazówki: Definiowanie klas](walkthrough-defining-classes.md)\
Zawiera opis krok po kroku dotyczący sposobu tworzenia klasy.

[Przeciążone właściwości i metody](overloaded-properties-and-methods.md)\
Przeciążone właściwości i metody

[Podstawowe informacje o dziedziczeniu](inheritance-basics.md)\
Obejmuje Modyfikatory dziedziczenia, zastępowanie metod i właściwości, MyClass i webbase.

[Okres istnienia obiektu: sposób tworzenia i zniszczenia obiektów](object-lifetime-how-objects-are-created-and-destroyed.md)\
Omawia tworzenie i usuwanie wystąpień klas.

[Typy anonimowe](anonymous-types.md)\
Opisuje sposób tworzenia i używania typów anonimowych, które umożliwiają tworzenie obiektów bez konieczności pisania definicji klasy dla typu danych.

[Inicjatory obiektów: typy nazwane i anonimowe](object-initializers-named-and-anonymous-types.md)\
Omawia Inicjatory obiektów, które są używane do tworzenia wystąpień nazwanych i anonimowych typów przy użyciu jednego wyrażenia.

[Instrukcje: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)\
Wyjaśnia, w jaki sposób można wywnioskować nazwy właściwości i typy w deklaracjach typu anonimowego. Zawiera przykłady udanych i nieudanych wnioskowania.
