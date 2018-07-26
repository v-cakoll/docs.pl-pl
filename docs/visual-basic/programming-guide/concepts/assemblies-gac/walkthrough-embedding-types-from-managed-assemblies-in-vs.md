---
title: 'Przewodnik: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 56ed12ba-adff-4e9c-a668-7fcba80c4795
ms.openlocfilehash: 1f6176746b783d020c809fb0b5d55d741ce0148b
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245479"
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-visual-basic"></a>Przewodnik: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (Visual Basic)
W przypadku osadzenia informacji o typie z zarządzanego zestawu z silną nazwą, luźno połączyć typy w aplikacji, aby osiągnąć niezależność. Oznacza to by używał typów z wielu wersji zarządzanej biblioteki bez konieczności ponownie skompilowana dla każdej wersji można napisać program.  
  
 Osadzenie typu jest często używany za pomocą modelu COM, takie jak aplikacja, która używa obiektów automatyzacji z Microsoft Office. Osadzanie informacji o typie umożliwia tym samym kompilację programu do pracy z różnymi wersjami pakietu Microsoft Office na różnych komputerach. Jednak można również użyć osadzanie przy użyciu w pełni zarządzane rozwiązanie typu.  
  
 Informacje o typie mogą być osadzone z zestawu, który ma następujące cechy:  
  
-   Zestaw udostępnia co najmniej jeden interfejs publiczny.  
  
-   Osadzone interfejsy są oznaczony za pomocą `ComImport` atrybutu i `Guid` atrybutu (i unikatowy identyfikator GUID).  
  
-   Zestaw jest oznaczony za pomocą `ImportedFromTypeLib` atrybutu lub `PrimaryInteropAssembly` atrybut i poziomie zestawu `Guid` atrybutu. (Domyślnie szablony projektów Visual Basic zawierają na poziomie zestawu `Guid` atrybutu.)  
  
 Po określeniu publicznych interfejsów, które mogą być osadzone, można utworzyć klasy środowiska wykonawczego, które implementują te interfejsy. Program kliencki następnie osadzić informacje o typie dla tych interfejsów w czasie projektowania, odwołując się do zestawu, który zawiera interfejsy publiczne i ustawienie `Embed Interop Types` właściwości odwołania do `True`. Jest to równoważne do używania kompilatora wiersza polecenia i odwołanie do zestawu przy użyciu `/link` — opcja kompilatora. Program kliencki może następnie załadować wystąpień obiektów środowiska uruchomieniowego wpisanych w formie tych interfejsów. Jeśli tworzysz nową wersję zestawu o silnej nazwie środowiska uruchomieniowego, program kliencki nie ma być ponownie kompilowane przy użyciu zestawu zaktualizowanego środowiska wykonawczego. Zamiast tego program kliencki w dalszym ciągu używać niezależnie od wersji zestawu środowiska wykonawczego dostępnego, korzystając z informacji osadzonego typu interfejsów publicznych.  
  
 Ponieważ główna funkcja osadzania typu jest do obsługi, osadzanie informacji o typie z zestawów międzyoperacyjnych COM, gdy osadzanie informacji o typie w pełni zarządzane rozwiązanie obowiązują następujące ograniczenia:  
  
-   Tylko atrybuty specyficzne dla współdziałania z modelem COM są osadzone; inne atrybuty są ignorowane.  
  
-   Jeśli typ używa parametrów ogólnych, typ parametru ogólnego jest osadzonym typem tego typu nie można użyć granicy zestawu. Przecinające się w granicach zestawu przykłady wywołanie metody z innego zestawu lub typem pochodząca z typu zdefiniowane w innym zestawie.  
  
-   Stałe nie są osadzone.  
  
-   <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Klasa nie obsługuje osadzonego typu jako klucz. Można zaimplementować swój własny typ słownika do obsługi osadzonego typu jako klucz.  
  
 W tym instruktażu wykonasz następujące:  
  
