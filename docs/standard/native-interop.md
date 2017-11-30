---
title: "Współdziałanie natywnego"
description: "Dowiedz się, jak interfejs ze składnikami natywnego programu .NET."
keywords: .NET, .NET core
author: blackdwarf
ms.author: ronpet
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3c357112-35fb-44ba-a07b-6a1c140370ac
ms.openlocfilehash: 9652986491f087b8fa175e2b4041063c71211178
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="native-interoperability"></a><span data-ttu-id="3e4d9-104">Współdziałanie natywnego</span><span class="sxs-lookup"><span data-stu-id="3e4d9-104">Native Interoperability</span></span>

<span data-ttu-id="3e4d9-105">W tym dokumencie, firma Microsoft będzie Poznaj nieco bardziej wszystkie trzy sposoby wykonanie "natywny współdziałania", które są dostępne przy użyciu platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-105">In this document, we will dive a little bit deeper into all three ways of doing "native interoperability" that are available using .NET.</span></span>

<span data-ttu-id="3e4d9-106">Istnieje kilka przyczyn, dlaczego warto wywoływać kodu natywnego:</span><span class="sxs-lookup"><span data-stu-id="3e4d9-106">There are a few of reasons why you would want to call into native code:</span></span>

*   <span data-ttu-id="3e4d9-107">Systemy operacyjne są dostarczane z dużą ilością interfejsów API, które nie są dostępne w bibliotekach klas zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-107">Operating Systems come with a large volume of APIs that are not present in the managed class libraries.</span></span> <span data-ttu-id="3e4d9-108">Podstawowym przykład dla tego będzie dostęp do sprzętu lub systemu operacyjnego funkcje zarządzania.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-108">A prime example for this would be access to hardware or operating system management functions.</span></span>
*   <span data-ttu-id="3e4d9-109">Podczas komunikacji z innymi składnikami, które lub można utworzyć ABIs stylu języka C (native ABIs).</span><span class="sxs-lookup"><span data-stu-id="3e4d9-109">Communicating with other components that have or can produce C-style ABIs (native ABIs).</span></span> <span data-ttu-id="3e4d9-110">Obejmuje, na przykład kodu języka Java, który jest dostępny za pośrednictwem [Java natywnego interfejsu (JNI)](http://docs.oracle.com/javase/8/docs/technotes/guides/jni/) lub dowolnego zarządzanego języka, który może utworzyć składnik macierzysty.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-110">This covers, for example, Java code that is exposed via [Java Native Interface (JNI)](http://docs.oracle.com/javase/8/docs/technotes/guides/jni/) or any other managed language that could produce a native component.</span></span>
*   <span data-ttu-id="3e4d9-111">W systemie Windows większość oprogramowania, które są instalowane, takich jak pakiet Microsoft Office, rejestruje składników COM, które reprezentują programów i umożliwiają deweloperom zautomatyzować je lub używać ich.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-111">On Windows, most of the software that gets installed, such as Microsoft Office suite, registers COM components that represent their programs and allow developers to automate them or use them.</span></span> <span data-ttu-id="3e4d9-112">Wymaga to współdziałanie macierzystego.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-112">This also requires native interoperability.</span></span>

<span data-ttu-id="3e4d9-113">Oczywiście powyższej listy nie obejmuje wszystkich potencjalnych sytuacji i scenariusze, w których deweloper może chcesz/podobne/potrzebę interfejs ze składnikami natywnego.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-113">Of course, the list above does not cover all of the potential situations and scenarios in which the developer would want/like/need to interface with native components.</span></span> <span data-ttu-id="3e4d9-114">Biblioteka klas programu .NET, na przykład używa Obsługa natywnego współdziałanie do implementacji odpowiedniego liczba interfejsów API, takie jak obsługa konsoli i manipulowania, dostępu do systemu plików i innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-114">.NET class library, for instance, uses the native interoperability support to implement a fair number of its APIs, like console support and manipulation, file system access and others.</span></span> <span data-ttu-id="3e4d9-115">Jednak ważne jest, należy pamiętać, że ma opcji, należy należy go.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-115">However, it is important to note that there is an option, should one need it.</span></span>

> [!NOTE]
> <span data-ttu-id="3e4d9-116">Większość przykładów w tym dokumencie będzie udostępniana dla wszystkich trzech obsługiwanych platform dla platformy .NET Core (Windows, Linux lub macOS).</span><span class="sxs-lookup"><span data-stu-id="3e4d9-116">Most of the examples in this document will be presented for all three supported platforms for .NET Core (Windows, Linux and macOS).</span></span> <span data-ttu-id="3e4d9-117">Jednak niektóre przykłady krótki i opisowy tylko jeden przykład jest przedstawić używającą Windows nazwy plików i rozszerzenia (to znaczy "dll" bibliotek).</span><span class="sxs-lookup"><span data-stu-id="3e4d9-117">However, for some short and illustrative examples, just one sample is shown that uses Windows filenames and extensions (that is, "dll" for libraries).</span></span> <span data-ttu-id="3e4d9-118">Oznacza to, że te funkcje nie są dostępne w systemie Linux lub macOS, została wykonana wyłącznie dla wygody sake.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-118">This does not mean that those features are not available on Linux or macOS, it was done merely for convenience sake.</span></span>

## <a name="platform-invoke-pinvoke"></a><span data-ttu-id="3e4d9-119">Wywołanie platformy (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="3e4d9-119">Platform Invoke (P/Invoke)</span></span>

<span data-ttu-id="3e4d9-120">P/Invoke jest technologia, która umożliwia dostęp do struktury, wywołania zwrotne i funkcji w bibliotekach niezarządzane z kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-120">P/Invoke is a technology that allows you to access structs, callbacks and functions in unmanaged libraries from your managed code.</span></span> <span data-ttu-id="3e4d9-121">Większość API P/Invoke znajduje się w dwóch obszarach nazw: `System` i `System.Runtime.InteropServices`.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-121">Most of the P/Invoke API is contained in two namespaces: `System` and `System.Runtime.InteropServices`.</span></span> <span data-ttu-id="3e4d9-122">Korzystanie z tych dwóch przestrzeni nazw będzie zezwalał na dostęp do atrybutów, które opisują sposób komunikowania się z składnik macierzysty.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-122">Using these two namespaces will allow you access to the attributes that describe how you want to communicate with the native component.</span></span>

<span data-ttu-id="3e4d9-123">Zacznijmy od najbardziej typowym przykładem, i który jest wywoływanie niezarządzanych funkcji w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-123">Let’s start from the most common example, and that is calling unmanaged functions in your managed code.</span></span> <span data-ttu-id="3e4d9-124">Umożliwia wyświetlanie okna komunikatu z wiersza polecenia aplikacji:</span><span class="sxs-lookup"><span data-stu-id="3e4d9-124">Let’s show a message box from a command-line application:</span></span>

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

<span data-ttu-id="3e4d9-125">W powyższym przykładzie jest dość proste, ale pokazywanie co jest potrzebne do wywołania niezarządzanej funkcji z kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-125">The example above is pretty simple, but it does show off what is needed to invoke unmanaged functions from managed code.</span></span> <span data-ttu-id="3e4d9-126">Załóżmy kroków opisanych w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3e4d9-126">Let’s step through the example:</span></span>

*   <span data-ttu-id="3e4d9-127">#1 wiersz zawiera za pomocą instrukcji dla `System.Runtime.InteropServices` czyli przestrzeni nazw, który zawiera wszystkie elementy potrzebne.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-127">Line #1 shows the using statement for the `System.Runtime.InteropServices` which is the namespace that holds all of the items we need.</span></span>
*   <span data-ttu-id="3e4d9-128">Wprowadza wiersza #5 `DllImport` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-128">Line #5 introduces the `DllImport` attribute.</span></span> <span data-ttu-id="3e4d9-129">Ten atrybut jest niezwykle ważny, ponieważ informuje środowiska uruchomieniowego, że należy załadować niezarządzanej DLL.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-129">This attribute is crucial, as it tells the runtime that it should load the unmanaged DLL.</span></span> <span data-ttu-id="3e4d9-130">Jest to plik DLL, do którego możemy chcesz wywołać.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-130">This is the DLL into which we wish to invoke.</span></span>
*   <span data-ttu-id="3e4d9-131">Wiersz #6 jest crux pracy P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-131">Line #6 is the crux of the P/Invoke work.</span></span> <span data-ttu-id="3e4d9-132">Definiuje metodę zarządzanych, która ma **dokładnie takiego samego podpisu** jako niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-132">It defines a managed method that has the **exact same signature** as the unmanaged one.</span></span> <span data-ttu-id="3e4d9-133">Deklaracja zawiera słowo kluczowe new, który można zauważysz, `extern`, który określa, że środowisko wykonawcze to jest zewnętrzną metodę, a gdy go wywołać, środowisko uruchomieniowe powinien go znaleźć w bibliotece DLL określone w `DllImport` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-133">The declaration has a new keyword that you can notice, `extern`, which tells the runtime this is an external method, and that when you invoke it, the runtime should find it in the DLL specified in `DllImport` attribute.</span></span>

<span data-ttu-id="3e4d9-134">Pozostałe przykładu jest tylko wywołania metody, jak w przypadku innych metod zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-134">The rest of the example is just invoking the method as you would any other managed method.</span></span>

<span data-ttu-id="3e4d9-135">Próbki jest podobny do macOS.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-135">The sample is similar for macOS.</span></span> <span data-ttu-id="3e4d9-136">Rzecz, którą chcesz zmienić jest oczywiście nazwę biblioteki w `DllImport` atrybutu jako macOS ma inny schemat nazewnictwa bibliotek dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-136">One thing that needs to change is, of course, the name of the library in the `DllImport` attribute, as macOS has a different scheme of naming dynamic libraries.</span></span> <span data-ttu-id="3e4d9-137">Przykładowe poniżej używa `getpid(2)` funkcji, aby pobrać Identyfikatora procesu aplikacji i wydrukuj go do konsoli.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-137">The sample below uses the `getpid(2)` function to get the process ID of the application and print it out to the console.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libc and define the method corresponding to the native function.
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

<span data-ttu-id="3e4d9-138">Przypomina on w systemie Linux, oczywiście.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-138">It is similar on Linux, of course.</span></span> <span data-ttu-id="3e4d9-139">Nazwa funkcji jest takie same, ponieważ `getpid(2)` jest [POSIX](https://en.wikipedia.org/wiki/POSIX) wywołanie systemowe.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-139">The function name is same, since `getpid(2)` is [POSIX](https://en.wikipedia.org/wiki/POSIX) system call.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libc and define the method corresponding to the native function.
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

### <a name="invoking-managed-code-from-unmanaged-code"></a><span data-ttu-id="3e4d9-140">Wywoływanie kodu zarządzanego z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="3e4d9-140">Invoking managed code from unmanaged code</span></span>

<span data-ttu-id="3e4d9-141">Oczywiście środowiska uruchomieniowego umożliwia komunikację przepływać w obu kierunkach, dzięki czemu można wywołać w zarządzanych artefaktów z funkcji macierzystym, przy użyciu wskaźników funkcji.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-141">Of course, the runtime allows communication to flow both ways which enables you to call into managed artifacts from native functions, using function pointers.</span></span> <span data-ttu-id="3e4d9-142">Najbliższy operacją do wskaźnika funkcji w kodzie zarządzanym jest **delegować**, więc jest to, co umożliwia wywołań zwrotnych z kodu natywnego kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-142">The closest thing to a function pointer in managed code is a **delegate**, so this is what is used to allow callbacks from native code into managed code.</span></span>

<span data-ttu-id="3e4d9-143">Sposób, aby użyć tej funkcji jest podobny do kodu zarządzanego do natywnych proces opisany powyżej.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-143">The way to use this feature is similar to managed to native process described above.</span></span> <span data-ttu-id="3e4d9-144">Dla danego wywołania zwrotnego zdefiniuj delegata, który odpowiada podpis, a który przekazywane do metody zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-144">For a given callback, you define a delegate that matches the signature, and pass that into the external method.</span></span> <span data-ttu-id="3e4d9-145">Wszystkie inne zajmie się środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-145">The runtime will take care of everything else.</span></span>

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

<span data-ttu-id="3e4d9-146">Zanim firma Microsoft przeprowadzenie naszym przykładzie jest gotowe za pośrednictwem podpisów niezarządzanych funkcji potrzebnych do pracy z.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-146">Before we walk through our example, it is good to go over the signatures of the unmanaged functions we need to work with.</span></span> <span data-ttu-id="3e4d9-147">Funkcję, którą chcesz wywołać wyliczyć wszystkie okna ma następującą sygnaturą:`BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`</span><span class="sxs-lookup"><span data-stu-id="3e4d9-147">The function we want to call to enumerate all of the windows has the following signature: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`</span></span>

<span data-ttu-id="3e4d9-148">Pierwszym parametrem jest wywołaniem zwrotnym.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-148">The first parameter is a callback.</span></span> <span data-ttu-id="3e4d9-149">Wspomniane wywołania zwrotnego ma następującą sygnaturą:`BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`</span><span class="sxs-lookup"><span data-stu-id="3e4d9-149">The said callback has the following signature: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`</span></span>

<span data-ttu-id="3e4d9-150">Pamiętając o tym Przejdźmy przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3e4d9-150">With this in mind, let’s walk through the example:</span></span>

*   <span data-ttu-id="3e4d9-151">Wiersz #8 w przykładzie definiuje delegata, który pasuje do podpisu wywołania zwrotnego z kodem niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-151">Line #8 in the example defines a delegate that matches the signature of the callback from unmanaged code.</span></span> <span data-ttu-id="3e4d9-152">Zwróć uwagę, jak LPARAM i HWND typy są przedstawiane za pomocą `IntPtr` w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-152">Notice how the LPARAM and HWND types are represented using `IntPtr` in the managed code.</span></span>
*   <span data-ttu-id="3e4d9-153">Wprowadzenie wierszy #10 i #11 `EnumWindows` funkcji z biblioteki user32.dll.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-153">Lines #10 and #11 introduce the `EnumWindows` function from the user32.dll library.</span></span>
*   <span data-ttu-id="3e4d9-154">Wiersze #13-16 implementuje delegata.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-154">Lines #13 - 16 implement the delegate.</span></span> <span data-ttu-id="3e4d9-155">W tym przykładzie prosty chcemy tylko dane wyjściowe dojścia do konsoli.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-155">For this simple example, we just want to output the handle to the console.</span></span>
*   <span data-ttu-id="3e4d9-156">Na koniec wiersza #19 możemy wywołanie metody zewnętrznej i podaj delegata.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-156">Finally, in line #19 we invoke the external method and pass in the delegate.</span></span>

<span data-ttu-id="3e4d9-157">Poniżej przedstawiono przykłady systemu Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-157">The Linux and macOS examples are shown below.</span></span> <span data-ttu-id="3e4d9-158">Ich używamy `ftw` funkcji, które znajdują się w `libc`, biblioteki C.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-158">For them, we use the `ftw` function that can be found in `libc`, the C library.</span></span> <span data-ttu-id="3e4d9-159">Ta funkcja umożliwia przechodzenie między hierarchiami katalogu i zajmuje wskaźnika do funkcji jako jeden z jego parametrów.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-159">This function is used to traverse directory hierarchies and it takes a pointer to a function as one of its parameters.</span></span> <span data-ttu-id="3e4d9-160">Funkcja wspomnianej ma następującą sygnaturą: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-160">The said function has the following signature: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.</span></span>

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

<span data-ttu-id="3e4d9-161">System macOS przykładzie użyto taką samą funkcję, a jedyną różnicą jest argumentem `DllImport` atrybutu, ponieważ przechowuje macOS `libc` w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-161">macOS example uses the same function, and the only difference is the argument to the `DllImport` attribute, as macOS keeps `libc` in a different place.</span></span>

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

<span data-ttu-id="3e4d9-162">Oba powyższe przykłady są zależne od parametrów, a w obu przypadkach parametry są następujące typy zarządzane.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-162">Both of the above examples depend on parameters, and in both cases, the parameters are given as managed types.</span></span> <span data-ttu-id="3e4d9-163">Środowisko uruchomieniowe nie "co" i przetwarza je w jego odpowiedników po drugiej stronie.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-163">Runtime does the "right thing" and processes these into its equivalents on the other side.</span></span> <span data-ttu-id="3e4d9-164">Ponieważ ten proces jest naprawdę ważne do pisania kodu natywnego międzyoperacyjnego jakości, Spójrzmy na co się stanie, gdy środowisko uruchomieniowe _marshals_ typów.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-164">Since this process is really important to writing quality native interop code, let’s take a look at what happens when the runtime _marshals_ the types.</span></span>

## <a name="type-marshalling"></a><span data-ttu-id="3e4d9-165">Kierowanie typu</span><span class="sxs-lookup"><span data-stu-id="3e4d9-165">Type marshalling</span></span>

<span data-ttu-id="3e4d9-166">**Kierowanie** jest procesem przekształcania typów, gdy konieczne jest przekraczają granicę zarządzanego do natywnego i na odwrót.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-166">**Marshalling** is the process of transforming types when they need to cross the managed boundary into native and vice versa.</span></span>

<span data-ttu-id="3e4d9-167">Kierowanie przyczyna jest wymagane jest, ponieważ różnią się typami w kodzie zarządzane i niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-167">The reason marshalling is needed is because the types in the managed and unmanaged code are different.</span></span> <span data-ttu-id="3e4d9-168">W kodzie zarządzanym, na przykład masz `String`, podczas gdy w świecie niezarządzane ciągi może być Unicode ("szeroka"), z systemem innym niż Unicode, zerem, ASCII, itp. Domyślnie podsystem P/Invoke spróbuje wykonać czynność prawej na zachowanie domyślne, które można wyświetlić na podstawie [MSDN](https://msdn.microsoft.com/library/zah6xy75.aspx).</span><span class="sxs-lookup"><span data-stu-id="3e4d9-168">In managed code, for instance, you have a `String`, while in the unmanaged world strings can be Unicode ("wide"), non-Unicode, null-terminated, ASCII, etc. By default, the P/Invoke subsystem will try to do the Right Thing based on the default behavior which you can see on [MSDN](https://msdn.microsoft.com/library/zah6xy75.aspx).</span></span> <span data-ttu-id="3e4d9-169">Jednak w tych sytuacjach konieczne dodatkowe formantu zostanie zastosowana `MarshalAs` atrybutu, aby określić, co to jest oczekiwany typ po stronie niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-169">However, for those situations where you need extra control, you can employ the `MarshalAs` attribute to specify what is the expected type on the unmanaged side.</span></span> <span data-ttu-id="3e4d9-170">Na przykład aby ciąg, który zostanie wysłany jako ciągu ANSI zerem, można go jak następująco:</span><span class="sxs-lookup"><span data-stu-id="3e4d9-170">For instance, if we want the string to be sent as a null-terminated ANSI string, we could do it like this:</span></span>

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

### <a name="marshalling-classes-and-structs"></a><span data-ttu-id="3e4d9-171">Kierowanie klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="3e4d9-171">Marshalling classes and structs</span></span>

<span data-ttu-id="3e4d9-172">Innym aspektem kierowania typu jest sposób przekazywania w strukturze do metody niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-172">Another aspect of type marshalling is how to pass in a struct to an unmanaged method.</span></span> <span data-ttu-id="3e4d9-173">Na przykład wymagać pewnych metod niezarządzane struktury jako parametr.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-173">For instance, some of the unmanaged methods require a struct as a parameter.</span></span> <span data-ttu-id="3e4d9-174">W takich sytuacjach należy utworzyć odpowiednie struktury lub klasy w zarządzanych części świecie, aby używać go jako parametr.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-174">In these cases, we need to create a corresponding struct or a class in managed part of the world to use it as a parameter.</span></span> <span data-ttu-id="3e4d9-175">Jednak tylko Definiowanie klasy nie jest wystarczająco, musimy także poinstruować organizatora sposób mapowania pól w klasie niezarządzanej strukturę.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-175">However, just defining the class is not enough, we also need to instruct the marshaler how to map fields in the class to the unmanaged struct.</span></span> <span data-ttu-id="3e4d9-176">Jest to, gdy `StructLayout` atrybutu wejścia play.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-176">This is where the `StructLayout` attribute comes into play.</span></span>

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

<span data-ttu-id="3e4d9-177">W powyższym przykładzie wyłączone przykładowe wywołanie `GetSystemTime()` funkcji.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-177">The example above shows off a simple example of calling into `GetSystemTime()` function.</span></span> <span data-ttu-id="3e4d9-178">Bit interesujące znajduje się w wierszu 4.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-178">The interesting bit is on line 4.</span></span> <span data-ttu-id="3e4d9-179">Ten atrybut określa, czy pola klasy powinny być mapowane sekwencyjnie strukturę po drugiej stronie (niezarządzany).</span><span class="sxs-lookup"><span data-stu-id="3e4d9-179">The attribute specifies that the fields of the class should be mapped sequentially to the struct on the other (unmanaged) side.</span></span> <span data-ttu-id="3e4d9-180">Oznacza, że nazwy pól nie ważne tylko ich kolejność jest ważna, ponieważ musi odpowiadać niezarządzane struktury, pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="3e4d9-180">This means that the naming of the fields is not important, only their order is important, as it needs to correspond to the unmanaged struct, shown below:</span></span>

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

<span data-ttu-id="3e4d9-181">Już widzieliśmy w przykładzie z systemami Linux i macOS tego w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-181">We already saw the Linux and macOS example for this in the previous example.</span></span> <span data-ttu-id="3e4d9-182">Jest on widoczny ponownie poniżej.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-182">It is shown again below.</span></span>

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

<span data-ttu-id="3e4d9-183">`StatClass` Klasy reprezentuje strukturę, która jest zwracana w wyniku `stat` wywołań systemowych na komputerach z systemem UNIX.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-183">The `StatClass` class represents a structure that is returned by the `stat` system call on UNIX systems.</span></span> <span data-ttu-id="3e4d9-184">Reprezentuje informacje dotyczące danego pliku.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-184">It represents information about a given file.</span></span> <span data-ttu-id="3e4d9-185">Klasa powyżej jest reprezentacja stat — struktura w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-185">The class above is the stat struct representation in managed code.</span></span> <span data-ttu-id="3e4d9-186">Ponownie pola w klasie muszą być w tej samej kolejności jako natywny — Struktura (można znaleźć tych elementów przy perusing man stron w ulubionych implementacji UNIX) i muszą mieć ten sam typ podstawowy.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-186">Again, the fields in the class have to be in the same order as the native struct (you can find these by perusing man pages on your favorite UNIX implementation) and they have to be of the same underlying type.</span></span>

## <a name="more-resources"></a><span data-ttu-id="3e4d9-187">Więcej zasobów</span><span class="sxs-lookup"><span data-stu-id="3e4d9-187">More resources</span></span>

*   <span data-ttu-id="3e4d9-188">[Witryna typu wiki PInvoke.net](http://www.pinvoke.net) znakomity Wiki z informacji o typowych API Win32 i połączeń telefonicznych z nimi.</span><span class="sxs-lookup"><span data-stu-id="3e4d9-188">[PInvoke.net wiki](http://www.pinvoke.net) an excellent Wiki with information on common Win32 APIs and how to call them.</span></span>
*   [<span data-ttu-id="3e4d9-189">P/Invoke w witrynie MSDN</span><span class="sxs-lookup"><span data-stu-id="3e4d9-189">P/Invoke on MSDN</span></span>](https://msdn.microsoft.com/library/zbz07712.aspx)
*   [<span data-ttu-id="3e4d9-190">Dokumentacja mono P/Invoke</span><span class="sxs-lookup"><span data-stu-id="3e4d9-190">Mono documentation on P/Invoke</span></span>](http://www.mono-project.com/docs/advanced/pinvoke/)
