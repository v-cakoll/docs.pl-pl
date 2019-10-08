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
ms.openlocfilehash: 3df7e622f97a5a1291736180e3964b1b3deaea2f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005445"
---
# <a name="-netcf"></a>-netcf

Ustawia kompilator jako docelowy .NET Compact Framework.

## <a name="syntax"></a>Składnia

```console
-netcf
```

## <a name="remarks"></a>Uwagi

Opcja `-netcf` powoduje, że kompilator Visual Basic ma kierować .NET Compact Framework a nie pełną .NET Framework. Funkcja języka, która jest obecna tylko w pełnej .NET Framework jest wyłączona.

Opcja `-netcf` została zaprojektowana tak, aby była używana z [-SdkPath](../../../visual-basic/reference/command-line-compiler/sdkpath.md). Funkcje języka wyłączone przez `-netcf` są tymi samymi funkcjami językowymi, które nie są obecne w plikach przeznaczonych dla `-sdkpath`.

> [!NOTE]
> Opcja `-netcf` nie jest dostępna w środowisku deweloperskim programu Visual Studio. jest on dostępny tylko w przypadku kompilowania z wiersza polecenia. Opcja `-netcf` jest ustawiana podczas ładowania projektu Visual Basic urządzenia.

Opcja `-netcf` zmienia następujące funkcje języka:

- Słowo kluczowe ["End \<keyword >](../../../visual-basic/language-reference/statements/end-keyword-statement.md) , które kończy wykonywanie programu, jest wyłączone. Następujący program kompiluje i uruchamia się bez `-netcf`, ale kończy się niepowodzeniem w czasie kompilacji z `-netcf`.

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- Późne wiązanie w obszarze wszystkie formularze jest wyłączone. Błędy czasu kompilacji są generowane po napotkaniu rozpoznanych scenariuszy późnego wiązania. Następujący program kompiluje i uruchamia się bez `-netcf`, ale kończy się niepowodzeniem w czasie kompilacji z `-netcf`.

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- Modyfikatory [Auto,](../../../visual-basic/language-reference/modifiers/auto.md) [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md)i [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) są wyłączone. Składnia instrukcji [Declare instrukcji](../../../visual-basic/language-reference/statements/declare-statement.md) jest również modyfikowana do `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`. Poniższy kod ilustruje wpływ `-netcf` na kompilację.

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- Używanie Visual Basic 6,0 słów kluczowych, które zostały usunięte z Visual Basic generuje inny błąd, gdy `-netcf` jest używany. Ma to wpływ na komunikaty o błędach dla następujących słów kluczowych:

  - `Open`

  - `Close`

  - `Put`

  - `Print`

  - `Write`

  - `Input`

  - `Lock`

  - `Unlock`

  - `Seek`

  - `Width`

  - `Name`

  - `FreeFile`

  - `EOF`

  - `Loc`

  - `LOF`

  - `Line`

## <a name="example"></a>Przykład

Poniższy kod kompiluje `Myfile.vb` z .NET Compact Framework przy użyciu wersji plików mscorlib. dll i Microsoft. VisualBasic. dll znajdujących się w domyślnym katalogu instalacyjnym .NET Compact Framework na dysku C. Zazwyczaj należy użyć najnowszej wersji .NET Compact Framework.

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
