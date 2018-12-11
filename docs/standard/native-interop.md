---
title: Współdziałanie natywne
description: Dowiedz się, jak współpracować z usługą składnikami macierzystymi na platformie .NET.
author: blackdwarf
ms.author: ronpet
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 3c357112-35fb-44ba-a07b-6a1c140370ac
ms.openlocfilehash: 2f427eb5d8f41f730d4263425e268213db92236d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143191"
---
# <a name="native-interoperability"></a><span data-ttu-id="4c4b9-103">Współdziałanie natywne</span><span class="sxs-lookup"><span data-stu-id="4c4b9-103">Native Interoperability</span></span>

<span data-ttu-id="4c4b9-104">W tym dokumencie będzie Zaczniemy nieco bardziej wszystkie trzy metody "współdziałanie natywne", które są dostępne przy użyciu platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-104">In this document, we will dive a little bit deeper into all three ways of doing "native interoperability" that are available using .NET.</span></span>

<span data-ttu-id="4c4b9-105">Istnieje kilka powodów dlaczego warto mogą wywoływać kodu natywnego:</span><span class="sxs-lookup"><span data-stu-id="4c4b9-105">There are a few of reasons why you would want to call into native code:</span></span>

*   <span data-ttu-id="4c4b9-106">Systemy operacyjne są dostarczane z dużą liczbą interfejsów API, które nie są obecne w bibliotekach klas zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-106">Operating Systems come with a large volume of APIs that are not present in the managed class libraries.</span></span> <span data-ttu-id="4c4b9-107">Podstawowy przykład to będzie dostęp do sprzętu lub systemu operacyjnego, funkcji zarządzania.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-107">A prime example for this would be access to hardware or operating system management functions.</span></span>
*   <span data-ttu-id="4c4b9-108">Komunikacja z innymi składnikami, które lub może tworzyć interfejsy ABI stylu języka C (natywnych interfejsów ABI).</span><span class="sxs-lookup"><span data-stu-id="4c4b9-108">Communicating with other components that have or can produce C-style ABIs (native ABIs).</span></span> <span data-ttu-id="4c4b9-109">W tym artykule opisano, na przykład, kod Java, który jest uwidaczniany za pomocą [interfejsem Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) lub dowolnym innym języku zarządzanych, które może powodować składnika macierzystego.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-109">This covers, for example, Java code that is exposed via [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) or any other managed language that could produce a native component.</span></span>
*   <span data-ttu-id="4c4b9-110">W Windows większość oprogramowania instalowanego, takich jak pakiet Microsoft Office rejestruje składników COM, które reprezentują swoich programów i umożliwiają deweloperom Automatyzowanie je lub używać ich.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-110">On Windows, most of the software that gets installed, such as Microsoft Office suite, registers COM components that represent their programs and allow developers to automate them or use them.</span></span> <span data-ttu-id="4c4b9-111">Wymaga to interoperacyjności macierzystej.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-111">This also requires native interoperability.</span></span>

<span data-ttu-id="4c4b9-112">Oczywiście na powyższej liście nie obejmuje wszystkich potencjalnych sytuacji i scenariusze, w których deweloper może chcesz/podobne/potrzebę do połączenia interfejsem z składnikami macierzystymi.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-112">Of course, the list above does not cover all of the potential situations and scenarios in which the developer would want/like/need to interface with native components.</span></span> <span data-ttu-id="4c4b9-113">Biblioteka klas programu .NET, na przykład korzysta z obsługi interoperacyjności macierzystej zaimplementować podejście liczbę interfejsów API, takich jak obsługa konsoli i manipulowania, dostęp do systemu plików i inne.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-113">.NET class library, for instance, uses the native interoperability support to implement a fair number of its APIs, like console support and manipulation, file system access and others.</span></span> <span data-ttu-id="4c4b9-114">Jednak ważne jest należy pamiętać, że jest dostępna opcja, należy jeden potrzebny.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-114">However, it is important to note that there is an option, should one need it.</span></span>

