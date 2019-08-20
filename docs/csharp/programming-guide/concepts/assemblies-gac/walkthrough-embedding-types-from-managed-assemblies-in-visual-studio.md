---
title: 'Przewodnik: Osadzanie typów z zestawów zarządzanych w programie Visual StudioC#()'
ms.date: 07/20/2015
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
ms.openlocfilehash: 5e6494f133128e3982aa07323d2c65b9fa5de47b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595797"
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-c"></a>Przewodnik: Osadzanie typów z zestawów zarządzanych w programie Visual StudioC#()

Jeśli osadzisz informacje o typie z zestawu o silnej nazwie zarządzanej, możesz luźno połączyć typy w aplikacji, aby osiągnąć niezależność wersji. Oznacza to, że program można napisać tak, aby używał typów z wielu wersji biblioteki zarządzanej bez konieczności ponownego kompilowania dla każdej wersji.

Osadzanie typów jest często używane z międzyoperacyjnym modelem COM, takim jak aplikacja, która korzysta z obiektów automatyzacji z Microsoft Office. Osadzanie informacji o typie umożliwia tej samej kompilacji programu do pracy z różnymi wersjami Microsoft Office na różnych komputerach. Można jednak również używać osadzania typu z w pełni zarządzanym rozwiązaniem.

Informacje o typie mogą być osadzone z zestawu o następujących cechach:

- Zestaw uwidacznia co najmniej jeden interfejs publiczny.

- Interfejsy osadzone mają adnotację z `ComImport` atrybutem `Guid` i atrybutem (i unikatowym identyfikatorem GUID).

