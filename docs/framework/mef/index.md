---
title: Managed Extensibility Framework (MEF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Managed Extensibility Framework, overview
- MEF, overview
ms.assetid: 6c61b4ec-c6df-4651-80f1-4854f8b14dde
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fa91b6f2866ba2dee6963d7258fe193ce058f61
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457183"
---
# <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)

Ten temat zawiera omówienie Managed Extensibility Framework, która została wprowadzona w programie .NET Framework 4.

<a name="what_is_mef"></a>
## <a name="what-is-mef"></a>Co to jest MEF?

Managed Extensibility Framework lub MEF to biblioteka do tworzenia aplikacji niewielka, rozszerzalna. Umożliwia deweloperom wykrywanie i używanie rozszerzeń, bez konieczności konfiguracji. Ponadto pozwala on deweloperzy rozszerzenia łatwo hermetyzacji kodu i uniknąć delikatna twardych zależności. MEF umożliwia nie tylko rozszerzenia, które mają być ponownie używane w aplikacjach, ale także aplikacjach.

<a name="the_problem_of_extensibility"></a>
## <a name="the-problem-of-extensibility"></a>Problem rozszerzalności
 Wyobraź sobie, czy architekta dużych aplikacji, które muszą obsługiwać rozszerzalności. Aplikacja musi zawierać potencjalnie dużą liczbę mniejszych składników i jest odpowiedzialny za tworzenie i uruchamianie ich.

 Najprostsza metoda tego problemu jest zawiera składniki jako kod źródłowy w aplikacji, a następnie wywołaj je bezpośrednio w kodzie. Ma to liczbę widocznych wady. Co najważniejsze nie można dodać nowych składników, bez konieczności modyfikowania kodu źródłowego, ograniczenia, która może być niedopuszczalne w, na przykład aplikacji sieci Web, ale jest niedziałającym w aplikacji klienckiej. Równie problematyczne, możesz nie mieć dostępu do kodu źródłowego, składników, ponieważ może być opracowane przez strony trzecie, a nie zezwala na Twój dostęp do tego samego powodu.

 Nieco bardziej wyszukane metody, byłoby punktu rozszerzenia lub interfejsu, aby zezwolić na oddzielenie między aplikacją i jej składniki. W tym modelu można określić interfejs, który można wdrożyć składnika i interfejs API, aby umożliwić interakcję z aplikacją. To rozwiązuje problem konieczności stosowania dostęp do kodu źródłowego, ale nadal ma swój własny trudności.

 Ponieważ aplikacja nie jest w stanie wszelkich odnajdywania składników samodzielnie, jego musi nadal dowiedzieć się, jawnie składniki, które są dostępne i powinna być załadowany. Zazwyczaj jest to osiągane przez jawnie rejestrowanie dostępne składniki w pliku konfiguracji. Oznacza to, że zapewnienia, że składniki są poprawne staje się konserwacyjne, szczególnie w przypadku, gdy użytkownik końcowy i nie Deweloper, który oczekuje się, czy aktualizację.

 Ponadto składniki mają tradycyjnej możliwości komunikowania się ze sobą, z wyjątkiem za pośrednictwem sztywno określonych kanałów samej aplikacji. Jeśli Architekt aplikacji nie ma oczekiwać konieczności w celu komunikacji, jest zazwyczaj niemożliwe.

 Ponadto deweloperzy składników musi zaakceptować twardych zależności, w jaki zestaw zawiera interfejs, które implementują. Utrudnia składnik, który ma być używany w więcej niż jedną aplikację, a można również tworzyć problemy podczas tworzenia platformę testową dla składników.

<a name="what_mef_provides"></a>
## <a name="what-mef-provides"></a>Udostępnia MEF
 Zamiast tego jawna rejestracja dostępne składniki MEF umożliwia ich wykrycie, niejawnie, przy użyciu *kompozycji*. Składnik MEF, o nazwie *część*, w sposób deklaratywny określa zarówno z jego zależności (nazywane *importuje*) i jakie funkcje (nazywane *eksportuje*) dostępnych. Gdy element zostanie utworzony, aparat składu MEF spełnia jego importów z tym, co dostępne z innych części.

 To podejście rozwiązuje problemy z opisanych w poprzedniej sekcji. Ponieważ części MEF deklaratywne określenie ich możliwości, są one wykrywalne w czasie wykonywania, co oznacza, że aplikacja może wprowadzać Użyj części bez zakodowanych odwołań i plików konfiguracyjnych słabe. MEF umożliwia aplikacjom odnaleźć i sprawdź elementy według ich metadanych bez tworzenia wystąpienia je lub nawet ładowania ich zestawów. W rezultacie nie ma potrzeby dokładnie określić, kiedy i jak można załadować rozszerzenia.

 Oprócz jego podana eksportuje element można określić jego importów, które zostaną wypełnione w innych częściach. To sprawia, że komunikacja między części nie tylko to możliwe, ale dzieje się tak proste i umożliwia dobre wyprowadzenie kodu. Na przykład wspólne dla wielu składników usług można być brana pod uwagę w osobnym obszarze i łatwo zmodyfikowane lub zastąpione.

 Ponieważ MEF model wymaga niezależne twarde w zestawie konkretnej aplikacji, umożliwia rozszerzenia, które mają zostać ponownie użyte z aplikacji do aplikacji. To ułatwia także do tworzenia kontroler testów, niezależnie od aplikacji, aby przetestować rozszerzenie składników.

 Rozszerzalne aplikacji napisanej za pomocą MEF deklaruje importu mogą zostać uzupełnione przez składniki rozszerzenia, która również może zadeklarować eksportuje w celu udostępnienia usługami aplikacji w celu rozszerzenia. Każdy składnik rozszerzenia deklaruje eksportu i może również zadeklarować importów. W ten sposób samych elementów rozszerzenia są automatycznie rozszerzonego.

<a name="where_is_mef_available"></a>
## <a name="where-is-mef-available"></a>Gdzie jest MEF?
 MEF jest integralną częścią programu .NET Framework 4 i jest dostępna wszędzie tam, gdzie .NET Framework jest używany. W aplikacjach klienckich można użyć MEF, używają Windows Forms, WPF i innych technologii, czy w aplikacji serwera, które używają platformy ASP.NET.

<a name="mef_and_maf"></a>
## <a name="mef-and-maf"></a>MEF i MAF
 Poprzednie wersje programu .NET Framework wprowadzono zarządzane dodatku Framework (MAF), który umożliwia aplikacji, aby izolować i zarządzać rozszerzeniami. MAF koncentruje się nieco wyższym poziomie niż MEF i skoncentrowanie się na rozszerzenie izolacji i ładowanie zestawów i wyładowywanie, podczas gdy firmy MEF koncentruje się na możliwości odnajdywania, rozszerzalność i przenośność. Dwie struktury współdziałania sprawnie, a pojedynczą aplikacją korzystać z zalet obu.

<a name="simplecalculator_an_example_application"></a>

## <a name="simplecalculator-an-example-application"></a>SimpleCalculator: Przykładowa aplikacja

Najprostszym sposobem, aby zobaczyć, co można zrobić MEF jest tworzenie prostej aplikacji MEF. W tym przykładzie utworzysz bardzo prosty kalkulator, o nazwie SimpleCalculator. Celem SimpleCalculator jest, aby utworzyć aplikację konsolową, która akceptuje podstawowe polecenia arytmetyczne, w postaci "5 + 3" lub "6-2" i zwraca poprawnych odpowiedzi. Za pomocą MEF, będziesz mieć możliwość dodawania nowych operatorów bez konieczności zmieniania kodu aplikacji.

Aby pobrać kompletny kod dla tego przykładu, zobacz [przykładowe SimpleCalculator](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).

> [!NOTE]
> Celem SimpleCalculator jest, aby zademonstrować pojęć i składnia MEF, a nie zapewnienie niekoniecznie realistyczny scenariusz, w ramach jego użycia. Wiele aplikacji, które będą korzystać z najbardziej z możliwości MEF jest bardziej skomplikowane niż SimpleCalculator. Aby bardziej rozległe przykładów, zobacz [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) w witrynie GitHub.

- Aby rozpocząć, w programie Visual Studio Utwórz nowy projekt aplikacji konsoli i nadaj mu nazwę `SimpleCalculator`.

- Dodaj odwołanie do zestawu System.ComponentModel.Composition, w którym znajduje się MEF.

- Otwórz Module1.vb lub plik Program.cs i Dodaj `Imports` lub `using` instrukcji dla elementy System.ComponentModel.Composition i System.ComponentModel.Composition.Hosting. Te dwie przestrzenie nazw zawierają typy MEF, konieczne będzie tworzenie aplikacji rozszerzalnej.

- Jeśli używasz języka Visual Basic, Dodaj `Public` — słowo kluczowe do wiersza, który deklaruje `Module1` modułu.

<a name="composition_container_and_catalogs"></a>

## <a name="composition-container-and-catalogs"></a>Kontener kompozycji i katalogi

Podstawowy model kompozycji MEF jest *pojemnik składu*, który zawiera wszystkie elementy i wykonuje kompozycji. Kompozycja działa dopasowywania importów do eksportu. Najczęściej spotykanym typem kontener kompozycji jest <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, i użyjesz to SimpleCalculator.

Jeśli używasz języka Visual Basic w Module1.vb, Dodaj klasę publiczną, o nazwie `Program`.

Dodaj następujący wiersz do `Program` klasy Module1.vb lub plik Program.cs:

```vb
Dim _container As CompositionContainer
```

```csharp
private CompositionContainer _container;
```

Aby odnaleźć elementy dostępne do niego kontenery kompozycji sprawia, że użycie *katalogu*. Wykaz jest obiektem, który sprawia, że dostępne elementy wykryte z określonego źródła. MEF zawiera katalogi, aby odnaleźć składniki Report Part z podany typ, zespół lub katalog. Deweloperzy aplikacji można łatwo tworzyć nowe katalogi do odnajdywania składniki Report Part z innych źródeł, takich jak usługi sieci Web.

Dodaj następującego konstruktora do `Program` klasy:

```vb
Public Sub New()
    'An aggregate catalog that combines multiple catalogs
     Dim catalog = New AggregateCatalog()

    'Adds all the parts found in the same assembly as the Program class
    catalog.Catalogs.Add(New AssemblyCatalog(GetType(Program).Assembly))

    'Create the CompositionContainer with the parts in the catalog
    _container = New CompositionContainer(catalog)

    'Fill the imports of this object
    Try
        _container.ComposeParts(Me)
    Catch ex As Exception
        Console.WriteLine(ex.ToString)
    End Try
End Sub
```

```csharp
private Program()
{
    //An aggregate catalog that combines multiple catalogs
    var catalog = new AggregateCatalog();
    //Adds all the parts found in the same assembly as the Program class
    catalog.Catalogs.Add(new AssemblyCatalog(typeof(Program).Assembly));

    //Create the CompositionContainer with the parts in the catalog
    _container = new CompositionContainer(catalog);

    //Fill the imports of this object
    try
    {
        this._container.ComposeParts(this);
    }
    catch (CompositionException compositionException)
    {
        Console.WriteLine(compositionException.ToString());
   }
}
```

Wywołanie <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> informuje tworzą zbiór części, w tym przypadku kontener kompozycji bieżące wystąpienie `Program`. W tym momencie jednak nic się nie stanie, ponieważ `Program` ma żadnych importów do wypełnienia.

<a name="imports_and_exports_with_attributes"></a>
## <a name="imports-and-exports-with-attributes"></a>Przywozu i wywozu za pomocą atrybutów
 Po pierwsze, masz `Program` zaimportować Kalkulator. Dzięki temu rozdzielenie użytkownika dotyczy interfejsu, takich jak konsola przychodzących i wychodzących, które zostaną umieszczone w `Program`, od logiki kalkulatora.

 Dodaj następujący kod do `Program` klasy:

```vb
<Import(GetType(ICalculator))>
Public Property calculator As ICalculator
```

```csharp
[Import(typeof(ICalculator))]
public ICalculator calculator;
```

 Należy zauważyć, że deklaracja `calculator` obiektu nie jest niczym niezwykłym, ale ma ona <xref:System.ComponentModel.Composition.ImportAttribute> atrybutu. Ten atrybut deklaruje ważne importu; oznacza to, że zostaną wprowadzone przez aparat kompozycji podczas składa się obiekt.

 Każdego importu ma *kontraktu*, która określa, jakie eksporty będzie porównywany z. Kontrakt może być jawnie określony ciąg lub mogą być automatycznie generowane przez MEF danego typu, w tym przypadku interfejs `ICalculator`. Wszelkie eksportu zadeklarowane za pomocą dopasowywania kontraktu zostanie spełnienia tego importu. Należy pamiętać, że podczas typ `calculator` obiekt jest w rzeczywistości `ICalculator`, nie jest to wymagane. Kontrakt jest niezależna od typu obiektu importowania. (W tym przypadku można pozostawisz `typeof(ICalculator)`. MEF automatycznie przyjmie kontraktu była oparta na typ importu, chyba że wyraźnie określono.)

 Dodaj to bardzo prosty interfejs do modułu lub `SimpleCalculator` przestrzeni nazw:

```vb
Public Interface ICalculator
    Function Calculate(ByVal input As String) As String
End Interface
```

```csharp
public interface ICalculator
{
    String Calculate(String input);
}
```

 Skoro zdefiniowano `ICalculator`, potrzebujesz klasę, która implementuje go. Dodaj poniższą klasę do modułu lub `SimpleCalculator` przestrzeni nazw:

```vb
<Export(GetType(ICalculator))>
Public Class MySimpleCalculator
   Implements ICalculator

End Class
```

```csharp
[Export(typeof(ICalculator))]
class MySimpleCalculator : ICalculator
{

}
```

 Oto eksportu, które będą zgodne importu w `Program`. Eksport do dopasowania importu, eksportu musi mieć ten sam kontrakt. Eksportowanie w ramach umowy na podstawie `typeof(MySimpleCalculator)` dałby w efekcie niezgodności i importowania nie będą wypełnione; kontrakt musi dokładnie pasować.

 Ponieważ kontener kompozycji zostanie wypełniony ze wszystkimi częściami dostępne w tym zestawie `MySimpleCalculator` część będą dostępne. Podczas konstruktora dla `Program` wykonuje kompozycji `Program` obiekt i jego importu będzie wypełniona `MySimpleCalculator` obiektu, który zostanie utworzony w tym celu.

 Warstwa interfejsu użytkownika (`Program`) nie musi wiedzieć niczego else. Pozostała część logika interfejsu użytkownika w związku z tym można wypełnić `Main` metody.

 Dodaj następujący kod do `Main` metody:

```vb
Sub Main()
    Dim p As New Program()
    Dim s As String
    Console.WriteLine("Enter Command:")
    While (True)
        s = Console.ReadLine()
        Console.WriteLine(p.calculator.Calculate(s))
    End While
End Sub
```

```csharp
static void Main(string[] args)
{
    Program p = new Program(); //Composition is performed in the constructor
    String s;
    Console.WriteLine("Enter Command:");
    while (true)
    {
        s = Console.ReadLine();
        Console.WriteLine(p.calculator.Calculate(s));
    }
}
```

 Ten kod po prostu odczytuje wiersz danych wejściowych i wywołania `Calculate` funkcji `ICalculator` w wyniku ponownie zapisuje się do konsoli. Oznacza to cały kod w `Program`. Wszystkie pozostałe pracy będzie miało miejsce, w części.

<a name="further_imports_and_importmany"></a>
## <a name="further-imports-and-importmany"></a>Dalsze przywozu i ImportMany
 Aby SimpleCalculator to rozszerzalny musi zaimportować listę operacji. Zwykłej <xref:System.ComponentModel.Composition.ImportAttribute> atrybutu jest wypełniana przez jeden i tylko jeden <xref:System.ComponentModel.Composition.ExportAttribute>. Jeśli jest więcej niż jeden dostępny, aparat składu powoduje błąd. Aby utworzyć importu, które mogą zostać uzupełnione przez dowolną liczbę eksportu, można użyć <xref:System.ComponentModel.Composition.ImportManyAttribute> atrybutu.

 Dodaj następującą właściwość operacji do `MySimpleCalculator` klasy:

```vb
<ImportMany()>
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))
```

```csharp
[ImportMany]
IEnumerable<Lazy<IOperation, IOperationData>> operations;
```

 <xref:System.Lazy%602> Typ świadczą MEF do przechowywania pośredniego odwołania do eksportu. W tym miejscu wyeksportowanego samego obiektu, możesz także uzyskać *Eksportowanie metadanych*, i informacje opisujące eksportowanego obiektu. Każdy <xref:System.Lazy%602> zawiera `IOperation` obiekt reprezentujący bieżącej operacji i `IOperationData` obiekt reprezentujący jego metadanych.

 Dodaj następujące proste interfejsy modułu lub `SimpleCalculator` przestrzeni nazw:

```vb
Public Interface IOperation
    Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer
End Interface

Public Interface IOperationData
    ReadOnly Property Symbol As Char
End Interface
```

```csharp
public interface IOperation
{
     int Operate(int left, int right);
}

public interface IOperationData
{
    Char Symbol { get; }
}
```

 W tym przypadku metadanych dla każdej operacji to symbol, który reprezentuje tej operacji, takich jak +, -, *, i tak dalej. Aby udostępnić operacja dodawania, Dodaj poniższą klasę do modułu lub `SimpleCalculator` przestrzeni nazw:

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "+"c)>
Public Class Add
    Implements IOperation

    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate
        Return left + right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '+')]
