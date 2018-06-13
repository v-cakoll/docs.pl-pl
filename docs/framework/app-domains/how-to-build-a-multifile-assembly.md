---
title: 'Porady: kompilacja zestawów wieloplikowych'
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
ms.openlocfilehash: 916db7ec9bee0c85db1f2fcf4db7a9f8a61f9be3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744086"
---
# <a name="how-to-build-a-multifile-assembly"></a>Porady: kompilacja zestawów wieloplikowych
W tym artykule opisano sposób tworzenia zestawów wieloplikowych i zawiera kod, który przedstawia każdego kroku w procedurze.  
  
> [!NOTE]
>  Aby utworzyć zestawy jednoplikowe można tylko programu Visual Studio IDE języka C# i Visual Basic. Jeśli chcesz utworzyć zestawy wieloplikowe muszą używać kompilatory w wierszu polecenia lub programu Visual Studio z programem Visual C++.  
  
### <a name="to-create-a-multifile-assembly"></a>Aby utworzyć zestawów wieloplikowych  
  
1.  Kompiluj wszystkie pliki, które zawierają odwołuje się innych modułów w zestawie do modułów kodu przestrzeni nazw. Domyślne rozszerzenie dla modułów kodu jest modułu .netmodule.  
  
     Na przykład, załóżmy, że `Stringer` plik ma przestrzeń nazw o nazwie `myStringer`, która obejmuje klasy o nazwie `Stringer`. `Stringer` Klasa zawiera metodę o nazwie `StringerMethod` który zapisuje pojedynczy wiersz do konsoli.  
  
     [!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]
     [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]
     [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]  
  
     Użyj następującego polecenia, aby skompilować ten kod:  
  
     [!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]
     [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]
     [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]  
  
     Określanie *modułu* parametr o **/t:** — opcja kompilatora wskazuje, że plik ma być kompilowana jako moduł, a nie jako do zestawu. Kompilator generuje modułu o nazwie `Stringer.netmodule`, które mogą być dodane do zestawu.  
  
2.  Kompiluj wszystkie inne moduły, przy użyciu opcji kompilatora niezbędne wskazująca modułów, które są używane w kodzie. Ten krok używa **/addmodule** — opcja kompilatora.  
  
     W poniższym przykładzie modułu kodu o nazwie `Client` ma punkt wejścia `Main` metodę, która odwołuje się do metody w `Stringer.dll` modułu utworzonego w kroku 1.  
  
     [!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]
     [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]
     [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]  
  
     Użyj następującego polecenia, aby skompilować ten kod:  
  
     [!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]
     [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]
     [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]  
  
     Określ **/t:module** opcja, ponieważ ten moduł zostaną dodane do zestawu w przyszłości kroku. Określ **/addmodule** opcja, ponieważ kod w `Client` odwołuje się do przestrzeni nazw tworzona przez kod w `Stringer.netmodule`. Kompilator generuje modułu o nazwie `Client.netmodule` zawiera odwołanie do innego modułu `Stringer.netmodule`.  
  
    > [!NOTE]
    >  C# i Visual Basic kompilatory obsługuje tworzenie bezpośrednio za pomocą następujących dwóch składnie zestawy wieloplikowe.  
    >   
    >  -   Dwie kompilacje utworzyć dwa pliku zestawu:  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]
      [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]
      [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]  
    > -   Kompilacja co tworzy zestaw dwóch plików:  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]
      [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]
      [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]  
  
3.  Użyj [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) można utworzyć pliku wyjściowego, który zawiera manifest zestawu. Ten plik zawiera informacje dotyczące wszystkich modułów lub zasobów, które są częścią zestawu.  
  
     W wierszu polecenia wpisz następujące polecenie:  
  
     **Al** \< *nazwy modułu*> \<*nazwy modułu*>... **/ main:**\<*nazwę metody*> **/out:**\<*nazwę pliku*>   **/target :**\<*typ pliku zestawu*>  
  
     W tym poleceniu *nazwy modułu* argumenty określają nazwę każdego modułu do uwzględnienia w zestawie. **/Main:** opcji określa nazwę metody, która jest punkt wejścia w zestawie. **/Out:** opcji określa nazwę pliku wyjściowego, który zawiera metadanych zestawu. **/Target:** opcja określa, że zestaw jest plik wykonywalny (.exe) aplikacji konsoli, plik wykonywalny (.win) systemu Windows lub pliku biblioteki (lib).  
  
     W poniższym przykładzie Al.exe tworzy zestawu, który jest plik wykonywalny aplikacji konsoli o nazwie `myAssembly.exe`. Aplikacja składa się z dwóch modułów o nazwie `Client.netmodule` i `Stringer.netmodule`, i wywołać plik wykonywalny `myAssembly.exe,` zawierającą tylko metadane zestawu. Punkt wejścia zestawu jest `Main` metody w klasie `MainClientApp`, który znajduje się w `Client.dll`.  
  
    ```  
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe   
    ```  
  
     Można użyć [dezasembler MSIL (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) Sprawdź zawartość zestawu lub określanie, czy plik jest zestawu lub modułu.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie zestawów](../../../docs/framework/app-domains/create-assemblies.md)  
 [Instrukcje: wyświetlanie zawartości zestawu](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Zestawy wieloplikowe](../../../docs/framework/app-domains/multifile-assemblies.md)
