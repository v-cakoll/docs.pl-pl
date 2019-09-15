---
title: 'Przewodnik: Osadź typy z zestawów zarządzanych w programie Visual Studio'
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1f32bd840efa97b62097a2d051c25d519785b381
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973272"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a>Przewodnik: Osadź typy z zestawów zarządzanych w programie Visual Studio

Jeśli osadzisz informacje o typie z zestawu o silnej nazwie zarządzanej, możesz luźno połączyć typy w aplikacji, aby osiągnąć niezależność wersji. Oznacza to, że program można napisać tak, aby używał typów z dowolnej wersji biblioteki zarządzanej bez konieczności ponownego kompilowania każdej nowej wersji.

Osadzanie typów jest często używane z międzyoperacyjnym modelem COM, takim jak aplikacja, która korzysta z obiektów automatyzacji z Microsoft Office. Osadzanie informacji o typie umożliwia tej samej kompilacji programu do pracy z różnymi wersjami Microsoft Office na różnych komputerach. Można jednak również użyć osadzania typu z w pełni zarządzanych rozwiązań.

Po określeniu interfejsów publicznych, które mogą być osadzone, należy utworzyć klasy środowiska uruchomieniowego, które implementują te interfejsy. Program kliencki może osadzić informacje o typie dla interfejsów w czasie projektowania, odwołując się do zestawu, który zawiera interfejsy publiczne i ustawiając `Embed Interop Types` Właściwość odwołania na. `True` Następnie program kliencki może ładować wystąpienia obiektów środowiska uruchomieniowego, które zostały wpisane jako te interfejsy. Jest to równoznaczne z użyciem kompilatora wiersza polecenia i odwołującego się do zestawu `/link` przy użyciu opcji kompilatora. 

Jeśli utworzysz nową wersję zestawu o silnej nazwie środowiska uruchomieniowego, nie trzeba ponownie kompilować programu klienckiego. Program kliencki nadal korzysta z niezależnej wersji zestawu środowiska uruchomieniowego, przy użyciu informacji o typie osadzonym dla interfejsów publicznych.

W tym instruktażu zawarto następujące instrukcje:

1. Utwórz zestaw o silnej nazwie z interfejsem publicznym zawierającym informacje o typie, które mogą być osadzone.
1. Utwórz zestaw o silnej nazwie środowiska uruchomieniowego, który implementuje interfejs publiczny.
1. Utwórz program kliencki, który osadzi informacje o typie z interfejsu publicznego i tworzy wystąpienie klasy z zestawu środowiska uruchomieniowego.
1. Modyfikowanie i ponowne kompilowanie zestawu środowiska uruchomieniowego.
1. Uruchom program kliencki, aby zobaczyć, że używa nowej wersji zestawu środowiska uruchomieniowego bez konieczności ponownego kompilowania.

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a>Warunki i ograniczenia

Informacje o typie można osadzić z zestawu w następujących warunkach: 

- Zestaw uwidacznia co najmniej jeden interfejs publiczny.
- Interfejsy osadzone mają adnotacje z `ComImport` atrybutami i `Guid` atrybutami o unikatowych identyfikatorach GUID.
- Zestaw jest oznaczony `ImportedFromTypeLib` atrybutem `PrimaryInteropAssembly` lub atrybutem i atrybutem na poziomie `Guid` zestawu. Szablony projektu C# wizualizacji i Visual Basic zawierają domyślnie atrybut na poziomie `Guid` zestawu.

Ponieważ podstawową funkcją osadzania typu jest obsługa zestawów międzyoperacyjnych COM, podczas osadzania informacji o typie w w pełni zarządzanym rozwiązaniu obowiązują następujące ograniczenia:

- Osadzone są tylko atrybuty charakterystyczne dla międzyoperacyjnych modelu COM. Inne atrybuty są ignorowane.
- Jeśli typ korzysta z parametrów ogólnych, a typ parametru generycznego jest typem osadzonym, ten typ nie może być używany między granicami zestawu. Przykłady przekroczenia granicy zestawu obejmują wywołanie metody z innego zestawu lub pochodny typ z typu zdefiniowanego w innym zestawie.
- Stałe nie są osadzone.
- <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Klasa nie obsługuje osadzonego typu jako klucza. Możesz zaimplementować własny typ słownika, aby obsługiwał typ osadzony jako klucz.