- Zestaw jest oznaczony `ImportedFromTypeLib` atrybutem `PrimaryInteropAssembly` lub atrybutem i atrybutem na poziomie `Guid` zestawu. (Domyślnie szablony projektów wizualnych C# zawierają atrybut na poziomie `Guid` zestawu).

Po określeniu interfejsów publicznych, które mogą być osadzone, można utworzyć klasy środowiska uruchomieniowego, które implementują te interfejsy. Program kliencki może następnie osadzić informacje o typie dla tych interfejsów w czasie projektowania, odwołując się do zestawu, który zawiera interfejsy publiczne, `Embed Interop Types` i ustawiając właściwość odwołania na `True`. Jest to równoznaczne z użyciem kompilatora wiersza polecenia i odwołującego się do zestawu `/link` przy użyciu opcji kompilatora. Następnie program kliencki może ładować wystąpienia obiektów środowiska uruchomieniowego, które zostały wpisane jako te interfejsy. Jeśli utworzysz nową wersję zestawu o silnej nazwie środowiska uruchomieniowego, program kliencki nie musi zostać ponownie skompilowany przy użyciu zaktualizowanego zestawu środowiska uruchomieniowego. Zamiast tego program kliencki nadal korzysta z niezależnej wersji zestawu środowiska uruchomieniowego, przy użyciu informacji o typie osadzonym dla interfejsów publicznych.

Ponieważ podstawową funkcją osadzania typu jest obsługa osadzania informacji o typie z zestawów międzyoperacyjnych modelu COM, podczas osadzania informacji o typie w w pełni zarządzanym rozwiązaniu obowiązują następujące ograniczenia:

- Osadzone są tylko atrybuty specyficzne dla międzyoperacyjnego modelu COM; inne atrybuty są ignorowane.

- Jeśli typ korzysta z parametrów ogólnych, a typ parametru generycznego jest typem osadzonym, ten typ nie może być używany między granicami zestawu. Przykłady przekroczenia granicy zestawu obejmują wywołanie metody z innego zestawu lub pochodny typ z typu zdefiniowanego w innym zestawie.

- Stałe nie są osadzone.

- <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Klasa nie obsługuje osadzonego typu jako klucza. Możesz zaimplementować własny typ słownika, aby obsługiwał typ osadzony jako klucz.

W tym instruktażu wykonasz następujące czynności:

- Utwórz zestaw o silnej nazwie z interfejsem publicznym zawierającym informacje o typie, które mogą być osadzone.

- Utwórz zestaw o silnej nazwie środowiska uruchomieniowego, który implementuje ten interfejs publiczny.

- Utwórz program kliencki, który osadzi informacje o typie z interfejsu publicznego i tworzy wystąpienie klasy z zestawu środowiska uruchomieniowego.

- Modyfikowanie i ponowne kompilowanie zestawu środowiska uruchomieniowego.

- Uruchom program kliencki, aby zobaczyć, że nowa wersja zestawu środowiska uruchomieniowego jest używana bez konieczności ponownego kompilowania programu klienckiego.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-an-interface"></a>Tworzenie interfejsu

#### <a name="to-create-the-type-equivalence-interface-project"></a>Aby utworzyć projekt interfejsu równoważności typu

1. W programie Visual Studio w menu **plik** wybierz polecenie **Nowy** , a następnie kliknij pozycję **projekt**.

2. W oknie dialogowym **Nowy projekt** w okienku **typy projektów** upewnij się, że wybrano opcję **Windows** . W okienku **Szablony** wybierz pozycję **Biblioteka klas** . W polu **Nazwa** wpisz `TypeEquivalenceInterface`, a następnie kliknij przycisk **OK**. Nowy projekt zostanie utworzony.

3. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik Class1.cs i kliknij polecenie **Zmień nazwę**. Zmień nazwę pliku na `ISampleInterface.cs` i naciśnij klawisz ENTER. Zmiana nazwy pliku spowoduje również zmianę nazwy klasy na `ISampleInterface`. Ta klasa będzie reprezentować interfejs publiczny dla klasy.

4. Kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface, a następnie kliknij pozycję **Właściwości**. Kliknij kartę **kompilacja** . Skonfiguruj ścieżkę wyjściową do prawidłowej lokalizacji na komputerze deweloperskim, `C:\TypeEquivalenceSample`na przykład. Ta lokalizacja będzie również używana w kolejnym kroku w tym instruktażu.

5. Edytując właściwości projektu, kliknij kartę podpisywanie . Wybierz opcję **podpisz zestaw** . Na liście **Wybierz plik klucza o silnej nazwie** kliknij pozycję  **\<nowy... >** . W polu **Nazwa pliku klucza** wpisz `key.snk`. Wyczyść pole wyboru **Chroń mój klucz plik hasłem** . Kliknij przycisk **OK**.

6. Otwórz plik ISampleInterface.cs. Dodaj następujący kod do pliku klasy ISampleInterface, aby utworzyć interfejs ISampleInterface.

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

7. W menu **Narzędzia** kliknij polecenie **Utwórz identyfikator GUID**. W oknie dialogowym **Tworzenie identyfikatora GUID** kliknij przycisk **Format rejestru** , a następnie kliknij przycisk **Kopiuj**. Kliknij przycisk **zakończenia**.

8. W atrybucie Usuń przykładowy identyfikator GUID i wklej identyfikator GUID, który został skopiowany z okna dialogowego **Tworzenie identyfikatora GUID.** `Guid` Usuń nawiasy klamrowe{}() ze skopiowanego identyfikatora GUID.

9. W **Eksplorator rozwiązań**rozwiń folder **Właściwości** . Kliknij dwukrotnie plik AssemblyInfo.cs. Dodaj do pliku następujący atrybut.

    ```csharp
    [assembly: ImportedFromTypeLib("")]
    ```

     Zapisz plik.

10. Zapisz projekt.

11. Kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface i kliknij pozycję **Kompiluj**. Plik Library. dll został skompilowany i zapisany w określonej ścieżce danych wyjściowych kompilacji (na przykład C:\TypeEquivalenceSample).

## <a name="creating-a-runtime-class"></a>Tworzenie klasy środowiska uruchomieniowego

#### <a name="to-create-the-type-equivalence-runtime-project"></a>Aby utworzyć projekt z równoważeniem typu w środowisku uruchomieniowym

1. W programie Visual Studio na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**.

2. W oknie dialogowym **Nowy projekt** w okienku **typy projektów** upewnij się, że wybrano opcję **Windows** . W okienku **Szablony** wybierz pozycję **Biblioteka klas** . W polu **Nazwa** wpisz `TypeEquivalenceRuntime`, a następnie kliknij przycisk **OK**. Nowy projekt zostanie utworzony.

3. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik Class1.cs i kliknij polecenie **Zmień nazwę**. Zmień nazwę pliku na `SampleClass.cs` i naciśnij klawisz ENTER. Zmiana nazwy pliku zmienia również nazwę klasy na `SampleClass`. Ta klasa będzie implementować `ISampleInterface` interfejs.

4. Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij pozycję **Właściwości**. Kliknij kartę **kompilacja** . Ustaw ścieżkę wyjściową do tej samej lokalizacji, która została użyta w projekcie TypeEquivalenceInterface, na `C:\TypeEquivalenceSample`przykład.

5. Edytując właściwości projektu, kliknij kartę podpisywanie . Wybierz opcję **podpisz zestaw** . Na liście **Wybierz plik klucza o silnej nazwie** kliknij pozycję  **\<nowy... >** . W polu **Nazwa pliku klucza** wpisz `key.snk`. Wyczyść pole wyboru **Chroń mój klucz plik hasłem** . Kliknij przycisk **OK**.

6. Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij pozycję **Dodaj odwołanie**. Kliknij kartę **Przeglądaj** i przejdź do folderu Ścieżka wyjściowa. Wybierz plik TypeEquivalenceInterface. dll, a następnie kliknij przycisk **OK**.

7. W **Eksplorator rozwiązań**rozwiń folder **odwołania** . Wybierz odwołanie TypeEquivalenceInterface. W okno Właściwości odwołania TypeEquivalenceInterface ustaw właściwość **określona wersja** na **false**.

8. Dodaj następujący kod do pliku klasy SampleClass, aby utworzyć klasę SampleClass.

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

9. Zapisz projekt.

10. Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime i kliknij pozycję **Kompiluj**. Plik Library. dll został skompilowany i zapisany w określonej ścieżce danych wyjściowych kompilacji (na przykład C:\TypeEquivalenceSample).

## <a name="creating-a-client-project"></a>Tworzenie projektu klienta

#### <a name="to-create-the-type-equivalence-client-project"></a>Aby utworzyć projekt klienta równoważność typu

1. W programie Visual Studio na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**.

2. W oknie dialogowym **Nowy projekt** w okienku **typy projektów** upewnij się, że wybrano opcję **Windows** . Wybierz pozycję **Aplikacja konsolowa** w okienku **Szablony** . W polu **Nazwa** wpisz `TypeEquivalenceClient`, a następnie kliknij przycisk **OK**. Nowy projekt zostanie utworzony.

3. Kliknij prawym przyciskiem myszy projekt TypeEquivalenceClient, a następnie kliknij pozycję **Właściwości**. Kliknij kartę **kompilacja** . Ustaw ścieżkę wyjściową do tej samej lokalizacji, która została użyta w projekcie TypeEquivalenceInterface, na `C:\TypeEquivalenceSample`przykład.

4. Kliknij prawym przyciskiem myszy projekt TypeEquivalenceClient, a następnie kliknij pozycję **Dodaj odwołanie**. Kliknij kartę **Przeglądaj** i przejdź do folderu Ścieżka wyjściowa. Wybierz plik TypeEquivalenceInterface. dll (nie TypeEquivalenceRuntime. dll), a następnie kliknij przycisk **OK**.

5. W **Eksplorator rozwiązań**rozwiń folder **odwołania** . Wybierz odwołanie TypeEquivalenceInterface. W okno Właściwości odwołania TypeEquivalenceInterface ustaw właściwość **Osadź typy** współdziałania na **wartość true**.

6. Dodaj następujący kod do pliku Program.cs, aby utworzyć program kliencki.

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

7. Naciśnij kombinację klawiszy CTRL + F5, aby skompilować i uruchomić program.

## <a name="modifying-the-interface"></a>Modyfikowanie interfejsu

#### <a name="to-modify-the-interface"></a>Aby zmodyfikować interfejs

1. W programie Visual Studio w menu **plik** wskaż polecenie **Otwórz**, a następnie kliknij pozycję **projekt/rozwiązanie**.

2. W oknie dialogowym **Otwórz projekt** kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface, a następnie kliknij polecenie **Właściwości**. Kliknij kartę **aplikacja** . Kliknij przycisk **Informacje o zestawie** . Zmień **wersję zestawu** i wartość **wersji pliku** na `2.0.0.0`.

3. Otwórz plik SampleInterface.cs. Dodaj następujący wiersz kodu do interfejsu ISampleInterface.

    ```csharp
    DateTime GetDate();
    ```

    Zapisz plik.

4. Zapisz projekt.

5. Kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface i kliknij pozycję **Kompiluj**. Nowa wersja pliku dll biblioteki klas została skompilowana i zapisana w określonej ścieżce danych wyjściowych kompilacji (na przykład C:\TypeEquivalenceSample).

## <a name="modifying-the-runtime-class"></a>Modyfikowanie klasy środowiska uruchomieniowego

#### <a name="to-modify-the-runtime-class"></a>Aby zmodyfikować klasę środowiska uruchomieniowego

1. W programie Visual Studio w menu **plik** wskaż polecenie **Otwórz**, a następnie kliknij pozycję **projekt/rozwiązanie**.

2. W oknie dialogowym **Otwórz projekt** kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij polecenie **Właściwości**. Kliknij kartę **aplikacja** . Kliknij przycisk **Informacje o zestawie** . Zmień **wersję zestawu** i wartość **wersji pliku** na `2.0.0.0`.

3. Otwórz plik SampleClass.cs. Dodaj następujące wiersze kodu do klasy SampleClass.

    ```csharp
    public DateTime GetDate()
    {
        return DateTime.Now;
    }
    ```

    Zapisz plik.

4. Zapisz projekt.

5. Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime i kliknij pozycję **Kompiluj**. Zaktualizowana wersja pliku dll biblioteki klas została skompilowana i zapisana w wcześniej określonej ścieżce danych wyjściowych kompilacji (na przykład C:\TypeEquivalenceSample).

6. W Eksploratorze plików otwórz folder Ścieżka wyjściowa (na przykład C:\TypeEquivalenceSample). Kliknij dwukrotnie plik TypeEquivalenceClient. exe, aby uruchomić program. Program będzie odzwierciedlał nową wersję zestawu TypeEquivalenceRuntime bez ponownego kompilowania.

## <a name="see-also"></a>Zobacz także

- [/Link (C# opcje kompilatora)](../../../language-reference/compiler-options/link-compiler-option.md)
- [Przewodnik programowania w języku C#](../../index.md)
- [Programowanie za pomocą zestawów](../../../../framework/app-domains/programming-with-assemblies.md)
- [Zestawy w środowisku .NET](../../../../standard/assembly/index.md)
