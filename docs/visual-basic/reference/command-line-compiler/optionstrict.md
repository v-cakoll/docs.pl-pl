---
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: 469e22aef9d746fc55e04ba884d17d60d8baa85a
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583074"
---
# <a name="-optionstrict"></a>-optionstrict

Wymusza ścisłą semantykę typu w celu ograniczenia niejawnych konwersji typów.

## <a name="syntax"></a>Składnia

```console
-optionstrict[+ | -]
-optionstrict[:custom]
```

## <a name="arguments"></a>Argumenty

`+` &#124; `-`  
Opcjonalny. Opcja `-optionstrict+` ogranicza niejawną konwersję typu. Wartość domyślna dla tej opcji to `-optionstrict-`. Opcja `-optionstrict+` jest taka sama jak `-optionstrict`. Można użyć obu typów jako nieograniczającej semantyki typu.

`custom`  
Wymagany. Ostrzegaj w przypadku nieprzestrzegania ścisłej semantyki języka.

## <a name="remarks"></a>Uwagi

Gdy `-optionstrict+`, tylko rozszerzone konwersje typów mogą być wykonywane niejawnie. Niejawne konwersje typów, takie jak przypisanie obiektu typu `Decimal` do obiektu typu Integer, są raportowane jako błędy.

Aby wygenerować ostrzeżenia dla niejawnych konwersji typów zawężających, użyj `-optionstrict:custom`. Użyj `-nowarn:numberlist` do ignorowania określonych ostrzeżeń i `-warnaserror:numberlist` do traktowania określonych ostrzeżeń jako błędów.

### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a>Aby ustawić-optionstrict w środowisku IDE programu Visual Studio

1. Zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **właściwości.**

2. Kliknij kartę **kompilacja** .

3. Zmodyfikuj wartość w polu **Option Strict** .

### <a name="to-set--optionstrict-programmatically"></a>Aby programowo ustawić — optionstrict

Zobacz [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md).

## <a name="example"></a>Przykład

Poniższy kod kompiluje `Test.vb` przy użyciu semantyki typu Strict.

```console
vbc -optionstrict+ test.vb
```

## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)
- [-warnaserror — (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
