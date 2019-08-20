---
title: Konstruktory prywatne C# — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: faa5132845a2d463d3b7d74dc0e0cce21dca61aa
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596215"
---
# <a name="private-constructors-c-programming-guide"></a>Konstruktory prywatne (Przewodnik programowania w języku C#)
Konstruktor prywatny jest specjalnym konstruktorem wystąpień. Jest on zazwyczaj używany w klasach, które zawierają tylko statyczne elementy członkowskie. Jeśli klasa ma jeden lub więcej konstruktorów prywatnych i nie ma konstruktorów publicznych, inne klasy (poza klasami zagnieżdżonymi) nie mogą tworzyć wystąpień tej klasy. Przykład:  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 Deklaracja pustego konstruktora uniemożliwia automatyczne generowanie konstruktora bez parametrów. Należy pamiętać, że jeśli nie używasz modyfikatora dostępu z konstruktorem, będzie on nadal domyślnie prywatny. Jednak modyfikator [prywatny](../../language-reference/keywords/private.md) jest zwykle używany jawnie, aby wyczyścił, że nie można utworzyć wystąpienia klasy.  
  
 Konstruktory prywatne są używane do zapobiegania tworzeniu wystąpień klasy w przypadku braku pól lub metod wystąpienia, takich jak <xref:System.Math> Klasa, lub gdy wywoływana jest metoda w celu uzyskania wystąpienia klasy. Jeśli wszystkie metody w klasie są statyczne, należy rozważyć uczynienie kompletnej klasy statycznej. Aby uzyskać więcej informacji [, zobacz klasy statyczne i statyczne elementy członkowskie klas](./static-classes-and-static-class-members.md).  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się przykład klasy korzystającej z konstruktora prywatnego.  
  
 [!code-csharp[csProgGuideObjects#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#12)]  
  
 Zwróć uwagę, że jeśli dodasz komentarz z następującej instrukcji z przykładu, zostanie wygenerowany błąd, ponieważ Konstruktor jest niedostępny z powodu swojego poziomu ochrony:  
  
 [!code-csharp[csProgGuideObjects#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#13)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [prywatne konstruktory](~/_csharplang/spec/classes.md#private-constructors) w [ C# specyfikacji języka](../../language-reference/language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](./index.md)
- [Konstruktory](./constructors.md)
- [Finalizatory](./destructors.md)
- [private](../../language-reference/keywords/private.md)
- [public](../../language-reference/keywords/public.md)
