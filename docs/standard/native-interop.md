---
title: Współdziałanie natywnego
description: Dowiedz się, jak interfejs ze składnikami natywnego programu .NET.
author: blackdwarf
ms.author: ronpet
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 3c357112-35fb-44ba-a07b-6a1c140370ac
ms.openlocfilehash: 7da86cfe483a2355c53206f4c491fbd07e4c3046
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="native-interoperability"></a>Współdziałanie natywnego

W tym dokumencie, firma Microsoft będzie Poznaj nieco bardziej wszystkie trzy sposoby wykonanie "natywny współdziałania", które są dostępne przy użyciu platformy .NET.

Istnieje kilka przyczyn, dlaczego warto wywoływać kodu natywnego:

*   Systemy operacyjne są dostarczane z dużą ilością interfejsów API, które nie są dostępne w bibliotekach klas zarządzanych. Podstawowym przykład dla tego będzie dostęp do sprzętu lub systemu operacyjnego funkcje zarządzania.
*   Podczas komunikacji z innymi składnikami, które lub można utworzyć ABIs stylu języka C (native ABIs). Obejmuje, na przykład kodu języka Java, który jest dostępny za pośrednictwem [Java natywnego interfejsu (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) lub dowolnego zarządzanego języka, który może utworzyć składnik macierzysty.
*   W systemie Windows większość oprogramowania, które są instalowane, takich jak pakiet Microsoft Office, rejestruje składników COM, które reprezentują programów i umożliwiają deweloperom zautomatyzować je lub używać ich. Wymaga to współdziałanie macierzystego.

Oczywiście powyższej listy nie obejmuje wszystkich potencjalnych sytuacji i scenariusze, w których deweloper może chcesz/podobne/potrzebę interfejs ze składnikami natywnego. Biblioteka klas programu .NET, na przykład używa Obsługa natywnego współdziałanie do implementacji odpowiedniego liczba interfejsów API, takie jak obsługa konsoli i manipulowania, dostępu do systemu plików i innych użytkowników. Jednak ważne jest, należy pamiętać, że ma opcji, należy należy go.

> [!NOTE]
> Większość przykładów w tym dokumencie będzie udostępniana dla wszystkich trzech obsługiwanych platform dla platformy .NET Core (Windows, Linux lub macOS). Jednak niektóre przykłady krótki i opisowy tylko jeden przykład jest przedstawić używającą Windows nazwy plików i rozszerzenia (to znaczy "dll" bibliotek). Oznacza to, że te funkcje nie są dostępne w systemie Linux lub macOS, została wykonana wyłącznie dla wygody sake.

## <a name="platform-invoke-pinvoke"></a>Wywołanie platformy (P/Invoke)

P/Invoke jest technologia, która umożliwia dostęp do struktury, wywołania zwrotne i funkcji w bibliotekach niezarządzane z kodu zarządzanego. Większość API P/Invoke znajduje się w dwóch obszarach nazw: `System` i `System.Runtime.InteropServices`. Korzystanie z tych dwóch przestrzeni nazw będzie zezwalał na dostęp do atrybutów, które opisują sposób komunikowania się z składnik macierzysty.

Zacznijmy od najbardziej typowym przykładem, i który jest wywoływanie niezarządzanych funkcji w kodzie zarządzanym. Umożliwia wyświetlanie okna komunikatu z wiersza polecenia aplikacji:

```csharp
using System.Runtime.InteropServices;

public class Program {

    // Import user32.dll (containing the function we need) and define
    // the method corresponding to the native function.
    [DllImport("user32.dll")]
    public static extern int MessageBox(IntPtr hWnd, String text, String caption, int options);

    public static void Main(string[] args) {
        // Invoke the function as a regular managed method.
        MessageBox(IntPtr.Zero, "Command-line message box", "Attention!", 0);
    }
}
```

W powyższym przykładzie jest dość proste, ale pokazywanie co jest potrzebne do wywołania niezarządzanej funkcji z kodu zarządzanego. Załóżmy kroków opisanych w tym przykładzie:

*   #1 wiersz zawiera za pomocą instrukcji dla `System.Runtime.InteropServices` czyli przestrzeni nazw, który zawiera wszystkie elementy potrzebne.
*   Wprowadza wiersza #5 `DllImport` atrybutu. Ten atrybut jest niezwykle ważny, ponieważ informuje środowiska uruchomieniowego, że należy załadować niezarządzanej DLL. Jest to plik DLL, do którego możemy chcesz wywołać.
*   Wiersz #6 jest crux pracy P/Invoke. Definiuje metodę zarządzanych, która ma **dokładnie takiego samego podpisu** jako niezarządzane. Deklaracja zawiera słowo kluczowe new, który można zauważysz, `extern`, który określa, że środowisko wykonawcze to jest zewnętrzną metodę, a gdy go wywołać, środowisko uruchomieniowe powinien go znaleźć w bibliotece DLL określone w `DllImport` atrybutu.

Pozostałe przykładu jest tylko wywołania metody, jak w przypadku innych metod zarządzanych.

Próbki jest podobny do macOS. Rzecz, którą chcesz zmienić jest oczywiście nazwę biblioteki w `DllImport` atrybutu jako macOS ma inny schemat nazewnictwa bibliotek dynamicznych. Przykładowe poniżej używa `getpid(2)` funkcji, aby pobrać Identyfikatora procesu aplikacji i wydrukuj go do konsoli.

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libSystem shared library and define the method corresponding to the native function.
        [DllImport("libSystem.dylib")]
        private static extern int getpid();

        public static void Main(string[] args){
            // Invoke the function and get the process ID.
            int pid = getpid();
            Console.WriteLine(pid);
        }
    }
}
```

Jest również podobne w systemie Linux. Nazwa funkcji jest taki sam, ponieważ `getpid(2)` jest standardem [POSIX](https://en.wikipedia.org/wiki/POSIX) wywołanie systemowe.

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libc shared library and define the method corresponding to the native function.
        [DllImport("libc.so.6")]
        private static extern int getpid();

        public static void Main(string[] args){
            // Invoke the function and get the process ID.
            int pid = getpid();
            Console.WriteLine(pid);
        }
    }
}
```

