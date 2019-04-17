---
title: -quiet
ms.date: 07/20/2015
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
ms.openlocfilehash: a22773e2e37eb60ab6f1e88305266f41764311e7
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612592"
---
# <a name="-quiet"></a>-quiet

Kompilator uniemożliwia wyświetlanie kodu dotyczące składni błędów i ostrzeżeń.

## <a name="syntax"></a>Składnia

```
-quiet
```

## <a name="remarks"></a>Uwagi

Domyślnie `-quiet` nie jest włączone. Gdy kompilator zgłosi błąd związany z składni lub ostrzeżenie, również generuje wiersza z kodu źródłowego. W przypadku aplikacji, które przeanalizować dane wyjściowe kompilatora może być bardziej wygodne do kompilatora w danych wyjściowych tylko tekst diagnostyki.

W poniższym przykładzie `Module1` generuje błąd, który zawiera kod źródłowy, gdy kompilowany bez `-quiet`.

```vb
Module Module1
    Sub Main()
        x()
    End Sub
End Module
```

Dane wyjściowe:

```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
```

Skompilowany przy użyciu `-quiet`, kompilator generuje jedynie następujące elementy:

```
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> `-quiet` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.

## <a name="example"></a>Przykład

Poniższy kod kompiluje `T2.vb` i nie zawiera kod dla diagnostyki kompilatora dotyczące składni:

```
vbc -quiet t2.vb
```

## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
