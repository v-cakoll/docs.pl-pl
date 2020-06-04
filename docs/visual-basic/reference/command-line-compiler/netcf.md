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
ms.openlocfilehash: 16fb6b3b63c848ea6c09cc18b0fcc488670f0926
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397478"
---
# <a name="-netcf"></a>-netcf

Ustawia kompilator jako docelowy .NET Compact Framework.

## <a name="syntax"></a>Składnia

```console
-netcf
```

## <a name="remarks"></a>Uwagi

`-netcf`Opcja powoduje, że kompilator Visual Basic ma kierować .NET Compact Framework, a nie pełną .NET Framework. Funkcja języka, która jest obecna tylko w pełnej .NET Framework jest wyłączona.

`-netcf`Opcja jest przeznaczona do użycia z [-SdkPath](sdkpath.md). Funkcje języka wyłączone przez `-netcf` są tymi samymi funkcjami językowymi, które nie są obecne w plikach objętych usługą `-sdkpath` .

> [!NOTE]
> `-netcf`Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia. `-netcf`Opcja jest ustawiana podczas ładowania projektu urządzenia Visual Basic.

`-netcf`Opcja zmienia następujące funkcje języka:

- Słowo [kluczowe \<keyword> instrukcji End](../../language-reference/statements/end-keyword-statement.md) , które kończy wykonywanie programu, jest wyłączone. Następujący program kompiluje i uruchamia się bez, `-netcf` ale kończy się niepowodzeniem w czasie kompilacji z `-netcf` .

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- Późne wiązanie w obszarze wszystkie formularze jest wyłączone. Błędy czasu kompilacji są generowane po napotkaniu rozpoznanych scenariuszy późnego wiązania. Następujący program kompiluje i uruchamia się bez, `-netcf` ale kończy się niepowodzeniem w czasie kompilacji z `-netcf` .

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- Modyfikatory [Auto,](../../language-reference/modifiers/auto.md) [ANSI](../../language-reference/modifiers/ansi.md)i [Unicode](../../language-reference/modifiers/unicode.md) są wyłączone. Składnia [instrukcji DECLARE](../../language-reference/statements/declare-statement.md) jest również modyfikowana `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]` . Poniższy kod przedstawia efekt `-netcf` kompilacji.

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

Poniższy kod kompiluje `Myfile.vb` się z .NET Compact Framework przy użyciu wersji plików mscorlib. dll i Microsoft. VisualBasic. dll znajdujących się w domyślnym katalogu instalacyjnym .NET Compact Framework na dysku C. Zazwyczaj należy użyć najnowszej wersji .NET Compact Framework.

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](index.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)
- [-sdkpath](sdkpath.md)