## <a name="create-an-interface"></a>Tworzenie interfejsu

Pierwszym krokiem jest utworzenie zestawu interfejsu równoważność typu. 

1. W programie Visual Studio, wybierz **pliku** > **New** > **projektu**.
   
1. W oknie dialogowym **Utwórz nowy projekt** wpisz *Biblioteka klas* w polu **Wyszukaj szablony** . Wybierz z listy C# szablon lub **bibliotekę klas vb (.NET Framework)** , a następnie wybierz przycisk **dalej**. 
   
1. W oknie dialogowym **Konfigurowanie nowego projektu** w obszarze **Nazwa projektu**wpisz *TypeEquivalenceInterface*, a następnie wybierz pozycję **Utwórz**. Nowy projekt zostanie utworzony.
   
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik *Class1.cs* lub *Class1. vb* , wybierz polecenie **Zmień nazwę**, a następnie zmień nazwę pliku z *Class1* na *ISampleInterface*. Należy **odpowiedzieć na** monit, aby zmienić nazwę klasy na `ISampleInterface`. Ta klasa reprezentuje interfejs publiczny dla klasy.
   
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceInterface** , a następnie wybierz polecenie **Właściwości**. 
   
1. Wybierz opcję **Kompiluj** w lewym okienku ekranu **Właściwości** , a następnie ustaw **ścieżkę wyjściową** do lokalizacji na komputerze, na przykład *C:\TypeEquivalenceSample*. Ta sama lokalizacja jest używana w tym instruktażu. 
   
1. Wybierz pozycję Podpisz w lewym **okienku na ekranie** **Właściwości** , a następnie zaznacz pole wyboru **podpisywania zestawu** . Z listy rozwijanej **Wybierz plik klucza o silnej nazwie**, wybierz pozycję **Nowy**. 
   
1. W oknie dialogowym **Tworzenie klucza o silnej nazwie** w obszarze **Nazwa pliku klucza**wpisz polecenie *Key. snk*. Usuń zaznaczenie pola wyboru **Chroń mój klucz plik hasłem** , a następnie wybierz przycisk **OK**.
   
1. Otwórz plik klasy *ISampleInterface* w edytorze kodu i Zastąp jego zawartość następującym kodem, aby utworzyć `ISampleInterface` interfejs:
   
   ```csharp
   using System;
   using System.Runtime.InteropServices;
   
   namespace TypeEquivalenceInterface
   {
       [ComImport]
       [Guid("8DA56996-A151-4136-B474-32784559F6DF")]
       public interface ISampleInterface
       {
           void GetUserInput();
           string UserInput { get; }
       }
   }
   ```
   
   ```vb
   Imports System.Runtime.InteropServices
   
   <ComImport()>
   <Guid("8DA56996-A151-4136-B474-32784559F6DF")>
   Public Interface ISampleInterface
       Sub GetUserInput()
       ReadOnly Property UserInput As String
   End Interface
   ```
   
1. W menu **Narzędzia** wybierz pozycję **Utwórz identyfikator GUID**, a następnie w oknie dialogowym **Tworzenie identyfikatora GUID** wybierz pozycję **Format rejestru**. Wybierz pozycję **Kopiuj**, a następnie wybierz pozycję **Zakończ**.
   
1. W atrybucie kodu Zastąp przykładowy identyfikator GUID identyfikatorem, który został skopiowany, i Usuń nawiasy klamrowe ( **{}** ). `Guid`
   
1. W **Eksplorator rozwiązań**rozwiń folder **Właściwości** i wybierz plik *AssemblyInfo.cs* lub *AssemblyInfo. vb* . W edytorze kodu Dodaj następujący atrybut do pliku:
   
   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```
   
   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```
   
