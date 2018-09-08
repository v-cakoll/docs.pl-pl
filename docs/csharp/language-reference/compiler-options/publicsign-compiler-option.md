---
title: -publicsign (opcje kompilatora C#)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: 01ce30b9ac5997f56f29dcbbfa43a27738fa5556
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44184986"
---
# <a name="-publicsign-c-compiler-options"></a>-publicsign (opcje kompilatora C#)

Ta opcja powoduje, że kompilator zastosować klucz publiczny, ale nie faktycznego podpisywania zestawu. **- Publicsign** również ustawia bit w zestawie, który informuje środowiska uruchomieniowego, w rzeczywistości podpisania pliku.

## <a name="syntax"></a>Składnia

```console
-publicsign
```

## <a name="arguments"></a>Argumenty

Brak.

## <a name="remarks"></a>Uwagi

**- Publicsign** opcja wymaga użycia [- keyfile](keyfile-compiler-option.md) lub [- keycontainer](keycontainer-compiler-option.md). **Keyfile** lub **keycontainer** opcji Określ klucz publiczny.

**- Publicsign** i **- delaysign** opcje wykluczają się wzajemnie.

Czasami nazywane "fałszywych znak" lub "OSS znak", publiczne podpisywanie zawiera klucz publiczny w zestawie danych wyjściowych i ustawia flagę "podpisem", ale faktycznie nie podpisać zestaw przy użyciu klucza prywatnego. Jest to przydatne w przypadku projektów "open source", gdzie użytkownicy chcą utworzyć zestawy, które są zgodne z wydana w zestawach "niecałkowicie podpisany", ale nie mają dostępu do prywatnego klucza używanego do podpisywania zestawów. Ponieważ niemal żadnych użytkowników jest potrzebna do sprawdzenia, jeśli zestaw jest niecałkowicie podpisany, publicznie skompilowanych zestawów są niemożliwe w prawie w każdym scenariuszu, w której będzie służyć całkowicie podpisanego jeden.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz **właściwości** strony dla projektu.
1. Modyfikowanie **opóźnienie logowania tylko** właściwości.

## <a name="see-also"></a>Zobacz też

- [-Delaysign — opcja kompilatora C#](delaysign-compiler-option.md)  
- [-Keyfile — opcja kompilatora C#](keyfile-compiler-option.md)  
- [Kompilator języka C# - keycontainer — opcja](keycontainer-compiler-option.md)  
- [Opcje kompilatora C#](index.md)  
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
