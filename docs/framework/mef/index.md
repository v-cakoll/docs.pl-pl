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
ms.openlocfilehash: da73200513d451ee391fb6dd9c214a5b8ca771c6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126348"
---
# <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)

Ten temat zawiera omówienie Managed Extensibility Framework, które zostały wprowadzone w .NET Framework 4.

<a name="what_is_mef"></a>
## <a name="what-is-mef"></a>Co to jest MEF?

Managed Extensibility Framework lub MEF to biblioteka służąca do tworzenia uproszczonych, rozszerzalnych aplikacji. Dzięki temu deweloperzy aplikacji mogą odnajdywać i używać rozszerzeń bez konieczności konfigurowania. Pozwala to również deweloperom rozszerzeń na łatwe hermetyzację kodu i uniknięcie delikatnych zależności. MEF umożliwia nie tylko używanie rozszerzeń w aplikacjach, ale również w aplikacjach.

<a name="the_problem_of_extensibility"></a>
## <a name="the-problem-of-extensibility"></a>Problem z rozszerzalnością
 Załóżmy, że jesteś architektem dużej aplikacji, która musi zapewnić obsługę rozszerzalności. Aplikacja musi zawierać potencjalnie dużą liczbę mniejszych składników i jest odpowiedzialna za tworzenie i uruchamianie ich.

 Najprostszym podejściem do problemu jest dołączenie składników jako kodu źródłowego w aplikacji i wywołanie ich bezpośrednio w kodzie. Ma to wiele oczywistych niedogodności. Co najważniejsze, nie można dodawać nowych składników bez modyfikowania kodu źródłowego, ograniczenia, które mogą być akceptowane na przykład aplikacji sieci Web, ale nie są w aplikacji klienckiej. Jednakowe problemy mogą nie mieć dostępu do kodu źródłowego składników, ponieważ mogą one być opracowywane przez inne osoby. z tego powodu nie można zezwolić na dostęp do niego.

 Nieco bardziej zaawansowaną metodą jest udostępnienie punktu rozszerzenia lub interfejsu, aby umożliwić rozdzielenie między aplikacją i jej składnikami. W ramach tego modelu można podać interfejs, który może być zaimplementowany przez składnik, oraz interfejs API umożliwiający współistnienie działania aplikacji. Rozwiązuje to problem z wymaganiem dostępu do kodu źródłowego, ale nadal ma własne problemy.

 Ze względu na to, że aplikacja nie ma żadnej pojemności do odnajdowania składników samodzielnie, nadal musi być jawnie powiadamiana, które składniki są dostępne i powinny być ładowane. Jest to zazwyczaj realizowane przez jawne zarejestrowanie składników dostępnych w pliku konfiguracji. Oznacza to, że zapewnienie, że składniki są poprawne, jest problemem konserwacji, szczególnie jeśli jest to użytkownik końcowy, a nie Deweloper, który powinien wykonać aktualizację.

 Ponadto składniki nie mogą komunikować się ze sobą, z wyjątkiem sztywno zdefiniowanych kanałów samej aplikacji. Jeśli architekt aplikacji nie przewiduje potrzeby określonej komunikacji, zwykle jest to niemożliwe.

 Na koniec Deweloperzy składników muszą akceptować twardą zależność od zestawu zawierającego interfejs, który implementuje. Utrudnia to używanie składnika w więcej niż jednej aplikacji, a także umożliwia tworzenie problemów podczas tworzenia środowiska testowego dla składników.

