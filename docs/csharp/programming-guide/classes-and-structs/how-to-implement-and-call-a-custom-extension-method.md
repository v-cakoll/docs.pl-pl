---
title: Jak zaimplementować i wywołać metodę rozszerzenia niestandardowego — Przewodnik programowania w języku C#
description: Dowiedz się, jak zaimplementować metody rozszerzenia dla dowolnego typu .NET. Kod klienta może korzystać z metod przez dodanie odwołania do biblioteki DLL i dodanie dyrektywy using.
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: 7856e78713648a42d1c961f50f7e83f2f7ef05b7
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865063"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a>Implementowanie i wywoływanie niestandardowej metody rozszerzenia (Przewodnik programowania w języku C#)
W tym temacie przedstawiono sposób implementacji własnych metod rozszerzenia dla dowolnego typu .NET. Kod klienta może korzystać z metod rozszerzenia przez dodanie odwołania do biblioteki DLL, która zawiera te metody, i dodanie dyrektywy [using](../../language-reference/keywords/using-directive.md) , która określa przestrzeń nazw, w której są zdefiniowane metody rozszerzenia.  
  
## <a name="to-define-and-call-the-extension-method"></a>Aby zdefiniować i wywołać metodę rozszerzenia  
  
1. Zdefiniuj [klasę](./static-classes-and-static-class-members.md) statyczną, aby zawierała metodę rozszerzenia.  
  
     Klasa musi być widoczna dla kodu klienta. Aby uzyskać więcej informacji na temat reguł ułatwień dostępu, zobacz [Modyfikatory dostępu](./access-modifiers.md).  
  
2. Zaimplementuj metodę rozszerzenia jako metodę statyczną z co najmniej taką samą widocznością jak zawierająca klasy.  
  
3. Pierwszy parametr metody Określa typ, na którym działa Metoda; musi być poprzedzony [tym](../../language-reference/keywords/this.md) modyfikatorem.  
  
4. W kodzie wywołującym Dodaj dyrektywę, `using` Aby określić [przestrzeń nazw](../../language-reference/keywords/namespace.md) , która zawiera klasę metody rozszerzenia.  
  
5. Wywołaj metody tak, jakby były metodami wystąpień w typie.  
  
     Należy zauważyć, że pierwszy parametr nie jest określony przez wywołanie kodu, ponieważ reprezentuje typ, na którym jest stosowany operator, a kompilator już zna typ obiektu. Musisz podać argumenty dla parametrów 2 przez `n` .  
  
## <a name="example"></a>Przykład  
 Poniższy przykład implementuje metodę rozszerzającą o nazwie `WordCount` w `CustomExtensions.StringExtension` klasie. Metoda działa na <xref:System.String> klasie, która jest określona jako pierwszy parametr metody. `CustomExtensions`Przestrzeń nazw jest importowana do przestrzeni nazw aplikacji, a metoda jest wywoływana wewnątrz `Main` metody.  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-security"></a>Zabezpieczenia platformy .NET  
 Metody rozszerzające nie stwarzają określonych luk w zabezpieczeniach. Nigdy nie mogą być używane do personifikacji istniejących metod dla typu, ponieważ wszystkie kolizje nazw są rozwiązywane na korzyść wystąpienia lub statycznej metody zdefiniowanej przez sam typ. Metody rozszerzające nie mogą uzyskać dostępu do żadnych prywatnych danych w klasie rozszerzonej.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Metody rozszerzające](./extension-methods.md)
- [LINQ (zapytanie zintegrowane z językiem)](../../linq/linq-in-csharp.md)
- [Klasy statyczne i statyczni członkowie klas](./static-classes-and-static-class-members.md)
- [protected](../../language-reference/keywords/protected.md)
- [internal](../../language-reference/keywords/internal.md)
- [public](../../language-reference/keywords/public.md)
- [this](../../language-reference/keywords/this.md)
- [obszaru](../../language-reference/keywords/namespace.md)