### <a name="invoking-managed-code-from-unmanaged-code"></a>Wywoływanie kodu zarządzanego z kodem niezarządzanym

Oczywiście środowiska uruchomieniowego umożliwia komunikację przepływać w obu kierunkach, dzięki czemu można wywołać w zarządzanych artefaktów z funkcji macierzystym, przy użyciu wskaźników funkcji. Najbliższy operacją do wskaźnika funkcji w kodzie zarządzanym jest **delegować**, więc jest to, co umożliwia wywołań zwrotnych z kodu natywnego kodu zarządzanego.

Sposób, aby użyć tej funkcji jest podobny do kodu zarządzanego do natywnych proces opisany powyżej. Dla danego wywołania zwrotnego zdefiniuj delegata, który odpowiada podpis, a który przekazywane do metody zewnętrznej. Wszystkie inne zajmie się środowiska uruchomieniowego.

```csharp
using System;
using System.Runtime.InteropServices;

namespace ConsoleApplication1 {

    class Program {

        // Define a delegate that corresponds to the unmanaged function.
        delegate bool EnumWC(IntPtr hwnd, IntPtr lParam);

        // Import user32.dll (containing the function we need) and define
        // the method corresponding to the native function.
        [DllImport("user32.dll")]
        static extern int EnumWindows(EnumWC lpEnumFunc, IntPtr lParam);

        // Define the implementation of the delegate; here, we simply output the window handle.
        static bool OutputWindow(IntPtr hwnd, IntPtr lParam) {
            Console.WriteLine(hwnd.ToInt64());
            return true;
        }

        static void Main(string[] args) {
            // Invoke the method; note the delegate as a first parameter.
            EnumWindows(OutputWindow, IntPtr.Zero);
        }
    }
}
```

Zanim firma Microsoft przeprowadzenie naszym przykładzie jest gotowe za pośrednictwem podpisów niezarządzanych funkcji potrzebnych do pracy z. Funkcję, którą chcesz wywołać wyliczyć wszystkie okna ma następującą sygnaturą: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`

Pierwszym parametrem jest wywołaniem zwrotnym. Wspomniane wywołania zwrotnego ma następującą sygnaturą: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`

Pamiętając o tym Przejdźmy przykładzie:

