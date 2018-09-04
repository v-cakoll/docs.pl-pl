---
title: Konstruktory wystąpień (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: cd7105ec61e5c878dc148c30b27706b1eda3ae72
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530382"
---
# <a name="instance-constructors-c-programming-guide"></a>Konstruktory wystąpień (Przewodnik programowania w języku C#)
Konstruktory wystąpień są używane do Utwórz i zainicjuj wszystkie zmienne elementu członkowskiego wystąpienia, gdy używasz [nowe](../../../csharp/language-reference/keywords/new.md) wyrażenie do utworzenia obiektu [klasy](../../../csharp/language-reference/keywords/class.md). Można zainicjować [statyczne](../../../csharp/language-reference/keywords/static.md) klasy lub statycznych zmiennych w niestatycznych klas, należy zdefiniować Konstruktor statyczny. Aby uzyskać więcej informacji, zobacz [konstruktorów statycznych](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
 Poniższy przykład pokazuje konstruktora wystąpień:  
  
 [!code-csharp[csProgGuideObjects#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_1.cs)]  
  
> [!NOTE]
>  W celu uściślenia ta klasa zawiera pola publiczne. Użycie pola publiczne nie jest zalecana praktyka programowania, ponieważ zezwala ona na dowolną metodę w dowolnym miejscu w programie bez ograniczeń i niezweryfikowane dostęp do obiektu wewnętrznego działania. Elementy członkowskie danych zwykle powinny być prywatne i powinni mieć dostęp tylko za pośrednictwem metod i właściwości klasy.  
  
 Ten konstruktor wystąpienia jest wywoływane, gdy na podstawie obiektu `CoOrds` klasa jest tworzona. Konstruktor, takie jak nazywa się ten zestaw, który nie przyjmuje żadnych argumentów, *domyślnego konstruktora*. Jednak często jest przydatne zapewnić dodatkowe konstruktorów. Na przykład można dodać do konstruktora `CoOrds` klasę, która pozwala określić wartości początkowe dla składowych danych:  
  
 [!code-csharp[csProgGuideObjects#76](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_2.cs)]  
  
 Dzięki temu `CoOrd` obiekty są tworzone z domyślne lub określone wartości początkowej, podobnie do następującego:  
  
 [!code-csharp[csProgGuideObjects#77](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_3.cs)]  
  
 Jeśli klasa nie ma konstruktora, Konstruktor domyślny jest generowany automatycznie i wartości domyślne są stosowane do inicjalizacji pola obiektu. Na przykład [int](../../../csharp/language-reference/keywords/int.md) jest inicjowana wartością 0. Aby uzyskać więcej informacji na temat wartości domyślnych, zobacz [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md). W związku z tym ponieważ `CoOrds` Konstruktor domyślny klasy inicjuje wszystkie elementy członkowskie danych do zera, można je usunąć w całkowicie bez konieczności zmieniania sposobu działania klasy. Pełny przykład za pomocą wiele konstruktorów podano w przykładzie 1 w dalszej części tego tematu, a przykład automatycznie generowany Konstruktor jest podawany jako przykład 2.  
  
 Konstruktory wystąpień może również wywoływać konstruktorów wystąpienia klas bazowych. Konstruktor klasy można wywołać konstruktora klasy podstawowej za pomocą inicjatora, w następujący sposób:  
  
 [!code-csharp[csProgGuideObjects#78](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_4.cs)]  
  
 W tym przykładzie `Circle` klasy przekazuje wartość reprezentuje konstruktora udostępniane przez usługi radius i wysokość `Shape` z którego `Circle` pochodzi. Pełny przykład za pomocą `Shape` i `Circle` pojawia się w tym temacie jako przykład 3.  
  
## <a name="example-1"></a>Przykład 1  
 W poniższym przykładzie pokazano klasę z klasy dwa konstruktory, bez argumentów i jeden z dwóch argumentów.  
  
 [!code-csharp[csProgGuideObjects#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_5.cs)]  
  
## <a name="example-2"></a>Przykład 2  
 W tym przykładzie klasa `Person` nie ma żadnych konstruktorów, w których przypadku domyślnego konstruktora jest dostarczana automatycznie, a pola są inicjowane do wartości domyślnych.  
  
 [!code-csharp[csProgGuideObjects#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_6.cs)]  
  
 Należy zauważyć, że wartość domyślna `age` jest `0` i wartość domyślną `name` jest `null`. Aby uzyskać więcej informacji na temat wartości domyślnych, zobacz [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md).  
  
## <a name="example-3"></a>Przykład 3  
 Poniższy przykład pokazuje, za pomocą inicjatora klasy bazowej. `Circle` Klasa pochodzi od klasy ogólnej `Shape`i `Cylinder` klasa pochodzi od `Circle` klasy. Konstruktor w każdej klasie pochodnej korzysta z inicjatora swojej klasy bazowej.  
  
 [!code-csharp[csProgGuideObjects#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_7.cs)]  
  
 Aby uzyskać więcej przykładów na wywoływaniu Konstruktory klasy bazowej, zobacz [wirtualnego](../../../csharp/language-reference/keywords/virtual.md), [zastąpienia](../../../csharp/language-reference/keywords/override.md), i [podstawowy](../../../csharp/language-reference/keywords/base.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
- [static](../../../csharp/language-reference/keywords/static.md)
