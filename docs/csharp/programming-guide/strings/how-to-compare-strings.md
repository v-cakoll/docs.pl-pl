---
title: "Porady: porównywanie ciągów (C# przewodnik programowania w języku)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
ms.assetid: e1268e28-ee98-4695-98e9-92280f1c33c0
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4837fa57c962cba841ffcc83c5bd4475a4faff0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-compare-strings-c-programming-guide"></a>Porady: porównywanie ciągów (C# przewodnik programowania w języku)

Podczas porównywania ciągów są generująca wynik informacją jednego ciągu jest większa lub mniejsza niż drugi lub czy dwa ciągi są takie same. Zasady, według których ustalić wyniku są różne w zależności od tego, czy działają *porównanie liczby porządkowej* lub *porównania z uwzględnieniem kultury*. Należy użyć poprawny typ porównania dla określonego zadania.

 Podstawowe liczby porządkowej porównania należy użyć w przypadku do porównywania lub posortować wartości dwa ciągi niezależnie konwencje językowe. Porównanie liczby porządkowej podstawowe (`System.StringComparison.Ordinal`) jest rozróżniana wielkość liter, co oznacza, że dwa ciągi musi odpowiadać znaków dla znaku: "i" nie równa się "I" lub "I". Jest odmianą często używane `System.StringComparison.OrdinalIgnoreCase`, która będzie odpowiadała "i", "I" i "I". `StringComparison.OrdinalIgnoreCase`często służy do porównywania nazw plików, nazwy ścieżek ścieżek sieciowych i inny ciąg której wartość nie ulega zmianie oparte na ustawieniach regionalnych komputera użytkownika. Aby uzyskać więcej informacji, zobacz <xref:System.StringComparison?displayProperty=nameWithType>.

 Zależne od kultury porównań są zwykle używane do porównywanie i sortowanie ciągów, które są wejściowych przez użytkowników końcowych, ponieważ znaków i konwencje sortowania ciągów te mogą się różnić w zależności od ustawień regionalnych komputera użytkownika. Nawet ciągów, które zawierają znaki identyczne może sortować inaczej w zależności od kultury bieżącej wątku.

> [!NOTE]
> Podczas porównywania ciągów, należy użyć metody, które jawnie określić, jakiego rodzaju porównania zamierzasz wykonać. Dzięki temu kodu bardziej łatwy w obsłudze i do odczytu. Jeśli to możliwe, użyj przeciążeń metody <xref:System.String?displayProperty=nameWithType> i <xref:System.Array?displayProperty=nameWithType> klas, które trwają <xref:System.StringComparison> parametru wyliczenia, dzięki czemu można określić typ porównania do wykonania. Zaleca się unikać `==` i `!=` operatory podczas porównywania ciągów. Ponadto należy unikać <xref:System.String.CompareTo%2A?displayProperty=nameWithType> wystąpienia metody, ponieważ brak przeciążeń <xref:System.StringComparison>.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak poprawnie porównywanie ciągów, których wartości nie spowoduje zmiany oparte na ustawieniach regionalnych komputera użytkownika. Ponadto ilustruje też *interning ciąg* funkcji języka C#. Jeśli program deklaruje co najmniej dwa identyczne ciągu zmiennych, kompilator przechowuje je w tej samej lokalizacji. Wywołując <xref:System.Object.ReferenceEquals%2A> metody widać, że dwa ciągi faktycznie odwołują się do tego samego obiektu w pamięci. Użyj <xref:System.String.Copy%2A?displayProperty=nameWithType> metody w celu uniknięcia interning, jak pokazano w przykładzie.

[!code-csharp[csProgGuideStrings#11](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#11)]

## <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób porównywania ciągów preferowany sposób za pomocą <xref:System.String?displayProperty=nameWithType> metod, które przyjmują <xref:System.StringComparison> wyliczenia. Należy pamiętać, że <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody wystąpienia nie są używane w tym miejscu, ponieważ brak przeciążeń <xref:System.StringComparison>.

[!code-csharp[csProgGuideStrings#31](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#31)]

## <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób sortowanie i wyszukiwanie ciągów w tablicy w sposób zależne od kultury przy użyciu statycznych <xref:System.Array> metod, które przyjmują <xref:System.StringComparer?displayProperty=nameWithType> parametru.

[!code-csharp[csProgGuideStrings#32](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#32)]

Kolekcja klas takich jak <xref:System.Collections.Hashtable?displayProperty=nameWithType>, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>, i <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> ma konstruktorów przyjmujących <xref:System.StringComparer?displayProperty=nameWithType> parametru, gdy typ elementów lub kluczy to `string`. Ogólnie rzecz biorąc, należy te konstruktorów w miarę możliwości używać i określ `Ordinal` lub `OrdinalIgnoreCase`.

## <a name="see-also"></a>Zobacz także
 <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>  
 <xref:System.StringComparer?displayProperty=nameWithType>  
 [Ciągi](../../../csharp/programming-guide/strings/index.md)  
 [Porównywanie ciągów](../../../standard/base-types/comparing.md)  
 [Globalizacja i lokalizacja aplikacji](/visualstudio/ide/globalizing-and-localizing-applications)