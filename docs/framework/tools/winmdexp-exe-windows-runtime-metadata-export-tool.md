---
title: Winmdexp.exe (narzędzie eksportowania metadanych środowiska wykonawczego systemu Windows)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Runtime Metadata Export Tool
- Winmdexp.exe
ms.assetid: d2ce0683-343d-403e-bb8d-209186f7a19d
ms.openlocfilehash: 52820b78f6ed7b02e80df66f90a01143b31d9b29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74447278"
---
# <a name="winmdexpexe-windows-runtime-metadata-export-tool"></a>Winmdexp.exe (narzędzie eksportowania metadanych środowiska wykonawczego systemu Windows)
Narzędzie do eksportowania metadanych środowiska wykonawczego systemu Windows (Winmdexp.exe) przekształca moduł .NET Framework w plik zawierający metadane środowiska wykonawczego systemu Windows. Chociaż zestawy .NET Framework i pliki metadanych środowiska wykonawczego systemu Windows używają tego samego formatu fizycznego, istnieją różnice w zawartości tabel metadanych, co oznacza, że zestawy .NET Framework nie są automatycznie używane jako składniki środowiska wykonawczego systemu Windows . Proces przekształcania modułu .NET Framework w składnik środowiska wykonawczego systemu Windows jest określany jako *eksportowanie*. W programie .NET Framework 4.5 i .NET Framework 4.5.1 wynikowy plik metadanych systemu Windows (.winmd) zawiera zarówno metadane, jak i implementację.  
  
 Korzystając z **szablonu składnika środowiska wykonawczego systemu Windows,** który znajduje się w **sklepie Windows** dla języka C# i Visual Basic w programie Visual Studio 2013 lub Visual Studio 2012, obiekt docelowy kompilatora jest plikiem .winmdobj, a kolejny krok kompilacji wywołuje program Winmdexp.exe w celu wyeksportowania pliku .winmdobj do pliku .winmd. Jest to zalecany sposób tworzenia składnika środowiska wykonawczego systemu Windows. Programu Winmdexp.exe należy używać bezpośrednio, gdy potrzebna jest większa kontrola nad procesem kompilacji niż dostępna w Visual Studio.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console  
winmdexp [options] winmdmodule  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument lub opcja|Opis|  
|------------------------|-----------------|  
|`winmdmodule`|Określa moduł (winmdobj) do wyeksportowania. Dozwolony jest tylko jeden moduł. Aby utworzyć ten moduł, należy użyć opcji `/target` kompilatora z obiektem docelowym. `winmdobj` Zobacz [-target:winmdobj (Opcje kompilatora C#)](../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md) lub [-target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`/docfile:` `docfile`<br /><br /> `/d:` `docfile`|Określa wyjściowy plik dokumentacji XML, który zostanie wygenerowany przez Winmdexp.exe. W .NET Framework 4.5 plik wyjściowy jest zasadniczo taki sam jak wejściowy plik dokumentacji XML.|  
|`/moduledoc:` `docfile`<br /><br /> `/md:` `docfile`|Określa nazwę pliku dokumentacji XML, który kompilator wyprodukował za pomocą `winmdmodule`pliku .|  
|`/modulepdb:` `symbolfile`<br /><br /> `/mp:` `symbolfile`|Określa nazwę pliku bazy danych programu (PDB), który `winmdmodule`zawiera symbole .|  
|`/nowarn:` `warning`|Wyłącza ostrzeżenie o podanym numerze. W *przypadku ostrzeżenia*należy podać tylko numeryczną część kodu błędu, bez zer wiodących.|  
|`/out:` `file`<br /><br /> `/o:` `file`|Określa nazwę wyjściowego pliku metadanych systemu Windows (winmd).|  
|`/pdb:` `symbolfile`<br /><br /> `/p:` `symbolfile`|Określa nazwę wyjściowego pliku bazy danych programu (PDB), który będzie zawierał symbole dla eksportowanego pliku metadanych systemu Windows (winmd).|  
|`/reference:` `winmd`<br /><br /> `/r:` `winmd`|Określa plik metadanych (winmd lub zestaw) jako plik referencyjny podczas eksportowania. Jeśli używasz zestawów odwołań w "\Program Files (x86)\Reference Assemblies\Microsoft\Framework\\. NETCore\v4.5" ("\Pliki\\programów ..." na komputerach 32-bitowych) zawierają odwołania zarówno do pliku System.Runtime.dll, jak i mscorlib.dll.|  
|`/utf8output`|Określa, że komunikaty wyjściowe powinny mieć kodowanie UTF-8.|  
|`/warnaserror+`|Określa, że wszystkie ostrzeżenia powinny być traktowane jako błędy.|  
|**@** `responsefile`|Określa plik odpowiedzi (rsp), który zawiera opcje `winmdmodule`(i opcjonalnie ). Każdy wiersz `responsefile` powinien zawierać pojedynczy argument lub opcję.|  
  
## <a name="remarks"></a>Uwagi  
 Winmdexp.exe nie jest przeznaczony do konwertowania dowolnego zestawu .NET Framework do pliku winmd. Wymaga modułu, który jest `/target:winmdobj` kompilowany z opcją i obowiązują dodatkowe ograniczenia. Najważniejszym z tych ograniczeń jest to, że wszystkie typy, które są widoczne w powierzchni interfejsu API zestawu musi być typy środowiska wykonawczego systemu Windows. Aby uzyskać więcej informacji, zobacz sekcję "Deklarowanie typów w składnikach środowiska wykonawczego systemu Windows" artykułu [Tworzenie składników środowiska wykonawczego systemu Windows w językach C# i Visual Basic](https://docs.microsoft.com/previous-versions/br230301(v=vs.110)).
  
 Podczas pisania aplikacji ze Sklepu Windows 8.x lub składnika środowiska wykonawczego systemu Windows w języku C# lub Visual Basic program .NET Framework zapewnia obsługę programowania przy pomocy środowiska wykonawczego systemu Windows bardziej naturalnego. Zostało to omówione w artykule [.NET Framework Support for Windows Store Apps and Windows Runtime](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md). W procesie niektóre typy środowiska wykonawczego systemu Windows są mapowane na typy programu .NET Framework. Program Winmdexp.exe odwraca ten proces i tworzy powierzchnię interfejsu API, która używa odpowiednich typów środowiska wykonawczego systemu Windows. Na przykład typy, które <xref:System.Collections.Generic.IList%601> są skonstruowane z mapy interfejsu do <xref:Windows.Foundation.Collections.IVector%601> typów, które są zbudowane z interfejsu środowiska wykonawczego systemu Windows.  
  
## <a name="see-also"></a>Zobacz też

- [Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [Tworzenie składników środowiska wykonawczego systemu Windows w językach C# i Visual Basic](https://docs.microsoft.com/previous-versions/br230301(v=vs.110))
- [Winmdexp.exe — komunikaty o błędach](winmdexp-exe-error-messages.md)
- [Narzędzia kompilacji, wdrażania i konfiguracji (.NET Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd233108(v=vs.100))
