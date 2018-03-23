---
title: -netcf
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /netcf
- -netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82a0adc9e821df3a789cf19e798d4bad9e9a69e3
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-netcf"></a>-netcf
Ustawia kompilatora do docelowego [!INCLUDE[Compact](~/includes/compact-md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
-netcf  
```  
  
## <a name="remarks"></a>Uwagi  
 `-netcf` Opcji powoduje, że [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilatora do docelowego [!INCLUDE[Compact](~/includes/compact-md.md)] zamiast pełnego [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Funkcje języka, które są dostępne tylko w pełni [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] jest wyłączona.  
  
 `-netcf` Opcja jest przeznaczona do użycia z [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md). Funkcje języka wyłączone przez `-netcf` są takie same funkcje języka nie znajduje się w plikach z `-sdkpath`.  
  
> [!NOTE]
>  `-netcf` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia. `-netcf` Opcja jest ustawiona, gdy [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] urządzenia projektu jest ładowany.  
  
 `-netcf` Opcja zmiany następujące funkcje języka:  
  
-   [Zakończenia \<— słowo kluczowe > instrukcji](../../../visual-basic/language-reference/statements/end-keyword-statement.md) — słowo kluczowe, w którym kończy wykonywanie programu, jest wyłączona. Następujący program kompiluje i uruchamia bez `-netcf` , ale nie powiedzie się w czasie kompilacji z `-netcf`.  
  
     [!code-vb[VbVbalrCompiler#34](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]  
  
-   Późne wiązanie w wszystkich formularzy jest wyłączona. Błędy kompilacji są generowane, gdy wystąpią rozpoznanym scenariusze późne powiązania. Następujący program kompiluje i uruchamia bez `-netcf` , ale nie powiedzie się w czasie kompilacji z `-netcf`.  
  
     [!code-vb[VbVbalrCompiler#35](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]  
  
-   [Automatycznie](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), i [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) Modyfikatory są wyłączone. Składnia [instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md) instrukcji również są modyfikowane w celu `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`. Poniższy kod ilustruje efekt `-netcf` w kompilacji.  
  
     [!code-vb[VbVbalrCompiler#36](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]  
  
-   Za pomocą słów kluczowych Visual Basic 6.0, które zostały usunięte z [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] generuje inny błąd podczas `-netcf` jest używany. Ma to wpływ na komunikaty o błędach dla następujących słów kluczowych:  
  
    -   `Open`  
  
    -   `Close`  
  
    -   `Put`  
  
    -   `Print`  
  
    -   `Write`  
  
    -   `Input`  
  
    -   `Lock`  
  
    -   `Unlock`  
  
    -   `Seek`  
  
    -   `Width`  
  
    -   `Name`  
  
    -   `FreeFile`  
  
    -   `EOF`  
  
    -   `Loc`  
  
    -   `LOF`  
  
    -   `Line`  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `Myfile.vb` z [!INCLUDE[Compact](~/includes/compact-md.md)], przy użyciu wersji biblioteki mscorlib.dll i pliku Microsoft.VisualBasic.dll znajdujące się w katalogu instalacji domyślnej z [!INCLUDE[Compact](~/includes/compact-md.md)] na dysku C. Zazwyczaj należy użyć najnowszej wersji [!INCLUDE[Compact](~/includes/compact-md.md)].  
  
```console  
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
