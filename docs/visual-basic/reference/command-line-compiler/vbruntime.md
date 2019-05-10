---
title: -vbruntime —
ms.date: 03/13/2018
f1_keywords:
- vbruntime
- -vbruntime
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
ms.openlocfilehash: 56ea692d6e65d94c497fbc9406e03b40648c55a2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663500"
---
# <a name="-vbruntime"></a>-vbruntime —
Określa, czy kompilator powinien kompilować się bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic lub odwołanie do biblioteki środowiska uruchomieniowego określonych.  
  
## <a name="syntax"></a>Składnia  
  
```  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a>Argumenty  
 \-  
 Kompiluj bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic.  
  
 \+  
 Skompiluj z odwołaniem do domyślnej biblioteki środowiska uruchomieniowego Visual Basic.  
  
 \*  
 Skompilować bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic, a następnie osadź podstawowe funkcje z biblioteki środowiska uruchomieniowego Visual Basic w zestawie.  
  
 `path`  
 Skompiluj z odwołaniem do określonej biblioteki (DLL).  
  
## <a name="remarks"></a>Uwagi  
 `-vbruntime` — Opcja kompilatora umożliwia określenie, czy kompilator powinien kompilować się bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic. W przypadku kompilacji bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic, błędy lub ostrzeżenia są rejestrowane w konstrukcji kodu lub języka, które generuje wywołanie pomocnika środowiska uruchomieniowego języka Visual Basic. (A *pomocnika środowiska uruchomieniowego Visual Basic* jest funkcją zdefiniowaną w pliku Microsoft.VisualBasic.dll, która jest wywoływana w czasie wykonywania do wykonania określonego języka semantycznego.)  
  
 `-vbruntime+` Opcja zapewnia takie samo zachowanie, który występuje, jeśli nie `-vbruntime` określono przełącznik. Możesz użyć `-vbruntime+` możliwości zastąpienia poprzedniego `-vbruntime` przełączników.  
  
 Większość obiektów `My` typu są niedostępne, gdy używasz `-vbruntime-` lub `-vbruntime:path` opcje.  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a>Osadzanie środowiska uruchomieniowego Visual Basic podstawowe funkcje  
 `-vbruntime*` Opcja umożliwia kompilowanie bez odwołania do biblioteki środowiska uruchomieniowego. Zamiast tego podstawowe funkcje z biblioteki środowiska uruchomieniowego Visual Basic jest osadzony w zestawie użytkownika. Można użyć tej opcji, jeśli aplikacja działa na platformach, które nie zawierają środowisko uruchomieniowe języka Visual Basic.  
  
 Następujące składniki środowiska uruchomieniowego są osadzone:  
  
- <xref:Microsoft.VisualBasic.CompilerServices.Conversions> Klasa  
  
- <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> — Metoda  
  
- <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> — Metoda  
  
- <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> — Metoda  
  
- <xref:Microsoft.VisualBasic.Constants.vbBack> Stałe  
  
- <xref:Microsoft.VisualBasic.Constants.vbCr> Stałe  
  
- <xref:Microsoft.VisualBasic.Constants.vbCrLf> Stałe  
  
- <xref:Microsoft.VisualBasic.Constants.vbFormFeed> Stałe  
  
- <xref:Microsoft.VisualBasic.Constants.vbLf> Stałe  
  
- <xref:Microsoft.VisualBasic.Constants.vbNewLine> Stałe  
  
- <xref:Microsoft.VisualBasic.Constants.vbNullChar> Stałe  
  
- <xref:Microsoft.VisualBasic.Constants.vbNullString> Stałe  
  
- <xref:Microsoft.VisualBasic.Constants.vbTab> Stałe  
  
- <xref:Microsoft.VisualBasic.Constants.vbVerticalTab> Stałe  
  
- Niektóre obiekty `My` typu  
  
 Jeśli kompilujesz przy użyciu `-vbruntime*` opcji, a kod odwołuje się do elementu członkowskiego z biblioteki środowiska uruchomieniowego Visual Basic, który nie jest osadzony z podstawowych funkcji, kompilator zwraca komunikat o błędzie wskazujący, że element członkowski nie jest dostępna.  
  
## <a name="referencing-a-specified-library"></a>Odwoływanie się do określonej biblioteki  
 Możesz użyć `path` argument do kompilowania za pomocą odwołania do biblioteki niestandardowego środowiska uruchomieniowego zamiast domyślnego języka Visual Basic Runtime Library.  
  
 Jeśli wartość `path` argument jest w pełni kwalifikowaną ścieżkę do biblioteki DLL, kompilator użyje tego pliku jako biblioteka środowiska uruchomieniowego. Jeśli wartość `path` argument nie jest w pełni kwalifikowana ścieżka do biblioteki DLL, kompilator Visual Basic umożliwia wyszukiwanie określonych bibliotek DLL w bieżącym folderze najpierw. Następnie zostanie wyszukany w ścieżce zostali zdefiniowani za pomocą [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) — opcja kompilatora. Jeśli `-sdkpath` — opcja kompilatora nie jest używany, kompilator będzie wyszukiwał określonych bibliotek DLL w folderze .NET Framework (`%systemroot%\Microsoft.NET\Framework\versionNumber`).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać `-vbruntime` opcji, aby skompilować z odwołaniem do niestandardową biblioteką.  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe języka Visual Basic — nowy tryb kompilacji w Visual Studio 2010 z dodatkiem SP1](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
