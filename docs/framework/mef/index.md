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
ms.openlocfilehash: 1f950779514975a3ee76af76506c7579e046537f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393188"
---
# <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)
Ten temat zawiera omówienie Managed Extensibility Framework wprowadzone w .NET Framework 4.  
  
<a name="what_is_mef"></a>   
## <a name="what-is-mef"></a>Co to jest MEF?  
 Managed Extensibility Framework lub MEF to biblioteka dla tworzenia niewielka, rozszerzalne aplikacji. Umożliwia deweloperom aplikacji na wykrywanie i używanie rozszerzeń z wymagana żadna konfiguracja. Ponadto pozwala on usłudze deweloperów rozszerzenia łatwo Hermetyzowanie kodu i uniknąć wrażliwych twardych zależności. MEF umożliwia nie tylko rozszerzenia zostanie ponownie w ramach aplikacji, ale w aplikacjach oraz.  
  
<a name="the_problem_of_extensibility"></a>   
## <a name="the-problem-of-extensibility"></a>Problem rozszerzalności  
 Załóżmy, czy Architekt dużej aplikacji, który muszą obsługiwać rozszerzeń. Aplikacja musi zawierać potencjalnie dużej liczby składników mniejsze i jest odpowiedzialny za tworzenie i uruchamianie ich.  
  
 Najprostsza metoda problem jest zawiera składniki jako kod źródłowy w aplikacji i połączeń telefonicznych z nimi bezpośrednio w kodzie.  To jest liczba widocznych wady.  Najważniejsze nie można dodać nowych składników, bez konieczności modyfikacji kodu źródłowego, ograniczenia, może być do przyjęcia w, na przykład aplikacji sieci Web, ale niedziałającym w aplikacji klienckiej.  Równie powodować problemów, nie masz dostępu do kodu źródłowego dla składników, ponieważ może być opracowana przez osoby trzecie, a także z tego samego powodu się, że nie można zezwolić im dostęp do Ciebie.  
  
 Nieco bardziej złożone rozwiązanie byłoby Podaj punkt rozszerzenia lub interfejsu, aby zezwolić na oddzielenie od aplikacji i jej składniki.  W tym modelu można określić interfejs, który można wdrożyć składnika i interfejs API do interakcji z aplikacją.  To rozwiązuje problem polegający na wymaganiu dostęp do kodu źródłowego, ale nadal ma własną trudności.  
  
 Ponieważ aplikacja nie ma żadnych pojemności do odnajdywania składników samodzielnie, go musi nadal można jawnie informację składniki, które są dostępne i powinna być załadowana.  Zazwyczaj jest to osiągane przez jawnie rejestrowanie dostępne składniki w pliku konfiguracji. Oznacza to, że zapewnienia, że składniki są prawidłowe staje się konserwacyjne, zwłaszcza gdy jest użytkownika końcowego i nie projektanta, który powinien wykonać uaktualnienie.  
  
 Ponadto składniki są niezdolne do komunikacji ze sobą, z wyjątkiem kanałami zdefiniowanych sztywno z samej aplikacji.  Jeśli Architekt aplikacji nie ma oczekiwać potrzeby w celu komunikacji, jest zazwyczaj niemożliwe.  
  
 Na koniec deweloperzy składnika zaakceptować twardych zależność, jaki zestaw zawiera interfejs, który implementuje one.  Utrudnia składnika używanego w więcej niż jedną aplikację, a można również tworzyć problemy podczas tworzenia struktury testowej, składników.  
  
