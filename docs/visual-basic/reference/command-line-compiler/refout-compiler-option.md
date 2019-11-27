---
title: -refout
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: 3649a24a52cc6a448ea7cf4d850915adf02147fb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348654"
---
# <a name="-refout-visual-basic"></a>-opcji refout (Visual Basic)

Opcja **-opcji refout** określa ścieżkę pliku, w którym zestaw odniesienia powinien być wyjściowy.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Składnia

```console
-refout:filepath
```

## <a name="arguments"></a>Argumenty

`filepath`  
Ścieżka i nazwa pliku zestawu odwołania. Zwykle powinien znajdować się w podfolderze podstawowego zestawu. Zalecaną konwencją (używaną przez program MSBuild) jest umieszczenie zestawu odwołania w podfolderze "ref/" względem podstawowego zestawu. Wszystkie foldery w `filepath` muszą istnieć; Kompilator nie tworzy ich.

## <a name="remarks"></a>Uwagi

Visual Basic obsługuje przełącznik `-refout`, zaczynając od wersji 15,3.

Zestawy referencyjne są specjalnym typem zestawu, który zawiera tylko minimalną ilość metadanych wymaganą do reprezentowania publicznej powierzchni interfejsu API biblioteki. Obejmują one deklaracje dla wszystkich elementów członkowskich, które są istotne w przypadku odwoływania się do zestawu w narzędziach kompilacji, ale wyklucza wszystkie implementacje składowych i deklaracje prywatnych członków, którzy nie mają zauważalnego wpływu na ich kontrakt interfejsu API. Aby uzyskać więcej informacji, zobacz [zestawy referencyjne](../../../standard/assembly/reference-assemblies.md) w przewodniku .NET.

Opcje `-refout` i [`-refonly`](refonly-compiler-option.md) wykluczają się wzajemnie.

## <a name="see-also"></a>Zobacz także

- [-refonly](refonly-compiler-option.md)
- [Kompilator wiersza polecenia Visual Basic](index.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)