> [!NOTE]
> <span data-ttu-id="4c4b9-115">Większość przykładów w tym dokumencie, zostanie wyświetlone dla wszystkich trzech obsługiwanych platform dla platformy .NET Core (Windows, Linux i macOS).</span><span class="sxs-lookup"><span data-stu-id="4c4b9-115">Most of the examples in this document will be presented for all three supported platforms for .NET Core (Windows, Linux and macOS).</span></span> <span data-ttu-id="4c4b9-116">Kilka przykładów krótki i opisowy tylko jeden przykład jest jednak wyświetlany korzystający Windows nazwy plików i rozszerzenia (czyli "dll" jak biblioteki).</span><span class="sxs-lookup"><span data-stu-id="4c4b9-116">However, for some short and illustrative examples, just one sample is shown that uses Windows filenames and extensions (that is, "dll" for libraries).</span></span> <span data-ttu-id="4c4b9-117">Nie oznacza to, że te funkcje nie są dostępne w systemie Linux lub macOS, została wykonana jedynie dla wygody sake.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-117">This does not mean that those features are not available on Linux or macOS, it was done merely for convenience sake.</span></span>

## <a name="platform-invoke-pinvoke"></a><span data-ttu-id="4c4b9-118">Wywołanie platformy (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="4c4b9-118">Platform Invoke (P/Invoke)</span></span>

<span data-ttu-id="4c4b9-119">P/Invoke jest to technologia, która umożliwia dostęp do struktury, wywołania zwrotne i funkcji w bibliotekach niezarządzanych w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-119">P/Invoke is a technology that allows you to access structs, callbacks and functions in unmanaged libraries from your managed code.</span></span> <span data-ttu-id="4c4b9-120">Większość interfejsów API P/Invoke jest zawarta w dwie przestrzeni nazw: `System` i `System.Runtime.InteropServices`.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-120">Most of the P/Invoke API is contained in two namespaces: `System` and `System.Runtime.InteropServices`.</span></span> <span data-ttu-id="4c4b9-121">Używanie tych dwóch przestrzeni nazw zezwoli na dostęp do atrybutów, które opisują, jak chcesz nawiązać połączenia z usługą składnika macierzystego.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-121">Using these two namespaces will allow you access to the attributes that describe how you want to communicate with the native component.</span></span>

<span data-ttu-id="4c4b9-122">Zacznijmy od najbardziej typowym przykładem, a wywołującym niezarządzane funkcje w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-122">Let’s start from the most common example, and that is calling unmanaged functions in your managed code.</span></span> <span data-ttu-id="4c4b9-123">Umożliwia wyświetlanie pola komunikatu z aplikacji wiersza polecenia:</span><span class="sxs-lookup"><span data-stu-id="4c4b9-123">Let’s show a message box from a command-line application:</span></span>

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

<span data-ttu-id="4c4b9-124">W powyższym przykładzie jest dość prosta, ale stażysta co jest potrzebne do wywoływania funkcji niezarządzanych z kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-124">The example above is pretty simple, but it does show off what is needed to invoke unmanaged functions from managed code.</span></span> <span data-ttu-id="4c4b9-125">Rozważmy kroki przykładu:</span><span class="sxs-lookup"><span data-stu-id="4c4b9-125">Let’s step through the example:</span></span>

*   <span data-ttu-id="4c4b9-126">#1. wiersz zawiera za pomocą instrukcji for `System.Runtime.InteropServices` czyli przestrzeni nazw, który zawiera wszystkie elementy potrzebne.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-126">Line #1 shows the using statement for the `System.Runtime.InteropServices` which is the namespace that holds all of the items we need.</span></span>
*   <span data-ttu-id="4c4b9-127">Wiersz #5 wprowadza `DllImport` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-127">Line #5 introduces the `DllImport` attribute.</span></span> <span data-ttu-id="4c4b9-128">Ten atrybut jest niezwykle istotne, ponieważ informuje, środowisko uruchomieniowe, należy go załadować niezarządzaną biblioteką DLL.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-128">This attribute is crucial, as it tells the runtime that it should load the unmanaged DLL.</span></span> <span data-ttu-id="4c4b9-129">Jest to biblioteka DLL, do którego chcesz możemy wywołać.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-129">This is the DLL into which we wish to invoke.</span></span>
*   <span data-ttu-id="4c4b9-130">Wiersz #6 jest crux pracy P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-130">Line #6 is the crux of the P/Invoke work.</span></span> <span data-ttu-id="4c4b9-131">Definiuje metody zarządzanej, która ma **dokładnie tym samym podpisie** , niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-131">It defines a managed method that has the **exact same signature** as the unmanaged one.</span></span> <span data-ttu-id="4c4b9-132">Deklaracja ma nowe słowo kluczowe, które można zauważyć, `extern`informuje środowisko uruchomieniowe, to jest metody zewnętrznej oraz że po jej wywołaniu, środowisko wykonawcze powinno znajduje się w biblioteki DLL określonej w `DllImport` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-132">The declaration has a new keyword that you can notice, `extern`, which tells the runtime this is an external method, and that when you invoke it, the runtime should find it in the DLL specified in `DllImport` attribute.</span></span>