<a name="what_mef_provides"></a>   
## <a name="what-mef-provides"></a>Udostępnia MEF  
 Zamiast jawnego rejestracji dostępnych składników MEF pozwala wykrywać je niejawnie, przy użyciu *kompozycji*.  Składnik MEF, o nazwie *części*, deklaratywnego określa zarówno jego zależności (znane jako *importuje*) i jakie funkcje (nazywane *eksportuje*) dostępnych. Po utworzeniu części MEF aparat kompozycji spełnia jego procesów importu, co jest dostępne z innymi częściami.  
  
 Takie podejście rozwiązuje problemy opisanych w poprzedniej sekcji.  Ponieważ części MEF deklaratywnie określić ich możliwości, są one wykrywalny w czasie wykonywania, co oznacza, że aplikacja może sprawić, użyj elementów bez odwołań ustalony lub pliki wrażliwe konfiguracji.  MEF umożliwia aplikacjom na potrzeby odnajdywania i zbadać części ich metadanych bez tworzenia wystąpienia je lub nawet ładowania ich zestawów. W związku z tym jest niepotrzebna dokładnie określić, kiedy i jak można załadować rozszerzeń.  
  
 Oprócz jego podana eksportuje części można określić jego procesów importu, które zostaną wypełnione innych części.  To sprawia, że komunikacji między części nie tylko to możliwe, ale łatwa i pozwala na dobrej factoring kodu. Na przykład usług wspólnych dla wielu składników można być brana pod uwagę w osobnym obszarze i łatwo zmodyfikowane lub zastąpione.  
  
 MEF model wymaga nie twardych zależności zestawu aplikacji, dlatego umożliwia rozszerzenia ponowne użycie z aplikacji do aplikacji.  To ułatwia także do opracowywania kontroler testu, niezależnie od aplikacji, aby sprawdzić składniki rozszerzenia.  
  
 Aplikacji rozszerzalnej napisane przy użyciu MEF deklaruje obiektu import, który może zostać wypełniony przez składniki rozszerzenia i może deklarować także eksportuje w celu udostępnienia usług aplikacji do rozszerzenia.  Każdy składnik rozszerzenia deklaruje eksportu i może deklarować także importów.  W ten sposób samych elementów rozszerzenia są automatycznie rozszerzonego.  
  
<a name="where_is_mef_available"></a>   
## <a name="where-is-mef-available"></a>Gdzie jest MEF?  
 MEF jest integralną częścią [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]i jest dostępna we wszystkich programu .NET Framework jest używana.  Można użyć MEF w aplikacjach klienckich, korzystają z formularzy systemu Windows, WPF lub innych technologii, czy w aplikacji serwerowych, które używają programu ASP.NET.  
  
<a name="mef_and_maf"></a>   
## <a name="mef-and-maf"></a>MEF i MAF  
 Poprzednie wersje programu .NET Framework wprowadzono zarządzane dodatku Framework (MAF), umożliwia aplikacji w celu odizolowania i Zarządzaj rozszerzeniami.  MAF koncentruje się nieco wyższego niż MEF skupienie się na izolację rozszerzenia i zestawu ładowanie i zwalnianie podczas jego MEF skoncentrować się na rozszerzalności, przenośność i możliwości odnajdywania.  Dwie struktury bezproblemowe współdziałanie, a pojedynczą aplikacją można korzystać z obu.  
  
<a name="simplecalculator_an_example_application"></a>   
## <a name="simplecalculator-an-example-application"></a>SimpleCalculator: Przykładowa aplikacja  
 Najprostszym sposobem, aby zobaczyć, co można zrobić MEF jest utworzyć prostą aplikację MEF. W tym przykładzie kompilacji jest bardzo prosty kalkulator o nazwie SimpleCalculator. Celem SimpleCalculator jest tworzenie aplikacji konsoli, która akceptuje podstawowe polecenia arytmetyczne, w formie "5 + 3" lub "6-2" i zwraca poprawnych odpowiedzi. Przy użyciu MEF, można dodać nowych operatorów bez konieczności zmieniania kodu aplikacji.  
  
 Aby pobrać kompletny kod dla tego przykładu, zobacz [próbki SimpleCalculator](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).  
  
> [!NOTE]
>  Celem SimpleCalculator jest aby zademonstrować pojęcia i składni MEF, zamiast niekoniecznie zapewnienie scenariusza realistyczne jej wykorzystanie. Wiele aplikacji, które mogłyby, korzystają najbardziej z możliwości MEF jest bardziej złożone niż SimpleCalculator. Bardziej rozległych przykłady można znaleźć [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) w witrynie GitHub.
  
 Aby uruchomić w [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], Utwórz nowy projekt aplikacji konsoli o nazwie `SimpleCalculator`. Dodaj odwołanie do zestawu System.ComponentModel.Composition, w którym znajduje się MEF. Otwórz Module1.vb lub Program.cs i Dodaj `Imports` lub `using` instrukcje System.ComponentModel.Composition i System.ComponentModel.Composition.Hosting. Te dwie przestrzenie nazw zawierają typy MEF musisz utworzyć aplikację rozszerzonego. W języku Visual Basic, Dodaj `Public` — słowo kluczowe do wiersza, który deklaruje `Module1` modułu.  
  
<a name="composition_container_and_catalogs"></a>   
## <a name="composition-container-and-catalogs"></a>Kontener kompozycji i katalogi  
 Podstawowy model kompozycji MEF jest *kontenera kompozycji*, który zawiera wszystkie części i wykonuje kompozycji.  (To znaczy dopasowanie importów do eksportuje.)  Najczęściej spotykanym typem kontenera kompozycji jest <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, i zostanie ona użyta dla SimpleCalculator.  
  
 W języku Visual Basic Module1.vb, Dodaj Klasa publiczna o nazwie `Program`. Następnie dodaj następujący wiersz do `Program` klasy Module1.vb lub pliku Program.cs:  
  
