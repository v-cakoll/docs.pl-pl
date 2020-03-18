---
title: 'Instruktaż: Osadzanie typów z zestawów zarządzanych w programie Visual Studio'
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: f11fbedad766753ee462c5f597b823493cdaf7cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75338558"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a>Instruktaż: Osadzanie typów z zestawów zarządzanych w programie Visual Studio

Jeśli osadzasz informacje o typie z zestawu zarządzanego o silnej nazwie, można luźno pokilku typów w aplikacji, aby osiągnąć niezależność wersji. Oznacza to, że program może być napisany do używania typów z dowolnej wersji biblioteki zarządzanej bez konieczności ponownego kompilowania dla każdej nowej wersji.

Osadzanie typów jest często używane z współdziałaniacom COM, na przykład aplikacja, która używa obiektów automatyzacji z pakietu Microsoft Office. Osadzanie informacji o typie umożliwia tej samej kompilacji programu do pracy z różnymi wersjami pakietu Microsoft Office na różnych komputerach. Można jednak również użyć osadzania typów z w pełni zarządzanymi rozwiązaniami.

Po określeniu interfejsów publicznych, które mogą być osadzone, należy utworzyć klasy czasu wykonywania, które implementują te interfejsy. Program kliencki może osadzić informacje o typie interfejsów w czasie projektowania, `Embed Interop Types` odwołując się `True`do zestawu, który zawiera interfejsy publiczne i ustawiając właściwość odwołania do . Program kliencki może następnie załadować wystąpienia obiektów czasu wykonywania wpisanych jako te interfejsy. Jest to równoważne użyciu kompilatora wiersza polecenia i odwoływaniu się do zestawu przy użyciu [opcji kompilatora -link](../../csharp/language-reference/compiler-options/link-compiler-option.md).

Jeśli utworzysz nową wersję zestawu uruchomieniowego o silnej nazwie, program klienta nie musi być ponownie skompilowany. Program kliencki nadal używa niezależnie od wersji zestawu wykonywania jest dostępna dla niego, przy użyciu informacji o typie osadzonym dla interfejsów publicznych.

W tym instruktacie:

1. Utwórz zestaw o silnej nazwie z interfejsem publicznym zawierającym informacje o typie, które mogą być osadzone.
1. Tworzenie zestawu wykonywania o silnej nazwie, który implementuje interfejs publiczny.
1. Utwórz program kliencki, który osadza informacje o typie z interfejsu publicznego i tworzy wystąpienie klasy z zestawu czasu wykonywania.
1. Modyfikowanie i przebudowywanie zestawu w czasie wykonywania.
1. Uruchom program kliencki, aby zobaczyć, że używa nowej wersji zestawu runtime bez konieczności ponownego kompilowania.

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a>Warunki i ograniczenia

Informacje o typie można osadzać z zestawu w następujących warunkach:

- Zestaw udostępnia co najmniej jeden interfejs publiczny.
- Interfejsy osadzone są oanotowane `ComImport` `Guid` atrybutami i atrybutami za pomocą unikatowych identyfikatorów GUID.
- Zestaw jest oanotowany `ImportedFromTypeLib` atrybutem `PrimaryInteropAssembly` lub atrybutem i `Guid` atrybutem na poziomie zestawu. Szablony projektów Visual C# i Visual Basic `Guid` domyślnie zawierają atrybut na poziomie zestawu.

Ponieważ podstawową funkcją osadzania typu jest obsługa zestawów współdziałania COM, podczas osadzania informacji o typie w pełni zarządzanym rozwiązaniu obowiązują następujące ograniczenia:

- Osadzone są tylko atrybuty specyficzne dla współoperacji COM. Inne atrybuty są ignorowane.
- Jeśli typ używa parametrów ogólnych, a typ parametru ogólnego jest typem osadzonym, tego typu nie można użyć na granicy zestawu. Przykłady przekraczania granicy złożenia obejmują wywołanie metody z innego zestawu lub wyprowadzenie typu z typu zdefiniowanego w innym złożeniu.
- Stałe nie są osadzone.
- Klasa <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> nie obsługuje typu osadzonego jako klucz. Można zaimplementować własny typ słownika do obsługi typu osadzonego jako klucz.