-   Utwórz zestaw o silnej nazwie, która ma interfejs publiczny, który zawiera informacje o typie, który może zostać osadzony.  
  
-   Utwórz zestaw o silnej nazwie środowiska uruchomieniowego, który implementuje ten interfejs publiczny.  
  
-   Utwórz program kliencki osadza informacje o typie z publicznego interfejsu, która tworzy wystąpienie klasy z zestawu środowiska wykonawczego.  
  
-   Zmodyfikuj i ponownie skompiluj zestawu środowiska wykonawczego.  
  
-   Uruchom program klienta, aby zobaczyć, że nowa wersja zestawu środowiska wykonawczego jest używana bez konieczności ponownego kompilowania programów klienckich.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-an-interface"></a>Tworzenie interfejsu  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a>Aby utworzyć projekt interfejsu równoważności typu  
  
1.  W programie Visual Studio na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**.  
  
2.  W **nowy projekt** dialogowym **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone. Wybierz **biblioteki klas** w **szablony** okienka. W **nazwa** wpisz `TypeEquivalenceInterface`, a następnie kliknij przycisk **OK**. Nowy projekt zostanie utworzony.  
  
3.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik Class1.vb i kliknij przycisk **Zmień nazwę**. Zmień nazwę pliku do `ISampleInterface.vb` i naciśnij klawisz ENTER. Zmiana nazwy pliku spowoduje również zmianę nazwy klasy, która ma `ISampleInterface`. Ta klasa będzie reprezentować publiczny interfejs dla klasy.  
  
4.  Kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface, a następnie kliknij przycisk **właściwości**. Kliknij przycisk **skompilować** kartę. Ustaw ścieżkę wyjściową do prawidłowej lokalizacji na komputerze deweloperskim, takich jak `C:\TypeEquivalenceSample`. Ta lokalizacja będzie używana również w dalszej części tego przewodnika.  
  
5.  Podczas edytowania nadal właściwości projektu, kliknij przycisk **podpisywanie** kartę. Wybierz **Podpisz zestaw** opcji. W **wybierz plik klucza o silnej nazwie** kliknij **< nowy … >**. W **nazwę pliku klucza** wpisz `key.snk`. Wyczyść **Chroń mój plik klucza przy użyciu hasła** pole wyboru. Kliknij przycisk **OK**.  
  
6.  Otwórz plik ISampleInterface.vb. Dodaj następujący kod do pliku klasy ISampleInterface, aby utworzyć interfejs ISampleInterface.  
  
    ```vb  
    Imports System.Runtime.InteropServices  
  
    <ComImport()>  
    <Guid("8DA56996-A151-4136-B474-32784559F6DF")>  
    Public Interface ISampleInterface  
        Sub GetUserInput()  
        ReadOnly Property UserInput As String  
    End Interface  
    ```  
  
7.  Na **narzędzia** menu, kliknij przycisk **Utwórz Guid**. W **Utwórz GUID** okno dialogowe, kliknij przycisk **Format rejestru** a następnie kliknij przycisk **kopiowania**. Kliknij przycisk **zakończenia**.  
  
8.  W `Guid` atrybutu, usuwanie przykładowy identyfikator GUID i wkleić identyfikator GUID, który został skopiowany z **Utwórz GUID** okno dialogowe. Usuń nawiasy klamrowe ({}) ze skopiowanego identyfikatora GUID.  
  
9. Na **projektu** menu, kliknij przycisk **Pokaż wszystkie pliki**.  
  
10. W **Eksploratora rozwiązań**, rozwiń węzeł **mój projekt** folderu. Kliknij dwukrotnie AssemblyInfo.vb. Dodaj następujący atrybut w pliku.  
  
    ```vb  
    <Assembly: ImportedFromTypeLib("")>  
    ```  
  
     Zapisz plik.  
  
11. Zapisz projekt.  
  
12. Kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface, a następnie kliknij przycisk **kompilacji**. Plik klasy biblioteki .dll jest kompilowany i zapisać ścieżkę wyjściową określonej kompilacji (na przykład C:\TypeEquivalenceSample).  
  