```vb  
Dim _container As CompositionContainer  
```  
  
```csharp  
private CompositionContainer _container;  
```  
  
 Aby odnaleźć elementy dostępne do niego kontenery kompozycji sprawia, że użycie *katalogu*. Katalog jest obiekt, który sprawia, że dostępne elementy wykryte z określonego źródła.  MEF udostępnia katalogi do odnajdywania części z udostępnionego typu, zestawów lub katalogu. Deweloperzy aplikacji można łatwo utworzyć nowe katalogi do odnajdywania części z innych źródeł, takich jak usługi sieci Web.  
  
 Dodaj następujący Konstruktor do `Program` klasy:  
  
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
  
 Wywołanie <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> informuje kontenera kompozycji utworzenie określonych części, w tym przypadku bieżące wystąpienie klasy `Program`. W tym momencie, nic się nie stanie, ponieważ `Program` ma żadnych importów do wypełnienia.  
  
<a name="imports_and_exports_with_attributes"></a>   
## <a name="imports-and-exports-with-attributes"></a>Importu i eksportu z atrybutami  
 Po pierwsze, masz `Program` zaimportować Kalkulator. Dzięki temu rozdzielenie użytkownika interfejsu problemy, takie jak konsola przychodzących i wychodzących, które zostaną umieszczone w `Program`, z logiką Kalkulator.  
  
 Dodaj następujący kod do `Program` klasy:  
  
```vb  
<Import(GetType(ICalculator))>  
Public Property calculator As ICalculator  
```  
  
```csharp  
[Import(typeof(ICalculator))]  
public ICalculator calculator;  
```  
  
 Zwróć uwagę, że deklaracja `calculator` obiekt nie jest rzadko, ale ma ona <xref:System.ComponentModel.Composition.ImportAttribute> atrybutu.  Ten atrybut deklaruje coś się importu; oznacza to, że zostaną wprowadzone przez aparat kompozycji podczas składa się obiekt.  
  
 Każdego importu ma *kontraktu*, która określa, jakie eksportu zostanie dopasowana z. Kontrakt może być jawnie określony ciąg lub jego mogą być automatycznie generowane przez MEF z danego typu, w tym przypadku interfejs `ICalculator`.  Wszelkie eksportu zadeklarowana ze zgodnego kontraktu spełniają tego importu.  Należy pamiętać, że podczas typ `calculator` obiekt jest w rzeczywistości `ICalculator`, nie jest to wymagane. Kontrakt nie zależy od typu obiektu importowania.  (W takim przypadku można pozostawić `typeof(ICalculator)`.  MEF automatycznie przyjmie kontraktu opartego na typ importu, chyba że jawnie określony.)  
  
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
  
 Teraz, gdy zdefiniowano `ICalculator`, należy klasa, która implementuje go.  Dodaj następujące klasy modułu lub `SimpleCalculator` przestrzeni nazw:  
  
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
  
 Oto eksportu odpowiadających importu w `Program`. Aby eksportu do dopasowania importu eksportu muszą mieć ten sam kontrakt.  Eksportowanie na podstawie umowy, na podstawie `typeof(MySimpleCalculator)` dałby w efekcie niezgodność i importu nie może być wypełnione; kontrakt musi dokładnie pasować.  
  
 Ponieważ kontener kompozycji zostanie wypełniona części dostępne w tym zestawie `MySimpleCalculator` części będą dostępne.  Gdy konstruktora dla `Program` przeprowadzają kompozycji `Program` obiekt i jego import zostanie wypełniona `MySimpleCalculator` obiektu, który zostanie utworzony w tym celu.  
  
 Warstwę interfejsu użytkownika (`Program`) nie musi wiedzieć, inaczej.  W związku z tym można wprowadzić w pozostałej części logika interfejsu użytkownika w `Main` metody.  
  
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
  
 Ten kod po prostu odczytuje wiersz danych wejściowych i wywołania `Calculate` funkcji `ICalculator` w wyniku powrotem zapisuje się do konsoli. Oznacza to cały kod w `Program`.  Wszystkie pozostałe pracy nastąpi w częściach.  
  
