---
title: -vbruntime
ms.date: 03/13/2018
f1_keywords:
- vbruntime
- -vbruntime
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d28d0556a662099e4e5e74b22583fc3c8b4c313f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656116"
---
# <a name="-vbruntime"></a>-vbruntime
Określa, że kompilator powinien kompilować bez odwołanie w Visual Basic Runtime Library lub odwołanie do biblioteki środowiska uruchomieniowego określonych.  
  
## <a name="syntax"></a>Składnia  
  
```  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a>Argumenty  
 \-  
 Kompiluj bez odwołania do Visual Basic Runtime Library.  
  
 \+  
 Kompiluj z odwołaniem do domyślnego Visual Basic Runtime Library.  
  
 \*  
 Kompiluj bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic, a następnie osadź podstawowych funkcji z Visual Basic Runtime Library w zestawie.  
  
 `path`  
 Kompiluj z odwołaniem do określonej biblioteki (DLL).  
  
## <a name="remarks"></a>Uwagi  
 `-vbruntime` — Opcja kompilatora umożliwia określenie, czy kompilator powinien kompilować bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic. Jeśli kompilacja bez odwołania do Visual Basic Runtime Library błędy lub ostrzeżenia są rejestrowane na kod lub język konstrukcje generujących wywołanie pomocnika środowiska uruchomieniowego języka Visual Basic. (A *pomocnika środowisko uruchomieniowe Visual Basic* jest funkcją zdefiniowaną w pliku Microsoft.VisualBasic.dll, która jest wywoływana w czasie wykonywania, wykonanie określonego języka semantycznego.)  
  
 `-vbruntime+` Opcja zapewnia takie samo zachowanie, który występuje, jeśli nie `-vbruntime` został określony przełącznik. Można użyć `-vbruntime+` możliwość zastąpienia poprzedniego `-vbruntime` przełączników.  
  
 Większość obiektów z `My` typu są niedostępne, gdy używasz `-vbruntime-` lub `-vbruntime:path` opcje.  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a>Osadzanie funkcje podstawowe środowisko uruchomieniowe Visual Basic  
 `-vbruntime*` Opcja umożliwia kompilowanie bez odwołania do biblioteki środowiska uruchomieniowego. Zamiast tego podstawowych funkcji z Visual Basic Runtime Library jest osadzony w zestawie użytkownika. Tej opcji można użyć, gdy aplikacja działa na platformach, które nie zawierają środowisko uruchomieniowe Visual Basic.  
  
 Osadzone są następujące elementy członkowskie środowiska uruchomieniowego:  
  
-   <xref:Microsoft.VisualBasic.CompilerServices.Conversions> Klasy  
  
-   <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> — Metoda  
  
-   <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> — Metoda  
  
-   <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> — Metoda  
  
-   <xref:Microsoft.VisualBasic.Constants.vbBack> Stała  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCr> Stała  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCrLf> Stała  
  
-   <xref:Microsoft.VisualBasic.Constants.vbFormFeed> Stała  
  
-   <xref:Microsoft.VisualBasic.Constants.vbLf> Stała  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNewLine> Stała  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullChar> Stała  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullString> Stała  
  
-   <xref:Microsoft.VisualBasic.Constants.vbTab> Stała  
  
-   <xref:Microsoft.VisualBasic.Constants.vbVerticalTab> Stała  
  
-   Niektóre obiekty `My` typu  
  
 Jeśli kompilacja przy użyciu `-vbruntime*` opcji i kod odwołuje się do elementu członkowskiego z Visual Basic Runtime Library nie jest zagnieżdżony z podstawowych funkcji, kompilator zwraca błąd, który wskazuje, że element członkowski nie jest dostępna.  
  
## <a name="referencing-a-specified-library"></a>Odwołanie do określonej biblioteki  
 Można użyć `path` argument skompilować z odwołaniem do biblioteki środowiska uruchomieniowego niestandardowych zamiast domyślnej Visual Basic Runtime Library.  
  
 Jeśli wartość `path` argument jest w pełni kwalifikowana ścieżka do biblioteki DLL, kompilator użyje tego pliku jako biblioteka środowiska uruchomieniowego. Jeśli wartość `path` argument nie jest w pełni kwalifikowana ścieżka do biblioteki DLL, kompilator Visual Basic umożliwia wyszukiwanie określonych biblioteki DLL w bieżącym folderze najpierw. Następnie umożliwia wyszukiwanie w ścieżce określony za pomocą [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) — opcja kompilatora. Jeśli `-sdkpath` — opcja kompilatora nie jest używany, kompilator będzie szukał zidentyfikowanych biblioteki DLL w folderze .NET Framework (`%systemroot%\Microsoft.NET\Framework\versionNumber`).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `-vbruntime` opcję, aby skompilować z odwołaniem do niestandardowa biblioteka.  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe języka Visual Basic — nowy tryb kompilacji w programie Visual Studio 2010 z dodatkiem SP1](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx)  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
