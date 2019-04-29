---
title: Stałe — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
ms.openlocfilehash: 722e913403276cad48cf35a2d1923f74270feada
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651873"
---
# <a name="constants-c-programming-guide"></a>Stałe (Przewodnik programowania w języku C#)
Stałe są niezmienne wartości, które są znane w czasie kompilacji i nie zmieniają się przez cały okres istnienia programu. Stałe są uznane za pomocą [const](../../../csharp/language-reference/keywords/const.md) modyfikator. Tylko C# wbudowanych typów (z wyłączeniem <xref:System.Object?displayProperty=nameWithType>) mogą być deklarowane jako `const`. Aby uzyskać listę wbudowanych typów, zobacz [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md). Typy zdefiniowane przez użytkownika, w tym klasy, struktury i tablic, nie może być `const`. Użyj [tylko do odczytu](../../../csharp/language-reference/keywords/readonly.md) modyfikator, aby utworzyć klasy, struktury lub tablica, która jest inicjowany jeden raz w czasie wykonywania (na przykład w konstruktorze), a następnie nie można jej zmienić.  
  
 C# nie obsługuje `const` metody, właściwości lub zdarzeń.  
  
 Typ wyliczeniowy pozwala na zdefiniowanie nazwanych stałych całkowitych typów wbudowanych (na przykład `int`, `uint`, `long`i tak dalej). Aby uzyskać więcej informacji, zobacz [wyliczenia](../../../csharp/language-reference/keywords/enum.md).  
  
 Stałe muszą być zainicjowane, ponieważ są one zgłoszone. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#64](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#64)]  
  
 W tym przykładzie stała `months` zawsze 12, a nie można zmienić nawet przez samej klasy. W rzeczywistości, gdy kompilator napotka stałych identyfikatora w kodzie źródłowym języka C# (na przykład `months`), zastępuje bezpośrednio do kodu języka pośredniego (IL), który tworzy wartości literału. Ponieważ nie istnieje żaden adres zmiennej skojarzone ze stałą w czasie wykonywania, `const` pola nie mogą być przekazywane przez odwołanie i nie są wyświetlane jako l wartości w wyrażeniu.  
  
> [!NOTE]
>  Możesz odwołać się do wartości stałe zdefiniowane w innym kodzie, takich jak biblioteki dll, należy zachować ostrożność. Jeśli nową wersję biblioteki DLL Określa nową wartość dla stałej, program nadal posiadają stara wartość literału, dopóki nie jest zwrócenie względem nowej wersji.  
  
 Kilka stałych tego samego typu mogą być deklarowane w tym samym czasie, na przykład:  
  
 [!code-csharp[csProgGuideObjects#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#65)]  
  
 Wyrażenie, które służy do inicjowania stałą mogą odwoływać się do innej stałej, jeśli nie powoduje to powstanie odwołania cyklicznego. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#66](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#66)]  
  
 Stałe może być oznaczona jako [publicznych](../../../csharp/language-reference/keywords/public.md), [prywatnej](../../../csharp/language-reference/keywords/private.md), [chronione](../../../csharp/language-reference/keywords/protected.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), [chronionych wewnętrznych](../../../csharp/language-reference/keywords/protected-internal.md)lub [prywatny chroniony](../../../csharp/language-reference/keywords/private-protected.md). Następujące modyfikatory dostępu definiują, jak użytkownicy klasy mogą uzyskać dostępu do stałej. Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).   
  
 Stałe są dostępne, tak jakby [statyczne](../../../csharp/language-reference/keywords/static.md) pola, ponieważ wartość stałej jest taka sama dla wszystkich wystąpień tego typu. Nie używaj `static` — słowo kluczowe do deklarowania je. Wyrażeń, które nie znajdują się w klasie, która definiuje stałą, należy użyć nazwy klasy, kropka i nazwę stałej można uzyskać dostępu do stałej. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#67](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#67)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [Typy](../../../csharp/programming-guide/types/index.md)
- [readonly](../../../csharp/language-reference/keywords/readonly.md)
- [Niezmienność w C# pierwszej części: Rodzaje niezmienności](https://blogs.msdn.microsoft.com/ericlippert/2007/11/13/immutability-in-c-part-one-kinds-of-immutability)
