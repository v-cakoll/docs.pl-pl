---
title: 'Instrukcje: Zapoznaj się z różnicą między przekazywaniem struktury i przekazywaniem odwołania do klasy C# do przewodnika programowania metod'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], passing as method parameter
- passing parameters [C#], structs vs. classes
- methods [C#], passing classes vs. structs
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
ms.openlocfilehash: 889e1f5719e094d02f0cc27256e1c430ffce0b8e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596787"
---
# <a name="how-to-know-the-difference-between-passing-a-struct-and-passing-a-class-reference-to-a-method-c-programming-guide"></a>Instrukcje: Zapoznaj się z różnicą między przekazywaniem struktury i przekazywaniem odwołania do klasyC# do metody (Przewodnik programowania)
Poniższy przykład ilustruje sposób przekazywania [struktury](../../language-reference/keywords/struct.md) do metody różni się od przekazywania wystąpienia [klasy](../../language-reference/keywords/class.md) do metody. W przykładzie oba argumenty (wystąpienie struktury i klasy) są przekazane przez wartość, a obie te metody zmieniają wartość jednego pola argumentu. Jednak wyniki dwóch metod nie są takie same, ponieważ co jest przekazywane w przypadku przekazania struktury różni się od tego, co jest przekazywane podczas przekazywania wystąpienia klasy.  
  
 Ponieważ struktura jest [typem wartości](../../language-reference/keywords/value-types.md), po przejściu [struktury przez wartość](./passing-value-type-parameters.md) do metody Metoda otrzymuje i działa na kopii argumentu struktury. Metoda nie ma dostępu do oryginalnej struktury w metodzie wywołującej i w związku z tym nie może zmienić jej w jakikolwiek sposób. Metoda może zmienić tylko kopię.  
  
 Wystąpienie klasy jest [typem referencyjnym](../../language-reference/keywords/reference-types.md), a nie typem wartości. Gdy [typ referencyjny jest przekazywane przez wartość](./passing-reference-type-parameters.md) do metody, Metoda otrzymuje kopię odwołania do wystąpienia klasy. Oznacza to, że metoda otrzymuje kopię adresu wystąpienia, a nie kopię samego wystąpienia. Wystąpienie klasy w metodzie wywołującej ma adres, parametr w wywołanej metodzie ma kopię adresu, a oba adresy odwołują się do tego samego obiektu. Ponieważ parametr zawiera tylko kopię adresu, wywołana metoda nie może zmienić adresu wystąpienia klasy w metodzie wywołującej. Jednak wywołana metoda może używać adresu do uzyskiwania dostępu do elementów członkowskich klasy, które są zarówno oryginalnymi adresami, jak i odwołaniami kopiowania. Jeśli wywołana metoda zmienia element członkowski klasy, pierwotne wystąpienie klasy w metodzie wywołującej zmienia się również.  
  
 W danych wyjściowych w poniższym przykładzie pokazano różnicę. Wartość `willIChange` pola wystąpienia klasy jest zmieniana przez wywołanie metody `ClassTaker` , ponieważ metoda używa adresu w parametrze, aby znaleźć określone pole wystąpienia klasy. Pole struktury w metodzie wywołującej nie jest zmieniane przez wywołanie metody `StructTaker` , ponieważ wartość argumentu jest kopią samej struktury, a nie kopią jej adresu. `willIChange` `StructTaker`zmienia kopię, a kopia zostaje utracona po zakończeniu wywołania `StructTaker` .  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideObjects#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#32)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy](./classes.md)
- [Struktury](./structs.md)
- [Przekazywanie parametrów](./passing-parameters.md)
