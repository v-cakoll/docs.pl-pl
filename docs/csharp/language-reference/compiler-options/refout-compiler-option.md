---
title: -refout (opcje kompilatora C#)
ms.date: 08/08/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fbae6f461304c37ba2ef10da16b5d520377bb225
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-refout-c-compiler-options"></a>-refout (opcje kompilatora C#)

**- Refout** opcja określa ścieżkę pliku, w którym zestaw odwołania powinny być danymi wyjściowymi. Przekłada się `metadataPeStream` w interfejsie API emisji.

## <a name="syntax"></a>Składnia

```console
-refout:filepath
```

## <a name="arguments"></a>Argumenty

 `filepath`Ścieżka zestawu odwołania. Zazwyczaj powinien odpowiadać okresowi istnienia podstawowego zestawu. Zalecane Konwencji (używane przez program MSBuild) jest umieszczenie zestawu odwołania w "ref /" podfolderu względem podstawowego zestawu.

## <a name="remarks"></a>Uwagi

Zestawy tylko metadane mieć ich treści metody zastąpione pojedynczy `throw null` body, ale dołączone wszystkie elementy członkowskie z wyjątkiem typy anonimowe. Przyczyna przy użyciu `throw null` jest jednostki (w przeciwieństwie do treści), dzięki czemu PEVerify można uruchamiać i przekazywania (w związku z tym sprawdzanie poprawności kompletności metadanych).

Zestawy referencyjne obejmuje dane poziomu zestawu `ReferenceAssembly` atrybutu. Ten atrybut można określić w źródle (następnie kompilator nie będzie trzeba go syntetyzowania). Z powodu tego atrybutu środowisk uruchomieniowych będzie odmawiał załadowania zestawów odwołań do wykonania (ale nadal może być załadowany w trybie tylko do odbicia). Narzędzia, które odzwierciedlać na potrzebę zestawów upewnij się, że są ładowane zestawów odwołań w trybie tylko do odbicia, w przeciwnym razie otrzymają komunikat o błędzie typeload ze środowiska uruchomieniowego.

Dodatkowe zestawy referencyjne usunąć metadanych (prywatne elementy członkowskie) z zestawów zawierających tylko metadane:

- Zestaw odwołania ma tylko odwołania do potrzebne na powierzchni interfejsu API. Rzeczywiste zestawu może posiadać dodatkowe odwołania, powiązane z określonej implementacji. Na przykład zestaw odwołania dla `class C { private void M() { dynamic d = 1; ... } }` nie odwołuje się do wszystkich typów wymaganych do `dynamic`.
- Prywatne funkcji elementów członkowskich (metody, właściwości i zdarzenia) zostaną usunięte w przypadkach, gdy ich usunięcia ciemniejsza bez wpływu kompilacji. Jeśli istnieją nie `InternalsVisibleTo` atrybuty, są takie same dla wewnętrznej funkcji elementów członkowskich.
- Jednak wszystkie typy (w tym typy prywatny ani zagnieżdżony) są przechowywane w zestawów odwołań. Wszystkie atrybuty są zachowywane (nawet wewnętrzny z nich).
- Wszystkie metody wirtualne są przechowywane. Jawne implementacje interfejsu są zachowywane. Jawnie implementowane właściwości i zdarzenia są przechowywane, zgodnie z ich metod dostępu wirtualne (i w związku z tym są przechowywane).
- Wszystkie pola struktury są zachowywane. (To jest kandydatem do post-C# — uściślenia 7.1)

`-refout` i [ `-refonly` ](refonly-compiler-option.md) wykluczają się wzajemnie.

## <a name="see-also"></a>Zobacz też
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
