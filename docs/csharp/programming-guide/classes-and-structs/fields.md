---
title: Fields C# — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- fields [C#]
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
ms.openlocfilehash: c07f058eb081fa1c9e0a3756959570d1ba9e47f6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924517"
---
# <a name="fields-c-programming-guide"></a>Pola (Przewodnik programowania w języku C#)
*Pole* jest zmienną dowolnego typu, który jest zadeklarowany bezpośrednio w [klasie](../../language-reference/keywords/class.md) lub [strukturze](../../language-reference/keywords/struct.md). Pola są *elementami członkowskimi* typu zawierającego.  
  
 Klasa lub struktura może mieć pola wystąpienia lub pola statyczne lub oba te elementy. Pola wystąpienia są specyficzne dla wystąpienia typu. Jeśli masz klasę T z polem wystąpienia F, możesz utworzyć dwa obiekty typu T i zmodyfikować wartość F w każdym obiekcie bez wpływu na wartość w innym obiekcie. Z kolei pole statyczne należy do samej klasy i jest współużytkowane przez wszystkie wystąpienia tej klasy. Zmiany wprowadzone z wystąpienia A będą widoczne natychmiast w wystąpieniach B i C, jeśli uzyskują dostęp do pola.  
  
 Ogólnie rzecz biorąc, należy używać pól tylko dla zmiennych, które mają prywatną lub chronioną dostępność. Dane, które Klasa uwidacznia do kodu klienta, powinny być udostępniane za poorednictwem [metod](./methods.md), [Właściwości](./properties.md) i [indeksatorów](../indexers/index.md). Używając tych konstrukcji do pośredniego dostępu do pól wewnętrznych, można zabezpieczyć się przed nieprawidłowymi wartościami wejściowymi. Prywatne pole, które przechowuje dane uwidaczniane przez właściwość publiczną, nazywa się *magazynem zapasowym* lub *polem zapasowym*.  
  
 Pola zwykle przechowują dane, które muszą być dostępne dla więcej niż jednej metody klasy i muszą być przechowywane dłużej niż okres istnienia dowolnej pojedynczej metody. Na przykład Klasa, która reprezentuje datę kalendarza, może mieć trzy pola całkowite: jeden dla miesiąca, jeden dla danego dnia i jeden dla roku. Zmienne, które nie są używane poza zakresem pojedynczej metody, powinny być deklarowane jako *zmienne lokalne* w samej treści metody.  
  
 Pola są zadeklarowane w bloku klasy przez określenie poziomu dostępu pola, po którym następuje typ pola, po którym następuje nazwa pola. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#61](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#61)]  
  
 Aby uzyskać dostęp do pola w obiekcie, Dodaj kropkę po nazwie obiektu, a następnie nazwę pola, jak w `objectname.fieldname`. Przykład:  
  
 [!code-csharp[csProgGuideObjects#62](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#62)]  
  
 W polu można uzyskać wartość początkową przy użyciu operatora przypisania, gdy pole jest zadeklarowane. Aby automatycznie przypisać to `day` `"Monday"`pole, na przykład, należy zadeklarować `day` jak w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideObjects#63](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#63)]  
  
 Pola są inicjowane natychmiast przed wywołaniem konstruktora dla wystąpienia obiektu. Jeśli Konstruktor przypisze wartość pola, spowoduje to zastąpienie dowolnej wartości podaną podczas deklaracji pola. Aby uzyskać więcej informacji, zobacz [Używanie konstruktorów](./using-constructors.md).  
  
> [!NOTE]
> Inicjator pola nie może odwoływać się do innych pól wystąpień.  
  
 Pola mogą być oznaczone jako [publiczne](../../language-reference/keywords/public.md), [prywatne](../../language-reference/keywords/private.md), [chronione](../../language-reference/keywords/protected.md), [wewnętrzne](../../language-reference/keywords/internal.md), [chronione wewnętrznie](../../language-reference/keywords/protected-internal.md) lub [chronione prywatnie](../../language-reference/keywords/private-protected.md). Te Modyfikatory dostępu definiują sposób, w jaki użytkownicy klasy mogą uzyskać dostęp do pól. Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](./access-modifiers.md).  
  
 Opcjonalnie można zadeklarować pole jako [static](../../language-reference/keywords/static.md). To sprawia, że pole jest dostępne dla wywoływania w dowolnym momencie, nawet jeśli nie istnieje żadne wystąpienie klasy. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klas](./static-classes-and-static-class-members.md).  
  
 Pole można zadeklarować jako [tylko do odczytu](../../language-reference/keywords/readonly.md). W polu tylko do odczytu można przypisać wartość tylko podczas inicjowania lub w konstruktorze. Pole jest bardzo podobne do stałej, z tą różnicą, C# że kompilator nie ma dostępu do wartości statycznego pola tylko do odczytu w czasie kompilacji, tylko w czasie wykonywania. `static readonly` Aby uzyskać więcej informacji, zobacz [stałe](./constants.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](./index.md)
- [Używanie konstruktorów](./using-constructors.md)
- [Dziedziczenie](./inheritance.md)
- [Modyfikatory dostępu](./access-modifiers.md)
- [Klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klas](./abstract-and-sealed-classes-and-class-members.md)
