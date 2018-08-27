---
title: Using static, dyrektywa (odwołanie w C#)
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04e7368a6b6a4453f2dd07c7afdc0bffa7473ed1
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929681"
---
# <a name="using-static-directive-c-reference"></a>Using static, dyrektywa (odwołanie w C#)

`using static` Dyrektywy wyznacza typ, którego statycznych elementów członkowskich i typy zagnieżdżone, możesz uzyskać dostęp bez określenia nazwy typu. Jego składnia jest następująca:

```csharp
using static <fully-qualified-type-name>;
```

gdzie *w pełni kwalifikowana nazwa--typ* jest nazwa typu, którego statycznych elementów członkowskich i typy zagnieżdżone może znajdować się bez określania nazwy typu. Jeśli nie podasz w pełni kwalifikowana nazwa typu (nazwa przestrzeni nazw pełnej wraz z nazwą typu), C# generuje błąd kompilatora [CS0246](../compiler-messages/cs0246.md): "nie można odnaleźć nazwy typu lub przestrzeni nazw"/ przestrzeń nazw typu"(Brak using — dyrektywa lub odwołanie do zestawu?) ".

`using static` Dyrektywa odnosi się do dowolnego typu, który ma statyczne elementy członkowskie (lub zagnieżdżone typy), nawet wtedy, gdy w nim również elementy członkowskie wystąpień. Jednak składowych wystąpienia może być wywoływany przez wystąpienie typu.

`using static` Dyrektywa została wprowadzona w języku C# 6.

## <a name="remarks"></a>Uwagi
 
Zwykle po wywołaniu statycznego elementu członkowskiego, podaj nazwę typu, wraz z nazwą elementu członkowskiego. Wielokrotnego wprowadzania tej samej nazwie typu, aby wywołać elementy członkowskie tego typu może spowodować pełne zasłoniętej kodu. Na przykład poniższą definicję `Circle` klasy odwołuje się do liczby elementów członkowskich <xref:System.Math> klasy.
  
[!code-csharp[using-static#1](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

Dzięki wyeliminowaniu konieczności, aby jawnie odwołać <xref:System.Math> klasy zawsze odwołuje się do elementu członkowskiego, `using static` — dyrektywa generuje znacznie bardziej przejrzysty kod:

[!code-csharp[using-static#2](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

`using static` Importuje tylko dostępne statyczne elementy członkowskie i zagnieżdżone typy zadeklarowane w określonym typie.  Dziedziczone elementy członkowskie nie są importowane.  Można importować z dowolnego typu o nazwie z za pomocą dyrektywy statyczne, w tym moduły języka Visual Basic.  Jeśli funkcji najwyższego poziomu F # są wyświetlane w metadanych jako statyczne elementy członkowskie typu nazwanego, którego nazwa jest prawidłowym identyfikatorem języka C#, F # funkcje mogą zostać zaimportowane.  
  
 `using static` sprawia, że metody rozszerzenia zadeklarowana w określonego typu dostępne do przeszukiwania metody rozszerzenia.  Nazwy metody rozszerzenia nie są importowane w zakresie niekwalifikowanej odwołania w kodzie.  
  
 Metody o tej samej nazwie, zaimportowane z różnych typów przez różne `using static` dyrektywy w tej samej jednostce kompilacyjnej lub nazw tworzą grupy metod.  Rozpoznanie przeciążenia w tych grupach metoda regułom normalnego języka C#.  
  
## <a name="example"></a>Przykład

W poniższym przykładzie użyto `using static` dyrektywy, aby statyczne elementy członkowskie <xref:System.Console>, <xref:System.Math>, i <xref:System.String> klasy dostępne bez konieczności określania nazwy typu.

[!code-csharp[using-static#3](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

W tym przykładzie `using static` dyrektywy może również zostały zastosowane do <xref:System.Double> typu. To spowoduje umożliwiły wywołać <xref:System.Double.TryParse(System.String,System.Double@)> metody bez określania nazwy typu. Jednak powoduje to utworzenie mniej czytelny kod, ponieważ staje się to konieczne sprawdzić `using static` instrukcje, aby ustalić, jakiego typu liczbowego `TryParse` metoda jest wywoływana.

## <a name="see-also"></a>Zobacz także

- [Using — Dyrektywa](using-directive.md)
- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)
- [Używanie przestrzeni nazw](../../../csharp/programming-guide/namespaces/using-namespaces.md)
- [Słowa kluczowe przestrzeni nazw](../../../csharp/language-reference/keywords/namespace-keywords.md)
- [Przestrzenie nazw](../../../csharp/programming-guide/namespaces/index.md)