class Add: IOperation
{
    public int Operate(int left, int right)
    {
        return left + right;
    }
}
```

 <xref:System.ComponentModel.Composition.ExportAttribute> Atrybutu funkcji, tak jak poprzednio. <xref:System.ComponentModel.Composition.ExportMetadataAttribute> Atrybut dołącza metadane w postaci pary nazwa wartość, że Eksport. Gdy `Add` klasy implementuje `IOperation`, klasa, która implementuje `IOperationData` nie jest jawnie zdefiniowany. Zamiast tego klasy jest tworzone niejawnie za MEF z właściwościami na podstawie nazw metadanych pod warunkiem. (Jest to jeden z kilku sposobów dostępu do metadanych w MEF.)

 Kompozycja w MEF *cyklicznego*. Możesz jawnie składa się `Program` obiektu, który zaimportowany `ICalculator` , są typu `MySimpleCalculator`. `MySimpleCalculator`, z kolei importuje kolekcję `IOperation` obiektów i że importu zostaną wypełnione podczas `MySimpleCalculator` jest tworzony w tym samym czasie jako operacji importu `Program`. Jeśli `Add` klasy zadeklarowane dalsze importu, który zbyt musi zostać wypełniony i tak dalej. Dowolny zaimportować po lewej stronie powoduje błędu kompozycji. (Jest to możliwe, jednak do deklarowania Importy opcjonalne lub przypisać je wartościami domyślnymi.)

<a name="calculator_logic"></a>
## <a name="calculator-logic"></a>Logika Kalkulator
 Z tymi częściami w miejscu pozostaje logiki Kalkulator, sam. Dodaj następujący kod w `MySimpleCalculator` klasy do zaimplementowania `Calculate` metody:

```vb
Public Function Calculate(ByVal input As String) As String Implements ICalculator.Calculate
    Dim left, right As Integer
    Dim operation As Char
    Dim fn = FindFirstNonDigit(input) 'Finds the operator
    If fn < 0 Then
        Return "Could not parse command."
    End If
    operation = input(fn)
    Try
        left = Integer.Parse(input.Substring(0, fn))
        right = Integer.Parse(input.Substring(fn + 1))
    Catch ex As Exception
        Return "Could not parse command."
    End Try
    For Each i As Lazy(Of IOperation, IOperationData) In operations
        If i.Metadata.symbol = operation Then
            Return i.Value.Operate(left, right).ToString()
        End If
    Next
    Return "Operation not found!"
