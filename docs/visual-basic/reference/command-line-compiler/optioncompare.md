---
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: ed9adc7cddd9eb204937b9819e4eeff176821e95
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400564"
---
# <a name="-optioncompare"></a>-optioncompare

Określa sposób, w jaki są wykonywane porównania ciągów.

## <a name="syntax"></a>Składnia

```console
-optioncompare:{binary | text}
```

## <a name="remarks"></a>Uwagi

Możesz określić `-optioncompare` jedną z dwóch form: `-optioncompare:binary` , aby użyć porównań ciągów binarnych i `-optioncompare:text` użyć porównania ciągów tekstowych. Domyślnie kompilator używa programu `-optioncompare:binary` .

W systemie Microsoft Windows bieżąca strona kodowa Określa binarny porządek sortowania. Typowa binarna kolejność sortowania jest następująca:

`A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

Porównania ciągów tekstowych są oparte na kolejności sortowania tekstu bez uwzględniania wielkości liter, która zależy od ustawień regionalnych systemu. Typowy porządek sortowania tekstu jest następujący:

`(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`

### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a>Aby ustawić-optioncompare w środowisku IDE programu Visual Studio

1. Zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **kompilacja** .

3. Zmodyfikuj wartość w polu **PORÓWNAJ opcję** .

### <a name="to-set--optioncompare-programmatically"></a>Aby programowo ustawić — optioncompare

Zobacz [Option Compare instrukcji](../../language-reference/statements/option-compare-statement.md).

## <a name="example"></a>Przykład

Poniższy kod kompiluje `ProjFile.vb` i używa porównywania ciągów binarnych.

```console
vbc -optioncompare:binary projFile.vb
```

## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](index.md)
- [-optionexplicit](optionexplicit.md)
- [-optionstrict](optionstrict.md)
- [-optioninfer](optioninfer.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)
- [Option Compare — Instrukcja](../../language-reference/statements/option-compare-statement.md)
- [Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
