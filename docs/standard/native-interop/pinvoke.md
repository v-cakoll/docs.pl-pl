---
title: Wywołanie platformy (P/Invoke)
description: Dowiedz się, jak wywoływać funkcje natywne za pośrednictwem metody P/Invoke na platformie .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: ed1eb69a418317bbee2502418cc2521a68b65542
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063182"
---
# <a name="platform-invoke-pinvoke"></a>Wywołanie platformy (P/Invoke)

P/Invoke jest to technologia, która umożliwia dostęp do struktury, wywołania zwrotne i funkcji w bibliotekach niezarządzanych w kodzie zarządzanym. Większość interfejsów API P/Invoke jest zawarta w dwie przestrzeni nazw: `System` i `System.Runtime.InteropServices`. Używanie tych dwóch przestrzeni nazw zapewnią Ci narzędzia do opisywania sposobu komunikowania się za pomocą składnika macierzystego.

Zacznijmy od najbardziej typowym przykładem, a wywołującym niezarządzane funkcje w kodzie zarządzanym. Umożliwia wyświetlanie pola komunikatu z aplikacji wiersza polecenia:

```csharp
using System;
using System.Runtime.InteropServices;

public class Program
{
    // Import user32.dll (containing the function we need) and define
    // the method corresponding to the native function.
    [DllImport("user32.dll", CharSet = CharSet.Unicode, SetLastError = true)]
    public static extern int MessageBox(IntPtr hWnd, string lpText, string lpCaption, uint uType);

    public static void Main(string[] args)
    {
        // Invoke the function as a regular managed method.
        MessageBox(IntPtr.Zero, "Command-line message box", "Attention!", 0);
    }
}
```

Poprzedni przykład jest proste, ale stażysta co jest potrzebne do wywoływania funkcji niezarządzanych z kodu zarządzanego. Rozważmy kroki przykładu:

* #1. wiersz zawiera za pomocą instrukcji for `System.Runtime.InteropServices` przestrzeni nazw, który zawiera wszystkie elementy, które są potrzebne.
* Wprowadza wiersza #7 `DllImport` atrybutu. Ten atrybut jest niezwykle istotne, ponieważ informuje, środowisko uruchomieniowe, należy go załadować niezarządzaną biblioteką DLL. Przekazany ciąg jest biblioteką DLL, funkcja naszym docelowym znajduje się w. Ponadto określa, które [zestaw znaków](./charset.md) na potrzeby kierowania ciągi. Ponadto określa, że ta funkcja wywołuje [SetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-setlasterror) i środowiska uruchomieniowego należy przechwytywać tego kodu błędu, dzięki czemu użytkownik może pobrać go za pomocą <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error?displayProperty=nameWithType>.
* Wiersz #8 jest crux pracy P/Invoke. Definiuje metody zarządzanej, która ma **dokładnie tym samym podpisie** , niezarządzanych. Deklaracja ma nowe słowo kluczowe, które można zauważyć, `extern`informuje środowisko uruchomieniowe, to jest metody zewnętrznej oraz że po jej wywołaniu, środowisko wykonawcze powinno znajduje się w biblioteki DLL określonej w `DllImport` atrybutu.

Rest przykładu jest po prostu wywołania metody, tak jak każda inna metoda zarządzanych.

