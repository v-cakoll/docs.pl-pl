---
title: "Stałe (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 86c9371a6a82c4034b7bdf279e7b205cfcc84bea
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="constants-c-programming-guide"></a>Stałe (Przewodnik programowania w języku C#)
Stałe są niezmienne wartości, które są określane w czasie kompilacji i nie należy zmieniać przez cały okres istnienia program. Stałe są deklarowane jako z [const](../../../csharp/language-reference/keywords/const.md) modyfikator. Tylko C# wbudowanych typów (z wyłączeniem <xref:System.Object?displayProperty=nameWithType>) może być zadeklarowana jako `const`. Aby uzyskać listę wbudowanych typów, zobacz [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md). Typy zdefiniowane przez użytkownika, łącznie z klas, struktur i tablic, nie mogą być `const`. Użyj [tylko do odczytu](../../../csharp/language-reference/keywords/readonly.md) modyfikator można utworzyć klasy, struktury lub tablicy, która została zainicjowana jeden raz w czasie wykonywania (na przykład w konstruktorze), a następnie nie można zmienić.  
  
 C# nie obsługuje `const` metod, właściwości lub zdarzeń.  
  
 Typ wyliczeniowy umożliwia zdefiniowanie stałe nazwane dla wbudowanych typów całkowitych (na przykład `int`, `uint`, `long`i tak dalej). Aby uzyskać więcej informacji, zobacz [wyliczenia](../../../csharp/language-reference/keywords/enum.md).  
  
 Stałe muszą zostać zainicjowane, jak są deklarowane jako. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#64](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_1.cs)]  
  
 W tym przykładzie stała `months` jest zawsze 12, a nie można zmienić nawet przez samej klasy. W rzeczywistości, gdy kompilator napotka stałej identyfikator kodu źródłowego C# (na przykład `months`), bezpośrednio do kodu języku pośrednim (IL), który generuje ta funkcja zastępuje wartość literału. Ponieważ nie istnieje żaden adres zmiennej skojarzone ze stałą w czasie wykonywania, `const` pola nie mogą być przekazywane przez odwołanie i nie może występować jako l wartość w wyrażeniu.  
  
> [!NOTE]
>  W przypadku odwoływania się do wartości stałych zdefiniowanych w innym kodzie, takich jak biblioteki DLL należy zachować ostrożność. Jeśli nowa wersja biblioteki DLL Określa nową wartość stałą, program nadal posiadają stara wartość literału, dopóki nie jest zwrócenie przy użyciu nowej wersji.  
  
 Wiele stałych tego samego typu mogą być deklarowane w tym samym czasie, na przykład:  
  
 [!code-csharp[csProgGuideObjects#65](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_2.cs)]  
  
 Wyrażenie, które służy do inicjowania stałą może dotyczyć inną stałą, jeśli nie tworzy odwołania cyklicznego. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#66](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_3.cs)]  
  
 Stałe może być oznaczony jako [publicznego](../../../csharp/language-reference/keywords/public.md), [prywatnej](../../../csharp/language-reference/keywords/private.md), [chronione](../../../csharp/language-reference/keywords/protected.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), [chronionych wewnętrznych](../../../csharp/language-reference/keywords/protected-internal.md)lub [prywatne chronione](../../../csharp/language-reference/keywords/private-protected.md). Te modyfikatory dostępu zdefiniuj, jak użytkownicy klasy mają dostęp do stałej. Aby uzyskać więcej informacji, zobacz [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Stałe są dostępne, tak jakby były [statycznych](../../../csharp/language-reference/keywords/static.md) pola, ponieważ wartość stała jest taka sama dla wszystkich wystąpień tego typu. Nie używaj `static` — słowo kluczowe, aby zadeklarować je. Wyrażeń, które nie należą do klasy, który definiuje stałą musi Użyj nazwy klasy, okres i nazwę stałej dla dostępu stała. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#67](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_4.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Typy](../../../csharp/programming-guide/types/index.md)  
 [readonly](../../../csharp/language-reference/keywords/readonly.md)  
 [Część immutability w języku C#, pierwsza: rodzaje Immutability](https://blogs.msdn.microsoft.com/ericlippert/2007/11/13/immutability-in-c-part-one-kinds-of-immutability)
