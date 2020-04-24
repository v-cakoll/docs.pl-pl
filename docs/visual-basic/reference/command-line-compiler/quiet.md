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
ms.openlocfilehash: 6e773c60469e8426956c92a5aa377741ba5af4d3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005276"
---
# <a name="-quiet"></a>-quiet

Zapobiega wyświetlaniu przez kompilator kodu dla błędów i ostrzeżeń związanych z składnią.

## <a name="syntax"></a>Składnia

```console
-quiet
```

## <a name="remarks"></a>Uwagi

Domyślnie program `-quiet` nie działa. Gdy kompilator zgłosi błąd lub ostrzeżenie związane z składnią, wyprowadza również wiersz z kodu źródłowego. W przypadku aplikacji, które analizują dane wyjściowe kompilatora, może być wygodniejszy, aby kompilator wyprowadził tylko tekst diagnostyki.

W poniższym przykładzie `Module1` generuje błąd, który zawiera kod źródłowy, gdy jest kompilowany bez `-quiet`.

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

Skompilowany przy `-quiet`użyciu, kompilator wyprowadza tylko następujące elementy:

```console
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> `-quiet` Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio; jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.

## <a name="example"></a>Przykład

Poniższy kod kompiluje `T2.vb` i nie wyświetla kodu dla diagnostyki kompilatora powiązanego z składnią:

```console
vbc -quiet t2.vb
```

## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