<a name="what_mef_provides"></a>
## <a name="what-mef-provides"></a>Co zapewnia MEF
 Zamiast tej jawnej rejestracji dostępnych składników MEF zapewnia sposób ich niejawnego wykrycia za pośrednictwem *kompozycji*. Składnik MEF, zwany *częścią*, deklaratywnie określa zarówno jego zależności (znane jako *Importy*), jak i jakie możliwości (znane jako *eksporty*) stają się dostępne. Po utworzeniu części aparat kompozycji MEF jest zgodny z tym, co jest dostępne w innych częściach.

 Takie podejście rozwiązuje problemy omówione w poprzedniej sekcji. Ze względu na to, że MEF części jednoznacznie określają ich możliwości, są wykrywalne w czasie wykonywania, co oznacza, że aplikacja może korzystać z części bez zakodowanych odwołań lub plików konfiguracji. MEF umożliwia aplikacjom odnajdywanie i sprawdzanie części według ich metadanych, bez tworzenia ich wystąpień, a nawet ładowania ich zestawów. W związku z tym nie ma potrzeby dokładnego określania, kiedy i jak powinny być ładowane rozszerzenia.

 Poza dostarczonymi eksportami, część może określać jego Importy, które będą wypełniane innymi częściami. Dzięki temu komunikacja między częściami nie jest możliwa, ale prosta i pozwala na dobre factoring kodu. Na przykład usługi wspólne dla wielu składników mogą być uwzględniane w osobnych częściach i łatwo modyfikowane lub zastępowane.

 Ponieważ model MEF nie wymaga twardej zależności od określonego zestawu aplikacji, umożliwia on używanie rozszerzeń z aplikacji do aplikacji. Ułatwia to również tworzenie zespołu testowego, niezależnego od aplikacji, do testowania składników rozszerzenia.

 Rozszerzalna aplikacja zapisywana przy użyciu MEF deklaruje import, który może być wypełniony przez składniki rozszerzenia i może również deklarować Eksporty w celu udostępnienia usług aplikacji rozszerzenia. Każdy składnik rozszerzenia deklaruje eksport i może również deklarować Importy. W ten sposób składniki rozszerzenia są automatycznie rozszerzalne.

<a name="where_is_mef_available"></a>
## <a name="where-is-mef-available"></a>Gdzie jest dostępny MEF?
 MEF jest integralną częścią .NET Framework 4 i jest dostępna wszędzie tam, gdzie .NET Framework jest używany. Możesz używać MEF w aplikacjach klienckich, niezależnie od tego, czy korzystają z Windows Forms, WPF czy innej technologii, czy też w aplikacjach serwerowych, które korzystają z ASP.NET.

<a name="mef_and_maf"></a>
## <a name="mef-and-maf"></a>MEF i
 W poprzednich wersjach .NET Framework wprowadzono zarządzaną strukturę dodatków (nr.), która umożliwia aplikacjom izolowanie rozszerzeń i zarządzanie nimi. Skoncentrowano się na nieznacznie wyższym poziomie niż MEF, skoncentrowaniu się na izolacji rozszerzeń i ładowaniu zestawu i wyładowaniu, podczas gdy MEF jest wykrywalny, rozszerzalność i przenośność. Dwie struktury współdziałają bezproblemowo, a pojedyncza aplikacja może korzystać z obu tych elementów.

<a name="simplecalculator_an_example_application"></a>

## <a name="simplecalculator-an-example-application"></a>SimpleCalculator: przykładowa aplikacja

Najprostszym sposobem, aby sprawdzić, jakie MEF może być kompilacja prostej aplikacji MEF. W tym przykładzie utworzysz prosty kalkulator o nazwie SimpleCalculator. Celem SimpleCalculator jest utworzenie aplikacji konsolowej, która akceptuje podstawowe polecenia arytmetyczne w postaci "5 + 3" lub "6-2", i zwraca poprawne odpowiedzi. Korzystając z MEF, będziesz mieć możliwość dodawania nowych operatorów bez zmiany kodu aplikacji.

Aby pobrać kompletny kod dla tego przykładu, zobacz [przykład SimpleCalculator](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).

> [!NOTE]
> Celem SimpleCalculator jest przedstawienie koncepcji i składni MEF, a nie koniecznie zapewnienia realistycznego scenariusza do użycia. Wiele aplikacji, które byłyby korzystne dla większości możliwości MEF, jest bardziej skomplikowane niż SimpleCalculator. Aby uzyskać bardziej szczegółowe przykłady, zobacz [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) w witrynie GitHub.

- Aby rozpocząć, w programie Visual Studio Utwórz nowy projekt aplikacji konsolowej i nadaj mu nazwę `SimpleCalculator`.

- Dodaj odwołanie do zestawu System. ComponentModel. kompozycji, gdzie znajduje się MEF.

