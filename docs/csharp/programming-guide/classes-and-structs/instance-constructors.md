---
title: "Konstruktory wystąpień (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: efb82128ffc27a7c065d2ba12bfc08396d3b5cf1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="instance-constructors-c-programming-guide"></a>Konstruktory wystąpień (Przewodnik programowania w języku C#)
Konstruktory wystąpień są używane do tworzenia i inicjowania żadnych zmiennych Członkowskich wystąpienia, korzystając z [nowe](../../../csharp/language-reference/keywords/new.md) wyrażenia do utworzenia obiektu [klasy](../../../csharp/language-reference/keywords/class.md). Zainicjować [statycznej](../../../csharp/language-reference/keywords/static.md) klasy lub statycznych zmiennych w klasie niestatyczna musi definiować konstruktora statycznego. Aby uzyskać więcej informacji, zobacz [konstruktory statyczne](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
 W poniższym przykładzie przedstawiono być konstruktorem wystąpień:  
  
 [!code-csharp[csProgGuideObjects#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_1.cs)]  
  
> [!NOTE]
>  Dla uzyskania przejrzystości ta klasa zawiera pola publiczne. Korzystanie z pola publiczne nie jest zalecanym rozwiązaniem programowania, ponieważ umożliwia on dowolnej metody w dowolnym miejscu w programie bez ograniczeń i niezweryfikowane dostępu do obiektu wewnętrznego działania. Elementy członkowskie danych zwykle powinny być prywatne i powinni mieć dostęp tylko za pośrednictwem metod i właściwości klasy.  
  
 Ten konstruktor wystąpienia jest wywoływana, gdy na podstawie obiektu `CoOrds` utworzyć klasy. Konstruktor, np. ten zestaw, który nie przyjmuje żadnych argumentów, jest nazywany *domyślnego konstruktora*. Jednak warto często zapewniają dodatkowe konstruktorów. Na przykład można dodać do konstruktora `CoOrds` klasy, która pozwala określić wartości początkowych elementów członkowskich danych:  
  
 [!code-csharp[csProgGuideObjects#76](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_2.cs)]  
  
 Dzięki temu `CoOrd` obiekty są tworzone z domyślnej lub określonej wartości początkowej, podobnie do następującej:  
  
 [!code-csharp[csProgGuideObjects#77](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_3.cs)]  
  
 Jeśli klasa nie ma konstruktora, domyślny konstruktor jest generowany automatycznie i zainicjować pola obiektu są używane wartości domyślne. Na przykład [int](../../../csharp/language-reference/keywords/int.md) jest ustawiana na 0. Aby uzyskać więcej informacji o wartościach domyślnych, zobacz [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md). W związku z tym ponieważ `CoOrds` klasy Konstruktor domyślny inicjuje wszystkie elementy członkowskie danych do zera, całkowicie usunąć bez zmiany, jak działa klasy. Pełny przykład przy użyciu wiele konstruktorów podano w przykładzie 1 w dalszej części tego tematu, a przykład automatycznie wygenerowany Konstruktor podano w przykładzie 2.  
  
 Konstruktory wystąpień mogą służyć do wywołania konstruktorów wystąpienia klas podstawowych. Konstruktor klasy można wywołać konstruktora klasy podstawowej za pomocą inicjatora, w następujący sposób:  
  
 [!code-csharp[csProgGuideObjects#78](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_4.cs)]  
  
 W tym przykładzie `Circle` klasy przekazuje wartość reprezentuje konstruktora udostępniane przez usługi radius i wysokość `Shape` z którego `Circle` pochodzi. Pełny przykład za pomocą `Shape` i `Circle` pojawia się w tym temacie jako przykład 3.  
  
## <a name="example-1"></a>Przykład 1  
 W poniższym przykładzie pokazano klasę z klasy dwa konstruktory, bez argumentów i jeden z dwóch argumentów.  
  
 [!code-csharp[csProgGuideObjects#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_5.cs)]  
  
## <a name="example-2"></a>Przykład 2  
 W tym przykładzie klasa `Person` nie ma żadnych konstruktorów, w których przypadku domyślny konstruktor jest teraz udostępniana automatycznie i pola są inicjowane z wartościami domyślnymi.  
  
 [!code-csharp[csProgGuideObjects#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_6.cs)]  
  
 Zwróć uwagę, że wartość domyślna `age` jest `0` i wartość domyślną `name` jest `null`. Aby uzyskać więcej informacji o wartościach domyślnych, zobacz [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md).  
  
## <a name="example-3"></a>Przykład 3  
 W poniższym przykładzie pokazano, za pomocą inicjatora klasy podstawowej. `Circle` Klasa pochodzi od klasy ogólnej `Shape`i `Cylinder` jest pochodną klasy `Circle` klasy. Konstruktor dla każdej klasy pochodnej korzysta z inicjatora swojej klasy podstawowej.  
  
 [!code-csharp[csProgGuideObjects#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_7.cs)]  
  
 Więcej przykładów na temat wywoływania konstruktorów klasy podstawowej, zobacz [wirtualnego](../../../csharp/language-reference/keywords/virtual.md), [zastąpienia](../../../csharp/language-reference/keywords/override.md), i [podstawowej](../../../csharp/language-reference/keywords/base.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [statyczne](../../../csharp/language-reference/keywords/static.md)
