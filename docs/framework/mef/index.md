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
ms.openlocfilehash: 9a601ac860ac3bf81dd01980b020470d3323772f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181285"
---
# <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)

Ten temat zawiera omówienie zarządzanej struktury rozszerzalności, która została wprowadzona w .NET Framework 4.

## <a name="what-is-mef"></a>Co to jest MEF?

Managed Extensibility Framework lub MEF to biblioteka do tworzenia aplikacji odciążonych i rozszerzalnych. Umożliwia deweloperom aplikacji odnajdywanie i używanie rozszerzeń bez konieczności konfigurowania. Umożliwia również deweloperom rozszerzeń łatwe hermetyzowanie kodu i unikanie kruchych twardych zależności. Mef umożliwia nie tylko ponowneużycie rozszerzeń w aplikacjach, ale także w aplikacjach.

## <a name="the-problem-of-extensibility"></a>Problem rozszerzalności

Wyobraź sobie, że jesteś architektem dużej aplikacji, która musi zapewnić obsługę rozszerzalności. Aplikacja musi zawierać potencjalnie dużą liczbę mniejszych składników i jest odpowiedzialna za ich tworzenie i uruchamianie.

Najprostszym podejściem do problemu jest uwzględnienie składników jako kodu źródłowego w aplikacji i wywołanie ich bezpośrednio z kodu. Ma to wiele oczywistych wad. Co najważniejsze, nie można dodawać nowych składników bez modyfikowania kodu źródłowego, ograniczenia, które mogą być dopuszczalne w, na przykład, aplikacji sieci Web, ale jest niewykonalne w aplikacji klienckiej. Równie problematyczne, może nie mieć dostępu do kodu źródłowego dla składników, ponieważ mogą one być opracowane przez osoby trzecie i z tego samego powodu nie można zezwolić im na dostęp do Ciebie.

Nieco bardziej wyrafinowane podejście byłoby zapewnienie punktu rozszerzenia lub interfejsu, aby umożliwić oddzielenie między aplikacją i jej składników. W ramach tego modelu może zapewnić interfejs, który składnik można zaimplementować i interfejsu API, aby umożliwić mu interakcję z aplikacją. Rozwiązuje to problem wymaga dostępu do kodu źródłowego, ale nadal ma swoje własne trudności.

Ponieważ aplikacja nie ma żadnej pojemności do odnajdywania składników na własną rękę, nadal musi być jawnie poinformowani, które składniki są dostępne i powinny być ładowane. Zazwyczaj odbywa się to przez jawne rejestrowanie dostępnych składników w pliku konfiguracyjnym. Oznacza to, że zapewnienie, że składniki są poprawne staje się problem konserwacji, szczególnie jeśli jest to użytkownik końcowy, a nie deweloper, który ma wykonać aktualizację.

Ponadto komponenty nie są w stanie komunikować się ze sobą, z wyjątkiem sztywno zdefiniowanych kanałów samej aplikacji. Jeśli architekt aplikacji nie przewidział potrzeby określonej komunikacji, jest to zwykle niemożliwe.

Na koniec deweloperzy składników musi zaakceptować zależność od zestawu, który zawiera interfejs, który implementują. Utrudnia to składnik do użycia w więcej niż jednej aplikacji, a także może powodować problemy podczas tworzenia struktury testowej dla składników.

## <a name="what-mef-provides"></a>Co zapewnia MEF

Zamiast tej jawnej rejestracji dostępnych składników, MEF zapewnia sposób, aby odkryć je w sposób dorozumiany, poprzez *skład*. Składnik MEF, zwany *częścią,* deklaratywnie określa zarówno jego zależności (znane jako *import)* jak i jakie możliwości (znane jako *eksport)* udostępnia. Podczas tworzenia części silnik kompozycji MEF spełnia swoje wymagania przywozowe z tym, co jest dostępne z innych części.

Takie podejście rozwiązuje problemy omówione w poprzedniej sekcji. Ponieważ mef części deklaratywnie określić ich możliwości, są one wykrywalne w czasie wykonywania, co oznacza, że aplikacja może korzystać z części bez zakodowanych odwołań lub plików konfiguracji fragile. MEF umożliwia aplikacjom odnajdowanie i badanie części przez ich metadane, bez tworzenia ich wystąpienia, a nawet ładowania ich zestawów. W rezultacie nie ma potrzeby, aby dokładnie określić, kiedy i jak rozszerzenia powinny być ładowane.

