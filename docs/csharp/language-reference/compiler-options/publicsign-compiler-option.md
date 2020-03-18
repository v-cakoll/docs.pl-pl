---
title: -publicsign (Opcje kompilatora C#)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: de7d9c98b0f279b52bc93711c5b986a2b2e57215
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61662533"
---
# <a name="-publicsign-c-compiler-options"></a>-publicsign (Opcje kompilatora C#)

Ta opcja powoduje, że kompilator zastosować klucz publiczny, ale faktycznie nie podpisuje zestawu. Opcja **-publicsign** ustawia również nieco w zestawie, który informuje, że plik jest faktycznie podpisany.

## <a name="syntax"></a>Składnia

```console
-publicsign
```

## <a name="arguments"></a>Argumenty

Brak.

## <a name="remarks"></a>Uwagi

Opcja **-publicsign** wymaga użycia [pliku -keyfile](keyfile-compiler-option.md) lub [-keycontainer.](keycontainer-compiler-option.md) Opcje **pliku kluczy** lub **kontenera kluczy** określają klucz publiczny.

Opcje **-publicsign** i **-delaysign** wzajemnie się wykluczają.

Czasami nazywany "fałszywy znak" lub "znak OSS", podpisywanie publiczne zawiera klucz publiczny w zestawie wyjściowym i ustawia flagę "signed", ale w rzeczywistości nie podpisuje zestawu kluczem prywatnym. Jest to przydatne w przypadku projektów typu open source, w których ludzie chcą tworzyć zestawy, które są zgodne z wydanymi zestawami "w pełni podpisanymi", ale nie mają dostępu do klucza prywatnego używanego do podpisywania zestawów. Ponieważ prawie nie konsumenci rzeczywiście trzeba sprawdzić, czy zestaw jest w pełni podpisany, te publicznie zbudowane zestawy są użyteczne w prawie każdym scenariuszu, w którym w pełni podpisany jeden będzie używany.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz stronę **Właściwości** projektu.
1. Zmodyfikuj **tylko znak opóźnienia.**

## <a name="see-also"></a>Zobacz też

- [C# Kompilator -delaysign opcja](delaysign-compiler-option.md)
- [C# Kompilator -keyfile opcja](keyfile-compiler-option.md)
- [Opcja Kompilator c# - keycontainer](keycontainer-compiler-option.md)
- [Opcje kompilatora Języka C#](index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
