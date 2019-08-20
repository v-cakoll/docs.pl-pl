---
title: -opcji refout (C# opcje kompilatora)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: 97cbf540527d0449387b71bb1d97df95b6a4aba4
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602503"
---
# <a name="-refout-c-compiler-options"></a>-opcji refout (C# opcje kompilatora)

Opcja **-opcji refout** określa ścieżkę pliku, w którym zestaw odniesienia powinien być wyjściowy. Powoduje to przetłumaczenie na `metadataPeStream` w interfejsie API emisji. Ta opcja odnosi się do właściwości Project [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) programu MSBuild.

## <a name="syntax"></a>Składnia

```console
-refout:filepath
```

## <a name="arguments"></a>Argumenty

 `filepath`Ścieżka do zestawu referencyjnego. Zwykle powinna być zgodna z zestawem podstawowym. Zalecaną konwencją (używaną przez program MSBuild) jest umieszczenie zestawu odwołania w podfolderze "ref/" względem podstawowego zestawu.

## <a name="remarks"></a>Uwagi

Zestawy zawierające tylko metadane są zastępowane przez jedną `throw null` treść, ale obejmują wszystkie elementy członkowskie z wyjątkiem typów anonimowych. Powodem używania `throw null` treści (w przeciwieństwie do braku treści) jest to, że PEVerify może działać i kończyć się powodzeniem (w związku z tym sprawdzanie kompletności metadanych).

Zestawy referencyjne zawierają atrybut na poziomie `ReferenceAssembly` zestawu. Ten atrybut może być określony w źródle (a następnie kompilator nie będzie musiał przeprowadzić jego syntezy). Ze względu na ten atrybut środowiska uruchomieniowe będą odrzucać ładowanie zestawów odwołań do wykonania (ale nadal mogą być ładowane w trybie tylko odbicie). Narzędzia odzwierciedlające zestawy muszą mieć pewność, że ładują zestawy referencyjne jako tylko odbicie. w przeciwnym razie w środowisku uruchomieniowym wystąpi błąd typeload.

Zestawy referencyjne usuwają metadane (prywatne składowe) z zestawów samych metadanych:

- Zestaw odniesienia zawiera odwołania do potrzebnych elementów interfejsu API. Rzeczywisty zestaw może zawierać dodatkowe odwołania dotyczące konkretnych implementacji. Na przykład zestaw odwołania dla `class C { private void M() { dynamic d = 1; ... } }` nie odwołuje się do żadnych typów wymaganych przez. `dynamic`
- Prywatne funkcje — elementy członkowskie (metody, właściwości i zdarzenia) są usuwane w przypadkach, gdy ich usunięcie nie ma zauważalnego wpływu na kompilację. Jeśli nie ma żadnych <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutów, wykonaj te same czynności w przypadku wewnętrznych funkcji.
- Ale wszystkie typy (w tym typy prywatne lub zagnieżdżone) są przechowywane w zestawach referencyjnych. Wszystkie atrybuty są zachowywane (nawet wewnętrznie).
- Wszystkie metody wirtualne są zachowywane. Jawne implementacje interfejsu są zachowywane. Jawne zaimplementowane właściwości i zdarzenia są przechowywane, ponieważ ich metody dostępu są wirtualne (i dlatego są utrzymywane).
- Wszystkie pola struktury są przechowywane. (Jest to kandydat dla uściślenia poC#--7,1)

Opcje `-refout` [i`-refonly`](refonly-compiler-option.md) wzajemnie się wykluczają.

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
