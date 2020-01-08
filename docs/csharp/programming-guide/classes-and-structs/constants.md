---
title: Stałe — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
ms.openlocfilehash: b7c005063ed1d7f881a42d340525c21ee89948b4
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347132"
---
# <a name="constants-c-programming-guide"></a>Stałe (Przewodnik programowania w języku C#)
Stałe są niezmienne wartości, które są znane w czasie kompilacji i nie zmieniają się w okresie istnienia programu. Stałe są zadeklarowane za pomocą modyfikatora [const](../../language-reference/keywords/const.md) . Tylko typy C# wbudowane (z wyłączeniem <xref:System.Object?displayProperty=nameWithType>) mogą być zadeklarowane jako `const`. Aby uzyskać listę typów wbudowanych, zobacz [tabela typy wbudowane](../../language-reference/keywords/built-in-types-table.md). Typy zdefiniowane przez użytkownika, w tym klasy, struktury i tablice, nie mogą być `const`. Użyj modyfikatora [tylko do odczytu](../../language-reference/keywords/readonly.md) , aby utworzyć klasę, strukturę lub tablicę, która jest inicjowana jednokrotnie w czasie wykonywania (na przykład w konstruktorze) i nie można jej zmienić.  
  
 C#Program nie obsługuje `const` metod, właściwości ani zdarzeń.  
  
 Typ wyliczenia umożliwia zdefiniowanie stałych nazwanych dla wbudowanych typów całkowitych (na przykład `int`, `uint`, `long`itd.). Aby uzyskać więcej informacji, zobacz [Wyliczenie](../../language-reference/builtin-types/enum.md).  
  
 Stałe muszą zostać zainicjowane, ponieważ są one zadeklarowane. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#64](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#64)]  
  
 W tym przykładzie stała `months` jest zawsze 12 i nie może zostać zmieniona nawet przez samą klasę. W rzeczywistości, gdy kompilator napotyka stały identyfikator w C# kodzie źródłowym (na przykład `months`), zastępuje wartość literału bezpośrednio do kodu języka pośredniego (IL), który tworzy. Ponieważ nie istnieje żaden adres zmiennej skojarzony ze stałą w czasie wykonywania, `const` pola nie mogą być przesyłane przez odwołanie i nie mogą występować jako l-wartość w wyrażeniu.  
  
> [!NOTE]
> Należy zachować ostrożność w przypadku odwoływania się do wartości stałych zdefiniowanych w innym kodzie, takim jak dll. Jeśli nowa wersja biblioteki DLL definiuje nową wartość dla stałej, program będzie nadal przechowywać starą wartość literału, dopóki nie zostanie ponownie skompilowana względem nowej wersji.  
  
 Można jednocześnie zadeklarować wiele stałych tego samego typu, na przykład:  
  
 [!code-csharp[csProgGuideObjects#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#65)]  
  
 Wyrażenie, które jest używane do inicjowania stałej może odwoływać się do innej stałej, jeśli nie tworzy odwołania cyklicznego. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#66](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#66)]  
  
 Stałe mogą być oznaczone jako [publiczne](../../language-reference/keywords/public.md), [prywatne](../../language-reference/keywords/private.md), [chronione](../../language-reference/keywords/protected.md), [wewnętrzne](../../language-reference/keywords/internal.md), [chronione wewnętrznie](../../language-reference/keywords/protected-internal.md) lub [chronione prywatnie](../../language-reference/keywords/private-protected.md). Te Modyfikatory dostępu definiują sposób, w jaki użytkownicy klasy mogą uzyskać dostęp do stałej. Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](./access-modifiers.md).  
  
 Stałe są dostępne, tak jakby były polami [statycznymi](../../language-reference/keywords/static.md) , ponieważ wartość stałej jest taka sama dla wszystkich wystąpień tego typu. Nie używasz słowa kluczowego `static`, aby je zadeklarować. Wyrażenia, które nie znajdują się w klasie, która definiuje stałą, muszą używać nazwy klasy, kropki i nazwy stałej, aby uzyskać dostęp do stałej. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#67](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#67)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](./index.md)
- [Właściwości](./properties.md)
- [Typy](../types/index.md)
- [readonly](../../language-reference/keywords/readonly.md)
- [Niezmienności w C# części pierwszej: rodzaje niezmienności](https://blogs.msdn.microsoft.com/ericlippert/2007/11/13/immutability-in-c-part-one-kinds-of-immutability)
