---
title: -refonly
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: b906178abf8d159083d95e41448596d512e857de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348575"
---
# <a name="-refonly-visual-basic"></a>-refonly (Visual Basic)

Opcja **-refonly** wskazuje, że podstawowe dane wyjściowe kompilacji powinny być zestawem referencyjnym, a nie zestawem implementacji. `-refonly` Parametr dyskretnie wyłącza umieszczanie plików PDB, ponieważ nie można wykonać zestawów referencyjnych.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Składnia

```console
-refonly
```

## <a name="remarks"></a>Uwagi

Visual Basic obsługuje `-refonly` przełącznik zaczynający się od wersji 15,3.

Zestawy referencyjne są specjalnym typem zestawu, który zawiera tylko minimalną ilość metadanych wymaganą do reprezentowania publicznej powierzchni interfejsu API biblioteki. Obejmują one deklaracje dla wszystkich elementów członkowskich, które są istotne w przypadku odwoływania się do zestawu w narzędziach kompilacji, ale wyklucza wszystkie implementacje składowych i deklaracje prywatnych członków, którzy nie mają zauważalnego wpływu na ich kontrakt interfejsu API. Aby uzyskać więcej informacji, zobacz [zestawy referencyjne](../../../standard/assembly/reference-assemblies.md) w przewodniku .NET.

Opcje `-refonly` i [`-refout`](refout-compiler-option.md) wzajemnie się wykluczają.

## <a name="see-also"></a>Zobacz też

- [-refout](refout-compiler-option.md)
- [Kompilator wiersza polecenia Visual Basic](index.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)