End Function
```

```csharp
public String Calculate(String input)
{
    int left;
    int right;
    Char operation;
    int fn = FindFirstNonDigit(input); //finds the operator
    if (fn < 0) return "Could not parse command.";

    try
    {
        //separate out the operands
        left = int.Parse(input.Substring(0, fn));
        right = int.Parse(input.Substring(fn + 1));
    }
    catch
    {
        return "Could not parse command.";
    }

    operation = input[fn];

    foreach (Lazy<IOperation, IOperationData> i in operations)
    {
        if (i.Metadata.Symbol.Equals(operation)) return i.Value.Operate(left, right).ToString();
    }
    return "Operation Not Found!";
}
```

 Początkowe kroki przeanalizować ciągu wejściowego do lewego i prawego argumentów i znak operatora. W `foreach` pętli, każdy członek `operations` kolekcji jest sprawdzany pod. Te obiekty są typu <xref:System.Lazy%602>, i ich wartości metadanych i eksportowanego obiektu można uzyskać dostęp za pomocą <xref:System.Lazy%602.Metadata%2A> właściwości i <xref:System.Lazy%601.Value%2A> właściwość odpowiednio. W takim przypadku `Symbol` właściwość `IOperationData` obiekt został odnaleziony do dopasowania, wywołania kalkulatora `Operate` metody `IOperation` obiektu i zwraca wynik.

 Aby wykonać kalkulatorze, potrzebne są także metody pomocnika, która zwraca pozycję pierwszego wystąpienia znaku niebędący cyfrą w ciągu. Dodaj następującą metodę pomocnika do `MySimpleCalculator` klasy:

```vb
Private Function FindFirstNonDigit(ByVal s As String) As Integer
    For i = 0 To s.Length
        If (Not (Char.IsDigit(s(i)))) Then Return i
    Next
    Return -1
