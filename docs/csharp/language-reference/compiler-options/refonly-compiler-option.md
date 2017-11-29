---
title: -refonly (opcje kompilatora C#)
ms.date: 07/08/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c4c745416bda56f5f1b1b4ab8267274d972a990d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="refonly-c-compiler-options"></a>/refonly (opcje kompilatora C#)

**/Refonly** opcja wskazuje, że zestaw odwołania powinny być danymi wyjściowymi zamiast zestawu implementacji, jako główny wynik. `/refonly` Parametr dyskretnie wyłącza Generowanie plików PDB, jak zestawy odwołań nie może zostać wykonana.

## <a name="syntax"></a>Składnia

```console
/refonly
```

## <a name="remarks"></a>Uwagi

Zestawy tylko metadane mieć ich treści metody zastąpione pojedynczy `throw null` body, ale dołączone wszystkie elementy członkowskie z wyjątkiem typy anonimowe. Przyczyna przy użyciu `throw null` jest jednostki (w przeciwieństwie do treści), dzięki czemu PEVerify można uruchamiać i przekazywania (w związku z tym sprawdzanie poprawności kompletności metadanych).

Zestawy referencyjne obejmuje dane poziomu zestawu `ReferenceAssembly` atrybutu. Ten atrybut można określić w źródle (następnie kompilator nie będzie trzeba go syntetyzowania). Z powodu tego atrybutu środowisk uruchomieniowych będzie odmawiał załadowania zestawów odwołań do wykonania (ale nadal może być załadowany w trybie tylko do odbicia). Narzędzia, które odzwierciedlać na potrzebę zestawów upewnij się, że są ładowane zestawów odwołań w trybie tylko do odbicia, w przeciwnym razie otrzymają komunikat o błędzie typeload ze środowiska uruchomieniowego.

Dodatkowe zestawy referencyjne usunąć metadanych (prywatne elementy członkowskie) z zestawów zawierających tylko metadane:

- Zestaw odwołania ma tylko odwołania do potrzebne na powierzchni interfejsu API. Rzeczywiste zestawu może posiadać dodatkowe odwołania, powiązane z określonej implementacji. Na przykład zestaw odwołania dla `class C { private void M() { dynamic d = 1; ... } }` nie odwołuje się do wszystkich typów wymaganych do `dynamic`.
- Prywatne funkcji elementów członkowskich (metody, właściwości i zdarzenia) zostaną usunięte w przypadkach, gdy ich usunięcia ciemniejsza bez wpływu kompilacji. Jeśli istnieją nie `InternalsVisibleTo` atrybuty, są takie same dla wewnętrznej funkcji elementów członkowskich.
- Jednak wszystkie typy (w tym typy prywatny ani zagnieżdżony) są przechowywane w zestawów odwołań. Wszystkie atrybuty są zachowywane (nawet wewnętrzny z nich).
- Wszystkie metody wirtualne są przechowywane. Jawne implementacje interfejsu są zachowywane. Jawnie implementowane właściwości i zdarzenia są przechowywane, zgodnie z ich metod dostępu wirtualne (i w związku z tym są przechowywane).
- Wszystkie pola struktury są zachowywane. (To jest kandydatem do post-C# — uściślenia 7.1)

`/refonly` i [ `/refout` ](refout-compiler-option.md) wykluczają się wzajemnie.

## <a name="see-also"></a>Zobacz także
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