## <a name="create-an-interface"></a>Tworzenie interfejsu

Pierwszym krokiem jest utworzenie zestawu interfejsu równoważności typu.

1. W programie Visual Studio wybierz **pozycję Plik** > **nowy** > **projekt**.

1. W oknie **dialogowym Tworzenie nowego projektu** wpisz *bibliotekę klas* w polu **Wyszukaj szablony.** Wybierz z listy szablon C# lub Visual Basic **Class Library (.NET Framework),** a następnie wybierz pozycję **Dalej**.

1. W oknie dialogowym **Konfigurowanie nowego projektu** w obszarze **Nazwa projektu** *wpisz typeEquivalenceInterface*, a następnie wybierz pozycję **Utwórz**. Zostanie utworzony nowy projekt.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy plik *Class1.cs* lub *Class1.vb,* wybierz polecenie **Zmień nazwę**i zmień nazwę pliku z *Class1* na *ISampleInterface*. Odpowiedz **tak** na monit, `ISampleInterface`aby również zmienić nazwę klasy na . Ta klasa reprezentuje interfejs publiczny dla klasy.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceInterface,** a następnie wybierz polecenie **Właściwości**.

1. Wybierz **pozycję Konfiguruj** w lewym okienku ekranu **Właściwości** i ustaw **ścieżkę output** na lokalizację na komputerze, na przykład *C:\TypeEquivalenceSample*. W tym instruktacie jest używana ta sama lokalizacja.

1. Wybierz **pozycję Podpisywanie** w lewym okienku ekranu **Właściwości,** a następnie zaznacz pole wyboru **Podpisz złożenie.** W rozwijanym polu **Wybierz plik klucza o silnej nazwie**wybierz pozycję **Nowy**.

1. W oknie dialogowym **Tworzenie silnego klucza nazwy** w obszarze **Nazwa pliku klucza**wpisz polecenie *key.snk*. Usuń zaznaczenie pola wyboru **Chroń mój plik klucza hasłem,** a następnie wybierz przycisk **OK**.

1. Otwórz plik klasy *ISampleInterface* w edytorze kodu i zastąp `ISampleInterface` jego zawartość następującym kodem, aby utworzyć interfejs:

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

1. W menu **Narzędzia** wybierz polecenie **Utwórz guid**, a w oknie dialogowym **Tworzenie identyfikatora GUID** wybierz pozycję **Format rejestru**. Wybierz **pozycję Kopiuj**, a następnie wybierz pozycję **Zakończ**.

1. W `Guid` atrybucie kodu zastąp przykładowy identyfikator GUID skopiowanym identyfikatorem GUID i usuń nawiasy klamrowe (**{ }**).

1. W **Eksploratorze rozwiązań**rozwiń folder **Właściwości** i wybierz *plik AssemblyInfo.cs* lub *AssemblyInfo.vb.* W edytorze kodu dodaj następujący atrybut do pliku:

   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```

   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```

1. Wybierz **pozycję Zapisz wszystko** > **Save All** lub naciśnij **klawisz Etui Ctrl**+**Shift**+**S,** aby zapisać pliki i projekt.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceInterface** i wybierz polecenie **Zbuduj**. Plik DLL biblioteki klas jest kompilowany i zapisywany do określonej ścieżki wyjściowej kompilacji, na przykład *C:\TypeEquivalenceSample*.

## <a name="create-a-runtime-class"></a>Tworzenie klasy czasu wykonywania

Następnie utwórz klasę wykonywania równoważności typu.

1. W programie Visual Studio wybierz **pozycję Plik** > **nowy** > **projekt**.

1. W oknie **dialogowym Tworzenie nowego projektu** wpisz *bibliotekę klas* w polu **Wyszukaj szablony.** Wybierz z listy szablon C# lub Visual Basic **Class Library (.NET Framework),** a następnie wybierz pozycję **Dalej**.

1. W oknie dialogowym **Konfigurowanie nowego projektu** w obszarze **Nazwa projektu** *wpisz typeEquivalenceRuntime*, a następnie wybierz pozycję **Utwórz**. Zostanie utworzony nowy projekt.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem *myszy* plik Class1.cs lub *Class1.vb,* wybierz polecenie **Zmień nazwę**i zmień nazwę pliku z *Class1* na *SampleClass*. Odpowiedz **tak** na monit, `SampleClass`aby również zmienić nazwę klasy na . Ta klasa implementuje `ISampleInterface` interfejs.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceInterface** i wybierz polecenie **Właściwości**.