<span data-ttu-id="4c4b9-133">Rest przykładu jest po prostu wywołania metody, tak jak każda inna metoda zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-133">The rest of the example is just invoking the method as you would any other managed method.</span></span>

<span data-ttu-id="4c4b9-134">Przykład jest podobny dla systemu macOS.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-134">The sample is similar for macOS.</span></span> <span data-ttu-id="4c4b9-135">Jeden element, który wymaga wprowadzenia zmian jest oczywiście nazwę biblioteki w `DllImport` atrybutu, zgodnie z systemem macOS ma inny schemat nazewnictwa bibliotek dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-135">One thing that needs to change is, of course, the name of the library in the `DllImport` attribute, as macOS has a different scheme of naming dynamic libraries.</span></span> <span data-ttu-id="4c4b9-136">Przykładowe poniżej został użyty `getpid(2)` funkcję, aby pobrać Identyfikatora procesu aplikacji i wydrukuj go w konsoli.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-136">The sample below uses the `getpid(2)` function to get the process ID of the application and print it out to the console.</span></span>

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

<span data-ttu-id="4c4b9-137">Jest również w podobny sposób na systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-137">It is also similar on Linux.</span></span> <span data-ttu-id="4c4b9-138">Nazwa funkcji jest taka sama, ponieważ `getpid(2)` jest standardem [POSIX](https://en.wikipedia.org/wiki/POSIX) wywołanie systemowe.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-138">The function name is the same, since `getpid(2)` is a standard [POSIX](https://en.wikipedia.org/wiki/POSIX) system call.</span></span>

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

### <a name="invoking-managed-code-from-unmanaged-code"></a><span data-ttu-id="4c4b9-139">Wywoływanie kodu zarządzanego z niezarządzanego kodu</span><span class="sxs-lookup"><span data-stu-id="4c4b9-139">Invoking managed code from unmanaged code</span></span>

<span data-ttu-id="4c4b9-140">Oczywiście środowisko uruchomieniowe umożliwia komunikację do przepływu w obu kierunkach, co pozwala na wywołanie do zarządzanego artefaktów z funkcji natywnych, za pomocą wskaźników funkcji.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-140">Of course, the runtime allows communication to flow both ways which enables you to call into managed artifacts from native functions, using function pointers.</span></span> <span data-ttu-id="4c4b9-141">W najbliższej kolejności ze wskaźnikiem funkcji w kodzie zarządzanym **delegować**, więc jest to, co umożliwia wywołania zwrotne z kodu natywnego do zarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-141">The closest thing to a function pointer in managed code is a **delegate**, so this is what is used to allow callbacks from native code into managed code.</span></span>

<span data-ttu-id="4c4b9-142">Sposób, aby użyć tej funkcji jest podobny do kodu zarządzanego do natywnego opisany powyżej proces.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-142">The way to use this feature is similar to managed to native process described above.</span></span> <span data-ttu-id="4c4b9-143">Danego wywołania zwrotnego możesz zdefiniować delegata, która pasuje do oznaczenia i przekazać go do metody zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-143">For a given callback, you define a delegate that matches the signature, and pass that into the external method.</span></span> <span data-ttu-id="4c4b9-144">Środowisko uruchomieniowe będzie zajmujemy się całą resztą.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-144">The runtime will take care of everything else.</span></span>

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

<span data-ttu-id="4c4b9-145">Zanim omówimy naszym przykładzie warto omijają sygnatur funkcji niezarządzanych, potrzebne do pracy z.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-145">Before we walk through our example, it is good to go over the signatures of the unmanaged functions we need to work with.</span></span> <span data-ttu-id="4c4b9-146">Funkcję, którą chcesz wywołać, aby wyliczyć wszystkie okna ma następujący podpis: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`</span><span class="sxs-lookup"><span data-stu-id="4c4b9-146">The function we want to call to enumerate all of the windows has the following signature: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`</span></span>

<span data-ttu-id="4c4b9-147">Pierwszy parametr jest wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-147">The first parameter is a callback.</span></span> <span data-ttu-id="4c4b9-148">Wspomniane wywołanie zwrotne ma następujący podpis: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`</span><span class="sxs-lookup"><span data-stu-id="4c4b9-148">The said callback has the following signature: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`</span></span>

<span data-ttu-id="4c4b9-149">Pamiętając o tym Przejdźmy przykładu:</span><span class="sxs-lookup"><span data-stu-id="4c4b9-149">With this in mind, let’s walk through the example:</span></span>

*   <span data-ttu-id="4c4b9-150">Wiersz #8 w przykładzie definiuje delegata, która pasuje do oznaczenia wywołania zwrotnego z niezarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-150">Line #8 in the example defines a delegate that matches the signature of the callback from unmanaged code.</span></span> <span data-ttu-id="4c4b9-151">Zwróć uwagę, jak typy LPARAM i HWND są reprezentowane za pomocą `IntPtr` w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-151">Notice how the LPARAM and HWND types are represented using `IntPtr` in the managed code.</span></span>
*   <span data-ttu-id="4c4b9-152">Wprowadzenie wiersze #10 i #11 `EnumWindows` funkcji z biblioteki user32.dll.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-152">Lines #10 and #11 introduce the `EnumWindows` function from the user32.dll library.</span></span>
*   <span data-ttu-id="4c4b9-153">Wiersze #13 16 zaimplementować delegata.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-153">Lines #13 - 16 implement the delegate.</span></span> <span data-ttu-id="4c4b9-154">Na tym prostym przykładzie chcemy tylko się dane wyjściowe dojścia do konsoli.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-154">For this simple example, we just want to output the handle to the console.</span></span>
*   <span data-ttu-id="4c4b9-155">Na koniec w wierszu #19 możemy wywołać metody zewnętrznej i przekazać delegata.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-155">Finally, in line #19 we invoke the external method and pass in the delegate.</span></span>

<span data-ttu-id="4c4b9-156">Poniżej przedstawiono przykłady systemów Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-156">The Linux and macOS examples are shown below.</span></span> <span data-ttu-id="4c4b9-157">Dla nich używamy `ftw` funkcja, która znajduje się w `libc`, biblioteki C.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-157">For them, we use the `ftw` function that can be found in `libc`, the C library.</span></span> <span data-ttu-id="4c4b9-158">Ta funkcja jest używana na przechodzenie przez hierarchie katalogu i pobiera wskaźnik do funkcji jako jeden z jego parametrów.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-158">This function is used to traverse directory hierarchies and it takes a pointer to a function as one of its parameters.</span></span> <span data-ttu-id="4c4b9-159">Funkcja wspomniane ma następujący podpis: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-159">The said function has the following signature: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.</span></span>

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

<span data-ttu-id="4c4b9-160">przykład z systemem macOS używa tej samej funkcji, a jedyną różnicą jest argumentem `DllImport` atrybutu, ponieważ utrzymuje systemu macOS `libc` w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-160">macOS example uses the same function, and the only difference is the argument to the `DllImport` attribute, as macOS keeps `libc` in a different place.</span></span>

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

<span data-ttu-id="4c4b9-161">Oba powyższe przykłady są zależne od parametrów, a w obu przypadkach parametry są podane jako typami zarządzanymi.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-161">Both of the above examples depend on parameters, and in both cases, the parameters are given as managed types.</span></span> <span data-ttu-id="4c4b9-162">Środowisko uruchomieniowe wykonuje "dobre" i przetwarza je na ich odpowiedniki po drugiej stronie.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-162">Runtime does the "right thing" and processes these into its equivalents on the other side.</span></span> <span data-ttu-id="4c4b9-163">Ponieważ ten proces jest naprawdę ważne podczas pisania kodu macierzystego międzyoperacyjny jakości, Przyjrzyjmy się co się dzieje, gdy środowisko uruchomieniowe _marshals_ typów.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-163">Since this process is really important to writing quality native interop code, let’s take a look at what happens when the runtime _marshals_ the types.</span></span>

## <a name="type-marshalling"></a><span data-ttu-id="4c4b9-164">Typ zarządzany</span><span class="sxs-lookup"><span data-stu-id="4c4b9-164">Type marshalling</span></span>

<span data-ttu-id="4c4b9-165">**Kierowania** jest procesem przekształcania typów, kiedy ich potrzebują do przekroczenia granicę zarządzanych w trybie macierzystym i na odwrót.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-165">**Marshalling** is the process of transforming types when they need to cross the managed boundary into native and vice versa.</span></span>

<span data-ttu-id="4c4b9-166">Kierowania przyczyna jest wymagana, ponieważ różnią się typami w kodzie zarządzanym i niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-166">The reason marshalling is needed is because the types in the managed and unmanaged code are different.</span></span> <span data-ttu-id="4c4b9-167">W kodzie zarządzanym, na przykład masz `String`, natomiast w świecie niezarządzanych ciągi mogą być Unicode ("szerokiego"), innego niż Unicode, zakończony wartością null ASCII, itp. Domyślnie w podsystemie P/Invoke podejmie próbę postępują właściwie na podstawie [domyślne zachowanie](../../docs/framework/interop/default-marshaling-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="4c4b9-167">In managed code, for instance, you have a `String`, while in the unmanaged world strings can be Unicode ("wide"), non-Unicode, null-terminated, ASCII, etc. By default, the P/Invoke subsystem will try to do the right thing based on the [default behavior](../../docs/framework/interop/default-marshaling-behavior.md).</span></span> <span data-ttu-id="4c4b9-168">Jednak w tych sytuacjach, gdy potrzebujesz dodatkowych kontroli, zostanie zastosowana [MarshalAs](xref:System.Runtime.InteropServicxes.MarshalAs) atrybutu, aby określić, co to jest oczekiwany typ w niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-168">However, for those situations where you need extra control, you can employ the [MarshalAs](xref:System.Runtime.InteropServicxes.MarshalAs) attribute to specify what is the expected type on the unmanaged side.</span></span> <span data-ttu-id="4c4b9-169">Na przykład jeśli chcemy, aby ciąg do wysłania jako ciąg znaków zakończony znakiem null ANSI, można robimy to następująco:</span><span class="sxs-lookup"><span data-stu-id="4c4b9-169">For instance, if we want the string to be sent as a null-terminated ANSI string, we could do it like this:</span></span>

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

### <a name="marshalling-classes-and-structs"></a><span data-ttu-id="4c4b9-170">Kierowania klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="4c4b9-170">Marshalling classes and structs</span></span>

<span data-ttu-id="4c4b9-171">Innym aspektem kierowania typu jest sposób przekazywania w strukturze metody niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-171">Another aspect of type marshalling is how to pass in a struct to an unmanaged method.</span></span> <span data-ttu-id="4c4b9-172">Na przykład niektóre z niezarządzanych metod wymagają struktury jako parametr.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-172">For instance, some of the unmanaged methods require a struct as a parameter.</span></span> <span data-ttu-id="4c4b9-173">W takich przypadkach należy utworzyć odpowiednie struktury lub klasy w zarządzanych części świata, który będzie używany jako parametr.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-173">In these cases, we need to create a corresponding struct or a class in managed part of the world to use it as a parameter.</span></span> <span data-ttu-id="4c4b9-174">Jednak po prostu Definiowanie klasy nie jest wystarczająco dużo, musimy również poinstruować Organizator sposób mapowania pól w klasie do struktury niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-174">However, just defining the class is not enough, we also need to instruct the marshaler how to map fields in the class to the unmanaged struct.</span></span> <span data-ttu-id="4c4b9-175">Jest to miejsce `StructLayout` atrybut, który jest dostarczany do gry.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-175">This is where the `StructLayout` attribute comes into play.</span></span>

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

<span data-ttu-id="4c4b9-176">W powyższym przykładzie poza prosty przykład wywołanie `GetSystemTime()` funkcji.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-176">The example above shows off a simple example of calling into `GetSystemTime()` function.</span></span> <span data-ttu-id="4c4b9-177">Bit interesujące znajduje się w wierszu 4.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-177">The interesting bit is on line 4.</span></span> <span data-ttu-id="4c4b9-178">Ten atrybut określa, że pola klasy powinno zostać zamapowane sekwencyjnie struktury z drugiej strony (niezarządzanego).</span><span class="sxs-lookup"><span data-stu-id="4c4b9-178">The attribute specifies that the fields of the class should be mapped sequentially to the struct on the other (unmanaged) side.</span></span> <span data-ttu-id="4c4b9-179">Oznacza to, że nazwy pól są nieważne, tylko ich kolejność jest ważna, ponieważ musi on odpowiadać niezarządzane struktury, pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="4c4b9-179">This means that the naming of the fields is not important, only their order is important, as it needs to correspond to the unmanaged struct, shown below:</span></span>

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

<span data-ttu-id="4c4b9-180">Już widzieliśmy w systemie Linux i macOS przykładzie w tym w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-180">We already saw the Linux and macOS example for this in the previous example.</span></span> <span data-ttu-id="4c4b9-181">Jest on wyświetlany ponownie poniżej.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-181">It is shown again below.</span></span>

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

<span data-ttu-id="4c4b9-182">`StatClass` Klasa reprezentuje strukturę, która jest zwracana przez `stat` wywołanie systemowe w systemach UNIX.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-182">The `StatClass` class represents a structure that is returned by the `stat` system call on UNIX systems.</span></span> <span data-ttu-id="4c4b9-183">Reprezentuje informacje dotyczące danego pliku.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-183">It represents information about a given file.</span></span> <span data-ttu-id="4c4b9-184">Klasa powyżej jest reprezentacją stat — struktura w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-184">The class above is the stat struct representation in managed code.</span></span> <span data-ttu-id="4c4b9-185">Ponownie pola w klasie muszą znajdować się w tej samej kolejności jako natywny — Struktura (możesz znaleźć, perusing strony ataków typu man na Twojej ulubionej implementacji UNIX) i muszą mieć ten sam typ podstawowy.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-185">Again, the fields in the class have to be in the same order as the native struct (you can find these by perusing man pages on your favorite UNIX implementation) and they have to be of the same underlying type.</span></span>

## <a name="more-resources"></a><span data-ttu-id="4c4b9-186">Inne zasoby</span><span class="sxs-lookup"><span data-stu-id="4c4b9-186">More resources</span></span>

*   <span data-ttu-id="4c4b9-187">[PInvoke.net wiki](https://www.pinvoke.net/) doskonałe witryny typu Wiki przy użyciu informacji o typowych interfejsów API systemu Win32 i sposobie ich wywoływania.</span><span class="sxs-lookup"><span data-stu-id="4c4b9-187">[PInvoke.net wiki](https://www.pinvoke.net/) an excellent Wiki with information on common Win32 APIs and how to call them.</span></span>
*   [<span data-ttu-id="4c4b9-188">P/Invoke w witrynie MSDN</span><span class="sxs-lookup"><span data-stu-id="4c4b9-188">P/Invoke on MSDN</span></span>](https://msdn.microsoft.com/library/zbz07712.aspx)
*   [<span data-ttu-id="4c4b9-189">Dokumentacja narzędzia mono w P/Invoke</span><span class="sxs-lookup"><span data-stu-id="4c4b9-189">Mono documentation on P/Invoke</span></span>](https://www.mono-project.com/docs/advanced/pinvoke/)
