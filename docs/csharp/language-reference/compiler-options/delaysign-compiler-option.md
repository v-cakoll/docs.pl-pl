---
title: -delaysign (C# opcje kompilatora)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: ae309a8de6c4691f0009e5beb8ac2adc8772805b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69603029"
---
# <a name="-delaysign-c-compiler-options"></a>-delaysign (C# opcje kompilatora)

Ta opcja powoduje, że kompilator rezerwuje miejsce w pliku wyjściowym, aby można było później dodać podpis cyfrowy.

## <a name="syntax"></a>Składnia

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a>Argumenty

`+` &#124; `-`

Użyj **-delaysign —** Jeśli chcesz użyć w pełni podpisanego zestawu. Użyj **-delaysign +** , jeśli chcesz umieścić klucz publiczny w zestawie. Wartość domyślna to **-delaysign-** .

## <a name="remarks"></a>Uwagi

Opcja **-delaysign** nie ma żadnego efektu, chyba że jest używana z atrybutem [-KeyFile](./keyfile-compiler-option.md) lub [-Container](./keycontainer-compiler-option.md).

Opcje **-delaysign** i **-publicsign** wykluczają się wzajemnie.

Po zażądaniu w pełni podpisanego zestawu, kompilator skrótów pliku, który zawiera manifest (metadane zestawu) i podpisuje ten skrót z kluczem prywatnym. Ta operacja tworzy podpis cyfrowy, który jest przechowywany w pliku, który zawiera manifest. Gdy zestaw jest podpisany z opóźnieniem, kompilator nie oblicza i nie przechowuje podpisu, ale rezerwuje miejsce w pliku, aby podpis mógł zostać dodany później.

Na przykład przy użyciu polecenia **-delaysign +** umożliwia testerowi umieszczenie zestawu w globalnej pamięci podręcznej. Po przetestowaniu można w pełni podpisać zestaw, umieszczając klucz prywatny w zestawie przy użyciu narzędzia [konsolidatora zestawu](../../../framework/tools/al-exe-assembly-linker.md) .

Aby uzyskać więcej informacji, zobacz [Tworzenie i używanie zestawów o silnych nazwach](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) oraz [opóźnienie podpisywania zestawu](../../../framework/app-domains/delay-sign-assembly.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz stronę **Właściwości** dla projektu.
1. Zmodyfikuj właściwość **opóźnienia tylko do podpisywania** .

Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>tę opcję kompilatora, zobacz.

## <a name="see-also"></a>Zobacz także

- [C#-publicsign — opcja](publicsign-compiler-option.md)
- [Opcje kompilatora C#](index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
