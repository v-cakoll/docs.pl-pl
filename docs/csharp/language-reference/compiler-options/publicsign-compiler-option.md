---
title: -publicsign (opcje kompilatora C#)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: ec25f9c1f2ef943db41bcfa20c8efd1d05866acd
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472853"
---
# <a name="-publicsign-c-compiler-options"></a>-publicsign (opcje kompilatora C#)

Ta opcja powoduje, że kompilator zastosowanie klucza publicznego, ale faktycznie nie podpisać zestawu. **- Publicsign** również ustawia bit w zestawie środowiska uruchomieniowego informuje, że plik został podpisany faktycznie.

## <a name="syntax"></a>Składnia

```console
-publicsign
```

## <a name="arguments"></a>Argumenty

Brak.

## <a name="remarks"></a>Uwagi

**- Publicsign** opcja wymaga użycia [- keyfile](keyfile-compiler-option.md) lub [- keycontainer](keycontainer-compiler-option.md). **Keyfile** lub **keycontainer** opcje określić klucz publiczny.

**- Publicsign** i **- delaysign** wykluczają się wzajemnie.

Czasami nazywany "fałszywych znaku" lub "OSS znaku", publiczne podpisywanie zawiera klucz publiczny w zestawie danych wyjściowych i ustawia flagę "podpisem", ale faktycznie nie Podpisz zestaw z kluczem prywatnym. Jest to przydatne dla projektów typu open source, której chcesz utworzyć zestawy, które są zgodne z wydaną zestawy "podpisany całkowicie", ale nie mają dostępu do klucza prywatnego, używany do podpisywania zestawy osób. Ponieważ prawie żadnych użytkowników faktycznie należy sprawdzić, czy zestaw jest niecałkowicie podpisany, publicznie skompilowane zestawy są użyteczny w niemal każdego scenariusz, gdzie będzie używane to całkowicie podpisane.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz **właściwości** strony dla projektu.
1. Modyfikowanie **opóźnienie tylko znak** właściwości.

## <a name="see-also"></a>Zobacz też
 [-Delaysign — opcja kompilatora C#](delaysign-compiler-option.md)  
 [-Keyfile — opcja kompilatora C#](keyfile-compiler-option.md)  
 [-Keycontainer — opcja kompilatora C#](keycontainer-compiler-option.md)  
 [Opcje kompilatora C#](index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