End Function
```

```csharp
private int FindFirstNonDigit(String s)
{
    for (int i = 0; i < s.Length; i++)
    {
        if (!(Char.IsDigit(s[i]))) return i;
    }
    return -1;
}
```

 Teraz można skompilować i uruchomić projekt. W języku Visual Basic, upewnij się, że dodano `Public` słowa kluczowego `Module1`. W oknie konsoli typu operacji dodawania, np. "5 + 3", a Kalkulator zwraca wyniki. Wszystkie inne podmioty wynikiem "nie znaleziono operacji!" Komunikat.

<a name="extending_simplecalculator_using_a_new_class"></a>
## <a name="extending-simplecalculator-using-a-new-class"></a>Rozszerzanie SimpleCalculator przy użyciu nowej klasy
 Teraz, gdy działa Kalkulator, Dodawanie nowej operacji jest proste. Dodaj poniższą klasę do modułu lub `SimpleCalculator` przestrzeni nazw:

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "-"c)>
Public Class Subtract
    Implements IOperation

    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate
        Return left - right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '-')]
class Subtract : IOperation
{
    public int Operate(int left, int right)
    {
        return left - right;
    }
}
```

 Skompiluj i uruchom projekt. Typ operacji odejmowania, takie jak "5-3". Kalkulator obsługuje teraz odejmowania, a także dodawanie.

