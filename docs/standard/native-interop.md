---
title: Współdziałanie natywne
description: Dowiedz się, jak współpracować z usługą składnikami macierzystymi na platformie .NET.
author: blackdwarf
ms.author: ronpet
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 3c357112-35fb-44ba-a07b-6a1c140370ac
ms.openlocfilehash: 14dfe7639a160af64e925018a4fd9e2bd44d4fe1
ms.sourcegitcommit: 49af435bfdd41faf26d38c20c5b0cc07e87bea60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53396815"
---
# <a name="native-interoperability"></a>Współdziałanie natywne

W tym dokumencie będzie Zaczniemy nieco bardziej wszystkie trzy metody "współdziałanie natywne", które są dostępne przy użyciu platformy .NET.

Istnieje kilka powodów dlaczego warto mogą wywoływać kodu natywnego:

*   Systemy operacyjne są dostarczane z dużą liczbą interfejsów API, które nie są obecne w bibliotekach klas zarządzanych. Podstawowy przykład to będzie dostęp do sprzętu lub systemu operacyjnego, funkcji zarządzania.
*   Komunikacja z innymi składnikami, które lub może tworzyć interfejsy ABI stylu języka C (natywnych interfejsów ABI). W tym artykule opisano, na przykład, kod Java, który jest uwidaczniany za pomocą [interfejsem Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) lub dowolnym innym języku zarządzanych, które może powodować składnika macierzystego.
*   W Windows większość oprogramowania instalowanego, takich jak pakiet Microsoft Office rejestruje składników COM, które reprezentują swoich programów i umożliwiają deweloperom Automatyzowanie je lub używać ich. Wymaga to interoperacyjności macierzystej.

Oczywiście na powyższej liście nie obejmuje wszystkich potencjalnych sytuacji i scenariusze, w których deweloper może chcesz/podobne/potrzebę do połączenia interfejsem z składnikami macierzystymi. Biblioteka klas programu .NET, na przykład korzysta z obsługi interoperacyjności macierzystej zaimplementować podejście liczbę interfejsów API, takich jak obsługa konsoli i manipulowania, dostęp do systemu plików i inne. Jednak ważne jest należy pamiętać, że jest dostępna opcja, należy jeden potrzebny.

> [!NOTE]
> Większość przykładów w tym dokumencie, zostanie wyświetlone dla wszystkich trzech obsługiwanych platform dla platformy .NET Core (Windows, Linux i macOS). Kilka przykładów krótki i opisowy tylko jeden przykład jest jednak wyświetlany korzystający Windows nazwy plików i rozszerzenia (czyli "dll" jak biblioteki). Nie oznacza to, że te funkcje nie są dostępne w systemie Linux lub macOS, została wykonana jedynie dla wygody sake.

## <a name="platform-invoke-pinvoke"></a>Wywołanie platformy (P/Invoke)

P/Invoke jest to technologia, która umożliwia dostęp do struktury, wywołania zwrotne i funkcji w bibliotekach niezarządzanych w kodzie zarządzanym. Większość interfejsów API P/Invoke jest zawarta w dwie przestrzeni nazw: `System` i `System.Runtime.InteropServices`. Używanie tych dwóch przestrzeni nazw zezwoli na dostęp do atrybutów, które opisują, jak chcesz nawiązać połączenia z usługą składnika macierzystego.

Zacznijmy od najbardziej typowym przykładem, a wywołującym niezarządzane funkcje w kodzie zarządzanym. Umożliwia wyświetlanie pola komunikatu z aplikacji wiersza polecenia:

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

W powyższym przykładzie jest dość prosta, ale stażysta co jest potrzebne do wywoływania funkcji niezarządzanych z kodu zarządzanego. Rozważmy kroki przykładu:

