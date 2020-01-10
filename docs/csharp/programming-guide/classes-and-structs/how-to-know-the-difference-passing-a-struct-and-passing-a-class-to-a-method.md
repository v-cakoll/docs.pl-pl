---
title: Jak poznać różnicę między przekazywaniem struktury i przekazywaniem odwołania do klasy do przewodnika C# programowania metod
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], passing as method parameter
- passing parameters [C#], structs vs. classes
- methods [C#], passing classes vs. structs
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
ms.openlocfilehash: 953b2edf23530dfdf9ea96c1ac49fe455306c542
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714887"
---
# <a name="how-to-know-the-difference-between-passing-a-struct-and-passing-a-class-reference-to-a-method-c-programming-guide"></a>Jak poznać różnicę między przekazaniem struktury i przekazaniem odwołania do klasy do metody (C# Przewodnik programowania)
Poniższy przykład ilustruje sposób przekazywania [struktury](../../language-reference/keywords/struct.md) do metody różni się od przekazywania wystąpienia [klasy](../../language-reference/keywords/class.md) do metody. W przykładzie oba argumenty (wystąpienie struktury i klasy) są przekazane przez wartość, a obie te metody zmieniają wartość jednego pola argumentu. Jednak wyniki dwóch metod nie są takie same, ponieważ co jest przekazywane w przypadku przekazania struktury różni się od tego, co jest przekazywane podczas przekazywania wystąpienia klasy.  
  
 Ponieważ struktura jest [typem wartości](../../language-reference/keywords/value-types.md), po [przejściu struktury przez wartość](./passing-value-type-parameters.md) do metody Metoda otrzymuje i działa na kopii argumentu struktury. Metoda nie ma dostępu do oryginalnej struktury w metodzie wywołującej i w związku z tym nie może zmienić jej w jakikolwiek sposób. Metoda może zmienić tylko kopię.  
  
 Wystąpienie klasy jest [typem referencyjnym](../../language-reference/keywords/reference-types.md), a nie typem wartości. Gdy [typ referencyjny jest przekazywane przez wartość](./passing-reference-type-parameters.md) do metody, Metoda otrzymuje kopię odwołania do wystąpienia klasy. Oznacza to, że wywołana metoda otrzymuje kopię adresu wystąpienia, a metoda wywołująca zachowuje oryginalny adres wystąpienia. Wystąpienie klasy w metodzie wywołującej ma adres, parametr w wywołanej metodzie ma kopię adresu, a oba adresy odwołują się do tego samego obiektu. Ponieważ parametr zawiera tylko kopię adresu, wywołana metoda nie może zmienić adresu wystąpienia klasy w metodzie wywołującej. Jednak wywołana metoda może użyć kopii adresu w celu uzyskania dostępu do składowych klasy, które zarówno oryginalny adres, jak i kopia odwołania do adresu. Jeśli wywołana metoda zmienia element członkowski klasy, pierwotne wystąpienie klasy w metodzie wywołującej zmienia się również.  
  
 W danych wyjściowych w poniższym przykładzie pokazano różnicę. Wartość pola `willIChange` wystąpienia klasy jest zmieniana przez wywołanie metody `ClassTaker`, ponieważ metoda używa adresu w parametrze, aby znaleźć określone pole wystąpienia klasy. Pole `willIChange` struktury w metodzie wywołującej nie jest zmieniane przez wywołanie metody `StructTaker`, ponieważ wartość argumentu jest kopią samej struktury, a nie kopią jej adresu. `StructTaker` zmienia kopię, a kopia zostanie utracona, gdy wywołanie `StructTaker` zostało zakończone.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideObjects#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#32)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy](./classes.md)
- [Struktury](./structs.md)
- [Przekazywanie parametrów](./passing-parameters.md)