<a name="extending_simplecalculator_using_a_new_assembly"></a>
## <a name="extending-simplecalculator-using-a-new-assembly"></a>Rozszerzanie SimpleCalculator za pomocą nowego zestawu
 Dodawanie klas do źródła kodu jest proste, ale MEF, udostępnia możliwość wyświetlenia poza źródłem własnych aplikacji dla części. Aby to wykazać, konieczne będzie modyfikować SimpleCalculator do wyszukiwania w katalogu, a także swój własny zestaw, dla części, przez dodanie <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.

 Dodaj nowy katalog o nazwie `Extensions` do projektu SimpleCalculator. Upewnij się dodać go na poziomie projektu, a nie na poziomie rozwiązania. Następnie dodaj nowy projekt biblioteki klas w rozwiązaniu o nazwie `ExtendedOperations`. Nowy projekt zostanie skompilowany w osobnym zestawie.

 Otwórz projektanta właściwości projektu dla projektu ExtendedOperations, a następnie kliknij przycisk **skompilować** lub **kompilacji** kartę. Zmiana **ścieżkę wyjściową kompilacji** lub **ścieżkę wyjściową** wskaż katalogu rozszerzeń w katalogu projektu SimpleCalculator (.. \SimpleCalculator\Extensions\\).

 W pliku Program.cs lub Module1.vb Dodaj następujący wiersz do `Program` Konstruktor:

