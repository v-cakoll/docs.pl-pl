---
title: -jest opcja SET refonly (opcje kompilatora C#)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: 06b246d6e5831563389efa402ccb6a942430efa4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589730"
---
# <a name="-refonly-c-compiler-options"></a>-jest opcja SET refonly (opcje kompilatora C#)

**Jest opcja refonly -** opcja wskazuje, że zestaw odwołania powinny być danych wyjściowych zamiast zestawu implementacji jako główny wynik. `-refonly` Parametr dyskretnie wyłącza podawania plików PDB, ponieważ zestawy odwołań nie można wykonać.

## <a name="syntax"></a>Składnia

```console
-refonly
```

## <a name="remarks"></a>Uwagi

Zestawy zawierające tylko metadane mieć ich treść metody zastąpione za pomocą jednego `throw null` treści, ale dołączone wszystkie elementy członkowskie z wyjątkiem typów anonimowych. Przyczyna przy użyciu `throw null` treści (w przeciwieństwie do treści) jest tak, aby PEVerify można uruchomić i przekazać (dlatego sprawdzanie poprawności kompletność metadanych).

Zestawy referencyjne zawierają poziomie zestawu `ReferenceAssembly` atrybutu. Ten atrybut może być określony w źródle (następnie kompilator nie będzie konieczne jej syntetyzowania). Z powodu tego atrybutu środowisk wykonawczych będzie odmawiał załadowania zestawy referencyjne do wykonania (ale nadal może być załadowany w trybie tylko do odbicia). Narzędzia, które odzwierciedlają na potrzeby zestawów, upewnij się, że są one ładowane odwołań do zestawów jako tylko do odbicia, w przeciwnym razie otrzymają błąd typeload ze środowiska wykonawczego.

Dodatkowo zestawy odwołań metadanych (prywatne składowe) należy usunąć z zestawów zawierających tylko metadane:

- Zestaw odwołania ma tylko odwołania do to, czego potrzebuje na powierzchni interfejsu API. Rzeczywistych zestaw może mieć dodatkowe informacje związane z określonych implementacji. Na przykład odwołanie do zestawu dla `class C { private void M() { dynamic d = 1; ... } }` nie odwołuje się do wszystkich typów wymaganych do `dynamic`.
- Prywatne funkcji elementów członkowskich (metody, właściwości i zdarzenia) są usuwane w przypadku, gdy ich usunięcia ciemniejsza nie ma wpływu na kompilację. W przypadku nie `InternalsVisibleTo` atrybutów, zrób to samo dla wewnętrznej funkcji elementów członkowskich.
- Jednak wszystkie typy (takie jak typy prywatny ani zagnieżdżony) są przechowywane w zestawach referencyjnych. Wszystkie atrybuty są utrzymywane (tymi nawet wewnętrznego).
- Wszystkie metody wirtualne są zachowywane. Jawne implementacje interfejsu są zachowywane. Jawnie implementowane właściwości i zdarzenia są zachowywane, zgodnie z ich metod dostępu wirtualne (i w związku z tym są przechowywane).
- Wszystkie pola struktury są zachowywane. (To jest kandydatem do wpisu — C# — 7.1 refinement)

`-refonly` i [ `-refout` ](refout-compiler-option.md) opcje wykluczają się wzajemnie.

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
