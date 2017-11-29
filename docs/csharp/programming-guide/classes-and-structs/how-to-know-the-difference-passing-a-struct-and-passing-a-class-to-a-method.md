---
title: "Porady: różnica między przekazywaniem struktury a przekazywaniem odwołań do klas do metody (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- structs [C#], passing as method parameter
- passing parameters [C#], structs vs. classes
- methods [C#], passing classes vs. structs
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b989c3cefe72c6c17d10dd91005dcecbfc84e389
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-know-the-difference-between-passing-a-struct-and-passing-a-class-reference-to-a-method-c-programming-guide"></a>Porady: różnica między przekazywaniem struktury a przekazywaniem odwołań do klas do metody (Przewodnik programowania w języku C#)
W poniższym przykładzie pokazano, jak przekazywanie [struktury](../../../csharp/language-reference/keywords/struct.md) do metody różni się od przekazywanie [klasy](../../../csharp/language-reference/keywords/class.md) wystąpienie do metody. W tym przykładzie jednego z argumentów (wystąpienia struktury i klasy) są przekazywane przez wartość, a obie metody zmienić wartość pola jednego argumentu. Jednak wyniki z dwóch metod nie są takie same ponieważ jak wartości przekazane podczas przekazywania struktury różni się od jak wartości przekazane podczas przekazywania wystąpienia klasy.  
  
 Ponieważ struktury jest [typu wartości](../../../csharp/language-reference/keywords/value-types.md), gdy użytkownik [przekazanie przez wartość struktury](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md) do metody, metoda odbiera i działa na kopię argumentu struktury. Metoda nie ma dostępu do oryginalnej struktury w przypadku wywołania metody i dlatego nie można go zmienić w dowolny sposób. Metoda, można zmienić tylko kopiowania.  
  
 To wystąpienie klasy [zawierają odwołania do typu](../../../csharp/language-reference/keywords/reference-types.md), nie jest typem wartości. Gdy [Typ referencyjny jest przekazywany przez wartość](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md) do metody, metoda wysyłana kopia odwołania do wystąpienia klasy. Oznacza to, że metoda wysyłana kopia adres obiektu, nie Kopiuj wystąpienia samej siebie. Wystąpienie klasy w przypadku wywołania metody ma adres parametru w metodzie wywołane ma kopię adres, przez co oba adresy odwoływać się do tego samego obiektu. Ponieważ parametr zawiera tylko kopii adresu, wywołaną metodę nie można zmienić adres wystąpienie klasy w przypadku wywołania metody. Jednak wywołaną metodę umożliwia adres: dostęp do elementów członkowskich klasy, które odwołują się zarówno oryginalnego adresu i kopii. W przypadku wywołaną metodę zmiany elementu członkowskiego klasy, zmieniają się także do oryginalnego wystąpienia klasy w przypadku wywołania metody  
  
 Poniższy przykład ilustruje różnicy. Wartość `willIChange` pola wystąpienia klasy zostanie zmieniona przez wywołanie do metody `ClassTaker` ponieważ metoda używa adresu w parametrze, aby znaleźć określone pole wystąpienia klasy. `willIChange` Pola struktury wywołanie metody nie ulega zmianie przez wywołanie do metody `StructTaker` , ponieważ wartość argumentu jest kopią struktury, nie Kopiuj adresu. `StructTaker`zmiany kopii, a następnie skopiuj zostaną utracone podczas wywołania `StructTaker` zostało zakończone.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideObjects#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy](../../../csharp/programming-guide/classes-and-structs/classes.md)  
 [Struktury](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [Przekazywanie parametrów](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)
