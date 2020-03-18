---
title: -refonly (Opcje kompilatora C#)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: 856b65d3b2217dbe5d53ecda00723b47247d80a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72773853"
---
# <a name="-refonly-c-compiler-options"></a>-refonly (Opcje kompilatora C#)

Opcja **-refonly** wskazuje, że zestaw odniesienia powinien być wyjściowy zamiast zestawu implementacji, jako dane wyjściowe podstawowe. Parametr `-refonly` dyskretnie wyłącza wyjmowanie pdb, ponieważ nie można wykonać zestawów odwołań. Ta opcja odpowiada właściwości projektu [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) firmy MSBuild.

## <a name="syntax"></a>Składnia

```console
-refonly
```

## <a name="remarks"></a>Uwagi

Zestawy odwołań są specjalnym typem zestawu, który zawiera tylko minimalną ilość metadanych wymaganych do reprezentowania publicznej powierzchni interfejsu API biblioteki. Obejmują one deklaracje dla wszystkich elementów członkowskich, które są istotne podczas odwoływania się do zestawu w narzędziakompilacji, ale wykluczają wszystkie implementacje elementów członkowskich i deklaracje prywatnych elementów członkowskich, które nie mają zauważalnego wpływu na ich kontrakt interfejsu API. Aby uzyskać więcej informacji, zobacz [Zestawy odwołań](../../../standard/assembly/reference-assemblies.md) w przewodniku .NET.

Opcje `-refonly` [`-refout`](refout-compiler-option.md) i wzajemnie się wykluczają.

## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