1. Wybierz **pozycję Konfiguruj** w lewym okienku ekranu **Właściwości,** a następnie ustaw **ścieżkę output** w tej samej lokalizacji, która została użyta dla projektu TypeEquivalenceInterface, na przykład *C:\TypeEquivalenceSample*.

1. Wybierz **pozycję Podpisywanie** w lewym okienku ekranu **Właściwości,** a następnie zaznacz pole wyboru **Podpisz złożenie.** W rozwijanym polu **Wybierz plik klucza o silnej nazwie**wybierz pozycję **Nowy**.

1. W oknie dialogowym **Tworzenie silnego klucza nazwy** w obszarze **Nazwa pliku klucza**wpisz polecenie *key.snk*. Usuń zaznaczenie pola wyboru **Chroń mój plik klucza hasłem,** a następnie wybierz przycisk **OK**.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceRuntime** i wybierz polecenie **Dodaj** > **odwołanie**.

1. W oknie dialogowym **Menedżer odwołań** wybierz pozycję **Przeglądaj** i przejdź do folderu ścieżki wyjściowej. Wybierz plik *TypeEquivalenceInterface.dll,* wybierz pozycję **Dodaj**, a następnie wybierz przycisk **OK**.

1. W **Eksploratorze rozwiązań**rozwiń folder **Odwołania** i wybierz odwołanie **TypeEquivalenceInterface.** W okienku Właściwości ustaw **określoną wersję** na **Fałsz,** jeśli jeszcze nie jest. **Properties**

1. Otwórz plik klasy *SampleClass* w edytorze kodu i zastąp `SampleClass` jego zawartość następującym kodem, aby utworzyć klasę:

   ```csharp
   using System;
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

1. Wybierz **pozycję Zapisz wszystko** > **Save All** lub naciśnij **klawisz Etui Ctrl**+**Shift**+**S,** aby zapisać pliki i projekt.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceRuntime** i wybierz polecenie **Kompilacja**. Plik DLL biblioteki klas jest kompilowany i zapisywany do określonej ścieżki wyjściowej kompilacji.

## <a name="create-a-client-project"></a>Tworzenie projektu klienta

Na koniec utwórz program klienta równoważności typów, który odwołuje się do zestawu interfejsu.

1. W programie Visual Studio wybierz **pozycję Plik** > **nowy** > **projekt**.

1. W oknie **dialogowym Tworzenie nowego projektu** wpisz *konsolę* w polu **Wyszukaj szablony.** Wybierz z listy szablon C# lub Visual **Basic Console App (.NET Framework),** a następnie wybierz pozycję **Dalej**.

1. W oknie dialogowym **Konfigurowanie nowego projektu** w obszarze **Nazwa projektu** *wpisz typ Typ RównoważnościKlient*, a następnie wybierz pozycję **Utwórz**. Zostanie utworzony nowy projekt.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceClient** i wybierz polecenie **Właściwości**.

1. Wybierz **pozycję Konfiguruj** w lewym okienku ekranu **Właściwości,** a następnie ustaw **ścieżkę output** w tej samej lokalizacji, która została użyta dla projektu TypeEquivalenceInterface, na przykład *C:\TypeEquivalenceSample*.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceClient** i wybierz polecenie **Dodaj** > **odwołanie**.

1. Jeśli w oknie dialogowym **Menedżer odwołań,** jeśli plik **TypeEquivalenceInterface.dll** jest już wymieniony, wybierz go. Jeśli nie, wybierz pozycję **Przeglądaj**, przejdź do folderu ścieżki wyjściowej, wybierz plik *TypeEquivalenceInterface.dll* (nie *typeEquivalenceRuntime.dll)* i wybierz pozycję **Dodaj**. Kliknij przycisk **OK**.

1. W **Eksploratorze rozwiązań**rozwiń folder **Odwołania** i wybierz odwołanie **TypeEquivalenceInterface.** W okienku **Właściwości** ustaw **osadzanie typów pooperacji** na **Wartość True**.

1. Otwórz *plik Program.cs* lub *Module1.vb* w edytorze kodu i zastąp jego zawartość następującym kodem, aby utworzyć program kliencki:

   ```csharp
   using System;
   using System.Reflection;
   using TypeEquivalenceInterface;

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
   Imports System.Reflection
   Imports TypeEquivalenceInterface

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

