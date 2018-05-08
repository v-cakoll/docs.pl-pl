---
title: 'Porady: testowanie równości odwołań (tożsamości) (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 78a6bf1f5d4a93bd561faada91b4a11f52692dbf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a>Porady: testowanie równości odwołań (tożsamości) (Przewodnik programowania w języku C#)
Nie masz wdrożenia dowolnej niestandardowej logiki do obsługi odwołania porównywanie równości w typach sieci. Ta funkcja jest udostępniane na potrzeby wszystkich typów statycznych <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> metody.  
  
 Poniższy przykład przedstawia sposób sprawdzić, czy dwie zmienne *odwołania równości*, co oznacza, że odnoszą się do tego samego obiektu w pamięci.  
  
 W przykładzie przedstawiono również Dlaczego <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> zawsze zwraca `false` dla typów wartości i dlaczego nie należy używać <xref:System.Object.ReferenceEquals%2A> do określenia ciągu równości.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideObjects#90](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-test-for-reference-equality-identity_1.cs)]  
  
 Implementacja `Equals` w <xref:System.Object?displayProperty=nameWithType> uniwersalnych klasy podstawowej również przeprowadza sprawdzanie równość odwołania, ale najlepiej nie można użyć, ponieważ w przypadku klasy Aby przesłonić metodę, wyniki mogą być oczekiwań. Dotyczy to także `==` i `!=` operatorów. Gdy działają w odwołaniu do typów domyślne zachowanie == i `!=` ma wykonywać sprawdzania równości odwołania. Klasy pochodne mogą jednak przeciążenia operatora równości wartości sprawdzania. Aby zminimalizować potencjalnych błędów, jest zawsze używać <xref:System.Object.ReferenceEquals%2A> gdy trzeba sprawdzić, czy dwa obiekty równości odwołań.  
  
 Stałe ciągów wewnątrz tego samego zestawu są zawsze interned w czasie wykonywania. Oznacza to obsługiwane jest tylko jedno wystąpienie każdego unikatowy ciąg literału. Jednak środowiska uruchomieniowego nie gwarantuje, że są interned ciągów utworzone w czasie wykonywania, ani gwarantuje to, że interned są takie same dwa ciągi stałej w różnych zestawach.  
  
## <a name="see-also"></a>Zobacz też  
 [Porównywanie równości](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)