Oprócz dostarczonego wywozu część może określić swój przywóz, który zostanie wypełniony innymi częściami. To sprawia, że komunikacja między częściami nie tylko możliwe, ale łatwe i pozwala na dobre faktoringu kodu. Na przykład usługi wspólne dla wielu komponentów mogą być brane pod uwagę w oddzielnej części i łatwo modyfikować lub wymieniać.

Ponieważ model MEF nie wymaga żadnych twardych zależności od określonego zestawu aplikacji, umożliwia rozszerzenia do ponownegou stosowania z aplikacji do aplikacji. Ułatwia to również opracowanie uprzęży testowej, niezależnie od zastosowania, w celu przetestowania komponentów przedłużających.

Rozszerzalna aplikacja napisana przy użyciu MEF deklaruje import, który może być wypełniony przez składniki rozszerzenia, a także może deklarować eksport w celu udostępnienia usług aplikacji na rozszerzenia. Każdy składnik rozszerzenia deklaruje eksport i może również deklarować import. W ten sposób same składniki rozszerzenia są automatycznie rozszerzalne.

## <a name="where-mef-is-available"></a>Gdzie mef jest dostępny

MEF jest integralną częścią .NET Framework 4 i jest dostępny wszędzie tam, gdzie jest używany program .NET Framework. MeF można używać w aplikacjach klienckich, czy używają windows forms, WPF lub innej technologii lub w aplikacjach serwera, które używają ASP.NET.

## <a name="mef-and-maf"></a>MEF i MAF

Poprzednie wersje programu .NET Framework wprowadzono managed add-in framework (MAF), zaprojektowany, aby umożliwić aplikacjom izolowanie i zarządzanie rozszerzeniami. Maf koncentruje się na nieco wyższym poziomie niż MEF, koncentrując się na izolacji rozszerzenia i montażu załadunku i rozładunku, podczas gdy MEF koncentruje się na wykrywalności, rozszerzalności i przenośności. Dwie struktury współdziałają płynnie, a pojedyncza aplikacja może korzystać z obu.

## <a name="simplecalculator-an-example-application"></a>SimpleCalculator: przykładowa aplikacja

Najprostszym sposobem, aby zobaczyć, co MEF może zrobić, to zbudować prostą aplikację MEF. W tym przykładzie można utworzyć bardzo prosty kalkulator o nazwie SimpleCalculator. Celem SimpleCalculator jest utworzenie aplikacji konsoli, która akceptuje podstawowe polecenia arytmetyczne, w postaci "5 + 3" lub "6-2", i zwraca poprawne odpowiedzi. Za pomocą MEF, będziesz mógł dodać nowe operatory bez zmiany kodu aplikacji.