## <a name="creating-a-runtime-class"></a>Tworzenie klasy środowiska uruchomieniowego  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a>Aby utworzyć projekt środowiska uruchomieniowego równoważności typu  
  
1.  W programie Visual Studio na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**.  
  
2.  W **nowy projekt** dialogowym **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone. Wybierz **biblioteki klas** w **szablony** okienka. W **nazwa** wpisz `TypeEquivalenceRuntime`, a następnie kliknij przycisk **OK**. Nowy projekt zostanie utworzony.  
  
3.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik Class1.vb i kliknij przycisk **Zmień nazwę**. Zmień nazwę pliku do `SampleClass.vb` i naciśnij klawisz ENTER. Również zmienić nazwę pliku zmienia nazwę klasy, która ma `SampleClass`. Ta klasa wdroży `ISampleInterface` interfejsu.  
  
4.  Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij przycisk **właściwości**. Kliknij przycisk **skompilować** kartę. Ustaw ścieżkę wyjściową do tej samej lokalizacji, które są używane w projekcie TypeEquivalenceInterface, na przykład `C:\TypeEquivalenceSample`.  
  
5.  Podczas edytowania nadal właściwości projektu, kliknij przycisk **podpisywanie** kartę. Wybierz **Podpisz zestaw** opcji. W **wybierz plik klucza o silnej nazwie** kliknij **< nowy … >**. W **nazwę pliku klucza** wpisz `key.snk`. Wyczyść **Chroń mój plik klucza przy użyciu hasła** pole wyboru. Kliknij przycisk **OK**.  
  
6.  Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij przycisk **Dodaj odwołanie**. Kliknij przycisk **Przeglądaj** kartę, a następnie przejdź do folderu o podanej ścieżce danych wyjściowych. Wybierz plik TypeEquivalenceInterface.dll, a następnie kliknij przycisk **OK**.  
  
7.  Na **projektu** menu, kliknij przycisk **Pokaż wszystkie pliki**.  
  
8.  W **Eksploratora rozwiązań**, rozwiń węzeł **odwołania** folderu. Wybierz odwołanie TypeEquivalenceInterface. W oknie dialogowym właściwości odwołania TypeEquivalenceInterface ustaw **określonej wersji** właściwości **False**.  
  
9. Dodaj następujący kod do pliku klasy SampleClass, aby utworzyć klasę SampleClass.  
  
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
  
10. Zapisz projekt.  
  
11. Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij przycisk **kompilacji**. Plik klasy biblioteki .dll jest kompilowany i zapisać ścieżkę wyjściową określonej kompilacji (na przykład C:\TypeEquivalenceSample).  
  
## <a name="creating-a-client-project"></a>Tworzenie projektu klienta  
  
#### <a name="to-create-the-type-equivalence-client-project"></a>Aby utworzyć projekt klienta równoważności typu  
  
1.  W programie Visual Studio na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**.  
  
2.  W **nowy projekt** dialogowym **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone. Wybierz **aplikację Konsolową** w **szablony** okienka. W **nazwa** wpisz `TypeEquivalenceClient`, a następnie kliknij przycisk **OK**. Nowy projekt zostanie utworzony.  
  
3.  Kliknij prawym przyciskiem myszy projekt TypeEquivalenceClient, a następnie kliknij przycisk **właściwości**. Kliknij przycisk **skompilować** kartę. Ustaw ścieżkę wyjściową do tej samej lokalizacji, które są używane w projekcie TypeEquivalenceInterface, na przykład `C:\TypeEquivalenceSample`.  
  
4.  Kliknij prawym przyciskiem myszy projekt TypeEquivalenceClient, a następnie kliknij przycisk **Dodaj odwołanie**. Kliknij przycisk **Przeglądaj** kartę, a następnie przejdź do folderu o podanej ścieżce danych wyjściowych. Wybierz plik TypeEquivalenceInterface.dll (nie TypeEquivalenceRuntime.dll), a następnie kliknij przycisk **OK**.  
  