```vb
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))
```

```csharp
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));
```

 Przykładowa ścieżka Zamień na ścieżkę do katalogu rozszerzeń. (Jest to ścieżka bezwzględna do debugowania tylko do celów. W przypadku aplikacji produkcyjnych należy użyć ścieżki względnej.) <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> Teraz należy dodać częściami w żadnych zestawów w katalogu rozszerzeń do kontenera kompozycji.

 W projekcie ExtendedOperations dodać odwołania do SimpleCalculator i System.ComponentModel.Composition. W pliku klasy ExtendedOperations Dodaj `Imports` lub `using` poufności informacji dotyczące System.ComponentModel.Composition. W języku Visual Basic należy również dodać `Imports` poufności informacji dotyczące SimpleCalculator. Następnie dodaj poniższą klasę do pliku klasy ExtendedOperations:

```vb
<Export(GetType(SimpleCalculator.IOperation))>
<ExportMetadata("Symbol", "%"c)>
Public Class Modulo
    Implements IOperation

    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate
        Return left Mod right
    End Function
End Class
```

```csharp
[Export(typeof(SimpleCalculator.IOperation))]
[ExportMetadata("Symbol", '%')]
public class Mod : SimpleCalculator.IOperation
{
    public int Operate(int left, int right)
    {
        return left % right;
    }
}
```

 Należy pamiętać, tej w kolejności dla kontraktu dopasować, <xref:System.ComponentModel.Composition.ExportAttribute> atrybut musi mieć taki sam typ co <xref:System.ComponentModel.Composition.ImportAttribute>.

 Skompiluj i uruchom projekt. Testowanie nowych dzielenie modulo (%) operator.