Aby pobrać pełny kod w tym przykładzie, zobacz [przykład SimpleCalculator (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).

> [!NOTE]
> Celem SimpleCalculator jest zademonstrowanie pojęć i składni MEF, a nie koniecznie zapewnić realistyczny scenariusz jego użycia. Wiele aplikacji, które najbardziej skorzystają z mocy MEF są bardziej złożone niż SimpleCalculator. Aby uzyskać bardziej obszerne przykłady, zobacz [managed extensibility framework](https://github.com/MicrosoftArchive/mef) w usłudze GitHub.

- Aby rozpocząć, w programie Visual Studio utwórz `SimpleCalculator`nowy projekt aplikacji konsoli i nadaj jego nazwę .

- Dodaj odwołanie do `System.ComponentModel.Composition` zestawu, gdzie znajduje się MEF.

- Otwórz *module1.vb* lub *Program.cs* i `Imports` `using` dodaj `System.ComponentModel.Composition` lub `System.ComponentModel.Composition.Hosting`wyciągi dla i . Te dwa obszary nazw zawierają typy MEF, które należy opracować rozszerzalną aplikację.

- Jeśli używasz języka Visual Basic, dodaj `Public` słowo kluczowe `Module1` do wiersza, który deklaruje moduł.

## <a name="composition-container-and-catalogs"></a>Kontener kompozycji i katalogi

Rdzeniem modelu kompozycji MEF jest *pojemnik na kompozycję,* który zawiera wszystkie dostępne części i wykonuje kompozycję. Skład jest dopasowanie do importu do eksportu. Najczęstszym typem kontenera <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>kompozycji jest , i użyjesz go dla SimpleCalculator.

Jeśli używasz języka Visual Basic, dodaj `Program` klasę publiczną o nazwie w *module 1.vb*.

Dodaj następujący wiersz `Program` do klasy w *module1.vb* lub *Program.cs:*

```vb
Dim _container As CompositionContainer
```

```csharp
private CompositionContainer _container;
```

Aby odkryć dostępne części, pojemniki kompozycji korzystają z *katalogu.* Katalog jest obiektem, który udostępnia części odnalezione z jakiegoś źródła. MEF udostępnia katalogi do odnajdywać części z podanego typu, zestawu lub katalogu. Deweloperzy aplikacji można łatwo tworzyć nowe katalogi do odnajdowania części z innych źródeł, takich jak usługa sieci Web.

Dodaj do `Program` klasy następujący konstruktor:

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

Wywołanie <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> informuje kontenera kompozycji, aby skomponować określony zestaw części, w tym przypadku bieżące `Program`wystąpienie . W tym momencie jednak nic `Program` się nie stanie, ponieważ nie ma importu do wypełnienia.

## <a name="imports-and-exports-with-attributes"></a>Import i eksport z atrybutami

Najpierw `Program` zaimportujesz kalkulator. Pozwala to na oddzielenie problemów interfejsu użytkownika, takich jak `Program`wejście konsoli i wyjście, które zostaną wprowadzone , od logiki kalkulatora.

Dodaj następujący kod `Program` do klasy:

```vb
<Import(GetType(ICalculator))>
Public Property calculator As ICalculator
```

```csharp
[Import(typeof(ICalculator))]
public ICalculator calculator;
```

Należy zauważyć, że `calculator` deklaracja obiektu nie jest niczym niezwykłym, ale jest ozdobiony atrybutem. <xref:System.ComponentModel.Composition.ImportAttribute> Ten atrybut deklaruje coś do importu; oznacza to, że zostanie on wypełniony przez aparat kompozycji, gdy obiekt jest złożony.

Każdy import ma *umowę,* która określa, z jakim eksportem będzie on dopasowany. Kontrakt może być jawnie określony ciąg lub może być generowany automatycznie przez MEF z `ICalculator`danego typu, w tym przypadku interfejsu . Każdy eksport zadeklarowany z pasującym kontraktem będzie spełniał ten import. Należy zauważyć, że `calculator` podczas gdy `ICalculator`typ obiektu jest w rzeczywistości, nie jest to wymagane. Kontrakt jest niezależny od typu obiektu importującego. (W takim przypadku można pominąć `typeof(ICalculator)`. MEF automatycznie przyjmie, że umowa będzie oparta na typie importu, chyba że określisz ją jawnie.)

Dodaj ten bardzo prosty interfejs `SimpleCalculator` do modułu lub przestrzeni nazw:

```vb
Public Interface ICalculator
    Function Calculate(input As String) As String
End Interface
```

```csharp
public interface ICalculator
{
    String Calculate(String input);
}
```

Teraz, gdy `ICalculator`zostały zdefiniowane , trzeba klasy, która implementuje go. Dodaj następującą klasę do `SimpleCalculator` modułu lub obszaru nazw:

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

Oto eksport, który będzie pasował `Program`do importu w . Aby eksport był zgodny z importem, eksport musi mieć ten sam kontrakt. Wywóz na podstawie umowy opartej na `typeof(MySimpleCalculator)` spowoduje niezgodność, a przywóz nie zostanie wypełniony; kontrakt musi dokładnie odpowiadać.

Ponieważ kontener kompozycji zostanie wypełniony wszystkimi częściami `MySimpleCalculator` dostępnymi w tym złożeniu, część będzie dostępna. Gdy konstruktor `Program` wykonuje kompozycję `Program` na obiekcie, jego `MySimpleCalculator` import zostanie wypełniony obiektem, który zostanie utworzony w tym celu.

Warstwa interfejsu`Program`użytkownika ( ) nie musi wiedzieć nic więcej. W związku z tym można wypełnić w `Main` pozostałej części logiki interfejsu użytkownika w metodzie.

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
    string s;
    Console.WriteLine("Enter Command:");
    while (true)
    {
        s = Console.ReadLine();
        Console.WriteLine(p.calculator.Calculate(s));
    }
}
```

 Ten kod po prostu odczytuje `Calculate` wiersz `ICalculator` danych wejściowych i wywołuje funkcję na wynik, który zapisuje z powrotem do konsoli. To jest cały kod, `Program`którego potrzebujesz w . Cała reszta pracy będzie się działo w częściach.

## <a name="further-imports-and-importmany"></a>Dalsze importy i importwież

Aby SimpleCalculator był rozszerzalny, musi zaimportować listę operacji. Zwykły <xref:System.ComponentModel.Composition.ImportAttribute> atrybut jest wypełniany przez <xref:System.ComponentModel.Composition.ExportAttribute>jeden i tylko jeden . Jeśli dostępnych jest więcej niż jeden, aparat kompozycji generuje błąd. Aby utworzyć import, który może być wypełniony przez dowolną <xref:System.ComponentModel.Composition.ImportManyAttribute> liczbę eksportu, można użyć atrybutu.

Dodaj do klasy następującą `MySimpleCalculator` właściwość operations:

```vb
<ImportMany()>
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))
```

```csharp
[ImportMany]
IEnumerable<Lazy<IOperation, IOperationData>> operations;
```

<xref:System.Lazy%602>jest typem dostarczonym przez MEF w celu posiadania pośrednich odniesień do wywozu. W tym miejscu, oprócz samego wyeksportowanego obiektu, otrzymasz również *metadane eksportu*lub informacje opisujące eksportowany obiekt. Każdy <xref:System.Lazy%602> zawiera `IOperation` obiekt reprezentujący rzeczywistą operację `IOperationData` i obiekt reprezentujący jego metadane.

Dodaj następujące proste interfejsy do `SimpleCalculator` modułu lub obszaru nazw:

```vb
Public Interface IOperation
    Function Operate(left As Integer, right As Integer) As Integer
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

 W takim przypadku metadane dla każdej operacji jest symbolem, który reprezentuje \*tę operację, takich jak +, -, i tak dalej. Aby udostępnić operację dodawania, dodaj następującą `SimpleCalculator` klasę do modułu lub obszaru nazw:

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "+"c)>
Public Class Add
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
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