*   Wiersz #8 w przykładzie definiuje delegata, który pasuje do podpisu wywołania zwrotnego z kodem niezarządzanym. Zwróć uwagę, jak LPARAM i HWND typy są przedstawiane za pomocą `IntPtr` w kodzie zarządzanym.
*   Wprowadzenie wierszy #10 i #11 `EnumWindows` funkcji z biblioteki user32.dll.
*   Wiersze #13-16 implementuje delegata. W tym przykładzie prosty chcemy tylko dane wyjściowe dojścia do konsoli.
*   Na koniec wiersza #19 możemy wywołanie metody zewnętrznej i podaj delegata.

Poniżej przedstawiono przykłady systemu Linux i macOS. Ich używamy `ftw` funkcji, które znajdują się w `libc`, biblioteki C. Ta funkcja umożliwia przechodzenie między hierarchiami katalogu i zajmuje wskaźnika do funkcji jako jeden z jego parametrów. Funkcja wspomnianej ma następującą sygnaturą: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

            // Define a delegate that has the same signature as the native function.
            delegate int DirClbk(string fName, StatClass stat, int typeFlag);

            // Import the libc and define the method to represent the native function.
            [DllImport("libc.so.6")]
            static extern int ftw(string dirpath, DirClbk cl, int descriptors);

            // Implement the above DirClbk delegate;
            // this one just prints out the filename that is passed to it.
            static int DisplayEntry(string fName, StatClass stat, int typeFlag) {
                    Console.WriteLine(fName);
                    return 0;
            }

            public static void Main(string[] args){
                    // Call the native function.
                    // Note the second parameter which represents the delegate (callback).
                    ftw(".", DisplayEntry, 10);
            }
    }

    // The native callback takes a pointer to a struct. The below class
    // represents that struct in managed code. You can find more information
    // about this in the section on marshalling below.
    [StructLayout(LayoutKind.Sequential)]
    public class StatClass {
            public uint DeviceID;
            public uint InodeNumber;
            public uint Mode;
            public uint HardLinks;
            public uint UserID;
            public uint GroupID;
            public uint SpecialDeviceID;
            public ulong Size;
            public ulong BlockSize;
            public uint Blocks;
            public long TimeLastAccess;
            public long TimeLastModification;
            public long TimeLastStatusChange;
    }
}
```

System macOS przykładzie użyto taką samą funkcję, a jedyną różnicą jest argumentem `DllImport` atrybutu, ponieważ przechowuje macOS `libc` w innym miejscu.

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
        public static class Program {

                // Define a delegate that has the same signature as the native function.
                delegate int DirClbk(string fName, StatClass stat, int typeFlag);

                // Import the libc and define the method to represent the native function.
                [DllImport("libSystem.dylib")]
                static extern int ftw(string dirpath, DirClbk cl, int descriptors);

                // Implement the above DirClbk delegate;
                // this one just prints out the filename that is passed to it.
                static int DisplayEntry(string fName, StatClass stat, int typeFlag) {
                        Console.WriteLine(fName);
                        return 0;
                }

                public static void Main(string[] args){
                        // Call the native function.
                        // Note the second parameter which represents the delegate (callback).
                        ftw(".", DisplayEntry, 10);
                }
        }

        // The native callback takes a pointer to a struct. The below class
        // represents that struct in managed code. You can find more information
        // about this in the section on marshalling below.
        [StructLayout(LayoutKind.Sequential)]
        public class StatClass {
                public uint DeviceID;
                public uint InodeNumber;
                public uint Mode;
                public uint HardLinks;
                public uint UserID;
                public uint GroupID;
                public uint SpecialDeviceID;
                public ulong Size;
                public ulong BlockSize;
                public uint Blocks;
                public long TimeLastAccess;
                public long TimeLastModification;
                public long TimeLastStatusChange;
        }
}
```

Oba powyższe przykłady są zależne od parametrów, a w obu przypadkach parametry są następujące typy zarządzane. Środowisko uruchomieniowe nie "co" i przetwarza je w jego odpowiedników po drugiej stronie. Ponieważ ten proces jest naprawdę ważne do pisania kodu natywnego międzyoperacyjnego jakości, Spójrzmy na co się stanie, gdy środowisko uruchomieniowe _marshals_ typów.

## <a name="type-marshalling"></a>Kierowanie typu

**Kierowanie** jest procesem przekształcania typów, gdy konieczne jest przekraczają granicę zarządzanego do natywnego i na odwrót.

