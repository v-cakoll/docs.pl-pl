---
title: "przy użyciu statycznych — dyrektywa (odwołanie w C#)"
ms.date: 03/10/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5838bede475cf2ad1b72518770241e86206a06bb
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="using-static-directive-c-reference"></a>przy użyciu statycznych — dyrektywa (odwołanie w C#)

`using static` Dyrektywy wyznacza typ którego statyczne elementy członkowskie użytkownik ma dostęp bez określania nazwy typu. Składnia to:

```csharp
using static <fully-qualified-type-name>
```

gdzie *pełni kwalifikowana nazwa--typu* jest nazwa typu, w których statyczne elementy członkowskie można odwoływać się bez określania nazwy typu. Jeśli podasz typu w pełni kwalifikowaną nazwę (pełna przestrzeni nazw wraz z nazwą typu), C# generuje błąd kompilatora CS0246: "nie można odnaleźć nazwy typu lub przestrzeni nazw"< Nazwa typu >"."

`using static` Dyrektywę stosuje się do dowolnego typu, który ma elementy członkowskie static, nawet jeśli ma również elementów członkowskich wystąpień. Jednak elementów członkowskich wystąpienia można wywołać tylko za pomocą wystąpienia typu.

`using static` Dyrektywy wprowadzono w języku C# 6.

## <a name="remarks"></a>Uwagi
 
Zwykle po wywołaniu statyczny element członkowski, musisz podać nazwy typu oraz nazwę elementu członkowskiego. Wielokrotnie wprowadzania tej samej nazwy typu do wywołania elementy członkowskie tego typu może spowodować pełne zasłoniętej kodu. Na przykład następujące definicji `Circle` klasy odwołuje się do liczby elementów członkowskich <xref:System.Math> klasy.
  
[!code-csharp[using-static#1](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

Dzięki wyeliminowaniu konieczności jawnie odwoływać się do <xref:System.Math> klasy zawsze odwołuje się element członkowski, `using static` dyrektywy tworzy dużo czyszczący kodu:

[!code-csharp[using-static#2](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

`using static`Importuje tylko dostępny statyczne elementy członkowskie i typy zagnieżdżone zadeklarowany w określonego typu.  Dziedziczone elementy członkowskie nie zostaną zaimportowane.  Można importować z dowolnego typu o nazwie using dyrektywy statycznych, w tym moduły Visual Basic.  Jeśli F # najwyższego poziomu funkcji są wyświetlane w metadanych jako statyczne elementy członkowskie typu nazwanego, którego nazwa jest prawidłowym identyfikatorem języka C#, F # funkcje mogą zostać zaimportowane.  
  
 `using static`udostępnia metody rozszerzenia zadeklarowany w określonym typie dostępne do wyszukiwania — metoda rozszerzenia.  Jednak nazwy metody rozszerzenia nie są importowane do zakresu niekwalifikowane odwołania w kodzie.  
  
 Metody o tej samej nazwie zaimportowane z różnych typów przez różne `using static` dyrektywy w tej samej jednostce kompilacyjnej lub przestrzeni nazw tworzą grupy metod.  Rozpoznanie przeciążenia w tych grupach — metoda zgodna normalnych C# reguł.  
  
## <a name="example"></a>Przykład

W poniższym przykładzie użyto `using static` dyrektywy Aby statyczne elementy członkowskie <xref:System.Console>, <xref:System.Math>, i <xref:System.String> klasy dostępne bez konieczności określania nazwy typu.

[!code-csharp[using-static#3](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

W tym przykładzie `using static` dyrektywy można również zostały zastosowane do <xref:System.Double> typu. To spowoduje umożliwiły do wywołania <xref:System.Double.TryParse(System.String,System.Double@)> metody bez określania nazwy typu. Jednak spowoduje to utworzenie kodu mniej do odczytu, ponieważ trzeba sprawdzić `using static` instrukcje, aby określić, którego typ liczbowy `TryParse` metoda jest wywoływana.

## <a name="see-also"></a>Zobacz także

[Using — Dyrektywa](using-directive.md)   
[Odwołanie w C#](../../../csharp/language-reference/index.md)   
[Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)   
[Używanie usługi przestrzenie nazw](../../../csharp/programming-guide/namespaces/using-namespaces.md)   
[Słowa kluczowe Namespace](../../../csharp/language-reference/keywords/namespace-keywords.md)   
[Przestrzenie nazw](../../../csharp/programming-guide/namespaces/index.md)   