Atrybut <xref:System.ComponentModel.Composition.ExportAttribute> działa tak, jak wcześniej. Atrybut <xref:System.ComponentModel.Composition.ExportMetadataAttribute> dołącza metadane, w postaci pary nazwa wartość, do tego eksportu. Podczas `Add` gdy klasa `IOperation`implementuje , `IOperationData` klasa, która implementuje nie jest jawnie zdefiniowane. Zamiast tego klasa jest niejawnie tworzony przez MEF z właściwości na podstawie nazw metadanych pod warunkiem. (Jest to jeden z kilku sposobów dostępu do metadanych w MEF.)

Skład w MEF jest *cykliczny*. Obiekt został jawnie skomponowany, `Program` który zaimportował `ICalculator` obiekt, który okazał się typem `MySimpleCalculator`. `MySimpleCalculator`, z kolei importuje `IOperation` kolekcję obiektów, a import `MySimpleCalculator` zostanie wypełniony podczas tworzenia, w `Program`tym samym czasie co przywóz pliku . Gdyby `Add` klasa zadeklarowała dalszy przywóz, to też musiałoby zostać wypełnione i tak dalej. Każdy import pozostawiony niewypełniony powoduje błąd składu. (Możliwe jest jednak zadeklarowanie importu jako opcjonalnego lub przypisanie im wartości domyślnych).

## <a name="calculator-logic"></a>Logika kalkulatora

Z tych części w miejscu, wszystko, co pozostaje jest sama logika kalkulatora. Dodaj następujący kod `MySimpleCalculator` w klasie, `Calculate` aby zaimplementować metodę:

```vb
Public Function Calculate(input As String) As String Implements ICalculator.Calculate
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
public String Calculate(string input)
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

Początkowe kroki analizują ciąg wejściowy w lewej i prawej opery i znak operatora. W `foreach` pętli każdy element `operations` członkowski kolekcji jest badane. Obiekty te są <xref:System.Lazy%602>typu , a ich wartości metadanych i <xref:System.Lazy%602.Metadata%2A> eksportowany <xref:System.Lazy%601.Value%2A> obiekt można uzyskać za pomocą właściwości i właściwości odpowiednio. W takim przypadku `Symbol` jeśli właściwość `IOperationData` obiektu zostanie wykryta jako zgodne, `Operate` kalkulator wywołuje `IOperation` metodę obiektu i zwraca wynik.

Aby ukończyć kalkulator, potrzebujesz również metody pomocniczej, która zwraca pozycję pierwszego znaku niecyfrowego w ciągu. Dodaj następującą metodę pomocnika `MySimpleCalculator` do klasy:

```vb
Private Function FindFirstNonDigit(s As String) As Integer
    For i = 0 To s.Length - 1
        If Not Char.IsDigit(s(i)) Then Return i
    Next
    Return -1
