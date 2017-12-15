---
title: "Wskazówki: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5b07b940d6287de0caf41c7d15f3036ad4041ad0
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2017
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-c"></a>Wskazówki: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (C#)
Osadzenie informacji o typie z zarządzanego zestawu o silnej nazwie słabo można połączyć typów w aplikacji w celu osiągnięcia niezależność od wersji. Oznacza to, że program mogą być zapisywane na użyć typów z wielu wersji biblioteki zarządzanej, bez konieczności ponownie skompilowana dla każdej wersji.  
  
 Osadzenie typu jest często używany pomocą modelu COM, takie jak aplikacji, która używa obiekty automatyzacji z witryny Microsoft Office. Osadzanie informacji o typie włącza tę samą kompilację programu w różnych wersjach pakietu Microsoft Office na różnych komputerach. Jednak umożliwia także osadzanie z pełni zarządzane rozwiązanie typu.  
  
 Można ją osadzić informacji o typie z zestawu, który ma następującą charakterystykę:  
  
-   Zestaw ujawnia co najmniej jeden interfejs publiczny.  
  
-   Osadzony interfejsy są opatrzoną `ComImport` atrybutu i `Guid` atrybutu (i unikatowy identyfikator GUID).  
  
-   Zestaw jest oznaczony za pomocą `ImportedFromTypeLib` atrybutu lub `PrimaryInteropAssembly` atrybut i poziomu zestawu `Guid` atrybutu. (Domyślnie szablony projektów Visual C# obejmuje dane poziomu zestawu `Guid` atrybutu.)  
  
 Po określeniu interfejsów publicznych, które mogą być osadzone, można utworzyć klasy środowiska uruchomieniowego, które implementują te interfejsy. Program kliencki może następnie osadź informacji o typie dla tych interfejsów w czasie projektowania, umieszczając odwołanie do zestawu, który zawiera interfejsy publiczne i ustawienie `Embed Interop Types` właściwości odwołania do `True`. Jest to równoważne przy użyciu kompilatora wiersza polecenia i odwołanie do zestawu przy użyciu `/link` — opcja kompilatora. Program kliencki może następnie załadowanie wystąpień obiektów czasu wykonywania typu te interfejsy. Jeśli tworzysz nową wersję używanemu zestawowi silną nazwą środowiska uruchomieniowego, program kliencki nie ma do ponownej kompilacji z zestawu zaktualizowane środowiska wykonawczego. Zamiast tego program kliencki będzie później nadal używać niezależnie od wersji zestawu środowiska wykonawczego jest dostępna, korzystając z informacji osadzonym typem interfejsów publicznych.  
  
 Ponieważ podstawowej funkcji typu osadzenia obsługuje osadzanie informacji o typie z zestawów międzyoperacyjnych COM, osadzenia informacji o typie w pełni zarządzane rozwiązanie obowiązują następujące ograniczenia:  
  
-   Tylko atrybuty specyficzne dla międzyoperacyjności z modelem COM są osadzone; inne atrybuty są ignorowane.  
  
-   Jeśli typem używa parametrów ogólnych i typ parametru ogólnego jest osadzonym typem, tego typu nie można użyć granicy zestawu. Przekraczaniu granic zestawu przykładów wywoływanie metody z innego zestawu lub typu pochodnego od typu zdefiniowanej w innym zestawie.  
  
-   Stałe nie są osadzone.  
  
-   <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Klasa nie obsługuje typu osadzonego jako klucza. Można zaimplementować własne typu słownika do obsługi typu osadzonego jako klucza.  
  
 W tym przewodniku spowoduje wykonanie następujących czynności:  
  
-   Utwórz zestaw o silnej nazwie zawiera interfejs publiczny, który zawiera informacje o typie, który można ją osadzić.  
  
-   Tworzenie zestawu o silnej nazwie środowiska uruchomieniowego, który implementuje ten interfejs publiczny.  
  
-   Utwórz program kliencki osadza informacje o typie z interfejsu publicznego, który tworzy wystąpienie klasy z zestawu środowiska wykonawczego.  
  
-   Zmodyfikuj i skompiluj ponownie zestawu środowiska wykonawczego.  
  
-   Uruchom program klienta, aby zobaczyć, że nowa wersja zestawu czasu wykonywania jest używana bez konieczności ponownego kompilowania programu klienckiego.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-an-interface"></a>Tworzenie interfejsu  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a>Aby utworzyć projekt interfejsu pełnienia roli równoważnika typu  
  
1.  W programie Visual Studio na **pliku** menu, wybierz **nowy** , a następnie kliknij przycisk **projektu**.  
  
2.  W **nowy projekt** okna dialogowego, **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone. Wybierz **biblioteki klas** w **szablony** okienka. W **nazwa** wpisz `TypeEquivalenceInterface`, a następnie kliknij przycisk **OK**. Nowy projekt zostanie utworzony.  
  
3.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik Class1.cs i kliknij przycisk **zmienić**. Zmień nazwę pliku do `ISampleInterface.cs` i naciśnij klawisz ENTER. Zmiana nazwy pliku spowoduje również zmianę nazwy klasy, która ma `ISampleInterface`. Ta klasa będzie reprezentować publiczny interfejs dla klasy.  
  
4.  Kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface, a następnie kliknij przycisk **właściwości**. Kliknij przycisk **kompilacji** kartę. Ustaw ścieżkę wyjściową do prawidłowej lokalizacji na komputerze deweloperskim takich jak `C:\TypeEquivalenceSample`. Ta lokalizacja będą również używane w kolejnym kroku w tym przewodniku.  
  
5.  Podczas edycji nadal właściwości projektu, kliknij przycisk **podpisywanie** kartę. Wybierz **Podpisz zestaw** opcji. W **wybierz plik klucza o silnej nazwie** kliknij **< nowy... >**. W **nazwę pliku klucza** wpisz `key.snk`. Wyczyść **ochrony pliku klucza przy użyciu hasła** pole wyboru. Kliknij przycisk **OK**.  
  
6.  Otwórz plik ISampleInterface.cs. Dodaj następujący kod do pliku klasy ISampleInterface utworzyć interfejsu ISampleInterface.  
  
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
  
7.  Na **narzędzia** menu, kliknij przycisk **utworzyć identyfikatora Guid**. W **utworzyć identyfikatora GUID** okno dialogowe, kliknij przycisk **Format rejestru** , a następnie kliknij przycisk **kopiowania**. Kliknij przycisk **zakończenia**.  
  
8.  W `Guid` atrybutu, usuń przykładowe identyfikator GUID i Wklej skopiowany z identyfikatora GUID **utworzyć identyfikatora GUID** okno dialogowe. Usuń nawiasy klamrowe ({}) skopiowanych identyfikatora GUID.  
  
9. W **Eksploratora rozwiązań**, rozwiń węzeł **właściwości** folderu. Kliknij dwukrotnie plik AssemblyInfo.cs. Dodaj następujący atrybut w pliku.  
  
    ```csharp  
    [assembly: ImportedFromTypeLib("")]  
    ```  
  
     Zapisz plik.  
  
10. Zapisz projekt.  
  
11. Kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface, a następnie kliknij przycisk **kompilacji**. Plik klasy biblioteki DLL są kompilowane i zapisane w ścieżce wyjściowej określonej kompilacji (na przykład C:\TypeEquivalenceSample).  
  
## <a name="creating-a-runtime-class"></a>Tworzenie klasy środowiska wykonawczego  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a>Aby utworzyć projekt środowiska uruchomieniowego pełnienia roli równoważnika typu  
  
1.  W programie Visual Studio na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu**.  
  
2.  W **nowy projekt** okna dialogowego, **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone. Wybierz **biblioteki klas** w **szablony** okienka. W **nazwa** wpisz `TypeEquivalenceRuntime`, a następnie kliknij przycisk **OK**. Nowy projekt zostanie utworzony.  
  
3.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik Class1.cs i kliknij przycisk **zmienić**. Zmień nazwę pliku do `SampleClass.cs` i naciśnij klawisz ENTER. Zmiana nazwy pliku również zmienia nazwę klasy, która ma `SampleClass`. Ta klasa będzie implementowany `ISampleInterface` interfejsu.  
  
4.  Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij przycisk **właściwości**. Kliknij przycisk **kompilacji** kartę. Ustaw ścieżkę danych wyjściowych do tej samej lokalizacji, używany w projekcie TypeEquivalenceInterface, na przykład `C:\TypeEquivalenceSample`.  
  
5.  Podczas edycji nadal właściwości projektu, kliknij przycisk **podpisywanie** kartę. Wybierz **Podpisz zestaw** opcji. W **wybierz plik klucza o silnej nazwie** kliknij **< nowy... >**. W **nazwę pliku klucza** wpisz `key.snk`. Wyczyść **ochrony pliku klucza przy użyciu hasła** pole wyboru. Kliknij przycisk **OK**.  
  
6.  Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij przycisk **Dodaj odwołanie**. Kliknij przycisk **Przeglądaj** karcie i przejdź do folderu o podanej ścieżce danych wyjściowych. Wybierz plik TypeEquivalenceInterface.dll, a następnie kliknij przycisk **OK**.  
  
7.  W **Eksploratora rozwiązań**, rozwiń węzeł **odwołania** folderu. Wybierz odwołanie TypeEquivalenceInterface. W oknie właściwości odwołania TypeEquivalenceInterface ustawić **określonej wersji** właściwości **False**.  
  
8.  Dodaj następujący kod do pliku klasy SampleClass, aby utworzyć klasę SampleClass.  
  
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
    )  
    ```  
  
9. Zapisz projekt.  
  
10. Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij przycisk **kompilacji**. Plik klasy biblioteki DLL są kompilowane i zapisane w ścieżce wyjściowej określonej kompilacji (na przykład C:\TypeEquivalenceSample).  
  
## <a name="creating-a-client-project"></a>Tworzenie projektu klienta  
  
#### <a name="to-create-the-type-equivalence-client-project"></a>Aby utworzyć projekt klienta pełnienia roli równoważnika typu  
  
1.  W programie Visual Studio na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu**.  
  
2.  W **nowy projekt** okna dialogowego, **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone. Wybierz **aplikacji konsoli** w **szablony** okienka. W **nazwa** wpisz `TypeEquivalenceClient`, a następnie kliknij przycisk **OK**. Nowy projekt zostanie utworzony.  
  
3.  Kliknij prawym przyciskiem myszy projekt TypeEquivalenceClient, a następnie kliknij przycisk **właściwości**. Kliknij przycisk **kompilacji** kartę. Ustaw ścieżkę danych wyjściowych do tej samej lokalizacji, używany w projekcie TypeEquivalenceInterface, na przykład `C:\TypeEquivalenceSample`.  
  
4.  Kliknij prawym przyciskiem myszy projekt TypeEquivalenceClient, a następnie kliknij przycisk **Dodaj odwołanie**. Kliknij przycisk **Przeglądaj** karcie i przejdź do folderu o podanej ścieżce danych wyjściowych. Wybierz plik TypeEquivalenceInterface.dll (nie TypeEquivalenceRuntime.dll), a następnie kliknij przycisk **OK**.  
  
5.  W **Eksploratora rozwiązań**, rozwiń węzeł **odwołania** folderu. Wybierz odwołanie TypeEquivalenceInterface. W oknie właściwości odwołania TypeEquivalenceInterface ustawić **Osadź typy międzyoperacyjne** właściwości **True**.  
  
6.  Dodaj następujący kod do pliku Program.cs, aby utworzyć program klienta.  
  
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
  
7.  Naciśnij klawisze CTRL + F5, aby skompilować i uruchomić program.  
  
## <a name="modifying-the-interface"></a>Modyfikowanie interfejsu  
  
#### <a name="to-modify-the-interface"></a>Aby zmodyfikować interfejs  
  
1.  W programie Visual Studio na **pliku** menu wskaż **Otwórz**, a następnie kliknij przycisk **projektu/rozwiązania**.  
  
2.  W **Otwórz projekt** okno dialogowe, kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface, a następnie kliknij przycisk **właściwości**. Kliknij przycisk **aplikacji** kartę. Kliknij przycisk **informacji o zestawie** przycisku. Zmień **wersja zestawu** i **wersja pliku** wartości do `2.0.0.0`.  
  
3.  Otwórz plik SampleInterface.cs. Dodaj następujący wiersz kodu do interfejsu ISampleInterface.  
  
    ```csharp  
    DateTime GetDate();  
    ```  
  
     Zapisz plik.  
  
4.  Zapisz projekt.  
  
5.  Kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface, a następnie kliknij przycisk **kompilacji**. Nowa wersja pliku klasy biblioteki DLL są kompilowane i zapisać w ścieżce wyjściowej określonej kompilacji (na przykład C:\TypeEquivalenceSample).  
  
## <a name="modifying-the-runtime-class"></a>Modyfikowanie klasy środowiska wykonawczego  
  
#### <a name="to-modify-the-runtime-class"></a>Aby zmodyfikować klasy środowiska wykonawczego  
  
1.  W programie Visual Studio na **pliku** menu wskaż **Otwórz**, a następnie kliknij przycisk **projektu/rozwiązania**.  
  
2.  W **Otwórz projekt** okno dialogowe, kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime i kliknij przycisk **właściwości**. Kliknij przycisk **aplikacji** kartę. Kliknij przycisk **informacji o zestawie** przycisku. Zmień **wersja zestawu** i **wersja pliku** wartości do `2.0.0.0`.  
  
3.  Otwórz plik SampleClass.cs. Dodaj następujące wiersze kodu do klasy SampleClass.  
  
    ```csharp  
    public DateTime GetDate()  
    {  
        return DateTime.Now;  
    }  
    ```  
  
     Zapisz plik.  
  
4.  Zapisz projekt.  
  
5.  Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij przycisk **kompilacji**. Zaktualizowaną wersję pliku klasy biblioteki DLL są kompilowane i zapisać w ścieżce wyjściowej wcześniej określonej kompilacji (na przykład C:\TypeEquivalenceSample).  
  
6.  W Eksploratorze plików otwórz folder wyjściowy ścieżki (na przykład C:\TypeEquivalenceSample). Kliknij dwukrotnie TypeEquivalenceClient.exe do uruchomienia programu. Program będzie odzwierciedlać nową wersję zestawu TypeEquivalenceRuntime bez konieczności została ponownie skompilowana.  
  
## <a name="see-also"></a>Zobacz też  
 [/ Link (opcje kompilatora C#)](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)  
 [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)  
 [Programowanie za pomocą zestawów](../../../../framework/app-domains/programming-with-assemblies.md)  
 [Zestawy i Globalna pamięć podręczna zestawów (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)
