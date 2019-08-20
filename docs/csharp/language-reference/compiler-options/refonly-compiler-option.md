---
title: -refonly (C# opcje kompilatora)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: eb62f98c5d548fe3583d3422eb7b6020a82c296a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606483"
---
# <a name="-refonly-c-compiler-options"></a>-refonly (C# opcje kompilatora)

Opcja **-refonly** wskazuje, że zestaw odwołania powinien być wyjściem, a nie zestawem implementacji, jako podstawowy wynik. `-refonly` Parametr dyskretnie wyłącza umieszczanie plików PDB, ponieważ nie można wykonać zestawów referencyjnych. Ta opcja odnosi się do właściwości Project [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) programu MSBuild.

## <a name="syntax"></a>Składnia

```console
-refonly
```

## <a name="remarks"></a>Uwagi

Zestawy zawierające tylko metadane są zastępowane przez jedną `throw null` treść, ale obejmują wszystkie elementy członkowskie z wyjątkiem typów anonimowych. Powodem używania `throw null` treści (w przeciwieństwie do braku treści) jest to, że PEVerify może działać i kończyć się powodzeniem (w związku z tym sprawdzanie kompletności metadanych).

Zestawy referencyjne zawierają atrybut na poziomie `ReferenceAssembly` zestawu. Ten atrybut może być określony w źródle (a następnie kompilator nie będzie musiał przeprowadzić jego syntezy). Ze względu na ten atrybut środowiska uruchomieniowe będą odrzucać ładowanie zestawów odwołań do wykonania (ale nadal mogą być ładowane w trybie tylko odbicie). Narzędzia odzwierciedlające zestawy muszą mieć pewność, że ładują zestawy referencyjne jako tylko odbicie. w przeciwnym razie w środowisku uruchomieniowym wystąpi błąd typeload.

Zestawy referencyjne usuwają metadane (prywatne składowe) z zestawów samych metadanych:

- Zestaw odniesienia zawiera odwołania do potrzebnych elementów interfejsu API. Rzeczywisty zestaw może zawierać dodatkowe odwołania dotyczące konkretnych implementacji. Na przykład zestaw odwołania dla `class C { private void M() { dynamic d = 1; ... } }` nie odwołuje się do żadnych typów wymaganych przez. `dynamic`
- Prywatne funkcje — elementy członkowskie (metody, właściwości i zdarzenia) są usuwane w przypadkach, gdy ich usunięcie nie ma zauważalnego wpływu na kompilację. Jeśli nie ma żadnych <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutów, wykonaj te same czynności w przypadku wewnętrznych funkcji.
- Ale wszystkie typy (w tym typy prywatne lub zagnieżdżone) są przechowywane w zestawach referencyjnych. Wszystkie atrybuty są zachowywane (nawet wewnętrznie).
- Wszystkie metody wirtualne są zachowywane. Jawne implementacje interfejsu są zachowywane. Jawne zaimplementowane właściwości i zdarzenia są przechowywane, ponieważ ich metody dostępu są wirtualne (i dlatego są utrzymywane).
- Wszystkie pola struktury są przechowywane. (Jest to kandydat dla uściślenia poC#--7,1)

Opcje `-refonly` [i`-refout`](refout-compiler-option.md) wzajemnie się wykluczają.

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
