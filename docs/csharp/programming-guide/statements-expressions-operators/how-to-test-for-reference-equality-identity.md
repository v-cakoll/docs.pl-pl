---
title: Jak przetestować równość odwołań (tożsamość) — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 77ce2ef0ccf47d619134c120101ba2aa04f485e6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75699057"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a>Testowanie równości odwołań (tożsamość) (C# Przewodnik programowania)
Nie trzeba implementować żadnej logiki niestandardowej w celu obsługi porównania równości odwołań w typach. Ta funkcja jest dostępna dla wszystkich typów przez metodę static <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>.  
  
 Poniższy przykład pokazuje, jak określić, czy dwie zmienne mają *równość odwołania*, co oznacza, że odwołują się do tego samego obiektu w pamięci.  
  
 W przykładzie pokazano również, dlaczego <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> zawsze zwraca `false` dla typów wartości i dlaczego nie należy używać <xref:System.Object.ReferenceEquals%2A> do określania równości ciągów.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideObjects#90](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#90)]  
  
 Implementacja `Equals` w klasie <xref:System.Object?displayProperty=nameWithType> Universal Base wykonuje również kontrolę równości odwołań, ale najlepszym rozwiązaniem jest użycie tego elementu, ponieważ, jeśli klasa ma przesłonić metodę, wyniki mogą nie być oczekiwane. Ta sama wartość dotyczy operatorów `==` i `!=`. W przypadku korzystania z typów referencyjnych domyślne zachowanie `==` i `!=` ma na celu wykonanie kontroli równości odwołań. Jednak klasy pochodne mogą przeciążać operator, aby wykonać kontrolę równości wartości. Aby zminimalizować prawdopodobieństwo wystąpienia błędu, najlepiej jest zawsze używać <xref:System.Object.ReferenceEquals%2A>, gdy konieczne jest określenie, czy dwa obiekty mają równość odwołań.  
  
 Stałe ciągi w tym samym zestawie są zawsze Interni przez środowisko uruchomieniowe. Oznacza to, że jest obsługiwane tylko jedno wystąpienie każdego unikatowego ciągu literału. Jednak środowisko uruchomieniowe nie gwarantuje, że ciągi utworzone w czasie wykonywania są InterNIC, ani nie gwarantujemy, że dwie równe ciągi stałe w różnych zestawach są InterNIC.  
  
## <a name="see-also"></a>Zobacz także

- [Porównywanie równości](./equality-comparisons.md)