<a name="further_imports_and_importmany"></a>   
## <a name="further-imports-and-importmany"></a>Importy i ImportMany  
 Aby SimpleCalculator być rozszerzalny musi zaimportować listę operacji. Zwykły <xref:System.ComponentModel.Composition.ImportAttribute> atrybutu jest wypełniana przez jeden i tylko jeden <xref:System.ComponentModel.Composition.ExportAttribute>.  Jeśli jest więcej niż jeden dostępny, aparat kompozycji powoduje błąd.  Aby utworzyć obiektu import, który może zostać wypełniony przez dowolną liczbę eksportu, można użyć <xref:System.ComponentModel.Composition.ImportManyAttribute> atrybutu.  
  
 Dodaj następujące właściwości działania do `MySimpleCalculator` klasy:  
  
```vb  
<ImportMany()>  
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))  
```  
  
```csharp  
[ImportMany]  
IEnumerable<Lazy<IOperation, IOperationData>> operations;  
```  
  
 <xref:System.Lazy%602> Typ jest zapewniana przez MEF do przechowywania pośredniego odwołania do eksportu.  W tym miejscu, oprócz samego obiektu wyeksportowanego umożliwia również wyświetlenie *Eksportowanie metadanych*, lub informacje opisujące eksportowanego obiektu. Każdy <xref:System.Lazy%602> zawiera `IOperation` obiekt reprezentujący bieżącej operacji i `IOperationData` obiekt reprezentujący jego metadanych.  
  
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
  
 W takim przypadku metadanych dla każdej operacji jest symbol, który reprezentuje danej operacji, takich jak +, -, *, i tak dalej. Aby udostępnić operacja dodawania, należy dodać następujące klasy modułu lub `SimpleCalculator` przestrzeni nazw:  
  
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
  
 <xref:System.ComponentModel.Composition.ExportAttribute> Atrybutu funkcje, tak jak poprzednio.  <xref:System.ComponentModel.Composition.ExportMetadataAttribute> Atrybut dołącza metadanych w postaci pary nazwa wartość do tego eksportu.  Gdy `Add` klasa implementuje `IOperation`, klasy, która implementuje `IOperationData` nie jest jawnie zdefiniowany. Zamiast tego klasy niejawnie jest tworzony przez MEF o właściwościach opartych na nazwach podane metadanych.  (Jest to jeden z kilku sposobów uzyskuje dostęp do metadanych w MEF.)  
  
 Kompozycja w MEF *cykliczne*. Należy jawnie składane `Program` obiektu, który zaimportowane `ICalculator` , który był typu `MySimpleCalculator`.  `MySimpleCalculator`, z kolei importuje Kolekcja `IOperation` obiektów i że import zostanie wprowadzona podczas `MySimpleCalculator` jest tworzony w tym samym czasie jako importów elementu `Program`. Jeśli `Add` klasy zadeklarowany dalsze importu, który zbyt musi być wypełnione i tak dalej. Wszelkie zaimportować po lewej stronie powoduje błąd kompozycji.  (Jest to możliwe, jednak aby zadeklarować importów jako opcjonalną lub przypisać te wartości domyślne.)  
  
<a name="calculator_logic"></a>   
## <a name="calculator-logic"></a>Kalkulator logiki  
 Z tych elementów w miejscu liście nie zostanie samej logiki Kalkulator. Dodaj następujący kod w `MySimpleCalculator` klasy do zaimplementowania `Calculate` metody:  
  
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
  
 Początkowe kroki przeanalizować ciągu wejściowego w lewy i prawy operandy i znaku operatora.  W `foreach` pętli, każdy element członkowski `operations` się zbadana kolekcji. Te obiekty są typu <xref:System.Lazy%602>, i ich wartości metadanych i eksportowanego obiektu są dostępne z <xref:System.Lazy%602.Metadata%2A> właściwości i <xref:System.Lazy%601.Value%2A> właściwości odpowiednio. W tym przypadku jeśli `Symbol` właściwość `IOperationData` obiektu po odnalezieniu jako dopasowania, wywołania Kalkulator `Operate` metody `IOperation` obiektu i zwraca wynik.  
  
 Do wykonania Kalkulator, potrzebne są również metody pomocnika, która zwraca położenie pierwszego znaku,-cyfrowy w ciągu.  Dodaj następującą metodę pomocnika do `MySimpleCalculator` klasy:  
  
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
  
 Teraz można skompilować i uruchomić projekt. W języku Visual Basic, upewnij się, że dodane `Public` słowa kluczowego `Module1`. W oknie konsoli wpisz operacja dodawania, np. "5 + 3", a Kalkulator zwróci wyniki.  Inne operator spowoduje "Operacja nie została odnaleziona!" Komunikat.  
  
