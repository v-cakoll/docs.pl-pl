---
title: -delaysign (Opcje kompilatora C#)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: 9fdc02c22d9d8c8a709155e43a17ebf0d86dfd69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970447"
---
# <a name="-delaysign-c-compiler-options"></a>-delaysign (Opcje kompilatora C#)

Ta opcja powoduje, że kompilator rezerwuje miejsce w pliku wyjściowym, dzięki czemu podpis cyfrowy można dodać później.

## <a name="syntax"></a>Składnia

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a>Argumenty

`+`&#124;`-`

Użyj **-delaysign-** jeśli chcesz mieć w pełni podpisany zestaw. Użyj **-delaysign+,** jeśli chcesz umieścić tylko klucz publiczny w zestawie. Wartością domyślną jest **-delaysign-**.

## <a name="remarks"></a>Uwagi

Opcja **-delaysign** nie ma wpływu, chyba że jest używana z [-keyfile](./keyfile-compiler-option.md) lub [-keycontainer](./keycontainer-compiler-option.md).

Opcje **-delaysign** i **-publicsign** wzajemnie się wykluczają.

Gdy zażądasz w pełni podpisanego zestawu, kompilator poszumowa plik zawierający manifest (metadane zestawu) i znaki, które hash z kluczem prywatnym. Ta operacja tworzy podpis cyfrowy, który jest przechowywany w pliku, który zawiera manifest. Gdy zestaw jest podpisany opóźnienie, kompilator nie oblicza i przechowywania podpisu, ale rezerwuje miejsce w pliku, więc podpis można dodać później.

Na przykład za pomocą **-delaysign+** umożliwia tester umieścić zestaw w globalnej pamięci podręcznej. Po przetestowaniu można w pełni podpisać zestaw, umieszczając klucz prywatny w zestawie za pomocą narzędzia [Łącze zestawu.](../../../framework/tools/al-exe-assembly-linker.md)

Aby uzyskać więcej informacji, zobacz [Tworzenie i używanie zestawów o silnych nazwach](../../../standard/assembly/create-use-strong-named.md) i [Opóźnianie podpisywania zestawu](../../../standard/assembly/delay-sign.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz stronę **Właściwości** projektu.
1. Zmodyfikuj **tylko znak opóźnienia.**

Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>kompilatora, zobacz .

## <a name="see-also"></a>Zobacz też

- [C# -opcja publicsign](publicsign-compiler-option.md)
- [Opcje kompilatora Języka C#](index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
