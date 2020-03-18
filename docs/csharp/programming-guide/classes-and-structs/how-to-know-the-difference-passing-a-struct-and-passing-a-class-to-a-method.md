---
title: Jak poznać różnicę między przekazywaniem struktury a przekazywaniem odwołania do klasy metody - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], passing as method parameter
- passing parameters [C#], structs vs. classes
- methods [C#], passing classes vs. structs
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
ms.openlocfilehash: a280a6df873d7c03c204bc5c86468e7e7298d723
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77673436"
---
# <a name="how-to-know-the-difference-between-passing-a-struct-and-passing-a-class-reference-to-a-method-c-programming-guide"></a>Jak poznać różnicę między przekazywaniem struktury a przekazywaniem odwołania do klasy metody (Przewodnik programowania C#)
W poniższym przykładzie pokazano, jak przekazywanie [struktury](../../language-reference/builtin-types/struct.md) do metody różni się od przekazywania wystąpienia [klasy](../../language-reference/keywords/class.md) do metody. W tym przykładzie zarówno argumenty (struct i wystąpienie klasy) są przekazywane przez wartość, a obie metody zmieniają wartość jednego pola argumentu. Jednak wyniki dwóch metod nie są takie same, ponieważ to, co jest przekazywane po przekazaniu struktury różni się od tego, co jest przekazywane po przekazaniu wystąpienia klasy.  
  
 Ponieważ struktura jest [typem wartości](../../language-reference/builtin-types/value-types.md), po [przekazaniu struktury przez wartość](./passing-value-type-parameters.md) do metody, metoda odbiera i działa na kopii argumentu struktury. Metoda nie ma dostępu do oryginalnej struktury w metodzie wywołującej i dlatego nie można go zmienić w żaden sposób. Metoda może zmienić tylko kopię.  
  
 Wystąpienie klasy jest [typem odwołania,](../../language-reference/keywords/reference-types.md)a nie typem wartości. Gdy [typ odwołania jest przekazywany przez wartość](./passing-reference-type-parameters.md) do metody, metoda odbiera kopię odwołania do wystąpienia klasy. Oznacza to, że wywoływana metoda odbiera kopię adresu wystąpienia, a metoda wywołująca zachowuje oryginalny adres wystąpienia. Wystąpienie klasy w metodzie wywołującej ma adres, parametr w wywoływanej metody ma kopię adresu, a oba adresy odnoszą się do tego samego obiektu. Ponieważ parametr zawiera tylko kopię adresu, wywoływana metoda nie może zmienić adresu wystąpienia klasy w metodzie wywołującej. Jednak wywoływana metoda może użyć kopii adresu, aby uzyskać dostęp do elementów członkowskich klasy, które zarówno oryginalny adres, jak i kopia odwołania do adresu. Jeśli wywoływana metoda zmienia element członkowski klasy, oryginalne wystąpienie klasy w metodzie wywołującej również zmienia.  
  
 Dane wyjściowe w poniższym przykładzie ilustruje różnicę. Wartość `willIChange` pola wystąpienia klasy jest zmieniana przez wywołanie metody, `ClassTaker` ponieważ metoda używa adresu w parametrze, aby znaleźć określone pole wystąpienia klasy. Pole `willIChange` struktury w metodzie wywołującej nie jest zmieniane `StructTaker` przez wywołanie metody, ponieważ wartość argumentu jest kopią samej struktury, a nie kopią jego adresu. `StructTaker`zmienia kopię, a kopia zostanie utracona po zakończeniu połączenia. `StructTaker`  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideObjects#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#32)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Klasy](./classes.md)
- [Typy konstrukcji](../../language-reference/builtin-types/struct.md)
- [Przekazywanie parametrów](./passing-parameters.md)