<a name="extending_simplecalculator_using_a_new_class"></a>   
## <a name="extending-simplecalculator-using-a-new-class"></a>Rozszerzanie SimpleCalculator przy użyciu nowej klasy  
 Teraz, gdy działa Kalkulator, Dodawanie nowej operacji jest bardzo proste. Dodaj następujące klasy modułu lub `SimpleCalculator` przestrzeni nazw:  
  
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
  
 Kompilowanie i uruchamianie projektu. Wpisz operację odejmowania, takie jak "5-3". Kalkulator obsługuje teraz odejmowania, a także dodanie.  
  
<a name="extending_simplecalculator_using_a_new_assembly"></a>   
## <a name="extending-simplecalculator-using-a-new-assembly"></a>Rozszerzanie SimpleCalculator przy użyciu nowego zestawu  
 Dodawanie klas do źródła kodu jest prosta, ale MEF pozwala, aby wyszukać części poza źródła własnych aplikacji. Aby zademonstrować, to, należy zmodyfikować SimpleCalculator do przeszukania katalogu, a także własny zestaw składników, dodając <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.  
  
 Dodaj nowy katalog o nazwie `Extensions` do projektu SimpleCalculator.  Upewnij się dodać go na poziomie projektu, a nie na poziomie rozwiązania. Następnie dodaj nowego projektu biblioteki klas w rozwiązaniu o nazwie `ExtendedOperations`. Nowy projekt zostanie skompilowany w ramach oddzielnego zestawu.  
  
 Otwórz w Projektancie właściwości projektu dla projektu ExtendedOperations i kliknij przycisk **skompilować** lub **kompilacji** kartę. Zmień **ścieżki wyjściowej kompilacji** lub **ścieżka wyjściowa** wskaż katalogu rozszerzeń w katalogu projektu SimpleCalculator (.. \SimpleCalculator\Extensions\\).  
  
 W Module1.vb lub pliku Program.cs Dodaj następujący wiersz do `Program` konstruktora:  
  
```vb  
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))  
```  
  
```csharp  
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));  
```  
  
 Zamień ścieżki przykład ścieżki do katalogu rozszerzenia.  (Jest to ścieżka bezwzględna do debugowania tylko do celów.  W aplikacji produkcyjnej należy użyć ścieżki względnej.) <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> Teraz doda żadnych części w wszystkie zestawy w katalogu rozszerzeń do kontenera kompozycji.  
  
 W projekcie ExtendedOperations Dodaj odwołania do SimpleCalculator i System.ComponentModel.Composition. Plik klasy ExtendedOperations, Dodaj `Imports` lub `using` instrukcji dla System.ComponentModel.Composition. W języku Visual Basic, należy również dodać `Imports` instrukcji dla SimpleCalculator. Następnie dodaj następujące klasy w pliku klasy ExtendedOperations:  
  
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
  
 Należy pamiętać, aby tej umowy do dopasowania, <xref:System.ComponentModel.Composition.ExportAttribute> atrybut musi mieć taki sam typ jak <xref:System.ComponentModel.Composition.ImportAttribute>.  
  
 Kompilowanie i uruchamianie projektu. Przetestuj nowy operator Mod (%).  
  
<a name="conclusion"></a>   
## <a name="conclusion"></a>Wniosek  
 W tym temacie opisano podstawowe pojęcia MEF.  
  
-   Części, katalogów i kontener kompozycji  
  
     Części i kontener kompozycji są podstawowe bloki konstrukcyjne aplikacji MEF. Element jest dowolny obiekt, który importuje lub eksportuje wartość, w tym sam. Katalog udostępnia kolekcję części z określonego źródła.  Kontener kompozycji używa części udostępniane przez wykaz do utworzenia powiązania importów do eksportu.  
  
-   Importu i eksportu  
  
     Importu i eksportu są sposób za pomocą którego komunikują się składników. Importowania składnika określa potrzeba obiektu lub określonej wartości, i z eksportu określa dostępność wartość. Każdej operacji importowania jest zgodny z listą eksporty i jej kontrakt.  
  
<a name="where_do_i_go_now"></a>   
## <a name="where-do-i-go-now"></a>Gdzie mogę teraz?  
 Aby pobrać kompletny kod dla tego przykładu, zobacz [próbki SimpleCalculator](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).  
  
 Aby uzyskać więcej informacji oraz przykłady kodu, zobacz [Managed Extensibility Framework](http://go.microsoft.com/fwlink/?LinkId=144282). Aby uzyskać listę typów MEF, zobacz <xref:System.ComponentModel.Composition?displayProperty=nameWithType> przestrzeni nazw.
