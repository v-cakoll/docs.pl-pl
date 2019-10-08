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
ms.openlocfilehash: 8c7789c6af7b82ecb40ecd73d09f64aa1da3fd4b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005055"
---
# <a name="-vbruntime"></a>-vbruntime
Określa, że kompilator ma kompilować bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic lub z odwołaniem do określonej biblioteki środowiska uruchomieniowego.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a>Argumenty  
 \-  
 Kompiluj bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic.  
  
 \+  
 Kompiluj z odwołaniem do domyślnej biblioteki środowiska uruchomieniowego Visual Basic.  
  
 \*  
 Kompiluj bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic i Osadź podstawowe funkcje z biblioteki środowiska uruchomieniowego Visual Basic do zestawu.  
  
 `path`  
 Kompiluj z odwołaniem do określonej biblioteki (DLL).  
  
## <a name="remarks"></a>Uwagi  
 Opcja kompilatora `-vbruntime` pozwala określić, że kompilator ma kompilować bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic. Jeśli kompilujesz bez odniesienia do biblioteki środowiska uruchomieniowego Visual Basic, błędy lub ostrzeżenia są rejestrowane dla kodu lub konstrukcje języka, które generują wywołanie do pomocnika Visual Basic środowiska uruchomieniowego. ( *Pomocnik środowiska uruchomieniowego Visual Basic* jest funkcją zdefiniowaną w pliku Microsoft. VisualBasic. dll, która jest wywoływana w czasie wykonywania, aby wykonać określoną semantykę języka).  
  
 Opcja `-vbruntime+` daje takie samo zachowanie, które występuje, jeśli nie określono przełącznika `-vbruntime`. Możesz użyć opcji `-vbruntime+`, aby zastąpić poprzednie przełączniki `-vbruntime`.  
  
 Większość obiektów typu `My` jest niedostępna w przypadku korzystania z opcji `-vbruntime-` lub `-vbruntime:path`.  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a>Osadzanie podstawowych funkcji środowiska uruchomieniowego Visual Basic  
 Opcja `-vbruntime*` umożliwia skompilowanie bez odwołania do biblioteki środowiska uruchomieniowego. Zamiast tego, podstawowe funkcje z biblioteki środowiska uruchomieniowego Visual Basic są osadzane w zestawie użytkownika. Tej opcji można użyć, jeśli aplikacja działa na platformach, które nie zawierają środowiska uruchomieniowego Visual Basic.  
  
 Następujące elementy członkowskie środowiska uruchomieniowego są osadzone:  
  
- Klasa <xref:Microsoft.VisualBasic.CompilerServices.Conversions>  
  
- Metoda <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29>  
  
- Metoda <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29>  
  
- Metoda <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29>  
  
- stała <xref:Microsoft.VisualBasic.Constants.vbBack>  
  
- stała <xref:Microsoft.VisualBasic.Constants.vbCr>  
  
- stała <xref:Microsoft.VisualBasic.Constants.vbCrLf>  
  
- stała <xref:Microsoft.VisualBasic.Constants.vbFormFeed>  
  
- stała <xref:Microsoft.VisualBasic.Constants.vbLf>  
  
- stała <xref:Microsoft.VisualBasic.Constants.vbNewLine>  
  
- stała <xref:Microsoft.VisualBasic.Constants.vbNullChar>  
  
- stała <xref:Microsoft.VisualBasic.Constants.vbNullString>  
  
- stała <xref:Microsoft.VisualBasic.Constants.vbTab>  
  
- stała <xref:Microsoft.VisualBasic.Constants.vbVerticalTab>  
  
- Niektóre obiekty typu `My`  
  
 Jeśli kompilujesz przy użyciu opcji `-vbruntime*`, a kod odwołuje się do elementu członkowskiego z biblioteki środowiska uruchomieniowego Visual Basic, która nie jest osadzona w funkcji podstawowych, kompilator zwróci błąd wskazujący, że element członkowski nie jest dostępny.  
  
## <a name="referencing-a-specified-library"></a>Odwoływanie się do określonej biblioteki  
 Można użyć argumentu `path` do kompilowania z odwołaniem do niestandardowej biblioteki środowiska uruchomieniowego zamiast domyślnej biblioteki środowiska uruchomieniowego Visual Basic.  
  
 Jeśli wartość argumentu `path` jest w pełni kwalifikowana ścieżka do biblioteki DLL, kompilator użyje tego pliku jako biblioteki środowiska uruchomieniowego. Jeśli wartość argumentu `path` nie jest w pełni kwalifikowaną ścieżką do biblioteki DLL, kompilator Visual Basic przeszuka najpierw zidentyfikowaną bibliotekę DLL w bieżącym folderze. Następnie wyszukuje ścieżkę określoną przy użyciu opcji kompilatora [-SdkPath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) . Jeśli opcja kompilatora `-sdkpath` nie jest używana, kompilator wyszuka zidentyfikowaną bibliotekę DLL w folderze .NET Framework (`%systemroot%\Microsoft.NET\Framework\versionNumber`).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać opcji `-vbruntime` do kompilowania z odwołaniem do biblioteki niestandardowej.  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a>Zobacz także

- [Visual Basic Core — nowy tryb kompilacji w programie Visual Studio 2010 z dodatkiem SP1](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
