---
title: -refout (Opcje kompilatora C#)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: f48316a1e6f657e3bd0190d269dfe0e875a833d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72771759"
---
# <a name="-refout-c-compiler-options"></a>-refout (Opcje kompilatora C#)

Opcja **-refout** określa ścieżkę pliku, w której powinien być wyjściowy zestaw odniesienia. Przekłada się `metadataPeStream` to na interfejs API emituj. Ta opcja odpowiada właściwości projektu [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) msbuild.

## <a name="syntax"></a>Składnia

```console
-refout:filepath
```

## <a name="arguments"></a>Argumenty

 `filepath`Ścieżka pliku dla zestawu odniesienia. Ogólnie powinien odpowiadać zestawu podstawowego. Zalecaną konwencją (używaną przez MSBuild) jest umieszczenie zestawu odniesienia w podfolderze "ref/" względem zestawu podstawowego.

## <a name="remarks"></a>Uwagi

Zestawy odwołań są specjalnym typem zestawu, który zawiera tylko minimalną ilość metadanych wymaganych do reprezentowania publicznej powierzchni interfejsu API biblioteki. Obejmują one deklaracje dla wszystkich elementów członkowskich, które są istotne podczas odwoływania się do zestawu w narzędziakompilacji, ale wykluczają wszystkie implementacje elementów członkowskich i deklaracje prywatnych elementów członkowskich, które nie mają zauważalnego wpływu na ich kontrakt interfejsu API. Aby uzyskać więcej informacji, zobacz [Zestawy odwołań](../../../standard/assembly/reference-assemblies.md) w przewodniku .NET.

Opcje `-refout` [`-refonly`](refonly-compiler-option.md) i wzajemnie się wykluczają.

## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
