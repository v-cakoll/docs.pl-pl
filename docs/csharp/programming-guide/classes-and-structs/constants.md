---
title: Stałe — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
ms.openlocfilehash: 85f6684617b893bdd85eb5b530aa2481941fbc5d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093555"
---
# <a name="constants-c-programming-guide"></a>Stałe (Przewodnik programowania w języku C#)
Stałe są wartościami niezmiennymi, które są znane w czasie kompilacji i nie zmieniają się przez cały okres użytkowania programu. Stałe są deklarowane za pomocą modyfikatora [const.](../../language-reference/keywords/const.md) Tylko typy [wbudowane](../../language-reference/builtin-types/built-in-types.md) c# (z <xref:System.Object?displayProperty=nameWithType>wyłączeniem) `const`mogą być zadeklarowane jako . Nie można określić `const`typów zdefiniowanych przez użytkownika, w tym klas, struktur i tablic. Użyj modyfikatora [tylko do odczytu,](../../language-reference/keywords/readonly.md) aby utworzyć klasę, strukturę lub tablicę, która jest inicjowana jeden raz w czasie wykonywania (na przykład w konstruktorze), a następnie nie można zmienić.  
  
 C# nie `const` obsługuje metody, właściwości lub zdarzenia.  
  
 Typ wyliczenia umożliwia definiowanie nazwanych stałych dla wbudowanych `uint` `long`typów (na przykład `int`, , i tak dalej). Aby uzyskać więcej informacji, zobacz [wyliczenie](../../language-reference/builtin-types/enum.md).  
  
 Stałe muszą być inicjowane, ponieważ są deklarowane. Przykład:  
  
 [!code-csharp[csProgGuideObjects#64](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#64)]  
  
 W tym przykładzie `months` stała jest zawsze 12 i nie może być zmieniona nawet przez samą klasę. W rzeczywistości, gdy kompilator napotka stały identyfikator w kodzie `months`źródłowym Języka C# (na przykład), zastępuje wartość literału bezpośrednio do kodu języka pośredniego (IL), który tworzy. Ponieważ nie ma adresu zmiennej skojarzonego ze stałą w czasie wykonywania, `const` pola nie mogą być przekazywane przez odwołanie i nie mogą być wyświetlane jako wartość l w wyrażeniu.  
  
> [!NOTE]
> Należy zachować ostrożność podczas odwoływania się do stałych wartości zdefiniowanych w innym kodzie, takich jak biblioteki DLL. Jeśli nowa wersja dll definiuje nową wartość dla stałej, program będzie nadal posiadać starą wartość literału, dopóki nie zostanie ponownie skompilowany względem nowej wersji.  
  
 W tym samym czasie można zadeklarować wiele stałych tego samego typu, na przykład:  
  
 [!code-csharp[csProgGuideObjects#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#65)]  
  
 Wyrażenie, które jest używane do inicjowania stałej może odwoływać się do innej stałej, jeśli nie tworzy odwołanie cykliczne. Przykład:  
  
 [!code-csharp[csProgGuideObjects#66](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#66)]  
  
 Stałe mogą być oznaczone jako [publiczne,](../../language-reference/keywords/public.md) [prywatne,](../../language-reference/keywords/private.md) [chronione,](../../language-reference/keywords/protected.md) [wewnętrzne,](../../language-reference/keywords/internal.md) [chronione wewnętrzne](../../language-reference/keywords/protected-internal.md) lub [prywatne chronione.](../../language-reference/keywords/private-protected.md) Te modyfikatory dostępu definiują, w jaki sposób użytkownicy klasy mogą uzyskiwać dostęp do stałej. Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](./access-modifiers.md).  
  
 Stałe są dostępne tak, jakby były pola [statyczne,](../../language-reference/keywords/static.md) ponieważ wartość stałej jest taka sama dla wszystkich wystąpień typu. Nie należy używać `static` słowa kluczowego do deklarowania ich. Wyrażenia, które nie znajdują się w klasie, która definiuje stałą, muszą używać nazwy klasy, kropki i nazwy stałej, aby uzyskać dostęp do stałej. Przykład:  
  
 [!code-csharp[csProgGuideObjects#67](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#67)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Klasy i struktury](./index.md)
- [Właściwości](./properties.md)
- [Typy](../types/index.md)
- [Readonly](../../language-reference/keywords/readonly.md)
- [Niezmienność w C# Część pierwsze: Rodzaje niezmienności](https://docs.microsoft.com/archive/blogs/ericlippert/immutability-in-c-part-one-kinds-of-immutability)