1. Wybierz pozycję **plik** > **Zapisz wszystko** lub naciśnij **klawisze CTRL**+**SHIFT**+**S** , aby zapisać pliki i projekt.
   
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceInterface** i wybierz polecenie **Kompiluj**. Plik DLL biblioteki klas jest kompilowany i zapisywany w określonej ścieżce danych wyjściowych kompilacji, na przykład *C:\TypeEquivalenceSample*.

## <a name="create-a-runtime-class"></a>Tworzenie klasy środowiska uruchomieniowego

Następnie Utwórz klasę środowiska uruchomieniowego typu równoważność.

1. W programie Visual Studio, wybierz **pliku** > **New** > **projektu**.
   
1. W oknie dialogowym **Utwórz nowy projekt** wpisz *Biblioteka klas* w polu **Wyszukaj szablony** . Wybierz z listy C# szablon lub **bibliotekę klas vb (.NET Framework)** , a następnie wybierz przycisk **dalej**. 
   
1. W oknie dialogowym **Konfigurowanie nowego projektu** w obszarze **Nazwa projektu**wpisz *TypeEquivalenceRuntime*, a następnie wybierz pozycję **Utwórz**. Nowy projekt zostanie utworzony.
   
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik *Class1.cs* lub *Class1. vb* , wybierz polecenie **Zmień nazwę**, a następnie zmień nazwę pliku z *Class1* na *SampleClass*. Należy **odpowiedzieć na** monit, aby zmienić nazwę klasy na `SampleClass`. Ta klasa implementuje `ISampleInterface` interfejs.
   
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceInterface** i wybierz polecenie **Właściwości**. 
   
1. Wybierz opcję **Kompiluj** w lewym okienku ekranu **Właściwości** , a następnie ustaw **ścieżkę wyjściową** do tej samej lokalizacji, która została użyta dla projektu TypeEquivalenceInterface, na przykład *C:\TypeEquivalenceSample*.
   
1. Wybierz pozycję Podpisz w lewym **okienku na ekranie** **Właściwości** , a następnie zaznacz pole wyboru **podpisywania zestawu** . Z listy rozwijanej **Wybierz plik klucza o silnej nazwie**, wybierz pozycję **Nowy**. 
   
1. W oknie dialogowym **Tworzenie klucza o silnej nazwie** w obszarze **Nazwa pliku klucza**wpisz polecenie *Key. snk*. Usuń zaznaczenie pola wyboru **Chroń mój klucz plik hasłem** , a następnie wybierz przycisk **OK**.
   
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceRuntime** i wybierz polecenie **Dodaj** > **odwołanie**. 
   
1. W oknie dialogowym **Menedżer odwołań** wybierz **Przeglądaj** i przejdź do folderu Ścieżka wyjściowa. Wybierz plik *TypeEquivalenceInterface. dll* , wybierz pozycję **Dodaj**, a następnie wybierz przycisk **OK**.
   
1. W **Eksplorator rozwiązań**rozwiń folder **odwołania** i wybierz odwołanie **TypeEquivalenceInterface** . W okienku **Właściwości** Ustaw **określoną wersję** na **false** , jeśli nie została jeszcze wybrana.
   
