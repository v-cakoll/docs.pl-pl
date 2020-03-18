---
title: Konstruktory instancji — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: 621b8ca7510b0b9916c9c46f201ff77402c3c655
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75964738"
---
# <a name="instance-constructors-c-programming-guide"></a>Konstruktory wystąpień (Przewodnik programowania w języku C#)

Konstruktory wystąpienia są używane do tworzenia i inicjowania zmiennych członkowskich wystąpienia, gdy nowe [wyrażenie](../../language-reference/operators/new-operator.md) służy do tworzenia obiektu [klasy](../../language-reference/keywords/class.md). Aby zainicjować klasę [statyczną](../../language-reference/keywords/static.md) lub zmienne statyczne w klasie niestatycznej, należy zdefiniować konstruktora statycznego. Aby uzyskać więcej informacji, zobacz [Konstruktora statyczne](./static-constructors.md).  
  
 W poniższym przykładzie przedstawiono konstruktora wystąpienia:  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
> Dla jasności ta klasa zawiera pola publiczne. Korzystanie z pól publicznych nie jest zalecaną praktyką programowania, ponieważ umożliwia dowolną metodę w dowolnym miejscu w programie nieograniczony i niezweryfikowany dostęp do wewnętrznego działania obiektu. Elementy członkowskie danych zazwyczaj powinny być prywatne i powinny być dostępne tylko za pośrednictwem metod i właściwości klasy.  
  
 To wystąpienie konstruktora jest wywoływana `Coords` za każdym razem, gdy obiekt oparty na klasie jest tworzony. Konstruktora, jak ten, który nie przyjmuje żadnych argumentów, jest nazywany *konstruktorem bezparametrów*. Jednak często jest przydatne, aby zapewnić dodatkowe konstruktory. Na przykład możemy dodać konstruktora do `Coords` klasy, która pozwala nam określić początkowe wartości dla elementów członkowskich danych:  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 Dzięki `Coords` temu obiekty mogą być tworzone z domyślnymi lub określonymi wartościami początkowymi, takimi jak ten:  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 Jeśli klasa nie ma konstruktora, konstruktor bezparametrów jest generowany automatycznie, a wartości domyślne są używane do inicjowania pól obiektów. Na przykład [int](../../language-reference/builtin-types/integral-numeric-types.md) jest inicjowany do 0. Aby uzyskać informacje o wartościach domyślnych typu, zobacz [Wartości domyślne typów Języka C#](../../language-reference/builtin-types/default-values.md). W związku `Coords` z tym ponieważ klasy konstruktora bez parametrów inicjuje wszystkie elementy członkowskie danych do zera, można usunąć całkowicie bez zmiany sposobu działania klasy. Pełny przykład przy użyciu wielu konstruktorów znajduje się w przykładzie 1 w dalszej części tego tematu, a przykład automatycznie generowanekonstruktora znajduje się w przykładzie 2.  
  
 Konstruktorów wystąpienia można również wywołać konstruktory wystąpienia klas podstawowych. Konstruktor klasy może wywołać konstruktora klasy podstawowej za pośrednictwem inicjatora, w następujący sposób:  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 W tym przykładzie `Circle` klasa przekazuje wartości reprezentujące promień i `Shape` wysokość `Circle` do konstruktora dostarczonego przez którego pochodzi. Pełny przykład `Shape` przy `Circle` użyciu i pojawia się w tym temacie jako przykład 3.  
  
## <a name="example-1"></a>Przykład 1  
 W poniższym przykładzie przedstawiono klasę z dwoma konstruktorami klas, jeden bez argumentów i jeden z dwoma argumentami.  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## <a name="example-2"></a>Przykład 2  
 W tym przykładzie `Person` klasa nie ma żadnych konstruktorów, w którym to przypadku konstruktor bezparametrów jest automatycznie dostarczany, a pola są inicjowane do ich wartości domyślnych.  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 Należy zauważyć, że `age` `0` wartością domyślną `name` `null`jest i wartość domyślna jest .
  
## <a name="example-3"></a>Przykład 3  
 W poniższym przykładzie przedstawiono przy użyciu inicjatora klasy podstawowej. Klasa `Circle` jest pochodną klasy `Shape`ogólnej, `Cylinder` a klasa jest `Circle` pochodną klasy. Konstruktor na każdej klasy pochodnej używa jego inicjatorklasy podstawowej.  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 Aby uzyskać więcej przykładów na wywoływanie konstruktorów klasy podstawowej, zobacz [wirtualne](../../language-reference/keywords/virtual.md), [zastąpić](../../language-reference/keywords/override.md)i [base](../../language-reference/keywords/base.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Klasy i struktury](./index.md)
- [Konstruktory](./constructors.md)
- [Finalizatory](./destructors.md)
- [Statyczne](../../language-reference/keywords/static.md)
