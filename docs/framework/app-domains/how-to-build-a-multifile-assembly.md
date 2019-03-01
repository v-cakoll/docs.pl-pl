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
ms.openlocfilehash: 68f525244f2238ebdc44116fc91c3ddcb0a79bfd
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975059"
---
# <a name="how-to-build-a-multifile-assembly"></a>Instrukcje: Kompilacja zestawów wieloplikowych
W tym artykule wyjaśniono, jak utworzyć zestaw wieloplikowy i zawiera kod, który ilustruje każdy krok w procedurze.

> [!NOTE]
> Visual Studio IDE dla C# i Visual Basic należy używać tylko do tworzenia zespołów pojedynczego pliku. Jeśli chcesz utworzyć zestawy wieloplikowe, musisz podać kompilatorów wiersza polecenia lub programu Visual Studio z programem Visual C++.

### <a name="to-create-a-multifile-assembly"></a>Aby utworzyć zestaw wieloplikowy

01. Kompiluj wszystkie pliki zawierające przestrzenie nazw przywoływany przez inne moduły w zestawie do modułów kodu. Domyślnym rozszerzeniem dla modułów kodu jest .netmodule.

    Na przykład, załóżmy, że `Stringer` plik ma przestrzeń nazwy wywołaną `myStringer`, która zawiera klasę o nazwie `Stringer`. `Stringer` Klasa zawiera metodę o nazwie `StringerMethod` , zapisuje pojedynczy wiersz do konsoli.

    [!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]
    [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]
    [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]

    Użyj następującego polecenia, aby skompilować ten kod:

    [!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]
    [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]
    [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]

    Określanie *modułu* parametrem **t:** opcji kompilatora wskazuje, że pliku powinna być skompilowana jako moduł, a nie jako zespół. Kompilator generuje moduł o nazwie `Stringer.netmodule`, który może być dodany do zestawu.

02. Kompiluj wszystkie inne moduły, stosując niezbędne opcje kompilatora w celu wskazania innych modułów, do których istnieją odwołania w kodzie. Ten krok używa **/addmodule** — opcja kompilatora.

    W poniższym przykładzie moduł kodu o nazwie `Client` ma punkt wejścia `Main` metodę, która odwołuje się do metody w `Stringer.dll` modułu utworzonego w kroku 1.

    [!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]
    [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]
    [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]

    Użyj następującego polecenia, aby skompilować ten kod:

    [!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]
    [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]
    [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]

    Określ **/t:module** opcji, ponieważ ten moduł zostanie dodany do zestawu w przyszłym kroku. Określ **/addmodule** opcji, ponieważ kod w `Client` odwołuje się do przestrzeni nazwy utworzonej przez kod w `Stringer.netmodule`. Kompilator generuje moduł o nazwie `Client.netmodule` zawiera odwołanie do innego modułu `Stringer.netmodule`.

    >[!NOTE]
    >C# I Kompilatory języka Visual Basic obsługują bezpośrednio tworzenie zespołów wieloplikowych przy użyciu następujących dwóch różnych składni.
    >
    >- Dwie kompilacje tworzą zestaw dwóch plików:
    >
    >    [!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]
    >    [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]
    >    [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]
    >
    >- Jeden Kompilacja tworzy zestaw dwóch plików:
    >
    >    [!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]
    >    [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]
    >    [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]

03. Użyj [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) do tworzenia pliku wyjściowego, który zawiera manifest zestawu. Ten plik zawiera informacje dotyczące wszystkich modułów lub zasobów, które są częścią zestawu.

    W wierszu polecenia wpisz następujące polecenie:

    **Al** \< *Nazwa modułu*> \<*Nazwa modułu*>... **/ main:**\<*nazwę metody*> **/out:**\<*nazwy pliku*>   **/target :**\<*typ pliku zestawu*>

    W tym poleceniu *Nazwa modułu* argumenty określają nazwę każdego modułu, aby uwzględnić w zestawie. **/Main:** opcja określa nazwę metody punktu wejścia w zestawie. **/Out:** opcja określa nazwę pliku wyjściowego, który zawiera metadane zestawu. **/Target:** opcja określa, że zestaw jest plik wykonywalny (.exe) aplikacji konsoli, plikiem wykonywalnym (.exe) Windows lub plikiem biblioteki (.lib).

    W poniższym przykładzie Al.exe tworzy zestaw, który jest wykonywalną aplikacją konsoli o nazwie `myAssembly.exe`. Aplikacja składa się z dwóch modułów o nazwie `Client.netmodule` i `Stringer.netmodule`, a pliku wykonywalnego o nazwie `myAssembly.exe,` zawierającą tylko metadane zestawu. Punkt wejścia zestawu jest `Main` metody w klasie `MainClientApp`, który znajduje się w `Client.dll`.

    ```
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    Możesz użyć [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) Aby sprawdzić zawartość zestawu lub określić, czy plik jest zestawem lub modułem.

## <a name="see-also"></a>Zobacz także
- [Tworzenie zestawów](../../../docs/framework/app-domains/create-assemblies.md)
- [Instrukcje: Wyświetlanie zawartości zestawu](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Zestawy wieloplikowe](../../../docs/framework/app-domains/multifile-assemblies.md)
