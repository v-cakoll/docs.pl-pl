---
title: 'Instrukcje: Kompilacja zestawów wieloplikowych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
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
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a964e73cc41cebad33a3edc34b89ef240fbc62c8
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040855"
---
# <a name="how-to-build-a-multifile-assembly"></a>Instrukcje: Kompilacja zestawów wieloplikowych

W tym artykule opisano sposób tworzenia zestawu wieloplikowego i zawiera kod, który ilustruje każdy krok w procedurze.

> [!NOTE]
> Środowisko IDE programu Visual Studio C# dla i Visual Basic może być używane tylko do tworzenia zestawów jednoplikowych. Jeśli chcesz utworzyć zestawy wieloplikowe, musisz użyć kompilatorów wiersza polecenia lub programu Visual Studio z wizualizacją C++.

### <a name="to-create-a-multifile-assembly"></a>Aby utworzyć zestaw wieloplikowy

01. Kompiluj wszystkie pliki, które zawierają przestrzenie nazw, do których odwołują się inne moduły w zestawie, do modułów kodu. Domyślnym rozszerzeniem modułów kodu jest. module.

    Załóżmy na przykład, że `Stringer` plik ma przestrzeń nazw o nazwie `myStringer`, która zawiera klasę o nazwie `Stringer`. Klasa zawiera metodę o nazwie `StringerMethod` , która zapisuje jeden wiersz w konsoli. `Stringer`

    [!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]
    [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]
    [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]

    Użyj następującego polecenia, aby skompilować ten kod:

    [!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]
    [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]
    [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]

    Określenie parametru *modułu* z opcją **/t:** kompilator wskazuje, że plik powinien zostać skompilowany jako moduł, a nie jako zestaw. Kompilator tworzy moduł o nazwie `Stringer.netmodule`, który można dodać do zestawu.

02. Kompiluj wszystkie inne moduły przy użyciu niezbędnych opcji kompilatora, aby wskazać inne moduły, do których istnieją odwołania w kodzie. W tym kroku jest stosowana opcja kompilatora **/addmodule** .

    W poniższym przykładzie moduł kodu o nazwie `Client` ma metodę punktu `Main` wejścia, która `Stringer.dll` odwołuje się do metody w module utworzonym w kroku 1.

    [!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]
    [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]
    [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]

    Użyj następującego polecenia, aby skompilować ten kod:

    [!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]
    [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]
    [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]

    Określ opcję **/t: module** , ponieważ ten moduł zostanie dodany do zestawu w przyszłym kroku. Określ opcję **/addmodule** , ponieważ kod w `Client` odwołuje się do przestrzeni nazw utworzonej przez kod w. `Stringer.netmodule` Kompilator tworzy moduł o nazwie `Client.netmodule` , który zawiera odwołanie do innego `Stringer.netmodule`modułu.

    >[!NOTE]
    >Kompilatory C# i Visual Basic obsługują bezpośrednie tworzenie zestawów wieloplikowych przy użyciu następujących dwóch różnych składni.
    >
    >- Dwie kompilacje tworzą zestaw dwóch plików:[!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]
    >  [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]
    >  [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]
    >
    >- Jedna kompilacja tworzy zestaw dwóch plików:[!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]
    >  [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]
    >  [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]

03. Użyj [konsolidatora zestawu (Al. exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) , aby utworzyć plik wyjściowy, który zawiera manifest zestawu. Ten plik zawiera informacje referencyjne dotyczące wszystkich modułów lub zasobów, które są częścią zestawu.

    W wierszu polecenia wpisz następujące polecenie:

    **Al***Nazwa*modułunazw> modułów>... \<\< **/Main:** \<*Nazwa***metody/out:** nazwa pliku/Target:\<*Typ pliku* zestawu\<> > >

    W tym poleceniu argumenty *nazwy modułu* określają nazwę każdego modułu, który ma zostać uwzględniony w zestawie. **/Main:** opcja określa nazwę metody, która jest punktem wejścia zestawu. **/Out:** opcja określa nazwę pliku wyjściowego, który zawiera metadane zestawu. **/Target:** opcja określa, że zestaw to plik wykonywalny aplikacji konsoli (exe), plik wykonywalny systemu Windows (. win) lub plik biblioteki (. lib).

    W poniższym przykładzie Al. exe tworzy zestaw, który jest plikiem wykonywalnym aplikacji konsoli o nazwie `myAssembly.exe`. Aplikacja składa się z dwóch modułów `Client.netmodule` o `Stringer.netmodule`nazwie i, a plik wykonywalny o nazwie `myAssembly.exe,` , który zawiera tylko metadane zestawu. Punkt wejścia zestawu jest `Main` metodą w klasie `MainClientApp`, która znajduje się w `Client.dll`.

    ```
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    Aby sprawdzić zawartość zestawu lub określić, czy plik jest zestawem lub modułem, można użyć [Dezasembler MSIL (Ildasm. exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) .

## <a name="see-also"></a>Zobacz także

- [Tworzenie zestawów](../../../docs/framework/app-domains/create-assemblies.md)
- [Instrukcje: Wyświetl zawartość zestawu](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Zestawy wieloplikowe](../../../docs/framework/app-domains/multifile-assemblies.md)
