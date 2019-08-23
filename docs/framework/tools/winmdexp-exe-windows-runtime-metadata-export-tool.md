---
title: Winmdexp.exe (narzędzie eksportowania metadanych środowiska wykonawczego systemu Windows)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Runtime Metadata Export Tool
- Winmdexp.exe
ms.assetid: d2ce0683-343d-403e-bb8d-209186f7a19d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e6f9f553af4899d502584cbde5341f7061f169d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937952"
---
# <a name="winmdexpexe-windows-runtime-metadata-export-tool"></a>Winmdexp.exe (narzędzie eksportowania metadanych środowiska wykonawczego systemu Windows)
Narzędzie do eksportu metadanych środowisko wykonawcze systemu Windows (Winmdexp. exe) przekształca moduł .NET Framework do pliku, który zawiera środowisko wykonawcze systemu Windows metadane. Chociaż zestawy .NET Framework i środowisko wykonawcze systemu Windows pliki metadanych używają tego samego formatu fizycznego, istnieją różnice w zawartości tabel metadanych, co oznacza, że zestawy .NET Framework nie są automatycznie używane jako składniki środowisko wykonawcze systemu Windows . Proces przekształcania modułu .NET Framework do składnika środowisko wykonawcze systemu Windows jest określany jako *Eksportowanie*. W .NET Framework 4,5 i .NET Framework 4.5.1 utworzony plik metadanych systemu Windows (WinMD) zawiera metadane i implementację.  
  
 W przypadku korzystania z szablonu **składnika Środowisko wykonawcze systemu Windows** , który znajduje się w obszarze **Sklep Windows** dla C# i Visual Basic w Visual Studio 2013 lub w programie Visual Studio 2012, obiekt docelowy kompilatora jest plikiem. winmdobj, a kolejny krok kompilacji wywołuje Winmdexp. exe eksportuje plik winmdobj do pliku winmd. Jest to zalecany sposób tworzenia składnika środowisko wykonawcze systemu Windows. Programu Winmdexp.exe należy używać bezpośrednio, gdy potrzebna jest większa kontrola nad procesem kompilacji niż dostępna w Visual Studio.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersza polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
winmdexp [options] winmdmodule  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument lub opcja|Opis|  
|------------------------|-----------------|  
|`winmdmodule`|Określa moduł (winmdobj) do wyeksportowania. Dozwolony jest tylko jeden moduł. Aby utworzyć ten moduł, użyj `/target` opcji kompilatora `winmdobj` z elementem docelowym. Zobacz [/target: winmdobj (C# opcje kompilatora)](../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md) lub [/Target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`/docfile:``docfile`<br /><br /> `/d:``docfile`|Określa wyjściowy plik dokumentacji XML, który zostanie wygenerowany przez Winmdexp.exe. W .NET Framework 4,5 plik wyjściowy jest zasadniczo taki sam jak plik wejściowy dokumentacji XML.|  
|`/moduledoc:``docfile`<br /><br /> `/md:``docfile`|Określa nazwę pliku dokumentacji XML, z `winmdmodule`którym kompilator został utworzony.|  
|`/modulepdb:``symbolfile`<br /><br /> `/mp:``symbolfile`|Określa nazwę pliku bazy danych programu (PDB), który zawiera symbole dla `winmdmodule`.|  
|`/nowarn:``warning`|Wyłącza ostrzeżenie o podanym numerze. Aby uzyskać *Ostrzeżenie*, podaj tylko część numeryczną kodu błędu bez zer wiodących.|  
|`/out:``file`<br /><br /> `/o:``file`|Określa nazwę wyjściowego pliku metadanych systemu Windows (winmd).|  
|`/pdb:``symbolfile`<br /><br /> `/p:``symbolfile`|Określa nazwę wyjściowego pliku bazy danych programu (PDB), który będzie zawierał symbole dla eksportowanego pliku metadanych systemu Windows (winmd).|  
|`/reference:``winmd`<br /><br /> `/r:``winmd`|Określa plik metadanych (winmd lub zestaw) jako plik referencyjny podczas eksportowania. Jeśli używasz zestawów referencyjnych w "\Program Files (x86) \Reference Assemblies\Microsoft\Framework\\. NETCore\v4.5 "(" \Program Files\\... " na komputerach 32-bitowych) Uwzględnij odwołania do plików system. Runtime. dll i mscorlib. dll.|  
|`/utf8output`|Określa, że komunikaty wyjściowe powinny mieć kodowanie UTF-8.|  
|`/warnaserror+`|Określa, że wszystkie ostrzeżenia powinny być traktowane jako błędy.|  
|**@** `responsefile`|Określa plik odpowiedzi (. RSP), który zawiera opcje (i opcjonalnie `winmdmodule`). Każdy wiersz w `responsefile` powinien zawierać pojedynczy argument lub opcję.|  
  
## <a name="remarks"></a>Uwagi  
 Winmdexp.exe nie jest przeznaczony do konwertowania dowolnego zestawu .NET Framework do pliku winmd. Wymaga modułu, który jest kompilowany z `/target:winmdobj` opcją, i obowiązują dodatkowe ograniczenia. Najważniejsze te ograniczenia polegają na tym, że wszystkie typy, które są widoczne w obszarze interfejsu API zestawu, muszą być typu środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz sekcję "deklarowanie typów w składnikach środowisko wykonawcze systemu Windows" [w artykule tworzenie środowisko wykonawcze systemu Windows składników C# w programie i Visual Basic](https://go.microsoft.com/fwlink/p/?LinkID=238313) w centrum deweloperów systemu Windows.  
  
 Gdy piszesz [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikację lub składnik środowisko wykonawcze systemu Windows za pomocą C# lub Visual Basic, .NET Framework zapewnia pomoc techniczną w celu zapewnienia programowania z środowisko wykonawcze systemu Windows bardziej naturalny. W tym artykule omówiono [.NET Framework pomocy technicznej dla aplikacji ze sklepu Windows i środowisko wykonawcze systemu Windows](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md). W procesie niektóre często używane typy środowisko wykonawcze systemu Windows są mapowane na typy .NET Framework. Winmdexp. exe odwraca ten proces i tworzy powierzchnię interfejsu API korzystającą z odpowiednich typów środowisko wykonawcze systemu Windows. Na przykład typy, które są zbudowane z <xref:System.Collections.Generic.IList%601> mapy interfejsu do typów, które są zbudowane z środowisko wykonawcze systemu Windows interfejs[>\<IVector T](https://go.microsoft.com/fwlink/p/?LinkId=251132).  
  
## <a name="see-also"></a>Zobacz także

- [Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [Tworzenie składników środowisko wykonawcze systemu Windows w C# i Visual Basic](https://go.microsoft.com/fwlink/p/?LinkID=238313)
- [Winmdexp.exe — komunikaty o błędach](../../../docs/framework/tools/winmdexp-exe-error-messages.md)
- [Kompilacja, wdrażanie i Narzędzia konfiguracji (.NET Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd233108(v=vs.100))
