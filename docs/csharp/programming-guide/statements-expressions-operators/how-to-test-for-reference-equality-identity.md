---
title: 'Porady: testowanie równości odwołań (tożsamości) (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: d48c2cab7100d8227b33ee0eeefb825dd81a5f88
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43876651"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a>Porady: testowanie równości odwołań (tożsamości) (Przewodnik programowania w języku C#)
Nie masz implementuje żadnej logiki niestandardowej obsługuje porównania równości odwołań w typy. Ta funkcjonalność jest dostarczana dla wszystkich typów przez statyczną <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> metody.  
  
 Poniższy przykład pokazuje, jak ustalić, czy dwie zmienne mają *równości odwołań*, co oznacza, że odnoszą się do tego samego obiektu w pamięci.  
  
 W przykładzie pokazano też, dlaczego <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> zawsze zwraca `false` dla typów wartości i dlaczego nie należy używać <xref:System.Object.ReferenceEquals%2A> Aby określić ciąg znaków równości.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideObjects#90](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-test-for-reference-equality-identity_1.cs)]  
  
 Implementacja `Equals` w <xref:System.Object?displayProperty=nameWithType> universal klasa bazowa wykonuje sprawdzanie równości odwołań, ale zaleca się nie należy używać tego, ponieważ jeśli Klasa docelowa przesłonić metodę, wyniki mogą być czego oczekiwać. Dotyczy to także `==` i `!=` operatorów. Gdy działają w odwołaniu do typów, domyślne zachowanie == i `!=` jest sprawdzania równości odwołań. Jednak klasy pochodne doprowadzić do przeciążenia operatora sprawdzania równości wartości. Aby zminimalizować ryzyko błędów, najlepiej zawsze używaj <xref:System.Object.ReferenceEquals%2A> w przypadku określenia, czy dwa obiekty mają odniesienie równości.  
  
 Stałe ciągów w ramach tego samego zestawu są zawsze interned w czasie wykonywania. Oznacza to obsługiwane jest tylko jedno wystąpienie każdego unikatowy ciąg literału. Jednak środowisko uruchomieniowe nie gwarantuje, że są interned ciągi tworzony w czasie wykonywania, ponieważ gwarantuje to, że są interned równa dwa ciągi stałej w różnych zestawach.  
  
## <a name="see-also"></a>Zobacz też

- [Porównywanie równości](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)
