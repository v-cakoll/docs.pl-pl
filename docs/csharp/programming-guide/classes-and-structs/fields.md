---
title: Pola (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- fields [C#]
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
ms.openlocfilehash: 708bd4e768e795397624bcac6e5bc2594bff93f5
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44139257"
---
# <a name="fields-c-programming-guide"></a>Pola (Przewodnik programowania w języku C#)
A *pola* jest zmienna dowolnego typu, który jest zadeklarowany bezpośrednio w [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md). Pola są *członków* z ich typem zawierającym.  
  
 Klasa lub struktura może mieć wystąpienia pól pola statyczne i/lub. Pola wystąpienia są specyficzne dla wystąpienia typu. Jeśli klasa T, za pomocą pola wystąpienia F, można utworzyć dwa obiekty typu T i modyfikować wartość F w każdym obiekcie bez wpływu na wartość innego obiektu. Z kolei pole statyczne należy do samej klasy i jest współużytkowana przez wszystkie wystąpienia tej klasy. Zmiany wprowadzone w wystąpieniu będzie widoczny od razu do wystąpień B i C Jeśli uzyskują oni dostęp do pola.  
  
 Ogólnie rzecz biorąc należy użyć pola tylko do zmiennych, które mają prywatnych lub chronionych ułatwień dostępu. Dane, które klasa udostępnia kodom klienta powinny być dostarczane za pośrednictwem [metody](../../../csharp/programming-guide/classes-and-structs/methods.md), [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md) i [indeksatory](../../../csharp/programming-guide/indexers/index.md). Za pomocą te konstrukcje, aby uzyskać bezpośredni dostęp do wewnętrznych pól, można zabezpieczyć się przed nieprawidłowe wartości wejściowe. Nosi nazwę pola prywatnego, która przechowuje dane udostępniane przez właściwość publiczna *magazyn zapasowy* lub *pole zapasowe*.  
  
 W polach zazwyczaj przechowywane dane, które muszą być dostępne dla więcej niż jednej metody klasy i muszą być przechowywane przez czas dłuższy niż okres istnienia dowolnej pojedynczej metody. Na przykład klasa, która reprezentuje datę w kalendarzu może mieć trzy pola liczb całkowitych: jeden dla miesiąca: jeden dla danego dnia i jeden dla roku. Zmienne, które nie są używane poza zakresem pojedynczej metody powinny być deklarowane jako *zmienne lokalne* w metodzie treści sam.  
  
 Pola są deklarowane w bloku klasy, określając poziom dostępu, następuje pole typu pola, a następnie nazwę pola. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#61](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_1.cs)]  
  
 Aby uzyskać dostęp do pola w obiekcie, dodaj kropkę po nazwę obiektu, a następnie nazwę pola, podobnie jak w `objectname.fieldname`. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#62](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_2.cs)]  
  
 Pola można podać wartości początkowej za pomocą operatora przypisania, gdy pole jest zadeklarowane. Aby automatycznie przypisać `day` pole `"Monday"`, na przykład może deklarować `day` jak w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideObjects#63](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_3.cs)]  
  
 Pola są inicjowane od razu, przed wywołaniem konstruktora wystąpienia obiektu. Jeśli Konstruktor przypisuje wartości pola, zastąpi dowolną wartość podana podczas deklarację pola. Aby uzyskać więcej informacji, zobacz [korzystanie z konstruktorów](../../../csharp/programming-guide/classes-and-structs/using-constructors.md).  
  
> [!NOTE]
>  Inicjator pola nie może odwoływać się do innych pól wystąpienia.  
  
 Pola może być oznaczona jako [publicznych](../../../csharp/language-reference/keywords/public.md), [prywatnej](../../../csharp/language-reference/keywords/private.md), [chronione](../../../csharp/language-reference/keywords/protected.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), [chronionych wewnętrznych](../../../csharp/language-reference/keywords/protected-internal.md) lub [prywatny chroniony](../../../csharp/language-reference/keywords/private-protected.md). Następujące modyfikatory dostępu definiują, jak użytkownicy klasy mogą uzyskać dostęp do pól. Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).   
  
 Opcjonalnie można zadeklarować pole [statyczne](../../../csharp/language-reference/keywords/static.md). To udostępnienie pole dotyczące obiektów wywołujących w dowolnym momencie, nawet jeśli istnieje żadne wystąpienie klasy. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Pola mogą być deklarowane [tylko do odczytu](../../../csharp/language-reference/keywords/readonly.md). Pola tylko do odczytu można przypisać tylko wartość podczas inicjowania lub w konstruktorze. A `static readonly` pole jest bardzo podobne do stałą, z tą różnicą, że kompilator języka C# nie ma dostępu do wartości pola statycznego tylko do odczytu w czasie kompilacji, tylko w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [stałe](../../../csharp/programming-guide/classes-and-structs/constants.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Używanie konstruktorów](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
- [Dziedziczenie](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
- [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [Klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klas](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