Kierowanie przyczyna jest wymagane jest, ponieważ różnią się typami w kodzie zarządzane i niezarządzane. W kodzie zarządzanym, na przykład masz `String`, podczas gdy w świecie niezarządzane ciągi może być Unicode ("szeroka"), z systemem innym niż Unicode, zerem, ASCII, itp. Domyślnie podsystem P/Invoke spróbuje wykonać czynność prawej na zachowanie domyślne, które można wyświetlić na podstawie [MSDN](../../docs/framework/interop/default-marshaling-behavior.md). Jednak w tych sytuacjach konieczne dodatkowe formantu zostanie zastosowana `MarshalAs` atrybutu, aby określić, co to jest oczekiwany typ po stronie niezarządzane. Na przykład aby ciąg, który zostanie wysłany jako ciągu ANSI zerem, można go jak następująco:

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

### <a name="marshalling-classes-and-structs"></a>Kierowanie klasy i struktury

Innym aspektem kierowania typu jest sposób przekazywania w strukturze do metody niezarządzane. Na przykład wymagać pewnych metod niezarządzane struktury jako parametr. W takich sytuacjach należy utworzyć odpowiednie struktury lub klasy w zarządzanych części świecie, aby używać go jako parametr. Jednak tylko Definiowanie klasy nie jest wystarczająco, musimy także poinstruować organizatora sposób mapowania pól w klasie niezarządzanej strukturę. Jest to, gdy `StructLayout` atrybutu wejścia play.

```csharp
[DllImport("kernel32.dll")]
static extern void GetSystemTime(SystemTime systemTime);

[StructLayout(LayoutKind.Sequential)]
class SystemTime {
    public ushort Year;
    public ushort Month;
    public ushort DayOfWeek;
    public ushort Day;
    public ushort Hour;
    public ushort Minute;
    public ushort Second;
    public ushort Milsecond;
}

public static void Main(string[] args) {
    SystemTime st = new SystemTime();
    GetSystemTime(st);
    Console.WriteLine(st.Year);
}
```

W powyższym przykładzie wyłączone przykładowe wywołanie `GetSystemTime()` funkcji. Bit interesujące znajduje się w wierszu 4. Ten atrybut określa, czy pola klasy powinny być mapowane sekwencyjnie strukturę po drugiej stronie (niezarządzany). Oznacza, że nazwy pól nie ważne tylko ich kolejność jest ważna, ponieważ musi odpowiadać niezarządzane struktury, pokazano poniżej:

```c
typedef struct _SYSTEMTIME {
  WORD wYear;
  WORD wMonth;
  WORD wDayOfWeek;
  WORD wDay;
  WORD wHour;
  WORD wMinute;
  WORD wSecond;
  WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME*;
```

Już widzieliśmy w przykładzie z systemami Linux i macOS tego w poprzednim przykładzie. Jest on widoczny ponownie poniżej.

```csharp
[StructLayout(LayoutKind.Sequential)]
public class StatClass {
        public uint DeviceID;
        public uint InodeNumber;
        public uint Mode;
        public uint HardLinks;
        public uint UserID;
        public uint GroupID;
        public uint SpecialDeviceID;
        public ulong Size;
        public ulong BlockSize;
        public uint Blocks;
        public long TimeLastAccess;
        public long TimeLastModification;
        public long TimeLastStatusChange;
}
```

`StatClass` Klasy reprezentuje strukturę, która jest zwracana w wyniku `stat` wywołań systemowych na komputerach z systemem UNIX. Reprezentuje informacje dotyczące danego pliku. Klasa powyżej jest reprezentacja stat — struktura w kodzie zarządzanym. Ponownie pola w klasie muszą być w tej samej kolejności jako natywny — Struktura (można znaleźć tych elementów przy perusing man stron w ulubionych implementacji UNIX) i muszą mieć ten sam typ podstawowy.

## <a name="more-resources"></a>Więcej zasobów

*   [Witryna typu wiki PInvoke.net](https://www.pinvoke.net/) znakomity Wiki z informacji o typowych API Win32 i połączeń telefonicznych z nimi.
*   [P/Invoke w witrynie MSDN](https://msdn.microsoft.com/library/zbz07712.aspx)
*   [Dokumentacja mono P/Invoke](https://www.mono-project.com/docs/advanced/pinvoke/)