- Otwórz Module1. vb lub Program.cs i Dodaj instrukcje `Imports` lub `using` dla elementu System. ComponentModel. kompozycji i system. ComponentModel. kompozycji. hosting. Te dwie przestrzenie nazw zawierają typy MEF, które będą potrzebne do opracowania rozszerzalnej aplikacji.

- Jeśli używasz Visual Basic, Dodaj słowo kluczowe `Public` do wiersza, który deklaruje moduł `Module1`.

<a name="composition_container_and_catalogs"></a>

## <a name="composition-container-and-catalogs"></a>Kontener i wykazy kompozycji

Rdzeń modelu kompozycji MEF jest *kontenerem kompozycji*, który zawiera wszystkie dostępne części i wykonuje kompozycję. Kompozycja jest zgodna z importami do eksportu. Najbardziej typowym typem kontenera kompozycji jest <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>i będzie on używany do SimpleCalculator.

Jeśli używasz Visual Basic, w Module1. vb, Dodaj klasę publiczną o nazwie `Program`.

Dodaj następujący wiersz do klasy `Program` w Module1. vb lub Program.cs:

```vb
Dim _container As CompositionContainer
```

```csharp
private CompositionContainer _container;
```

Aby można było odnaleźć dostępne dla niego części, kontenery kompozycji używają *wykazu*. Wykaz jest obiektem, który udostępnia dostępne części wykryte z niektórych źródeł. MEF udostępnia wykazy do odnajdywania części z podanego typu, zestawu lub katalogu. Deweloperzy aplikacji mogą łatwo tworzyć nowe katalogi w celu odnajdywania części z innych źródeł, takich jak usługa sieci Web.

Dodaj następujący Konstruktor do klasy `Program`:

```vb
Public Sub New()
    ' An aggregate catalog that combines multiple catalogs.
     Dim catalog = New AggregateCatalog()

    ' Adds all the parts found in the same assembly as the Program class.
    catalog.Catalogs.Add(New AssemblyCatalog(GetType(Program).Assembly))

    ' Create the CompositionContainer with the parts in the catalog.
    _container = New CompositionContainer(catalog)

    ' Fill the imports of this object.
    Try
        _container.ComposeParts(Me)
    Catch ex As CompositionException
        Console.WriteLine(ex.ToString)
    End Try
End Sub
```