*   #1. wiersz zawiera za pomocą instrukcji for `System.Runtime.InteropServices` czyli przestrzeni nazw, który zawiera wszystkie elementy potrzebne.
*   Wiersz #5 wprowadza `DllImport` atrybutu. Ten atrybut jest niezwykle istotne, ponieważ informuje, środowisko uruchomieniowe, należy go załadować niezarządzaną biblioteką DLL. Jest to biblioteka DLL, do którego chcesz możemy wywołać.
*   Wiersz #6 jest crux pracy P/Invoke. Definiuje metody zarządzanej, która ma **dokładnie tym samym podpisie** , niezarządzanych. Deklaracja ma nowe słowo kluczowe, które można zauważyć, `extern`informuje środowisko uruchomieniowe, to jest metody zewnętrznej oraz że po jej wywołaniu, środowisko wykonawcze powinno znajduje się w biblioteki DLL określonej w `DllImport` atrybutu.

Rest przykładu jest po prostu wywołania metody, tak jak każda inna metoda zarządzanych.

Przykład jest podobny dla systemu macOS. Jeden element, który wymaga wprowadzenia zmian jest oczywiście nazwę biblioteki w `DllImport` atrybutu, zgodnie z systemem macOS ma inny schemat nazewnictwa bibliotek dynamicznych. Przykładowe poniżej został użyty `getpid(2)` funkcję, aby pobrać Identyfikatora procesu aplikacji i wydrukuj go w konsoli.

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

