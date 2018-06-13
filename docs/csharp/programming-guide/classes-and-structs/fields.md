---
title: Pola (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- fields [C#]
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
ms.openlocfilehash: 31073772fd42244167b5e68959ebb373ec759025
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33314330"
---
# <a name="fields-c-programming-guide"></a>Pola (Przewodnik programowania w języku C#)
A *pola* jest zmienną dowolnego typu, która jest zadeklarowana jako bezpośrednio w [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md). Pola są *członków* ich typu zawierającego.  
  
 Klasy lub struktury mogą mieć pól wystąpień pola statyczne i/lub. Pola wystąpienia są specyficzne dla wystąpienia typu. Klasa T, z polem wystąpienia F można utworzyć dwa obiekty typu T i zmodyfikuj wartość F w każdym obiekcie bez wpływu na wartość w innym obiekcie. Z kolei pola statycznego należy do samej klasy i jest współdzielona przez wszystkie wystąpienia tej klasy. Zmiany wprowadzone w wystąpieniu będzie widoczny od razu do wystąpień B i C Jeśli uzyskują oni dostęp do pola.  
  
 Ogólnie rzecz biorąc pól należy używać tylko w przypadku zmiennych, które mają dostępności prywatne lub chronione. Dane, które udostępnia klasy do kodu klienta powinny być dostarczane za pośrednictwem [metody](../../../csharp/programming-guide/classes-and-structs/methods.md), [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md) i [indeksatory](../../../csharp/programming-guide/indexers/index.md). Za pomocą tych konstrukcji uzyskać bezpośredni dostęp do wewnętrznych pól, można zabezpieczyć się przed nieprawidłowe wartości wejściowe. Pole prywatne, która przechowuje dane uwidaczniane przez właściwość publiczna jest nazywany *magazynu zapasowego* lub *pole zapasowe*.  
  
 Pola zwykle przechowywać dane, które muszą być dostępne dla więcej niż jednej metody klasy i muszą być przechowywane przez czas dłuższy niż okres istnienia żadnych pojedynczej metody. Na przykład klasa, która reprezentuje datę w kalendarzu może mieć trzy pola Liczba całkowita: jeden dla jeden dzień, miesiąc i jednego roku. Zmienne, które nie są używane poza zakresem pojedynczej metody powinien być zadeklarowany jako *zmiennych lokalnych* w metodzie body samej siebie.  
  
 Pola są zadeklarowane w bloku klasy, określając poziom dostępu do pola, następuje typ pola, a po niej nazwę pola. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#61](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_1.cs)]  
  
 Do uzyskania dostępu do pola w obiekcie, Dodaj okres, po nazwie obiektu, oraz nazwę pola, podobnie jak w `objectname.fieldname`. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#62](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_2.cs)]  
  
 Pole można podać wartości początkowej przy użyciu operatora przypisania, jeśli pole jest zadeklarowany. Automatyczne przypisywanie `day` do `"Monday"`, na przykład czy zadeklarować `day` jak w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideObjects#63](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_3.cs)]  
  
 Pola są inicjowane od razu, przed wywołaniem konstruktora wystąpienia obiektu. Konstruktor przypisuje wartość pola, zastąpi dowolną wartość podana podczas deklarację pola. Aby uzyskać więcej informacji, zobacz [za pomocą konstruktorów](../../../csharp/programming-guide/classes-and-structs/using-constructors.md).  
  
> [!NOTE]
>  Inicjator pola nie może odwoływać się do innych pól wystąpień.  
  
 Pola może być oznaczony jako [publicznego](../../../csharp/language-reference/keywords/public.md), [prywatnej](../../../csharp/language-reference/keywords/private.md), [chronione](../../../csharp/language-reference/keywords/protected.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), [chronionych wewnętrznych](../../../csharp/language-reference/keywords/protected-internal.md) lub [prywatne chronione](../../../csharp/language-reference/keywords/private-protected.md). Te modyfikatorów dostępu zdefiniuj, jak użytkownicy klasy mają dostęp do pola. Aby uzyskać więcej informacji, zobacz [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Opcjonalnie można zadeklarować jako pole [statycznych](../../../csharp/language-reference/keywords/static.md). Dzięki temu pole dostępne wywołań w dowolnym momencie, nawet jeśli nie ma wystąpień klasy. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statycznych elementów członkowskich klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Pola, które mogą być deklarowane [tylko do odczytu](../../../csharp/language-reference/keywords/readonly.md). Pola tylko do odczytu można przypisać tylko wartość podczas inicjowania lub w konstruktorze. A `static``readonly` pole jest bardzo podobny do wartości stałej z tą różnicą, że kompilator języka C# nie ma dostępu do wartości pola statycznego tylko do odczytu w czasie kompilacji, tylko w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [stałe](../../../csharp/programming-guide/classes-and-structs/constants.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Używanie konstruktorów](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
 [Dziedziczenie](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [Klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klas](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
