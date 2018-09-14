---
title: 'Porady: różnica między przekazywaniem struktury a przekazywaniem odwołań do klas do metody (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], passing as method parameter
- passing parameters [C#], structs vs. classes
- methods [C#], passing classes vs. structs
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
ms.openlocfilehash: 670dfad3b9fc22709a0ad7f8048a0468bce54a2e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45594727"
---
# <a name="how-to-know-the-difference-between-passing-a-struct-and-passing-a-class-reference-to-a-method-c-programming-guide"></a>Porady: różnica między przekazywaniem struktury a przekazywaniem odwołań do klas do metody (Przewodnik programowania w języku C#)
W poniższym przykładzie pokazano, jak przekazywanie [struktury](../../../csharp/language-reference/keywords/struct.md) do metody różni się od przekazywanie [klasy](../../../csharp/language-reference/keywords/class.md) wystąpienia do metody. W tym przykładzie oba argumenty (wystąpienia struktury i klasy) są przekazywane przez wartość, a obie metody Zmień wartość pola jednego argumentu. Jednak wyniki z dwóch metod nie są takie same ponieważ przekazywana jest, jeśli przekazujesz struktury różni się od co to jest przekazywana, jeśli przekazujesz wystąpienia klasy.  
  
 Ponieważ struktura jest [typu wartości](../../../csharp/language-reference/keywords/value-types.md), gdy użytkownik [przekazać wartość do struktury](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md) do metody, metody odbiera i przetwarza kopię argumentu struktury. Metoda nie ma dostępu do oryginalnej struktury w przypadku wywoływania metody i w związku z tym nie można go zmienić w dowolny sposób. Metoda można zmienić tylko kopii.  
  
 To wystąpienie klasy [odwołania do typu](../../../csharp/language-reference/keywords/reference-types.md), nie jest typem wartości. Gdy [typ odwołania jest przekazywany przez wartość](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md) do metody, metoda otrzymuje kopię odwołanie do wystąpienia klasy. Oznacza to, że metoda otrzymuje kopię adres obiektu, nie kopia samego wystąpienia. Adres jest wystąpienie klasy w przypadku wywoływania metody z parametrem w metodzie wywoływanej ma kopię adres i oba adresy odnoszą się do tego samego obiektu. Ponieważ parametr zawiera tylko kopię adres, wywoływanej metody nie można zmienić adres wystąpienia klasy w przypadku wywołania metody. Jednak wywoływanej metody umożliwia adres: dostęp do elementów członkowskich klasy, odwołujące się do oryginalnego adresu i kopiowania. Jeśli wywoływanej metody zmieni składowej klasy, zmienia się również oryginalnego wystąpienia klasy, w przypadku wywoływania metody  
  
 Poniższy przykład ilustruje różnicę. Wartość `willIChange` pola wystąpienia klasy zostanie zmieniony przez wywołanie metody `ClassTaker` ponieważ metoda używa adresu w parametrze można znaleźć określonego pola wystąpienia klasy. `willIChange` Pola struktury w przypadku wywołania metody nie jest zmieniany przez wywołanie metody `StructTaker` ponieważ wartość argumentu jest kopią struktury, nie kopia jego adres. `StructTaker` zmiany kopii i kopii zostaną utracone podczas wywołania `StructTaker` zostało zakończone.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideObjects#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Klasy](../../../csharp/programming-guide/classes-and-structs/classes.md)  
- [Struktury](../../../csharp/programming-guide/classes-and-structs/structs.md)  
- [Przekazywanie parametrów](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)
