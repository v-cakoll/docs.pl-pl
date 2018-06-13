---
title: Winmdexp.exe (narzędzie eksportowania metadanych środowiska wykonawczego systemu Windows)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Runtime Metadata Export Tool
- Winmdexp.exe
ms.assetid: d2ce0683-343d-403e-bb8d-209186f7a19d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7181f6f28d576c5ddbbbe57d27e1d41e412cef6c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408102"
---
# <a name="winmdexpexe-windows-runtime-metadata-export-tool"></a>Winmdexp.exe (narzędzie eksportowania metadanych środowiska wykonawczego systemu Windows)
[!INCLUDE[wrt](../../../includes/wrt-md.md)] Narzędzie eksportowania metadanych (Winmdexp.exe) przekształca moduł .NET Framework do pliku, który zawiera [!INCLUDE[wrt](../../../includes/wrt-md.md)] metadanych. Mimo że zestawy .NET Framework i [!INCLUDE[wrt](../../../includes/wrt-md.md)] pliki metadanych używać tego samego formatu fizycznych, istnieją różnice w zawartości tabel metadanych, co oznacza, że zestawy .NET Framework nie są automatycznie można używać jako [!INCLUDE[wrt](../../../includes/wrt-md.md)] składników . Proces przekształcania moduł .NET Framework do [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika jest określana jako *eksportowanie*. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], wynikowy plik metadanych (.winmd) systemu Windows zawiera metadanych i implementacji.  
  
 Jeśli używasz  **[!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika** szablonu, który znajduje się w **Sklepu Windows** języka C# i Visual Basic w [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] lub [!INCLUDE[vs_dev11_ext](../../../includes/vs-dev11-ext-md.md)], docelowy kompilatora jest plikiem .winmdobj i kroku kompilacji kolejne wywołania Winmdexp.exe Aby wyeksportować plik .winmdobj do pliku winmd. Jest to zalecany sposób tworzenia [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika. Programu Winmdexp.exe należy używać bezpośrednio, gdy potrzebna jest większa kontrola nad procesem kompilacji niż dostępna w Visual Studio.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
winmdexp [options] winmdmodule  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument lub opcja|Opis|  
|------------------------|-----------------|  
|`winmdmodule`|Określa moduł (winmdobj) do wyeksportowania. Dozwolony jest tylko jeden moduł. Aby utworzyć ten moduł, użyj `/target` — opcja kompilatora z `winmdobj` docelowej. Zobacz [/target: winmdobj (opcje kompilatora C#)](~/docs/csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md) lub [/TARGET (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/target.md).|  
|`/docfile:``docfile`<br /><br /> `/d:``docfile`|Określa wyjściowy plik dokumentacji XML, który zostanie wygenerowany przez Winmdexp.exe. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], plik wyjściowy jest zasadniczo taki sam jak wejściowego pliku dokumentacji XML.|  
|`/moduledoc:``docfile`<br /><br /> `/md:``docfile`|Określa nazwę pliku dokumentacji XML wytworzonego przez kompilator z `winmdmodule`.|  
|`/modulepdb:``symbolfile`<br /><br /> `/mp:``symbolfile`|Określa nazwę pliku bazy danych (PDB) program, który zawiera symbole `winmdmodule`.|  
|`/nowarn:``warning`|Wyłącza ostrzeżenie o podanym numerze. Aby uzyskać *ostrzeżenie*, podaj części liczbowej elementu kodu błędu, bez zerami.|  
|`/out:``file`<br /><br /> `/o:``file`|Określa nazwę wyjściowego pliku metadanych systemu Windows (winmd).|  
|`/pdb:``symbolfile`<br /><br /> `/p:``symbolfile`|Określa nazwę wyjściowego pliku bazy danych programu (PDB), który będzie zawierał symbole dla eksportowanego pliku metadanych systemu Windows (winmd).|  
|`/reference:``winmd`<br /><br /> `/r:``winmd`|Określa plik metadanych (winmd lub zestaw) jako plik referencyjny podczas eksportowania. Jeśli korzystasz z zestawów odwołań w "\Program pliki (x86) \Reference Assemblies\Microsoft\Framework\\. NETCore\v4.5 "(" \Program Files\\... "na komputerach z 32-bitowy), zawierają odwołania do biblioteki System.Runtime.dll i biblioteki mscorlib.dll.|  
|`/utf8output`|Określa, że komunikaty wyjściowe powinny mieć kodowanie UTF-8.|  
|`/warnaserror+`|Określa, że wszystkie ostrzeżenia powinny być traktowane jako błędy.|  
|**@** `responsefile`|Określa plik odpowiedzi (.rsp —), który zawiera opcje (i opcjonalnie `winmdmodule`). Każdy wiersz w `responsefile` powinien zawierać pojedynczy argument lub opcji.|  
  
## <a name="remarks"></a>Uwagi  
 Winmdexp.exe nie jest przeznaczony do konwertowania dowolnego zestawu .NET Framework do pliku winmd. Wymaga to moduł, który jest skompilowana przy użyciu `/target:winmdobj` opcji oraz dodatkowe ograniczenia są stosowane. Najważniejsze tych ograniczeń jest, że wszystkie typy, które są dostępne na powierzchni interfejsu API zestawu musi być [!INCLUDE[wrt](../../../includes/wrt-md.md)] typów. Aby uzyskać więcej informacji, zobacz sekcję "Deklarowanie typów składników środowiska wykonawczego systemu Windows" w artykule [tworzenia składników środowiska wykonawczego systemu Windows w języku C# i Visual Basic](http://go.microsoft.com/fwlink/p/?LinkID=238313) w Centrum deweloperów systemu Windows.  
  
 Podczas zapisu [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji lub [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika w języku C# lub Visual Basic, .NET Framework zapewnia obsługę programowania w języku upewnij [!INCLUDE[wrt](../../../includes/wrt-md.md)] bardziej naturalny. Jest to omówione w artykule [.NET Framework pomocy technicznej dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md). W rezultacie niektóre często używane [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy są mapowane do typów .NET Framework. Winmdexp.exe odwraca ten proces i tworzy powierzchni interfejsu API używającej odpowiadającego [!INCLUDE[wrt](../../../includes/wrt-md.md)] typów. Na przykład typy, które są tworzone na podstawie <xref:System.Collections.Generic.IList%601> mapy interfejsu do typów, które są tworzone na podstawie [!INCLUDE[wrt](../../../includes/wrt-md.md)] [IVector\<T >](http://go.microsoft.com/fwlink/p/?LinkId=251132)interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)  
 [Tworzenie składników środowiska wykonawczego systemu Windows w języku C# i Visual Basic](http://go.microsoft.com/fwlink/p/?LinkID=238313)  
 [Winmdexp.exe — komunikaty o błędach](../../../docs/framework/tools/winmdexp-exe-error-messages.md)  
 [Kompilacja, wdrażanie i narzędzia do konfiguracji (.NET Framework)](http://msdn.microsoft.com/library/b8c921be-6012-4181-b8d4-ab15813fc9a7)
