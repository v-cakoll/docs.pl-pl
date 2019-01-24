---
title: Winmdexp.exe (narzędzie eksportowania metadanych środowiska wykonawczego systemu Windows)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Runtime Metadata Export Tool
- Winmdexp.exe
ms.assetid: d2ce0683-343d-403e-bb8d-209186f7a19d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41bf58e4b7e9e284606e244cf3cfdf298f7a7ae8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667261"
---
# <a name="winmdexpexe-windows-runtime-metadata-export-tool"></a>Winmdexp.exe (narzędzie eksportowania metadanych środowiska wykonawczego systemu Windows)
[!INCLUDE[wrt](../../../includes/wrt-md.md)] Narzędzie do eksportu metadanych (Winmdexp.exe) przekształca modułu .NET Framework w pliku, który zawiera [!INCLUDE[wrt](../../../includes/wrt-md.md)] metadanych. Mimo że zestawów .NET Framework i [!INCLUDE[wrt](../../../includes/wrt-md.md)] pliki metadanych używają ten sam fizyczny format, istnieją różnice w zawartości tabel metadanych, co oznacza, że zestawów .NET Framework nie są automatycznie używać jako [!INCLUDE[wrt](../../../includes/wrt-md.md)] składników . Proces przekształcania modułu .NET Framework do [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnik nazywa się *eksportowanie*. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], wynikowy plik metadanych (.winmd) Windows zawiera zarówno metadane, jak i implementację.  
  
 Kiedy używasz  **[!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika** szablonu, który znajduje się w folderze **Windows Store** języka C# i Visual Basic w programie Visual Studio 2013 lub Visual Studio 2012, kompilator jest plik .winmdobj i krok kompilacji kolejne wywołanie Winmdexp.exe w celu wyeksportowania pliku winmdobj do pliku winmd. Jest to zalecany sposób tworzenia [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika. Programu Winmdexp.exe należy używać bezpośrednio, gdy potrzebna jest większa kontrola nad procesem kompilacji niż dostępna w Visual Studio.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersz polecenia programisty dla programu Visual Studio (lub wiersza polecenia programu Visual Studio Windows 7). Aby uzyskać więcej informacji, zobacz [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
winmdexp [options] winmdmodule  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument lub opcja|Opis|  
|------------------------|-----------------|  
|`winmdmodule`|Określa moduł (winmdobj) do wyeksportowania. Dozwolony jest tylko jeden moduł. Aby utworzyć ten moduł, użyj `/target` — opcja kompilatora przy użyciu `winmdobj` docelowej. Zobacz [/target: winmdobj (opcje kompilatora C#)](~/docs/csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md) lub [/TARGET (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/target.md).|  
|`/docfile:``docfile`<br /><br /> `/d:``docfile`|Określa wyjściowy plik dokumentacji XML, który zostanie wygenerowany przez Winmdexp.exe. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], plik wyjściowy jest zasadniczo taki sam jak wejściowy plik XML w dokumentacji.|  
|`/moduledoc:``docfile`<br /><br /> `/md:``docfile`|Określa nazwę pliku dokumentacji XML, wytworzonego przez kompilator za pomocą `winmdmodule`.|  
|`/modulepdb:``symbolfile`<br /><br /> `/mp:``symbolfile`|Określa nazwę pliku bazy danych (PDB) programu, który zawiera symbole dla `winmdmodule`.|  
|`/nowarn:``warning`|Wyłącza ostrzeżenie o podanym numerze. Aby uzyskać *ostrzeżenie*, podaj tylko liczbowej części kodu błędu, bez zer wiodących.|  
|`/out:``file`<br /><br /> `/o:``file`|Określa nazwę wyjściowego pliku metadanych systemu Windows (winmd).|  
|`/pdb:``symbolfile`<br /><br /> `/p:``symbolfile`|Określa nazwę wyjściowego pliku bazy danych programu (PDB), który będzie zawierał symbole dla eksportowanego pliku metadanych systemu Windows (winmd).|  
|`/reference:``winmd`<br /><br /> `/r:``winmd`|Określa plik metadanych (winmd lub zestaw) jako plik referencyjny podczas eksportowania. Jeśli używasz zestawów odwołań w "\Program pliki (x86) \Reference Assemblies\Microsoft\Framework\\. NETCore\v4.5 "(" \Program Files\\... "na komputerach z 32-bitowy), zawierają odwołania do System.Runtime.dll, jak i mscorlib.dll.|  
|`/utf8output`|Określa, że komunikaty wyjściowe powinny mieć kodowanie UTF-8.|  
|`/warnaserror+`|Określa, że wszystkie ostrzeżenia powinny być traktowane jako błędy.|  
|**@** `responsefile`|Określa plik odpowiedzi (rsp), który zawiera opcje (i opcjonalnie `winmdmodule`). Każdy wiersz w `responsefile` powinien zawierać pojedynczy argument lub opcję.|  
  
## <a name="remarks"></a>Uwagi  
 Winmdexp.exe nie jest przeznaczony do konwertowania dowolnego zestawu .NET Framework do pliku winmd. Wymaga modułu, który został skompilowany z `/target:winmdobj` opcji i dodatkowe ograniczenia są stosowane. Najważniejszym z tych ograniczeń jest, że wszystkie typy, które są widoczne w powierzchnię interfejsu API zestawu muszą być [!INCLUDE[wrt](../../../includes/wrt-md.md)] typów. Aby uzyskać więcej informacji, zobacz sekcję "Deklarowanie typów składników środowiska wykonawczego Windows" w artykule [Tworzenie składników środowiska wykonawczego Windows w języku C# i Visual Basic](https://go.microsoft.com/fwlink/p/?LinkID=238313) w Centrum deweloperów Windows.  
  
 Podczas wpisywania [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji lub [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika za pomocą języka C# lub Visual Basic, program .NET Framework oferuje wsparcie dla programowania dzięki [!INCLUDE[wrt](../../../includes/wrt-md.md)] stosować bardziej naturalne. Zostało to omówione w artykule [pomocy technicznej dla Windows Store aplikacji programu .NET Framework i środowiska wykonawczego Windows](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md). W procesie niektóre powszechnie używane [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy są mapowane na typy .NET Framework. Winmdexp.exe odwraca ten proces i wytwarza powierzchnię interfejsu API, która stosuje odpowiednie [!INCLUDE[wrt](../../../includes/wrt-md.md)] typów. Na przykład w przypadku typów, które są konstruowane na podstawie <xref:System.Collections.Generic.IList%601> mapę interfejsu na typy, które są konstruowane na podstawie [!INCLUDE[wrt](../../../includes/wrt-md.md)] [IVector\<T >](https://go.microsoft.com/fwlink/p/?LinkId=251132)interfejsu.  
  
## <a name="see-also"></a>Zobacz także
- [Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [Tworzenie składników środowiska wykonawczego Windows w języku C# i Visual Basic](https://go.microsoft.com/fwlink/p/?LinkID=238313)
- [Winmdexp.exe — komunikaty o błędach](../../../docs/framework/tools/winmdexp-exe-error-messages.md)
- [Tworzenia, wdrażania i narzędzia do konfiguracji (.NET Framework)](https://msdn.microsoft.com/library/b8c921be-6012-4181-b8d4-ab15813fc9a7)
