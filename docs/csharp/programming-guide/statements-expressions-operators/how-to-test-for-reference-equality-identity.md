---
title: 'Instrukcje: Test pod kątem równości odwołań (tożsamość) C# — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 2b4b7b7bdd03077a78aa2a6375764fa86a885ef5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588641"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a>Instrukcje: Testowanie równości odwołań (tożsamość) (C# Przewodnik programowania)
Nie trzeba implementować żadnej logiki niestandardowej w celu obsługi porównania równości odwołań w typach. Ta funkcja jest dostępna dla wszystkich typów przez metodę statyczną <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> .  
  
 Poniższy przykład pokazuje, jak określić, czy dwie zmienne mają *równość odwołania*, co oznacza, że odwołują się do tego samego obiektu w pamięci.  
  
 W przykładzie pokazano również, <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> dlaczego zawsze `false` są zwracane dla typów wartości i dlaczego nie należy <xref:System.Object.ReferenceEquals%2A> używać do określania równości ciągów.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideObjects#90](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#90)]  
  
 `Equals` Implementacja<xref:System.Object?displayProperty=nameWithType> w uniwersalnej klasie bazowej również wykonuje kontrolę równości odwołań, ale nie jest to zalecane, ponieważ jeśli klasa ma przesłonić metodę, wyniki mogą nie być oczekiwane. Ta sama wartość `==` dotyczy operatorów i `!=` . Gdy są one wykonywane na typach referencyjnych, domyślne zachowanie `==` i `!=` ma na celu wykonywanie kontroli równości odwołań. Jednak klasy pochodne mogą przeciążać operator, aby wykonać kontrolę równości wartości. Aby zminimalizować prawdopodobieństwo wystąpienia błędu, najlepiej jest zawsze używać <xref:System.Object.ReferenceEquals%2A> , gdy trzeba określić, czy dwa obiekty mają równość odwołania.  
  
 Stałe ciągi w tym samym zestawie są zawsze Interni przez środowisko uruchomieniowe. Oznacza to, że jest obsługiwane tylko jedno wystąpienie każdego unikatowego ciągu literału. Jednak środowisko uruchomieniowe nie gwarantuje, że ciągi utworzone w czasie wykonywania są InterNIC, ani nie gwarantujemy, że dwie równe ciągi stałe w różnych zestawach są InterNIC.  
  
## <a name="see-also"></a>Zobacz także

- [Porównywanie równości](./equality-comparisons.md)
