---
title: -opcji refout (opcje kompilatora C#)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: e204a053f6f68a4b848d22c95c98f04edff58716
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506628"
---
# <a name="-refout-c-compiler-options"></a>-opcji refout (opcje kompilatora C#)

**- Opcji refout** opcja określa ścieżkę pliku, gdzie zestaw odwołania powinny być danych wyjściowych. Przekłada się to `metadataPeStream` w interfejsie API emisji.

## <a name="syntax"></a>Składnia

```console
-refout:filepath
```

## <a name="arguments"></a>Argumenty

 `filepath` Ścieżka pliku dla zestawu odwołania. Zazwyczaj powinien odpowiadać okresowi istnienia podstawowego zestawu. Zalecane Konwencji (używane przez program MSBuild) jest umieszczenie zestawu odwołania w "ref /" podfolder względem podstawowego zestawu.

## <a name="remarks"></a>Uwagi

Zestawy zawierające tylko metadane mieć ich treść metody zastąpione za pomocą jednego `throw null` treści, ale dołączone wszystkie elementy członkowskie z wyjątkiem typów anonimowych. Przyczyna przy użyciu `throw null` treści (w przeciwieństwie do treści) jest tak, aby PEVerify można uruchomić i przekazać (dlatego sprawdzanie poprawności kompletność metadanych).

Zestawy referencyjne zawierają poziomie zestawu `ReferenceAssembly` atrybutu. Ten atrybut może być określony w źródle (następnie kompilator nie będzie konieczne jej syntetyzowania). Z powodu tego atrybutu środowisk wykonawczych będzie odmawiał załadowania zestawy referencyjne do wykonania (ale nadal może być załadowany w trybie tylko do odbicia). Narzędzia, które odzwierciedlają na potrzeby zestawów, upewnij się, że są one ładowane odwołań do zestawów jako tylko do odbicia, w przeciwnym razie otrzymają błąd typeload ze środowiska wykonawczego.

Dodatkowo zestawy odwołań metadanych (prywatne składowe) należy usunąć z zestawów zawierających tylko metadane:

- Zestaw odwołania ma tylko odwołania do to, czego potrzebuje na powierzchni interfejsu API. Rzeczywistych zestaw może mieć dodatkowe informacje związane z określonych implementacji. Na przykład odwołanie do zestawu dla `class C { private void M() { dynamic d = 1; ... } }` nie odwołuje się do wszystkich typów wymaganych do `dynamic`.
- Prywatne funkcji elementów członkowskich (metody, właściwości i zdarzenia) są usuwane w przypadku, gdy ich usunięcia ciemniejsza nie ma wpływu na kompilację. W przypadku nie `InternalsVisibleTo` atrybutów, zrób to samo dla wewnętrznej funkcji elementów członkowskich.
- Jednak wszystkie typy (takie jak typy prywatny ani zagnieżdżony) są przechowywane w zestawach referencyjnych. Wszystkie atrybuty są utrzymywane (tymi nawet wewnętrznego).
- Wszystkie metody wirtualne są zachowywane. Jawne implementacje interfejsu są zachowywane. Jawnie implementowane właściwości i zdarzenia są zachowywane, zgodnie z ich metod dostępu wirtualne (i w związku z tym są przechowywane).
- Wszystkie pola struktury są zachowywane. (To jest kandydatem do wpisu — C# — 7.1 refinement)

`-refout` i [ `-refonly` ](refonly-compiler-option.md) opcje wykluczają się wzajemnie.

## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
