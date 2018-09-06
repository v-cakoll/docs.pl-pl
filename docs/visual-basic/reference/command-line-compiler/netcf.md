---
title: -netcf
ms.date: 03/13/2018
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
ms.openlocfilehash: 36b2cba14f15cebdcc7f371f53f46b657ab12758
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43854405"
---
# <a name="-netcf"></a>-netcf
Ustawia kompilatora z docelowym [!INCLUDE[Compact](~/includes/compact-md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
-netcf  
```  
  
## <a name="remarks"></a>Uwagi  
 `-netcf` Opcji powoduje, że kompilator języka Visual Basic do obiektu docelowego [!INCLUDE[Compact](~/includes/compact-md.md)] zamiast pełnego [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Funkcje języka, które są dostępne tylko w pełni [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] jest wyłączona.  
  
 `-netcf` Opcja jest przeznaczona do użycia z [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md). Funkcje języka, wyłączona przez `-netcf` są te same funkcje języka, nie znajduje się w nim docelowych i związanych z `-sdkpath`.  
  
> [!NOTE]
>  `-netcf` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia. `-netcf` Ustawiono opcję po załadowaniu projektu urządzenia języka Visual Basic.  
  
 `-netcf` Opcji zmienia się następujące funkcje języka:  
  
-   [Zakończenia \<— słowo kluczowe > instrukcji](../../../visual-basic/language-reference/statements/end-keyword-statement.md) słowo kluczowe, które kończy wykonania programu, jest wyłączona. Następujący program kompiluje i uruchamia bez `-netcf` , ale nie powiedzie się w czasie kompilacji za pomocą `-netcf`.  
  
     [!code-vb[VbVbalrCompiler#34](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]  
  
-   Późne powiązania wszystkich formularzach jest wyłączona. Błędy czasu kompilacji są generowane, gdy zostaną napotkane rozpoznawanym scenariuszy późnego wiązania. Następujący program kompiluje i uruchamia bez `-netcf` , ale nie powiedzie się w czasie kompilacji za pomocą `-netcf`.  
  
     [!code-vb[VbVbalrCompiler#35](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]  
  
-   [Automatycznie](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), i [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) Modyfikatory są wyłączone. Składnia [instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md) instrukcji został też zmodyfikowany do `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`. Poniższy kod ilustruje efekt `-netcf` podczas kompilacji.  
  
     [!code-vb[VbVbalrCompiler#36](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]  
  
-   Przy użyciu słów kluczowych Visual Basic 6.0, które zostały usunięte z Visual Basic generuje inny błąd podczas `-netcf` jest używany. Ma to wpływ na komunikaty o błędach dla następujących słów kluczowych:  
  
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
 Poniższy kod kompiluje `Myfile.vb` z [!INCLUDE[Compact](~/includes/compact-md.md)], przy użyciu wersji biblioteki mscorlib.dll i Microsoft.VisualBasic.dll znajduje się w katalogu instalacji domyślnej z [!INCLUDE[Compact](~/includes/compact-md.md)] na dysku C. Zazwyczaj używasz najnowszej wersji [!INCLUDE[Compact](~/includes/compact-md.md)].  
  
```console  
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
