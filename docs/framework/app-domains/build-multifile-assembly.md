---
title: 'Instrukcje: kompilowanie zestawu wieloplikowego'
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- Al.exe
- command-line compilers
- assembly manifest, multifile assemblies
- assemblies [.NET Framework], compiling
- Assembly Linker
- code modules
- multifile assemblies
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
ms.openlocfilehash: 0f8c6d57425657e321d80f9edffa20f27bc28770
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429568"
---
# <a name="how-to-build-a-multifile-assembly"></a>Instrukcje: kompilowanie zestawu wieloplikowego

W tym artykule opisano sposób tworzenia zestawu wieloplikowego i zawiera kod, który ilustruje każdy krok w procedurze.

> [!NOTE]
> Środowisko IDE programu Visual Studio C# dla i Visual Basic może być używane tylko do tworzenia zestawów jednoplikowych. Jeśli chcesz utworzyć zestawy wieloplikowe, musisz użyć kompilatorów wiersza polecenia lub programu Visual Studio z wizualizacją C++. Zestawy wieloplikowe są obsługiwane tylko przez .NET Framework.

## <a name="create-a-multifile-assembly"></a>Tworzenie zestawu wieloplikowego

1. Kompiluj wszystkie pliki, które zawierają przestrzenie nazw, do których odwołują się inne moduły w zestawie, do modułów kodu. Domyślnym rozszerzeniem modułów kodu jest *. module*.

   Załóżmy na przykład, że plik `Stringer` ma przestrzeń nazw o nazwie `myStringer`, która zawiera klasę o nazwie `Stringer`. Klasa `Stringer` zawiera metodę o nazwie `StringerMethod`, która zapisuje jeden wiersz w konsoli.

   ```cpp
   // Assembly building example in the .NET Framework.
   using namespace System;

   namespace myStringer
   {
       public ref class Stringer
       {
       public:
           void StringerMethod()
           {
               System::Console::WriteLine("This is a line from StringerMethod.");
           }
       };
   }
   ```

   ```csharp
   // Assembly building example in the .NET Framework.
   using System;

   namespace myStringer
   {
       public class Stringer
       {
           public void StringerMethod()
           {
               System.Console.WriteLine("This is a line from StringerMethod.");
           }
       }
   }
   ```

   ```vb
   ' Assembly building example in the .NET Framework.
   Namespace myStringer
       Public Class Stringer
           Public Sub StringerMethod()
               System.Console.WriteLine("This is a line from StringerMethod.")
           End Sub
       End Class
   End Namespace
   ```

2. Użyj następującego polecenia, aby skompilować ten kod:

   ```cpp
   cl /clr:pure /LN Stringer.cpp
   ```

   ```csharp
   csc /t:module Stringer.cs
   ```

   ```vb
   vbc /t:module Stringer.vb
   ```

   Określenie parametru *modułu* z opcją **/t:** kompilator wskazuje, że plik powinien zostać skompilowany jako moduł, a nie jako zestaw. Kompilator tworzy moduł o nazwie *Stringer. webmodule*, który można dodać do zestawu.

3. Kompiluj wszystkie inne moduły przy użyciu niezbędnych opcji kompilatora, aby wskazać inne moduły, do których istnieją odwołania w kodzie. W tym kroku jest stosowana opcja kompilatora **/addmodule** .

   W poniższym przykładzie moduł kodu o nazwie *Client* ma punkt wejścia `Main` metodę, która odwołuje się do metody w module *Stringer. dll* utworzonym w kroku 1.

   ```cpp
   #using "Stringer.netmodule"

   using namespace System;
   using namespace myStringer; //The namespace created in Stringer.netmodule.

   ref class MainClientApp
   {
       // Static method Main is the entry point method.
   public:
       static void Main()
       {
           Stringer^ myStringInstance = gcnew Stringer();
           Console::WriteLine("Client code executes");
           myStringInstance->StringerMethod();
       }
   };

   int main()
   {
       MainClientApp::Main();
   }
   ```

   ```csharp
   using System;
   using myStringer;

   class MainClientApp
   {
       // Static method Main is the entry point method.
       public static void Main()
       {
           Stringer myStringInstance = new Stringer();
           Console.WriteLine("Client code executes");
           myStringInstance.StringerMethod();
       }
   }
   ```

   ```vb
   Imports myStringer

   Class MainClientApp
       ' Static method Main is the entry point method.
       Public Shared Sub Main()
           Dim myStringInstance As New Stringer()
           Console.WriteLine("Client code executes")
           myStringInstance.StringerMethod()
       End Sub
   End Class
   ```

