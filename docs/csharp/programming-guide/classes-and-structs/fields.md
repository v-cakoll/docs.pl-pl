---
title: Pola — przewodnik programowania Języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- fields [C#]
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
ms.openlocfilehash: 46d4f77a4a490b2acdb5da20b9a477f27c38d410
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628244"
---
# <a name="fields-c-programming-guide"></a>Pola (Przewodnik programowania w języku C#)

*Pole* jest zmienną dowolnego typu, która jest zadeklarowana bezpośrednio w [klasie](../../language-reference/keywords/class.md) lub [strukturze](../../language-reference/builtin-types/struct.md). Pola są *członkami* ich typu zawierającego.

Klasa lub struktura może mieć pola wystąpienia, pola statyczne lub oba te pola. Pola wystąpienia są specyficzne dla wystąpienia typu. Jeśli masz klasę T, z polem wystąpienia F, można utworzyć dwa obiekty typu T i zmodyfikować wartość F w każdym obiekcie bez wpływu na wartość w innym obiekcie. Natomiast pole statyczne należy do samej klasy i jest współużytkowane przez wszystkie wystąpienia tej klasy. Dostęp do pola statycznego można uzyskać tylko przy użyciu nazwy klasy. Jeśli dostęp do pola statycznego przez nazwę wystąpienia, pojawi się błąd [cs0176](../../misc/cs0176.md) czas kompilacji.

Ogólnie rzecz biorąc należy używać pól tylko dla zmiennych, które mają dostępność prywatną lub chronioną. Dane, które klasa udostępnia kod klienta powinny być dostarczane za pośrednictwem [metod,](./methods.md) [właściwości](./properties.md)i [indeksatorów](../indexers/index.md). Za pomocą tych konstrukcji dla pośredniego dostępu do pól wewnętrznych, można chronić przed nieprawidłowymi wartościami wejściowymi. Pole prywatne, które przechowuje dane udostępniane przez właściwość publiczną, jest nazywane *magazynem zapasowym* lub *polem zapasowym*.

Pola zazwyczaj przechowywać dane, które muszą być dostępne dla więcej niż jednej metody klasy i muszą być przechowywane dłużej niż okres istnienia dowolnej pojedynczej metody. Na przykład klasa reprezentująca datę kalendarzową może mieć trzy pola całkowite: jedno dla miesiąca, jedno dla dnia i jedno dla roku. Zmienne, które nie są używane poza zakresem pojedynczej metody powinny być zadeklarowane jako *zmienne lokalne* w samej treści metody.

Pola są deklarowane w bloku klasy, określając poziom dostępu pola, po którym następuje typ pola, po którym następuje nazwa pola. Przykład:

[!code-csharp[csProgGuideObjects#61](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#61)]

Aby uzyskać dostęp do pola w obiekcie, dodaj okres po nazwie obiektu, `objectname.fieldname`po którym następuje nazwa pola, tak jak w programie . Przykład:

[!code-csharp[csProgGuideObjects#62](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#62)]

Pole można nadać wartości początkowej przy użyciu operatora przypisania, gdy pole jest zadeklarowane. Aby automatycznie przypisać `day` pole `"Monday"`do , na przykład, należy zadeklarować, `day` jak w poniższym przykładzie:

[!code-csharp[csProgGuideObjects#63](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#63)]

Pola są inicjowane bezpośrednio przed konstruktora dla wystąpienia obiektu jest wywoływana. Jeśli konstruktor przypisuje wartość pola, zastąpi dowolną wartość podaną podczas deklaracji pola. Aby uzyskać więcej informacji, zobacz [Korzystanie z konstruktorów](./using-constructors.md).

> [!NOTE]
> Iinicjator pola nie może odwoływać się do innych pól wystąpienia.

Pola mogą być oznaczone jako [publiczne,](../../language-reference/keywords/public.md) [prywatne,](../../language-reference/keywords/private.md) [chronione,](../../language-reference/keywords/protected.md) [wewnętrzne,](../../language-reference/keywords/internal.md) [chronione wewnętrzne](../../language-reference/keywords/protected-internal.md)lub [prywatne chronione.](../../language-reference/keywords/private-protected.md) Te modyfikatory dostępu definiują, w jaki sposób użytkownicy klasy mogą uzyskiwać dostęp do pól. Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](./access-modifiers.md).

Pole można opcjonalnie zadeklarować [jako statyczne.](../../language-reference/keywords/static.md) Dzięki temu pole jest dostępne dla wywoływania w dowolnym momencie, nawet jeśli nie istnieje żadne wystąpienie klasy. Aby uzyskać więcej informacji, zobacz [Klasy statyczne i elementy członkowskie klasy statycznej](./static-classes-and-static-class-members.md).

Pole można zadeklarować [tylko do odczytu](../../language-reference/keywords/readonly.md). Pole tylko do odczytu można przypisać tylko wartość podczas inicjowania lub w konstruktorze. Pole `static readonly` jest bardzo podobny do stałej, z tą różnicą, że kompilator C# nie ma dostępu do wartości statycznego pola tylko do odczytu w czasie kompilacji, tylko w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Stałe](./constants.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Klasy i struktury](./index.md)
- [Używanie konstruktorów](./using-constructors.md)
- [Dziedziczenie](./inheritance.md)
- [Modyfikatory dostępu](./access-modifiers.md)
- [Klasy abstrakcyjne i zapieczętowane oraz członkowie klas](./abstract-and-sealed-classes-and-class-members.md)
