---
title: Konstruktory wystąpień C# — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: ee3cc30334154ef8aae6d7d26286463c537ff3dd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714810"
---
# <a name="instance-constructors-c-programming-guide"></a>Konstruktory wystąpień (Przewodnik programowania w języku C#)

Konstruktory wystąpień są używane do tworzenia i inicjowania wszelkich zmiennych składowych wystąpienia podczas używania [nowego](../../language-reference/operators/new-operator.md) wyrażenia do tworzenia obiektu [klasy](../../language-reference/keywords/class.md). Aby zainicjować klasę [statyczną](../../language-reference/keywords/static.md) lub zmienne statyczne w klasie niestatycznej, należy zdefiniować Konstruktor statyczny. Aby uzyskać więcej informacji, zobacz [statyczne konstruktory](./static-constructors.md).  
  
 Poniższy przykład pokazuje Konstruktor wystąpienia:  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
> Dla jasności Ta klasa zawiera pola publiczne. Korzystanie z pól publicznych nie jest zalecanym sposobem programowania, ponieważ umożliwia jakąkolwiek metodę w dowolnym miejscu w programie bez ograniczeń i niezweryfikowany dostęp do wewnętrznych zadań roboczych obiektu. Elementy członkowskie danych powinny być ogólnie prywatne i powinny być dostępne tylko za poorednictwem metod i właściwości klasy.  
  
 Ten konstruktor wystąpienia jest wywoływany za każdym razem, gdy tworzony jest obiekt oparty na klasie `Coords`. Konstruktor podobny do tego, który nie przyjmuje argumentów, jest nazywany *konstruktorem bez parametrów*. Jednak często przydatne jest zapewnienie dodatkowych konstruktorów. Na przykład możemy dodać konstruktora do klasy `Coords`, która umożliwia określenie wartości początkowych elementów członkowskich danych:  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 Pozwala to na tworzenie `Coords` obiektów z domyślnymi lub określonymi wartościami początkowymi, takimi jak:  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 Jeśli Klasa nie ma konstruktora, zostaje automatycznie wygenerowany Konstruktor bez parametrów, a wartości domyślne są używane do inicjowania pól obiektu. Na przykład liczba [całkowita](../../language-reference/builtin-types/integral-numeric-types.md) jest inicjowana do wartości 0. Aby uzyskać więcej informacji na temat wartości domyślnych, zobacz [tabela wartości domyślnych](../../language-reference/keywords/default-values-table.md). W związku z tym, ponieważ Konstruktor bez parametrów klasy `Coords` inicjuje wszystkie elementy członkowskie danych jako zero, można go usunąć całkowicie bez zmiany sposobu działania klasy. Kompletny przykład z użyciem wielu konstruktorów znajduje się w przykładzie 1 w dalszej części tego tematu, a przykład wygenerowanego automatycznie konstruktora jest dostępny w przykładzie 2.  
  
 Konstruktorów wystąpień można także używać do wywoływania konstruktorów wystąpień klas bazowych. Konstruktor klasy może wywoływać konstruktora klasy podstawowej za pomocą inicjatora w następujący sposób:  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 W tym przykładzie Klasa `Circle` przekazuje wartości reprezentujące promień i wysokość do konstruktora dostarczonego przez `Shape`, z którego `Circle` pochodzi. Pełny przykład przy użyciu `Shape` i `Circle` pojawia się w tym temacie jako przykład 3.  
  
## <a name="example-1"></a>Przykład 1  
 Poniższy przykład ilustruje klasę z dwoma konstruktorami klas, jeden bez argumentów i jeden z dwoma argumentami.  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## <a name="example-2"></a>Przykład 2  
 W tym przykładzie Klasa `Person` nie ma żadnych konstruktorów, w tym przypadku jest automatycznie dostarczany Konstruktor bez parametrów i pola są inicjowane do ich wartości domyślnych.  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 Zwróć uwagę, że wartość domyślna `age` jest `0` i wartość domyślna `name` jest `null`. Aby uzyskać więcej informacji na temat wartości domyślnych, zobacz [tabela wartości domyślnych](../../language-reference/keywords/default-values-table.md).  
  
## <a name="example-3"></a>Przykład 3  
 Poniższy przykład ilustruje użycie inicjatora klasy bazowej. Klasa `Circle` jest pochodną klasy ogólnej `Shape`, a Klasa `Cylinder` jest pochodną klasy `Circle`. Konstruktor dla każdej klasy pochodnej używa jej inicjatora klasy bazowej.  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 Aby uzyskać więcej przykładów dotyczących wywoływania konstruktorów klasy bazowej, zobacz [Virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md)i [Base](../../language-reference/keywords/base.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](./index.md)
- [Konstruktory](./constructors.md)
- [Finalizatory](./destructors.md)
- [static](../../language-reference/keywords/static.md)
