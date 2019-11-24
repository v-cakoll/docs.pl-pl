---
title: Winmdexp.exe (narzędzie eksportowania metadanych środowiska wykonawczego systemu Windows)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Runtime Metadata Export Tool
- Winmdexp.exe
ms.assetid: d2ce0683-343d-403e-bb8d-209186f7a19d
ms.openlocfilehash: 52820b78f6ed7b02e80df66f90a01143b31d9b29
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447278"
---
# <a name="winmdexpexe-windows-runtime-metadata-export-tool"></a>Winmdexp.exe (narzędzie eksportowania metadanych środowiska wykonawczego systemu Windows)
The Windows Runtime Metadata Export Tool (Winmdexp.exe) transforms a .NET Framework module into a file that contains Windows Runtime metadata. Although .NET Framework assemblies and Windows Runtime metadata files use the same physical format, there are differences in the content of the metadata tables, which means that .NET Framework assemblies are not automatically usable as Windows Runtime Components. The process of turning a .NET Framework module into a Windows Runtime component is referred to as *exporting*. In the .NET Framework 4.5 and .NET Framework 4.5.1, the resulting Windows metadata (.winmd) file contains both metadata and implementation.  
  
 When you use the **Windows Runtime Component** template, which is located under **Windows Store** for C# and Visual Basic in Visual Studio 2013 or Visual Studio 2012, the compiler target is a .winmdobj file, and a subsequent build step calls Winmdexp.exe to export the .winmdobj file to a .winmd file. This is the recommended way to build a Windows Runtime component. Programu Winmdexp.exe należy używać bezpośrednio, gdy potrzebna jest większa kontrola nad procesem kompilacji niż dostępna w Visual Studio.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). For more information, see [Command Prompts](developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console  
winmdexp [options] winmdmodule  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument lub opcja|Opis|  
|------------------------|-----------------|  
|`winmdmodule`|Określa moduł (winmdobj) do wyeksportowania. Dozwolony jest tylko jeden moduł. To create this module, use the `/target` compiler option with the `winmdobj` target. See [-target:winmdobj (C# Compiler Options)](../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md) or [-target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`/docfile:``docfile`<br /><br /> `/d:``docfile`|Określa wyjściowy plik dokumentacji XML, który zostanie wygenerowany przez Winmdexp.exe. In the .NET Framework 4.5, the output file is essentially the same as the input XML documentation file.|  
|`/moduledoc:``docfile`<br /><br /> `/md:``docfile`|Specifies the name of the XML documentation file that the compiler produced with `winmdmodule`.|  
|`/modulepdb:``symbolfile`<br /><br /> `/mp:``symbolfile`|Specifies the name of the program database (PDB) file that contains symbols for `winmdmodule`.|  
|`/nowarn:``warning`|Wyłącza ostrzeżenie o podanym numerze. For *warning*, supply only the numeric portion of the error code, without leading zeros.|  
|`/out:``file`<br /><br /> `/o:``file`|Określa nazwę wyjściowego pliku metadanych systemu Windows (winmd).|  
|`/pdb:``symbolfile`<br /><br /> `/p:``symbolfile`|Określa nazwę wyjściowego pliku bazy danych programu (PDB), który będzie zawierał symbole dla eksportowanego pliku metadanych systemu Windows (winmd).|  
|`/reference:``winmd`<br /><br /> `/r:``winmd`|Określa plik metadanych (winmd lub zestaw) jako plik referencyjny podczas eksportowania. If you use the reference assemblies in "\Program Files (x86)\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5" ("\Program Files\\..." on 32-bit computers), include references to both System.Runtime.dll and mscorlib.dll.|  
|`/utf8output`|Określa, że komunikaty wyjściowe powinny mieć kodowanie UTF-8.|  
|`/warnaserror+`|Określa, że wszystkie ostrzeżenia powinny być traktowane jako błędy.|  
|**@** `responsefile`|Specifies a response (.rsp) file that contains options (and optionally `winmdmodule`). Each line in `responsefile` should contain a single argument or option.|  
  
## <a name="remarks"></a>Uwagi  
 Winmdexp.exe nie jest przeznaczony do konwertowania dowolnego zestawu .NET Framework do pliku winmd. It requires a module that is compiled with the `/target:winmdobj` option, and additional restrictions apply. The most important of these restrictions is that all types that are exposed in the API surface of the assembly must be Windows Runtime types. For more information, see the "Declaring types in Windows Runtime Components" section of the article [Creating Windows Runtime Components in C# and Visual Basic](https://docs.microsoft.com/previous-versions/br230301(v=vs.110)).
  
 When you write a Windows 8.x Store app or a Windows Runtime component with C# or Visual Basic, the .NET Framework provides support to make programming with the Windows Runtime more natural. This is discussed in the article [.NET Framework Support for Windows Store Apps and Windows Runtime](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md). In the process, some commonly used Windows Runtime types are mapped to .NET Framework types. Winmdexp.exe reverses this process and produces an API surface that uses the corresponding Windows Runtime types. For example, types that are constructed from the <xref:System.Collections.Generic.IList%601> interface map to types that are constructed from the Windows Runtime <xref:Windows.Foundation.Collections.IVector%601> interface.  
  
## <a name="see-also"></a>Zobacz także

- [Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [Creating Windows Runtime Components in C# and Visual Basic](https://docs.microsoft.com/previous-versions/br230301(v=vs.110))
- [Winmdexp.exe — komunikaty o błędach](winmdexp-exe-error-messages.md)
- [Build, Deployment, and Configuration Tools (.NET Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd233108(v=vs.100))