Jest również w podobny sposób na systemie Linux. Nazwa funkcji jest taka sama, ponieważ `getpid(2)` jest standardem [POSIX](https://en.wikipedia.org/wiki/POSIX) wywołanie systemowe.

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

### <a name="invoking-managed-code-from-unmanaged-code"></a>Wywoływanie kodu zarządzanego z niezarządzanego kodu

Oczywiście środowisko uruchomieniowe umożliwia komunikację do przepływu w obu kierunkach, co pozwala na wywołanie do zarządzanego artefaktów z funkcji natywnych, za pomocą wskaźników funkcji. W najbliższej kolejności ze wskaźnikiem funkcji w kodzie zarządzanym **delegować**, więc jest to, co umożliwia wywołania zwrotne z kodu natywnego do zarządzanego kodu.

Sposób, aby użyć tej funkcji jest podobny do kodu zarządzanego do natywnego opisany powyżej proces. Danego wywołania zwrotnego możesz zdefiniować delegata, która pasuje do oznaczenia i przekazać go do metody zewnętrznej. Środowisko uruchomieniowe będzie zajmujemy się całą resztą.

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

Zanim omówimy naszym przykładzie warto omijają sygnatur funkcji niezarządzanych, potrzebne do pracy z. Funkcję, którą chcesz wywołać, aby wyliczyć wszystkie okna ma następujący podpis: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`

Pierwszy parametr jest wywołanie zwrotne. Wspomniane wywołanie zwrotne ma następujący podpis: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`

Pamiętając o tym Przejdźmy przykładu:

*   Wiersz #8 w przykładzie definiuje delegata, która pasuje do oznaczenia wywołania zwrotnego z niezarządzanego kodu. Zwróć uwagę, jak typy LPARAM i HWND są reprezentowane za pomocą `IntPtr` w kodzie zarządzanym.
*   Wprowadzenie wiersze #10 i #11 `EnumWindows` funkcji z biblioteki user32.dll.
*   Wiersze #13 16 zaimplementować delegata. Na tym prostym przykładzie chcemy tylko się dane wyjściowe dojścia do konsoli.
*   Na koniec w wierszu #19 możemy wywołać metody zewnętrznej i przekazać delegata.

Poniżej przedstawiono przykłady systemów Linux i macOS. Dla nich używamy `ftw` funkcja, która znajduje się w `libc`, biblioteki C. Ta funkcja jest używana na przechodzenie przez hierarchie katalogu i pobiera wskaźnik do funkcji jako jeden z jego parametrów. Funkcja wspomniane ma następujący podpis: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.

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

przykład z systemem macOS używa tej samej funkcji, a jedyną różnicą jest argumentem `DllImport` atrybutu, ponieważ utrzymuje systemu macOS `libc` w innym miejscu.

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

Oba powyższe przykłady są zależne od parametrów, a w obu przypadkach parametry są podane jako typami zarządzanymi. Środowisko uruchomieniowe wykonuje "dobre" i przetwarza je na ich odpowiedniki po drugiej stronie. Ponieważ ten proces jest naprawdę ważne podczas pisania kodu macierzystego międzyoperacyjny jakości, Przyjrzyjmy się co się dzieje, gdy środowisko uruchomieniowe _marshals_ typów.

## <a name="type-marshalling"></a>Typ zarządzany

**Kierowania** jest procesem przekształcania typów, kiedy ich potrzebują do przekroczenia granicę zarządzanych w trybie macierzystym i na odwrót.

Kierowania przyczyna jest wymagana, ponieważ różnią się typami w kodzie zarządzanym i niezarządzanym. W kodzie zarządzanym, na przykład masz `String`, natomiast w świecie niezarządzanych ciągi mogą być Unicode ("szerokiego"), innego niż Unicode, zakończony wartością null ASCII, itp. Domyślnie w podsystemie P/Invoke podejmie próbę postępują właściwie na podstawie [domyślne zachowanie](../../docs/framework/interop/default-marshaling-behavior.md). Jednak w tych sytuacjach, gdy potrzebujesz dodatkowych kontroli, zostanie zastosowana [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) atrybutu, aby określić, co to jest oczekiwany typ w niezarządzanym. Na przykład jeśli chcemy, aby ciąg do wysłania jako ciąg znaków zakończony znakiem null ANSI, można robimy to następująco:

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

### <a name="marshalling-classes-and-structs"></a>Kierowania klasy i struktury

Innym aspektem kierowania typu jest sposób przekazywania w strukturze metody niezarządzanego. Na przykład niektóre z niezarządzanych metod wymagają struktury jako parametr. W takich przypadkach należy utworzyć odpowiednie struktury lub klasy w zarządzanych części świata, który będzie używany jako parametr. Jednak po prostu Definiowanie klasy nie jest wystarczająco dużo, musimy również poinstruować Organizator sposób mapowania pól w klasie do struktury niezarządzanej. Jest to miejsce `StructLayout` atrybut, który jest dostarczany do gry.

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

W powyższym przykładzie poza prosty przykład wywołanie `GetSystemTime()` funkcji. Bit interesujące znajduje się w wierszu 4. Ten atrybut określa, że pola klasy powinno zostać zamapowane sekwencyjnie struktury z drugiej strony (niezarządzanego). Oznacza to, że nazwy pól są nieważne, tylko ich kolejność jest ważna, ponieważ musi on odpowiadać niezarządzane struktury, pokazano poniżej:

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

Już widzieliśmy w systemie Linux i macOS przykładzie w tym w poprzednim przykładzie. Jest on wyświetlany ponownie poniżej.

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

`StatClass` Klasa reprezentuje strukturę, która jest zwracana przez `stat` wywołanie systemowe w systemach UNIX. Reprezentuje informacje dotyczące danego pliku. Klasa powyżej jest reprezentacją stat — struktura w kodzie zarządzanym. Ponownie pola w klasie muszą znajdować się w tej samej kolejności jako natywny — Struktura (możesz znaleźć, perusing strony ataków typu man na Twojej ulubionej implementacji UNIX) i muszą mieć ten sam typ podstawowy.

## <a name="more-resources"></a>Inne zasoby

*   [PInvoke.net wiki](https://www.pinvoke.net/) doskonałe witryny typu Wiki przy użyciu informacji o typowych interfejsów API systemu Win32 i sposobie ich wywoływania.
*   [P/Invoke w witrynie MSDN](https://msdn.microsoft.com/library/zbz07712.aspx)
*   [Dokumentacja narzędzia mono w P/Invoke](https://www.mono-project.com/docs/advanced/pinvoke/)