5.  Na **projektu** menu, kliknij przycisk **Pokaż wszystkie pliki**.  
  
6.  W **Eksploratora rozwiązań**, rozwiń węzeł **odwołania** folderu. Wybierz odwołanie TypeEquivalenceInterface. W oknie dialogowym właściwości odwołania TypeEquivalenceInterface ustaw **Osadź typy współdziałania** właściwości **True**.  
  
7.  Dodaj następujący kod do pliku Module1.vb, aby utworzyć program klienta.  
  
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
  
8.  Naciśnij kombinację klawiszy CTRL + F5, aby skompilować i uruchomić program.  
  
## <a name="modifying-the-interface"></a>Modyfikowanie interfejsu  
  
#### <a name="to-modify-the-interface"></a>Aby zmodyfikować interfejs  
  
1.  W programie Visual Studio na **pliku** menu wskaż **Otwórz**, a następnie kliknij przycisk **projekt/rozwiązanie**.  
  
2.  W **Otwórz projekt** okno dialogowe, kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface, a następnie kliknij przycisk **właściwości**. Kliknij przycisk **aplikacji** kartę. Kliknij przycisk **informacje o zestawie** przycisku. Zmiana **wersji zestawu** i **wersja pliku** wartości `2.0.0.0`.  
  
3.  Otwórz plik ISampleInterface.vb. Dodaj następujący wiersz kodu do interfejsu ISampleInterface.  
  
    ```vb  
    Function GetDate() As Date  
    ```  
  
     Zapisz plik.  
  
4.  Zapisz projekt.  
  
5.  Kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface, a następnie kliknij przycisk **kompilacji**. Nową wersję pliku klasy biblioteki .dll jest kompilowany i zapisać w ścieżce wyjściowej określonej kompilacji (na przykład C:\TypeEquivalenceSample).  
  
## <a name="modifying-the-runtime-class"></a>Modyfikowanie klasy środowiska uruchomieniowego  
  
#### <a name="to-modify-the-runtime-class"></a>Aby zmodyfikować klasy środowiska uruchomieniowego  
  
1.  W programie Visual Studio na **pliku** menu wskaż **Otwórz**, a następnie kliknij przycisk **projekt/rozwiązanie**.  
  
2.  W **Otwórz projekt** okna dialogowego pole, kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime i kliknij przycisk **właściwości**. Kliknij przycisk **aplikacji** kartę. Kliknij przycisk **informacje o zestawie** przycisku. Zmiana **wersji zestawu** i **wersja pliku** wartości `2.0.0.0`.  
  
3.  Otwórz SampleClass.vbfile. Dodaj następujące wiersze kodu do klasy SampleClass.  
  
```vb  
Public Function GetDate() As DateTime Implements ISampleInterface.GetDate  
    Return Now  
End Function  
```  
  
     Save the file.  
  
4.  Zapisz projekt.  
  
5.  Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij przycisk **kompilacji**. Zaktualizowaną wersję pliku klasy biblioteki .dll jest kompilowany i zapisać w ścieżce wyjściowej wcześniej określonej kompilacji (na przykład C:\TypeEquivalenceSample).  
  
6.  W Eksploratorze plików otwórz folder wyjściowy ścieżki (na przykład C:\TypeEquivalenceSample). Kliknij dwukrotnie TypeEquivalenceClient.exe do uruchomienia programu. Program będzie odzwierciedlać nową wersję zestawu TypeEquivalenceRuntime bez konieczności został ponownie kompilowana.  
  
## <a name="see-also"></a>Zobacz też  
 [/ Link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)  
 [Pojęcia związane z programowaniem](../../../../visual-basic/programming-guide/concepts/index.md)  
 [Programowanie za pomocą zestawów](../../../../framework/app-domains/programming-with-assemblies.md)  
 [Zestawy i Globalna pamięć podręczna zestawów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)
