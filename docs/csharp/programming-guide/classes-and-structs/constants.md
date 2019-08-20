---
title: Stałe — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
ms.openlocfilehash: d179c1b8717f4247ce745104db2d0bb4faefb8ab
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597108"
---
# <a name="constants-c-programming-guide"></a>Stałe (Przewodnik programowania w języku C#)
Stałe są niezmienne wartości, które są znane w czasie kompilacji i nie zmieniają się w okresie istnienia programu. Stałe są zadeklarowane za pomocą modyfikatora [const](../../language-reference/keywords/const.md) . Tylko typy C# wbudowane (z wyjątkiem <xref:System.Object?displayProperty=nameWithType>) mogą być zadeklarowane jako. `const` Aby uzyskać listę typów wbudowanych, zobacz [tabela typy wbudowane](../../language-reference/keywords/built-in-types-table.md). Typy zdefiniowane przez użytkownika, w tym klasy, struktury i tablice, nie mogą być `const`. Użyj modyfikatora [tylko do odczytu](../../language-reference/keywords/readonly.md) , aby utworzyć klasę, strukturę lub tablicę, która jest inicjowana jednokrotnie w czasie wykonywania (na przykład w konstruktorze) i nie można jej zmienić.  
  
 C#nie obsługuje `const` metod, właściwości ani zdarzeń.  
  
 Typ wyliczenia pozwala definiować stałe nazwane dla wbudowanych typów całkowitych (na przykład `int` `uint` `long`,, i tak dalej). Aby uzyskać więcej informacji, zobacz [Wyliczenie](../../language-reference/keywords/enum.md).  
  
 Stałe muszą zostać zainicjowane, ponieważ są one zadeklarowane. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#64](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#64)]  
  
 W tym przykładzie stała `months` jest zawsze 12 i nie może być zmieniana nawet przez samą klasę. W rzeczywistości, gdy kompilator napotyka stały identyfikator w C# kodzie źródłowym (na przykład `months`), zastępuje wartość literału bezpośrednio do kodu języka pośredniego (IL), który tworzy. Ze względu na to, że żaden adres zmiennej nie jest skojarzony ze `const` stałą w czasie wykonywania, pola nie mogą być przesyłane przez odwołanie i nie mogą występować jako l-wartość w wyrażeniu.  
  
> [!NOTE]
>  Należy zachować ostrożność w przypadku odwoływania się do wartości stałych zdefiniowanych w innym kodzie, takim jak dll. Jeśli nowa wersja biblioteki DLL definiuje nową wartość dla stałej, program będzie nadal przechowywać starą wartość literału, dopóki nie zostanie ponownie skompilowana względem nowej wersji.  
  
 Można jednocześnie zadeklarować wiele stałych tego samego typu, na przykład:  
  
 [!code-csharp[csProgGuideObjects#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#65)]  
  
 Wyrażenie, które jest używane do inicjowania stałej może odwoływać się do innej stałej, jeśli nie tworzy odwołania cyklicznego. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#66](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#66)]  
  
 Stałe mogą być oznaczone jako [publiczne](../../language-reference/keywords/public.md), [prywatne](../../language-reference/keywords/private.md), [chronione](../../language-reference/keywords/protected.md), [wewnętrzne](../../language-reference/keywords/internal.md), [chronione wewnętrznie](../../language-reference/keywords/protected-internal.md) lub [chronione prywatnie](../../language-reference/keywords/private-protected.md). Te Modyfikatory dostępu definiują sposób, w jaki użytkownicy klasy mogą uzyskać dostęp do stałej. Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](./access-modifiers.md).  
  
 Stałe są dostępne, tak jakby były [](../../language-reference/keywords/static.md) polami statycznymi, ponieważ wartość stałej jest taka sama dla wszystkich wystąpień tego typu. Nie używasz słowa kluczowego `static` , aby je zadeklarować. Wyrażenia, które nie znajdują się w klasie, która definiuje stałą, muszą używać nazwy klasy, kropki i nazwy stałej, aby uzyskać dostęp do stałej. Przykład:  
  
 [!code-csharp[csProgGuideObjects#67](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#67)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](./index.md)
- [Właściwości](./properties.md)
- [Typy](../types/index.md)
- [readonly](../../language-reference/keywords/readonly.md)
- [Niezmienności w C# pierwszej części: Rodzaje niezmienności](https://blogs.msdn.microsoft.com/ericlippert/2007/11/13/immutability-in-c-part-one-kinds-of-immutability)
