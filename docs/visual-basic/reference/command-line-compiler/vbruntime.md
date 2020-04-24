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
 Opcja `-vbruntime` kompilatora pozwala określić, że kompilator ma kompilować bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic. Jeśli kompilujesz bez odniesienia do biblioteki środowiska uruchomieniowego Visual Basic, błędy lub ostrzeżenia są rejestrowane dla kodu lub konstrukcje języka, które generują wywołanie do pomocnika Visual Basic środowiska uruchomieniowego. ( *Pomocnik środowiska uruchomieniowego Visual Basic* jest funkcją zdefiniowaną w pliku Microsoft. VisualBasic. dll, która jest wywoływana w czasie wykonywania, aby wykonać określoną semantykę języka).  
  
 Ta `-vbruntime+` opcja daje takie samo zachowanie, które występuje, `-vbruntime` Jeśli nie określono przełącznika. Możesz użyć opcji, `-vbruntime+` aby zastąpić poprzednie `-vbruntime` przełączniki.  
  
 Większość obiektów `My` typu jest niedostępna w przypadku korzystania z `-vbruntime-` opcji `-vbruntime:path` lub.  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a>Osadzanie podstawowych funkcji środowiska uruchomieniowego Visual Basic  
 `-vbruntime*` Opcja umożliwia skompilowanie bez odwołania do biblioteki środowiska uruchomieniowego. Zamiast tego, podstawowe funkcje z biblioteki środowiska uruchomieniowego Visual Basic są osadzane w zestawie użytkownika. Tej opcji można użyć, jeśli aplikacja działa na platformach, które nie zawierają środowiska uruchomieniowego Visual Basic.  
  
 Następujące elementy członkowskie środowiska uruchomieniowego są osadzone:  
  
- Klasa <xref:Microsoft.VisualBasic.CompilerServices.Conversions>  
  
- Metoda <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29>  
  
- Metoda <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29>  
  
- Metoda <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29>  
  
- <xref:Microsoft.VisualBasic.Constants.vbBack>stałego  
  
- <xref:Microsoft.VisualBasic.Constants.vbCr>stałego  
  
- <xref:Microsoft.VisualBasic.Constants.vbCrLf>stałego  
  
- <xref:Microsoft.VisualBasic.Constants.vbFormFeed>stałego  
  
- <xref:Microsoft.VisualBasic.Constants.vbLf>stałego  
  
- <xref:Microsoft.VisualBasic.Constants.vbNewLine>stałego  
  
- <xref:Microsoft.VisualBasic.Constants.vbNullChar>stałego  
  
- <xref:Microsoft.VisualBasic.Constants.vbNullString>stałego  
  
- <xref:Microsoft.VisualBasic.Constants.vbTab>stałego  
  
- <xref:Microsoft.VisualBasic.Constants.vbVerticalTab>stałego  
  
- Niektóre obiekty `My` typu  
  
 Jeśli kompilujesz przy użyciu `-vbruntime*` opcji, a kod odwołuje się do elementu członkowskiego z biblioteki środowiska uruchomieniowego Visual Basic, która nie jest osadzona w podstawowej funkcji, kompilator zwróci błąd wskazujący, że element członkowski nie jest dostępny.  
  
## <a name="referencing-a-specified-library"></a>Odwoływanie się do określonej biblioteki  
 Można użyć argumentu, `path` aby skompilować z odwołaniem do niestandardowej biblioteki środowiska uruchomieniowego zamiast domyślnej biblioteki środowiska uruchomieniowego Visual Basic.  
  
 Jeśli wartość `path` argumentu jest w pełni kwalifikowana ścieżka do biblioteki DLL, kompilator użyje tego pliku jako biblioteki środowiska uruchomieniowego. Jeśli wartość `path` argumentu nie jest w pełni kwalifikowaną ścieżką do biblioteki DLL, kompilator Visual Basic będzie najpierw wyszukać ZIDENTYFIKOWANĄ bibliotekę DLL w bieżącym folderze. Następnie wyszukuje ścieżkę określoną przy użyciu opcji kompilatora [-SdkPath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) . Jeśli opcja `-sdkpath` kompilatora nie jest używana, kompilator wyszuka ZIDENTYFIKOWANĄ bibliotekę DLL w folderze .NET Framework (`%systemroot%\Microsoft.NET\Framework\versionNumber`).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, `-vbruntime` jak używać opcji do kompilowania z odwołaniem do biblioteki niestandardowej.  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a>Zobacz też

- [Visual Basic Core — nowy tryb kompilacji w programie Visual Studio 2010 z dodatkiem SP1](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