1. Otwórz plik klasy *SampleClass* w edytorze kodu i Zastąp jego zawartość następującym kodem, aby utworzyć `SampleClass` klasę:
   
   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;
   using TypeEquivalenceInterface;
   
   namespace TypeEquivalenceRuntime
   {
       public class SampleClass : ISampleInterface
       {
           private string p_UserInput;
           public string UserInput { get { return p_UserInput; } }
   
           public void GetUserInput()
           {
               Console.WriteLine("Please enter a value:");
               p_UserInput = Console.ReadLine();
           }
       }
   }
   ```
   
   ```vb
   Imports TypeEquivalenceInterface
   
   Public Class SampleClass
       Implements ISampleInterface
   
       Private p_UserInput As String
       Public ReadOnly Property UserInput() As String Implements ISampleInterface.UserInput
           Get
               Return p_UserInput
           End Get
       End Property
   
       Public Sub GetUserInput() Implements ISampleInterface.GetUserInput
           Console.WriteLine("Please enter a value:")
           p_UserInput = Console.ReadLine()
       End Sub
   End Class
   ```
   
1. Wybierz pozycję **plik** > **Zapisz wszystko** lub naciśnij **klawisze CTRL**+**SHIFT**+**S** , aby zapisać pliki i projekt.
   
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceRuntime** i wybierz polecenie **Kompiluj**. Plik DLL biblioteki klas zostanie skompilowany i zapisany w określonej ścieżce danych wyjściowych kompilacji.

## <a name="create-a-client-project"></a>Tworzenie projektu klienta

Na koniec Utwórz program kliencki typu równoważność, który odwołuje się do zestawu interfejsu.

1. W programie Visual Studio, wybierz **pliku** > **New** > **projektu**.
   
1. W oknie dialogowym **Utwórz nowy projekt** wpisz *Console* w polu **Wyszukaj szablony** . Wybierz z listy C# szablon lub **aplikację konsolową vb (.NET Framework)** , a następnie wybierz przycisk **dalej**. 
   
1. W oknie dialogowym **Konfigurowanie nowego projektu** w obszarze **Nazwa projektu**wpisz *TypeEquivalenceClient*, a następnie wybierz pozycję **Utwórz**. Nowy projekt zostanie utworzony.
   
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceClient** i wybierz polecenie **Właściwości**. 
   
1. Wybierz opcję **Kompiluj** w lewym okienku ekranu **Właściwości** , a następnie ustaw **ścieżkę wyjściową** do tej samej lokalizacji, która została użyta dla projektu TypeEquivalenceInterface, na przykład *C:\TypeEquivalenceSample*.
   
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceClient** i wybierz polecenie **Dodaj** > **odwołanie**. 
   
1. W oknie dialogowym **Menedżer odwołań** , jeśli plik **TypeEquivalenceInterface. dll** jest już wymieniony, zaznacz go. W przeciwnym razie wybierz pozycję **Przeglądaj**, przejdź do folderu Ścieżka wyjściowa, wybierz plik *TypeEquivalenceInterface. dll* (nie *TypeEquivalenceRuntime. dll*), a następnie wybierz pozycję **Dodaj**. Kliknij przycisk **OK**.
   
1. W **Eksplorator rozwiązań**rozwiń folder **odwołania** i wybierz odwołanie **TypeEquivalenceInterface** . W okienku **Właściwości** ustaw opcję **Osadź typy międzyoperacyjności** na **wartość true**.
   
1. Otwórz plik *program.cs* lub *Module1. vb* w edytorze kodu i Zastąp jego zawartość następującym kodem, aby utworzyć program kliencki:
   
   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;
   using TypeEquivalenceInterface;
   using System.Reflection;
   
   namespace TypeEquivalenceClient
   {
       class Program
       {
           static void Main(string[] args)
           {
               Assembly sampleAssembly = Assembly.Load("TypeEquivalenceRuntime");
               ISampleInterface sampleClass =
                   (ISampleInterface)sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass");
               sampleClass.GetUserInput();
               Console.WriteLine(sampleClass.UserInput);
               Console.WriteLine(sampleAssembly.GetName().Version.ToString());
               Console.ReadLine();
           }
       }
   }
   ```
   
   ```vb
   Imports TypeEquivalenceInterface
   Imports System.Reflection
   
   Module Module1
   
       Sub Main()
           Dim sampleAssembly = Assembly.Load("TypeEquivalenceRuntime")
           Dim sampleClass As ISampleInterface = CType( _
               sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass"), ISampleInterface)
           sampleClass.GetUserInput()
           Console.WriteLine(sampleClass.UserInput)
           Console.WriteLine(sampleAssembly.GetName().Version)
           Console.ReadLine()
       End Sub
   
   End Module
   ```
   
1. Wybierz pozycję **plik** > **Zapisz wszystko** lub naciśnij **klawisze CTRL**+**SHIFT**+**S** , aby zapisać pliki i projekt.
   