End Function
```

```csharp
private int FindFirstNonDigit(string s)
{
    for (int i = 0; i < s.Length; i++)
    {
        if (!Char.IsDigit(s[i])) return i;
    }
    return -1;
}
```

Teraz powinieneś być w stanie skompilować i uruchomić projekt. W języku Visual Basic upewnij `Public` się, `Module1`że słowo kluczowe zostało dodane do pliku . W oknie konsoli wpisz operację dodawania, taką jak "5+3", a kalkulator zwraca wyniki. Każdy inny operator skutkuje "Operacją Nie znaleziono!" .

## <a name="extending-simplecalculator-using-a-new-class"></a>Rozszerzanie simplecalculator przy użyciu nowej klasy

Teraz, gdy kalkulator działa, dodanie nowej operacji jest łatwe. Dodaj następującą klasę do `SimpleCalculator` modułu lub obszaru nazw:

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "-"c)>
Public Class Subtract
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
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

Skompiluj i uruchom projekt. Wpisz operację odejmowania, taką jak "5-3". Kalkulator obsługuje teraz odejmowanie, a także dodawanie.

## <a name="extending-simplecalculator-using-a-new-assembly"></a>Rozszerzanie simplecalculator przy użyciu nowego zestawu

Dodawanie klas do kodu źródłowego jest dość proste, ale MEF zapewnia możliwość wyszukiwania poza własne źródło aplikacji dla części. Aby to zademonstrować, należy zmodyfikować SimpleCalculator, aby przeszukać katalog, a także jego <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>własny zestaw, dla części, dodając program .

Dodaj nowy katalog `Extensions` o nazwie do projektu SimpleCalculator. Upewnij się, aby dodać go na poziomie projektu, a nie na poziomie rozwiązania. Następnie dodaj nowy projekt biblioteki klas `ExtendedOperations`do rozwiązania o nazwie . Nowy projekt zostanie skompilowany w oddzielnym zestawie.

Otwórz Projektanta właściwości projektu dla projektu Rozszerzoneoperacje i kliknij kartę **Kompilacja** lub **Kompilacja.** Zmień **ścieżkę wyjściową kompilacji** lub **ścieżkę wyjściową,** aby wskazać katalog Rozszerzeń w katalogu projektu SimpleCalculator (*.. \SimpleCalculator\Rozszerzenia\\*).

 W *module1.vb* lub *Program.cs*dodaj następujący wiersz `Program` do konstruktora:

```vb
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))
```

```csharp
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));
```

Zastąp przykładową ścieżkę ścieżką do katalogu Rozszerzeń. (Ta ścieżka bezwzględna służy tylko do debugowania. W aplikacji produkcyjnej należy użyć ścieżki względnej.) Teraz <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> doda wszystkie części znalezione we wszystkich złożeniach w katalogu Rozszerzenia do kontenera kompozycji.

W projekcie ExtendedOperations dodaj odwołania do SimpleCalculator i System.ComponentModel.Composition. W pliku klasy ExtendedOperations `Imports` dodaj `using` lub instrukcję dla System.ComponentModel.Composition. W języku Visual Basic `Imports` należy również dodać instrukcję dla SimpleCalculator. Następnie dodaj następującą klasę do pliku klasy ExtendedOperations:

```vb
<Export(GetType(SimpleCalculator.IOperation))>
<ExportMetadata("Symbol", "%"c)>
Public Class Modulo
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
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

Należy zauważyć, że aby kontrakt <xref:System.ComponentModel.Composition.ExportAttribute> był zgodny, atrybut musi <xref:System.ComponentModel.Composition.ImportAttribute>mieć ten sam typ co .

Skompiluj i uruchom projekt. Przetestuj nowy Mod (%) Operator.

## <a name="conclusion"></a>Podsumowanie

W tym temacie poruszono podstawowe pojęcia MEF.

- Części, katalogi i kontener kompozycji

     Części i kontener kompozycji są podstawowymi elementami składowymi aplikacji MEF. Częścią jest dowolny obiekt, który importuje lub eksportuje wartość, do siebie włącznie. Katalog zawiera kolekcję części z określonego źródła. Kontener kompozycji używa części dostarczonych przez katalog do wykonywania kompozycji, wiązania importu do eksportu.

- Import i eksport

     Import i eksport są sposobem, w jaki składniki komunikują się. W przypadku importu składnik określa potrzebę określonej wartości lub obiektu, a przy eksporcie określa dostępność wartości. Każdy import jest dopasowywał do listy wywozu w ramach jego umowy.

## <a name="next-steps"></a>Następne kroki

Aby pobrać pełny kod w tym przykładzie, zobacz [przykład SimpleCalculator (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).

 Aby uzyskać więcej informacji i przykłady kodu, zobacz [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef). Aby uzyskać listę typów MEF, <xref:System.ComponentModel.Composition?displayProperty=nameWithType> zobacz obszar nazw.
