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
ms.openlocfilehash: 3dd12971a082869c32b6292ed45e2014b8b0e2c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400542"
---
# <a name="-optionstrict"></a>-optionstrict

Wymusza ścisłą semantykę typu w celu ograniczenia niejawnych konwersji typów.

## <a name="syntax"></a>Składnia

```console
-optionstrict[+ | -]
-optionstrict[:custom]
```

## <a name="arguments"></a>Argumenty

`+`&#124;`-`  
Opcjonalny. `-optionstrict+`Opcja ogranicza niejawną konwersję typu. Wartość domyślna dla tej opcji to `-optionstrict-` . `-optionstrict+`Opcja jest taka sama jak `-optionstrict` . Można użyć obu typów jako nieograniczającej semantyki typu.

`custom`  
Wymagany. Ostrzegaj w przypadku nieprzestrzegania ścisłej semantyki języka.

## <a name="remarks"></a>Uwagi

Gdy to nastąpi `-optionstrict+` , można niejawnie wprowadzać tylko konwersje typów rozszerzających. Niejawne konwersje typów, takie jak przypisanie `Decimal` obiektu typu do obiektu typu Integer, są raportowane jako błędy.

Aby wygenerować ostrzeżenia dla niejawnych konwersji typów zawężania, użyj `-optionstrict:custom` . Służy `-nowarn:numberlist` do ignorowania określonych ostrzeżeń i `-warnaserror:numberlist` traktowania określonych ostrzeżeń jako błędów.

### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a>Aby ustawić-optionstrict w środowisku IDE programu Visual Studio

1. Zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **właściwości.**

2. Kliknij kartę **kompilacja** .

3. Zmodyfikuj wartość w polu **Option Strict** .

### <a name="to-set--optionstrict-programmatically"></a>Aby programowo ustawić — optionstrict

Zobacz [Option Strict, instrukcja](../../language-reference/statements/option-strict-statement.md).

## <a name="example"></a>Przykład

Poniższy kod kompiluje `Test.vb` przy użyciu semantyki typu Strict.

```console
vbc -optionstrict+ test.vb
```

## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](index.md)
- [-optioncompare](optioncompare.md)
- [-optionexplicit](optionexplicit.md)
- [-optioninfer](optioninfer.md)
- [-nowarn](nowarn.md)
- [-warnaserror — (Visual Basic)](warnaserror.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)
- [Option Strict — Instrukcja](../../language-reference/statements/option-strict-statement.md)
- [Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