1. Wybierz **pozycję Zapisz wszystko** > **Save All** lub naciśnij **klawisz Etui Ctrl**+**Shift**+**S,** aby zapisać pliki i projekt.

1. Naciśnij **klawisz Ctrl**+**F5,** aby zbudować i uruchomić program. Należy zauważyć, że wyjście konsoli zwraca zestaw w wersji **1.0.0.0**.

## <a name="modify-the-interface"></a>Modyfikowanie interfejsu

Teraz zmodyfikuj zestaw interfejsu i zmień jego wersję.

1. W programie Visual Studio wybierz pozycję Otwórz**Open** > **projekt/rozwiązanie** **File** > pliku i otwórz projekt **TypeEquivalenceInterface.**

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceInterface** i wybierz polecenie **Właściwości**.

1. Wybierz **pozycję Aplikacja** w lewym okienku ekranu **Właściwości,** a następnie wybierz pozycję Informacje o **złożeniu**.

1. W oknie dialogowym **Informacje o złożeniu** zmień wartości **wersja zestawu** i wersję **pliku** na *2.0.0.0*, a następnie wybierz przycisk **OK**.

1. Otwórz *plik SampleInterface.cs* lub *SampleInterface.vb* i dodaj następujący `ISampleInterface` wiersz kodu do interfejsu:

   ```csharp
   DateTime GetDate();
   ```

   ```vb
   Function GetDate() As Date
   ```

1. Wybierz **pozycję Zapisz wszystko** > **Save All** lub naciśnij **klawisz Etui Ctrl**+**Shift**+**S,** aby zapisać pliki i projekt.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceInterface** i wybierz polecenie **Zbuduj**. Nowa wersja pliku DLL biblioteki klas jest kompilowana i zapisywana w ścieżce wyjściowej kompilacji.

## <a name="modify-the-runtime-class"></a>Modyfikowanie klasy czasu wykonywania

Zmodyfikuj również klasę czasu wykonywania i zaktualizuj jej wersję.

1. W programie Visual Studio wybierz pozycję Otwórz**Open** > **projekt/rozwiązanie** **File** > pliku i otwórz projekt **TypeEquivalenceRuntime.**

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceRuntime** i wybierz **polecenie Właściwości**.

1. Wybierz **pozycję Aplikacja** w lewym okienku ekranu **Właściwości,** a następnie wybierz pozycję Informacje o **złożeniu**.

1. W oknie dialogowym **Informacje o złożeniu** zmień wartości **wersja zestawu** i wersję **pliku** na *2.0.0.0*, a następnie wybierz przycisk **OK**.

1. Otwórz *plik SampleClass.cs* lub *SampleClass.vb* i dodaj `SampleClass` następujący kod do klasy:

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

1. Wybierz **pozycję Zapisz wszystko** > **Save All** lub naciśnij **klawisz Etui Ctrl**+**Shift**+**S,** aby zapisać pliki i projekt.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceRuntime** i wybierz polecenie **Kompilacja**. Nowa wersja pliku DLL biblioteki klas jest kompilowana i zapisywana w ścieżce wyjściowej kompilacji.

## <a name="run-the-updated-client-program"></a>Uruchamianie zaktualizowanego programu klienta

Przejdź do lokalizacji folderu wyjściowego kompilacji i uruchom *program TypeEquivalenceClient.exe*. Należy zauważyć, że dane wyjściowe konsoli `TypeEquivalenceRuntime` odzwierciedla teraz nową wersję zestawu, *2.0.0.0*, bez ponownej kompilacji programu.

## <a name="see-also"></a>Zobacz też

- [-link (Opcje kompilatora C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
- [Przewodnik programowania w języku C#](../../csharp/programming-guide/index.md)
- [Koncepcje programowania (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Zestawy w środowisku .NET](index.md)