<a name="conclusion"></a>
## <a name="conclusion"></a>Wniosek
 W tym temacie opisano podstawowe pojęcia dotyczące środowiska MEF.

- Części, katalogi i kontener kompozycji

     Części i kontener kompozycji są podstawowe bloki konstrukcyjne aplikacji MEF. Część jest dowolnego obiektu, który importuje i eksportuje wartość, w tym sam. Wykaz zawiera zbiór składniki Report Part z określonego źródła. Pojemnik składu używa części, dostarczone przez katalog do utworzenia, wiązanie importu do eksportu.

- Przywozu i wywozu

     Przywozu i wywozu są sposób za pomocą którego komunikacji między składnikami. Importowania składnika określa na potrzeby określonej wartości lub obiekt, a z eksportową określa dostępność wartość. Każdej operacji importowania jest dopasowany do listy eksporty za pomocą jego kontraktu.

<a name="where_do_i_go_now"></a>
## <a name="where-do-i-go-now"></a>Gdzie mogę teraz?
 Aby pobrać kompletny kod dla tego przykładu, zobacz [przykładowe SimpleCalculator](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).

 Aby uzyskać więcej informacji i przykłady kodu, zobacz [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef). Aby uzyskać listę typów MEF, zobacz <xref:System.ComponentModel.Composition?displayProperty=nameWithType> przestrzeni nazw.