4. Użyj następującego polecenia, aby skompilować ten kod:

   ```cpp
   cl /clr:pure /FUStringer.netmodule /LN Client.cpp
   ```

   ```csharp
   csc /addmodule:Stringer.netmodule /t:module Client.cs
   ```

   ```vb
   vbc /addmodule:Stringer.netmodule /t:module Client.vb
   ```

   Określ opcję **/t: module** , ponieważ ten moduł zostanie dodany do zestawu w przyszłym kroku. Określ opcję **/addmodule** , ponieważ kod w *kliencie* odwołuje się do przestrzeni nazw utworzonej przez kod w *Stringer. module*. Kompilator generuje moduł o nazwie *Client. webmodule* , który zawiera odwołanie do innego modułu, *Stringer. webmodule*.

   > [!NOTE]
   > Kompilatory C# i Visual Basic obsługują bezpośrednie tworzenie zestawów wieloplikowych przy użyciu następujących dwóch różnych składni.
   >
   > Dwie kompilacje tworzą zestaw dwóch plików:
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /t:module Stringer.cs
   >   csc Client.cs /addmodule:Stringer.netmodule
   >   ```
   >
   >   ```vb
   >   vbc /t:module Stringer.vb
   >   vbc Client.vb /addmodule:Stringer.netmodule
   >   ```
   >
   > Jedna kompilacja tworzy zestaw dwóch plików:
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /out:Client.exe Client.cs /out:Stringer.netmodule Stringer.cs
   >   ```
   >
   >   ```vb
   >   vbc /out:Client.exe Client.vb /out:Stringer.netmodule Stringer.vb
   >   ```

5. Użyj [konsolidatora zestawu (Al. exe)](../tools/al-exe-assembly-linker.md) , aby utworzyć plik wyjściowy, który zawiera manifest zestawu. Ten plik zawiera informacje referencyjne dotyczące wszystkich modułów lub zasobów, które są częścią zestawu.

    W wierszu polecenia wpisz następujące polecenie:

    *Nazwa modułu* **Al** \<> *Nazwa modułu*\<>... **/Main:** \<*Nazwa metody*>  **/out:** \<*Nazwa pliku*>  **/target:** \<*Typ pliku zestawu*>

    W tym poleceniu argumenty *nazwy modułu* określają nazwę każdego modułu, który ma zostać uwzględniony w zestawie. **/Main:** opcja określa nazwę metody, która jest punktem wejścia zestawu. **/Out:** opcja określa nazwę pliku wyjściowego, który zawiera metadane zestawu. **/Target:** opcja określa, że zestaw to plik wykonywalny aplikacji konsoli (*exe*), plik wykonywalny systemu Windows ( *. win*) lub plik biblioteki ( *. lib*).

    W poniższym przykładzie *Al. exe* tworzy zestaw, który jest plikiem wykonywalnym aplikacji konsoli o nazwie mój *Assembly. exe*. Aplikacja składa się z dwóch modułów o nazwie *Client. webmodule* i *Stringer. webmodule*, a plik wykonywalny o nazwie *. exe*, który zawiera tylko metadane zestawu. Punkt wejścia zestawu jest metodą `Main` w klasie `MainClientApp`, która znajduje się w *pliku Client. dll*.

    ```cmd
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    Aby sprawdzić zawartość zestawu lub określić, czy plik jest zestawem lub modułem, można użyć [Dezasembler MSIL (Ildasm. exe)](../tools/ildasm-exe-il-disassembler.md) .

## <a name="see-also"></a>Zobacz także

- [Tworzenie zestawów](../../standard/assembly/create.md)
- [Instrukcje: wyświetlanie zawartości zestawu](../../standard/assembly/view-contents.md)
- [Jak środowisko uruchomieniowe lokalizuje zestawy](../deployment/how-the-runtime-locates-assemblies.md)
- [Zestawy wieloplikowe](multifile-assemblies.md)