```csharp
private Program()
{
    // An aggregate catalog that combines multiple catalogs.
    var catalog = new AggregateCatalog();
    // Adds all the parts found in the same assembly as the Program class.
    catalog.Catalogs.Add(new AssemblyCatalog(typeof(Program).Assembly));

    // Create the CompositionContainer with the parts in the catalog.
    _container = new CompositionContainer(catalog);

    // Fill the imports of this object.
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

Wywołanie <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> informuje kontener kompozycji o utworzeniu określonego zestawu części, w tym przypadku bieżącego wystąpienia `Program`. W tym momencie nic się nie stanie, ponieważ `Program` nie ma żadnych importów do wypełnienia.

<a name="imports_and_exports_with_attributes"></a>
## <a name="imports-and-exports-with-attributes"></a>Importy i eksporty z atrybutami
 Najpierw `Program` zaimportować Kalkulator. Dzięki temu można rozdzielić problemy związane z interfejsem użytkownika, takie jak dane wejściowe i wyjściowe konsoli, które przechodzą do `Program`, z logiki kalkulatora.

 Dodaj następujący kod do klasy `Program`:

```vb
<Import(GetType(ICalculator))>
Public Property calculator As ICalculator
```

```csharp
[Import(typeof(ICalculator))]
public ICalculator calculator;
```

 Należy zauważyć, że deklaracja obiektu `calculator` nie jest nietypowa, ale ma atrybut <xref:System.ComponentModel.Composition.ImportAttribute>. Ten atrybut deklaruje coś do zaimportowania; oznacza to, że zostanie wypełniony przez aparat kompozycji, gdy obiekt zostanie utworzony.

 Każdy import ma *umowę*, która określa, do czego eksportów będzie pasować. Kontrakt może być jawnie określonym ciągiem lub może być automatycznie generowany przez MEF z danego typu, w tym przypadku interfejs `ICalculator`. Wszystkie eksporty zadeklarowane za pomocą pasujących kontraktów zostaną spełnione. Należy zauważyć, że podczas gdy typ obiektu `calculator` jest w `ICalculator`fakt, nie jest to wymagane. Kontrakt jest niezależny od typu obiektu importującego. (W tym przypadku można opuścić `typeof(ICalculator)`. MEF automatycznie przyjmie, że kontrakt będzie oparty na typie importu, chyba że zostanie on jawnie określony.

 Dodaj ten bardzo prosty interfejs do modułu lub `SimpleCalculator` przestrzeni nazw:

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

 Teraz, gdy masz zdefiniowane `ICalculator`, potrzebujesz klasy implementującej ją. Dodaj następującą klasę do modułu lub `SimpleCalculator` przestrzeni nazw:

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

 Poniżej przedstawiono eksport, który będzie zgodny z importem w `Program`. Aby eksport był zgodny z importem, eksport musi mieć ten sam kontrakt. Eksportowanie w ramach kontraktu opartego na `typeof(MySimpleCalculator)` spowoduje niezgodność, a Importowanie nie zostanie wypełnione; kontrakt musi być dokładnie dopasowany.

 Ponieważ kontener kompozycji zostanie wypełniony wszystkimi częściami dostępnymi w tym zestawie, będzie dostępna `MySimpleCalculator` część. Gdy Konstruktor dla `Program` wykonuje kompozycję obiektu `Program`, jego import zostanie wypełniony obiektem `MySimpleCalculator`, który zostanie utworzony w tym celu.

 Warstwa interfejsu użytkownika (`Program`) nie musi wiedzieć coś innego. W związku z tym można wypełnić resztę logiki interfejsu użytkownika w metodzie `Main`.

 Dodaj następujący kod do metody `Main`:

```vb
Sub Main()
    ' Composition is performed in the constructor.
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
    // Composition is performed in the constructor.
    var p = new Program();
    String s;
    Console.WriteLine("Enter Command:");
    while (true)
    {
        s = Console.ReadLine();
        Console.WriteLine(p.calculator.Calculate(s));
    }
}
```

 Ten kod po prostu odczytuje wiersz danych wejściowych i wywołuje funkcję `Calculate` `ICalculator` w wyniku, którą zapisuje z powrotem w konsoli. To wszystko, co jest potrzebne w `Program`. Cała pozostała część pracy będzie występować w częściach.

<a name="further_imports_and_importmany"></a>
## <a name="further-imports-and-importmany"></a>Dalsze Importy i ImportMany
 Aby SimpleCalculator można było rozszerzyć, należy zaimportować listę operacji. Zwykły atrybut <xref:System.ComponentModel.Composition.ImportAttribute> jest wypełniany przez jeden i tylko jeden <xref:System.ComponentModel.Composition.ExportAttribute>. Jeśli jest dostępny więcej niż jeden, aparat kompozycji generuje błąd. Aby utworzyć import, który może zostać wypełniony przez dowolną liczbę eksportów, można użyć atrybutu <xref:System.ComponentModel.Composition.ImportManyAttribute>.

 Dodaj następującą właściwość Operations do klasy `MySimpleCalculator`:

```vb
<ImportMany()>
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))
```

```csharp
[ImportMany]
IEnumerable<Lazy<IOperation, IOperationData>> operations;
```

 <xref:System.Lazy%602> jest typem dostarczanym przez MEF do przechowywania pośrednich odwołań do eksportów. W tym miejscu oprócz wyeksportowanego obiektu można również uzyskać *metadane eksportu*lub informacje opisujące wyeksportowany obiekt. Każdy <xref:System.Lazy%602> zawiera obiekt `IOperation`, reprezentujący rzeczywistą operację i obiekt `IOperationData` reprezentujący swoje metadane.

 Dodaj następujące proste interfejsy do modułu lub `SimpleCalculator` przestrzeni nazw:

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

 W takim przypadku metadane dla każdej operacji są symbolem, który reprezentuje tę operację, taką jak +,-, * i tak dalej. Aby zapewnić dostępność operacji dodawania, Dodaj następującą klasę do modułu lub `SimpleCalculator` przestrzeni nazw:

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

 <xref:System.ComponentModel.Composition.ExportAttribute> atrybut działa jak wcześniej. Atrybut <xref:System.ComponentModel.Composition.ExportMetadataAttribute> dołącza metadane w postaci pary nazwa-wartość do tego eksportu. Chociaż Klasa `Add` implementuje `IOperation`, Klasa implementująca `IOperationData` nie jest jawnie zdefiniowana. Zamiast tego Klasa jest niejawnie tworzona przez MEF z właściwościami opartymi na nazwach dostarczonych metadanych. (Jest to jeden z kilku sposobów uzyskiwania dostępu do metadanych w MEF).

 Kompozycja w MEF jest *cykliczna*. Jawnie utworzysz obiekt `Program`, który zaimportował `ICalculator`, które wyłączyły się jako `MySimpleCalculator`. `MySimpleCalculator`, z kolei importuje kolekcję obiektów `IOperation` i że import zostanie wypełniony podczas tworzenia `MySimpleCalculator`, w tym samym czasie, co import z `Program`. Jeśli Klasa `Add` deklaruje dalsze importowanie, które nie powinny być wypełnione i tak dalej. Każdy import pozostał niewypełniony wynikami błędu kompozycji. (Istnieje jednak możliwość deklarowania importu jako opcjonalnego lub do przypisywania do nich wartości domyślnych).

<a name="calculator_logic"></a>
## <a name="calculator-logic"></a>Logika kalkulatora
 W przypadku tych części, wszystkie pozostające to logika kalkulatora. Dodaj następujący kod do klasy `MySimpleCalculator`, aby zaimplementować metodę `Calculate`:

```vb
Public Function Calculate(ByVal input As String) As String Implements ICalculator.Calculate
    Dim left, right As Integer
    Dim operation As Char
    ' Finds the operator.
    Dim fn = FindFirstNonDigit(input)
    If fn < 0 Then
        Return "Could not parse command."
    End If
    operation = input(fn)
    Try
        ' Separate out the operands.
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
    char operation;
    // Finds the operator.
    int fn = FindFirstNonDigit(input); 
    if (fn < 0) return "Could not parse command.";

    try
    {
        // Separate out the operands.
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

 Początkowe kroki analizują ciąg wejściowy do lewego i prawego operandu oraz znaku operatora. W pętli `foreach` są badane wszystkie składowe `operations` kolekcji. Te obiekty są typu <xref:System.Lazy%602>, a ich wartości metadanych i wyeksportowany obiekt są dostępne z właściwością <xref:System.Lazy%602.Metadata%2A> i właściwością <xref:System.Lazy%601.Value%2A>. W takim przypadku, jeśli właściwość `Symbol` obiektu `IOperationData` zostanie odnaleziona jako odpowiednik, kalkulator wywoła metodę `Operate` obiektu `IOperation` i zwróci wynik.

 Aby ukończyć kalkulator, należy również uzyskać metodę pomocnika zwracającą pozycję pierwszego znaku niebędącego cyfrą w ciągu. Dodaj następującą metodę pomocnika do klasy `MySimpleCalculator`:

```vb
Private Function FindFirstNonDigit(ByVal s As String) As Integer
    For i = 0 To s.Length - 1
        If (Not (Char.IsDigit(s(i)))) Then Return i
    Next
    Return -1
End Function
```

```csharp
private int FindFirstNonDigit(string s)
{
    for (int i = 0; i < s.Length; i++)
    {
        if (!(Char.IsDigit(s[i]))) return i;
    }
    return -1;
}
```

 Teraz powinno być możliwe skompilowanie i uruchomienie projektu. W Visual Basic upewnij się, że dodano słowo kluczowe `Public` do `Module1`. W oknie konsoli wpisz operację dodawania, taką jak "5 + 3", a Kalkulator zwraca wyniki. Wszystkie inne operatory mają wynik "nie znaleziono operacji!" Komunikat.

<a name="extending_simplecalculator_using_a_new_class"></a>
## <a name="extending-simplecalculator-using-a-new-class"></a>Rozszerzanie SimpleCalculator przy użyciu nowej klasy
 Teraz, gdy Kalkulator działa, Dodawanie nowej operacji jest proste. Dodaj następującą klasę do modułu lub `SimpleCalculator` przestrzeni nazw:

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

 Skompiluj i Uruchom projekt. Wpisz operację odejmowania, na przykład "5-3". Kalkulator obsługuje teraz również odejmowanie i Dodawanie.

<a name="extending_simplecalculator_using_a_new_assembly"></a>
## <a name="extending-simplecalculator-using-a-new-assembly"></a>Rozszerzanie SimpleCalculator przy użyciu nowego zestawu
 Dodawanie klas do kodu źródłowego jest wystarczająco proste, ale MEF zapewnia możliwość wyszukiwania poza źródłem części aplikacji. Aby to zademonstrować, należy zmodyfikować SimpleCalculator, aby przeszukać katalog, a także jego własny zestaw, dla części, dodając <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.

 Dodaj nowy katalog o nazwie `Extensions` do projektu SimpleCalculator. Upewnij się, że dodano ją na poziomie projektu, a nie na poziomie rozwiązania. Następnie Dodaj nowy projekt biblioteki klas do rozwiązania o nazwie `ExtendedOperations`. Nowy projekt zostanie skompilowany w osobnym zestawie.

 Otwórz projektanta właściwości projektu dla projektu ExtendedOperations, a następnie kliknij kartę **kompilacja** lub **kompilacja** . Zmień **ścieżkę wyjściową kompilacji** lub **ścieżkę wyjściową** , aby wskazywała katalog rozszerzeń w projekcie SimpleCalculator Katalog (.. \SimpleCalculator\Extensions\\).

 W Module1. vb lub Program.cs Dodaj następujący wiersz do konstruktora `Program`:

```vb
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))
```

```csharp
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));
```

 Zastąp przykładową ścieżkę ścieżką do katalogu rozszerzeń. (Ta ścieżka bezwzględna służy tylko do celów debugowania. W aplikacji produkcyjnej należy użyć ścieżki względnej. <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> doda teraz wszystkie części znajdujące się w każdym z zestawów w katalogu rozszerzeń do kontenera kompozycji.

 W projekcie ExtendedOperations Dodaj odwołania do SimpleCalculator i system. ComponentModel. kompozycji. W pliku klasy ExtendedOperations Dodaj instrukcję `Imports` lub `using` dla elementu System. ComponentModel. kompozycji. W Visual Basic Dodaj również instrukcję `Imports` dla SimpleCalculator. Następnie Dodaj następującą klasę do pliku klasy ExtendedOperations:

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

 Należy pamiętać, że w celu dopasowania kontraktu atrybut <xref:System.ComponentModel.Composition.ExportAttribute> musi mieć ten sam typ co <xref:System.ComponentModel.Composition.ImportAttribute>.

 Skompiluj i Uruchom projekt. Przetestuj nowy mod (%) zakład.

<a name="conclusion"></a>
## <a name="conclusion"></a>Wniosek
 W tym temacie omówiono podstawowe pojęcia dotyczące MEF.

- Części, wykazy i kontener kompozycji

     Części i kontener kompozycji są podstawowymi blokami konstrukcyjnymi aplikacji MEF. Część to każdy obiekt, który importuje lub eksportuje wartość, do i włącznie. Wykaz zawiera zbiór części z konkretnego źródła. Kontener kompozycji używa części dostarczonych przez wykaz do wykonywania kompozycji, powiązania importu do eksportu.

- Importy i eksporty

     Importy i eksporty są sposobem, w jaki składniki komunikują się. W przypadku importu składnik określa potrzebę konkretnej wartości lub obiektu, a eksport określa dostępność wartości. Każdy import jest dopasowywany do listy eksportów według jej kontraktu.

<a name="where_do_i_go_now"></a>
## <a name="where-do-i-go-now"></a>Gdzie teraz mogę przejść?
 Aby pobrać kompletny kod dla tego przykładu, zobacz [przykład SimpleCalculator](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).

 Aby uzyskać więcej informacji i przykładów kodu, zobacz [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef). Aby uzyskać listę typów MEF, zobacz Przestrzeń nazw <xref:System.ComponentModel.Composition?displayProperty=nameWithType>.
