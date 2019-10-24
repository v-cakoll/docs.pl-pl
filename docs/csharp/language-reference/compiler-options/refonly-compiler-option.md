---
title: -refonly (C# opcje kompilatora)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: 856b65d3b2217dbe5d53ecda00723b47247d80a4
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72773853"
---
# <a name="-refonly-c-compiler-options"></a>-refonly (C# opcje kompilatora)

Opcja **-refonly** wskazuje, że zestaw odwołania powinien być wyjściem, a nie zestawem implementacji, jako podstawowy wynik. Parametr `-refonly` dyskretnie wyłącza umieszczanie plików PDB, ponieważ nie można wykonać zestawów referencyjnych. Ta opcja odnosi się do właściwości Project [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) programu MSBuild.

## <a name="syntax"></a>Składnia

```console
-refonly
```

## <a name="remarks"></a>Uwagi

Zestawy referencyjne są specjalnym typem zestawu, który zawiera tylko minimalną ilość metadanych wymaganą do reprezentowania publicznej powierzchni interfejsu API biblioteki. Obejmują one deklaracje dla wszystkich elementów członkowskich, które są istotne w przypadku odwoływania się do zestawu w narzędziach kompilacji, ale wyklucza wszystkie implementacje składowych i deklaracje prywatnych członków, którzy nie mają zauważalnego wpływu na ich kontrakt interfejsu API. Aby uzyskać więcej informacji, zobacz [zestawy referencyjne](../../../standard/assembly/reference-assemblies.md) w przewodniku .NET.

Opcje `-refonly` i [`-refout`](refout-compiler-option.md) wykluczają się wzajemnie.

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
