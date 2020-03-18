---
title: Jak przetestować równość referencyjną (Tożsamość) - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 77ce2ef0ccf47d619134c120101ba2aa04f485e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75699057"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a>Jak przetestować równość referencyjną (Tożsamość) (Przewodnik programowania C#)
Nie trzeba implementować żadnej logiki niestandardowej do obsługi porównań równości odwołań w typach. Ta funkcja jest dostępna dla wszystkich <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> typów za pomocą metody statycznej.  
  
 W poniższym przykładzie pokazano, jak ustalić, czy dwie zmienne mają *równość odwołania*, co oznacza, że odnoszą się do tego samego obiektu w pamięci.  
  
 W przykładzie pokazano również, dlaczego <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> zawsze zwraca `false` <xref:System.Object.ReferenceEquals%2A> dla typów wartości i dlaczego nie należy używać do określania równości ciągów.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideObjects#90](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#90)]  
  
 Implementacja `Equals` w <xref:System.Object?displayProperty=nameWithType> uniwersalnej klasie podstawowej wykonuje również sprawdzanie równości odwołania, ale najlepiej nie używać tego, ponieważ jeśli klasa dzieje się zastąpić metodę, wyniki mogą nie być to, czego oczekujesz. To samo dotyczy `==` operatorów `!=` i operatorów. Gdy działają na typy odwołań, domyślne `==` `!=` zachowanie i jest do wykonywania kontroli równości odwołania. Jednak klasy pochodne można przeciążać operatora, aby wykonać sprawdzanie równości wartości. Aby zminimalizować ryzyko wystąpienia błędu, najlepiej <xref:System.Object.ReferenceEquals%2A> jest zawsze używać, gdy trzeba określić, czy dwa obiekty mają równość odwołania.  
  
 Ciągi stałe w tym samym zestawie są zawsze internowane przez czas wykonywania. Oznacza to, że jest zachowywany tylko jedno wystąpienie każdego unikatowego ciągu literału. Jednak czas wykonywania nie gwarantuje, że ciągi utworzone w czasie wykonywania są internowane, ani nie gwarantuje, że dwa równe ciągi stałej w różnych zestawach są internowane.  
  
## <a name="see-also"></a>Zobacz też

- [Porównania równości](./equality-comparisons.md)
