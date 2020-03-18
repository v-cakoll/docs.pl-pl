---
title: Konstruktory prywatne — przewodnik programowania c#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 2f8b93fbeb7c2996f3e2683fe86f159fbfa61a92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705447"
---
# <a name="private-constructors-c-programming-guide"></a>Konstruktory prywatne (Przewodnik programowania w języku C#)
Konstruktora prywatnego jest konstruktorem instancji specjalne. Zazwyczaj jest używany w klasach, które zawierają tylko elementy członkowskie statyczne. Jeśli klasa ma jeden lub więcej prywatnych konstruktorów i nie konstruktorów publicznych, inne klasy (z wyjątkiem klas zagnieżdżonych) nie można utworzyć wystąpienia tej klasy. Przykład:  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 Deklaracja pustego konstruktora uniemożliwia automatyczne generowanie konstruktora bezparametrowego. Należy zauważyć, że jeśli nie używasz modyfikatordostępu z konstruktorem nadal będzie prywatny domyślnie. Jednak [prywatny](../../language-reference/keywords/private.md) modyfikator jest zwykle używany jawnie, aby wyjaśnić, że klasa nie może być tworzone.  
  
 Konstruktory prywatne są używane do zapobiegania tworzeniu wystąpień klasy, gdy nie <xref:System.Math> ma pól lub metod wystąpienia, takich jak klasa lub gdy metoda jest wywoływana w celu uzyskania wystąpienia klasy. Jeśli wszystkie metody w klasie są statyczne, należy rozważyć uczynienie pełnej klasy statyczne. Aby uzyskać więcej informacji, zobacz [Klasy statyczne i Elementy członkowskie klasy statycznej](./static-classes-and-static-class-members.md).  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono przykład klasy przy użyciu konstruktora prywatnego.  
  
 [!code-csharp[csProgGuideObjects#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#12)]  
  
 Należy zauważyć, że jeśli odkomentować następującą instrukcję z przykładu, wygeneruje błąd, ponieważ konstruktor jest niedostępny ze względu na jego poziom ochrony:  
  
 [!code-csharp[csProgGuideObjects#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#13)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [Konstruktory prywatne](~/_csharplang/spec/classes.md#private-constructors) w [specyfikacji języka Języka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Klasy i struktury](./index.md)
- [Konstruktory](./constructors.md)
- [Finalizatory](./destructors.md)
- [Prywatny](../../language-reference/keywords/private.md)
- [Publicznego](../../language-reference/keywords/public.md)