1. Naciśnij klawisz **Ctrl**+**F5** , aby skompilować i uruchomić program. Zwróć uwagę, że dane wyjściowe konsoli zwracają zestaw w wersji **1.0.0.0**. 
   
## <a name="modify-the-interface"></a>Modyfikowanie interfejsu

Teraz zmodyfikuj zestaw interfejsów i zmień jego wersję. 

1. W programie Visual Studio wybierz pozycję **plik** > **Otwórz** > **projekt/rozwiązanie**, a następnie otwórz projekt **TypeEquivalenceInterface** .
   
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceInterface** i wybierz polecenie **Właściwości**. 
   
1. Wybierz pozycję **aplikacja** w lewym okienku ekranu **Właściwości** , a następnie wybierz pozycję **Informacje o zestawie**. 
   
1. W oknie dialogowym **Informacje o zestawie** Zmień **wersję zestawu** i wartość **wersji pliku** na *2.0.0.0*, a następnie wybierz przycisk **OK**.
   
1. Otwórz plik *SampleInterface.cs* lub *SampleInterface. vb* i Dodaj następujący wiersz `ISampleInterface` kodu do interfejsu:
   
   ```csharp
   DateTime GetDate();
   ```
   
   ```vb
   Function GetDate() As Date
   ```
   
1. Wybierz pozycję **plik** > **Zapisz wszystko** lub naciśnij **klawisze CTRL**+**SHIFT**+**S** , aby zapisać pliki i projekt.
   
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceInterface** i wybierz polecenie **Kompiluj**. Nowa wersja pliku DLL biblioteki klas jest kompilowana i zapisywana w ścieżce danych wyjściowych kompilacji.

## <a name="modify-the-runtime-class"></a>Modyfikowanie klasy środowiska uruchomieniowego

Należy również zmodyfikować klasę środowiska uruchomieniowego i zaktualizować jej wersję. 

1. W programie Visual Studio wybierz pozycję **plik** > **Otwórz** > **projekt/rozwiązanie**, a następnie otwórz projekt **TypeEquivalenceRuntime** .
   
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceRuntime** i wybierz polecenie **Właściwości**. 
   
1. Wybierz pozycję **aplikacja** w lewym okienku ekranu **Właściwości** , a następnie wybierz pozycję **Informacje o zestawie**. 
   
1. W oknie dialogowym **Informacje o zestawie** Zmień **wersję zestawu** i wartość **wersji pliku** na *2.0.0.0*, a następnie wybierz przycisk **OK**.
   
1. Otwórz plik *SampleClass.cs* lub *SampleClass. vb* i Dodaj następujący `SampleClass` kod do klasy:
   
   ```csharp
    public DateTime GetDate()
    {
        return DateTime.Now;
    }
   ```
   
   ```vb
   Public Function GetDate() As DateTime Implements ISampleInterface.GetDate
       Return Now
   End Function
   ```
   
1. Wybierz pozycję **plik** > **Zapisz wszystko** lub naciśnij **klawisze CTRL**+**SHIFT**+**S** , aby zapisać pliki i projekt.
   
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceRuntime** i wybierz polecenie **Kompiluj**. Nowa wersja pliku DLL biblioteki klas jest kompilowana i zapisywana w ścieżce danych wyjściowych kompilacji.

## <a name="run-the-updated-client-program"></a>Uruchom zaktualizowany program kliencki 

Przejdź do lokalizacji folderu danych wyjściowych kompilacji i uruchom *TypeEquivalenceClient. exe*. Zwróć uwagę, że dane wyjściowe konsoli teraz odzwierciedlają nową wersję `TypeEquivalenceRuntime` zestawu, *2.0.0.0*, bez ponownej kompilacji programu.

## <a name="see-also"></a>Zobacz także

- [/Link (C# opcje kompilatora)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
- [C#Przewodnik programowania](../../csharp/programming-guide/index.md)
- [Koncepcje programowania (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Program z zestawami](program.md)
- [Zestawy w środowisku .NET](index.md)