Przykład jest podobny dla systemu macOS. Nazwa biblioteki w `DllImport` atrybut wymaga wprowadzenia zmian, ponieważ inny schemat nazewnictwa bibliotek dynamicznych z systemem macOS. Następujące przykładowe używa `getpid(2)` funkcję, aby pobrać Identyfikatora procesu aplikacji i wydrukuj go do konsoli:

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples
{
    public static class Program
    {
        // Import the libSystem shared library and define the method
        // corresponding to the native function.
        [DllImport("libSystem.dylib")]
        private static extern int getpid();

        public static void Main(string[] args)
        {
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

namespace PInvokeSamples
{
    public static class Program
    {
        // Import the libc shared library and define the method
        // corresponding to the native function.
        [DllImport("libc.so.6")]
        private static extern int getpid();

        public static void Main(string[] args)
        {
            // Invoke the function and get the process ID.
            int pid = getpid();
            Console.WriteLine(pid);
        }
    }
}
```

## <a name="invoking-managed-code-from-unmanaged-code"></a>Wywoływanie kodu zarządzanego z niezarządzanego kodu

Środowisko uruchomieniowe umożliwia komunikację do przepływu w obu kierunkach, co umożliwia wywołanie zwrotne wywołanie kodu zarządzanego z natywnych funkcji za pomocą wskaźnika funkcji. W najbliższej kolejności ze wskaźnikiem funkcji w kodzie zarządzanym **delegować**, więc jest to, co umożliwia wywołania zwrotne z kodu natywnego do zarządzanego kodu.

Sposób, aby użyć tej funkcji jest podobny do procesu zarządzanego do natywnego opisany wcześniej. Dla danego wywołania zwrotnego zdefiniowanie pełnomocnika, który pasuje do podpisu i przekazać go do metody zewnętrznej. Środowisko uruchomieniowe będzie zajmujemy się całą resztą.

```csharp
using System;
using System.Runtime.InteropServices;

namespace ConsoleApplication1
{
    class Program
    {
        // Define a delegate that corresponds to the unmanaged function.
        delegate bool EnumWC(IntPtr hwnd, IntPtr lParam);

        // Import user32.dll (containing the function we need) and define
        // the method corresponding to the native function.
        [DllImport("user32.dll")]
        static extern int EnumWindows(EnumWC lpEnumFunc, IntPtr lParam);

        // Define the implementation of the delegate; here, we simply output the window handle.
        static bool OutputWindow(IntPtr hwnd, IntPtr lParam)
        {
            Console.WriteLine(hwnd.ToInt64());
            return true;
        }

        static void Main(string[] args)
        {
            // Invoke the method; note the delegate as a first parameter.
            EnumWindows(OutputWindow, IntPtr.Zero);
        }
    }
}
```

Przed zalet w przykładzie, dobrze jest przejrzeć sygnatur funkcji niezarządzanych, które są potrzebne do pracy z. Funkcja wywoływana, aby wyliczyć wszystkie okna ma następujący podpis: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`

Pierwszy parametr jest wywołanie zwrotne. Wspomniane wywołanie zwrotne ma następujący podpis: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`

Teraz przejdźmy przykładu:

* Wiersz #9, w tym przykładzie definiuje delegata, która pasuje do oznaczenia wywołania zwrotnego z niezarządzanego kodu. Zwróć uwagę, jak typy LPARAM i HWND są reprezentowane za pomocą `IntPtr` w kodzie zarządzanym.
* Wprowadzenie wiersze #13 i #14 `EnumWindows` funkcji z biblioteki user32.dll.
* Wiersze #17-20 zaimplementować delegata. Na tym prostym przykładzie chcemy tylko się dane wyjściowe dojścia do konsoli.
* W wierszu #24 metody zewnętrznej jest na końcu, nazywana i przekazywana w delegacie.

Poniżej przedstawiono przykłady systemów Linux i macOS. Dla nich używamy `ftw` funkcja, która znajduje się w `libc`, biblioteki C. Ta funkcja jest używana na przechodzenie przez hierarchie katalogu i pobiera wskaźnik do funkcji jako jeden z jego parametrów. Funkcja wspomniane ma następujący podpis: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples
{
    public static class Program
    {
        // Define a delegate that has the same signature as the native function.
        delegate int DirClbk(string fName, StatClass stat, int typeFlag);

        // Import the libc and define the method to represent the native function.
        [DllImport("libc.so.6")]
        static extern int ftw(string dirpath, DirClbk cl, int descriptors);

        // Implement the above DirClbk delegate;
        // this one just prints out the filename that is passed to it.
        static int DisplayEntry(string fName, StatClass stat, int typeFlag)
        {
            Console.WriteLine(fName);
            return 0;
        }

        public static void Main(string[] args)
        {
            // Call the native function.
            // Note the second parameter which represents the delegate (callback).
            ftw(".", DisplayEntry, 10);
        }
    }

    // The native callback takes a pointer to a struct. The below class
    // represents that struct in managed code. You can find more information
    // about this in the section on marshaling below.
    [StructLayout(LayoutKind.Sequential)]
    public class StatClass
    {
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

namespace PInvokeSamples
{
    public static class Program
    {
        // Define a delegate that has the same signature as the native function.
        delegate int DirClbk(string fName, StatClass stat, int typeFlag);

        // Import the libc and define the method to represent the native function.
        [DllImport("libSystem.dylib")]
        static extern int ftw(string dirpath, DirClbk cl, int descriptors);

        // Implement the above DirClbk delegate;
        // this one just prints out the filename that is passed to it.
        static int DisplayEntry(string fName, StatClass stat, int typeFlag)
        {
            Console.WriteLine(fName);
            return 0;
        }

        public static void Main(string[] args)
        {
            // Call the native function.
            // Note the second parameter which represents the delegate (callback).
            ftw(".", DisplayEntry, 10);
        }
    }

    // The native callback takes a pointer to a struct. The below class
    // represents that struct in managed code.
    [StructLayout(LayoutKind.Sequential)]
    public class StatClass
    {
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

Zarówno poprzednich przykładach są zależne od parametrów, a w obu przypadkach parametry są podane jako typami zarządzanymi. Środowisko uruchomieniowe wykonuje "dobre" i przetwarza je na ich odpowiedniki po drugiej stronie. Dowiedz się więcej o jak typy są przekazywane do kodu natywnego w naszej strony na [marshaling typu](type-marshaling.md).

## <a name="more-resources"></a>Inne zasoby

- [PInvoke.net wiki](https://www.pinvoke.net/) doskonałe witryny typu Wiki przy użyciu informacji o typowych Windows interfejsów API oraz sposób ich wywoływania.
- [P/Invoke w C++sposób niezamierzony](/cpp/dotnet/native-and-dotnet-interoperability)
- [Dokumentacja narzędzia mono w P/Invoke](https://www.mono-project.com/docs/advanced/pinvoke/)
