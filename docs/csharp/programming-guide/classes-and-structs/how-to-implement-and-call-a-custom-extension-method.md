---
title: Jak zaimplementować i wywołać niestandardową metodę rozszerzenia - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: 7e2092a37c1f042a087e03f4a272139b585156c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705603"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a>Jak zaimplementować i wywołać niestandardową metodę rozszerzenia (Przewodnik programowania C#)
W tym temacie pokazano, jak zaimplementować własne metody rozszerzenia dla dowolnego typu .NET. Kod klienta można użyć metod rozszerzenia, dodając odwołanie do dll, który je zawiera i dodanie [using](../../language-reference/keywords/using-directive.md) dyrektywy, która określa obszar nazw, w którym metody rozszerzenia są zdefiniowane.  
  
## <a name="to-define-and-call-the-extension-method"></a>Aby zdefiniować i wywołać metodę rozszerzenia  
  
1. Zdefiniuj [klasę](./static-classes-and-static-class-members.md) statyczną, która zawiera metodę rozszerzenia.  
  
     Klasa musi być widoczna dla kodu klienta. Aby uzyskać więcej informacji na temat reguł ułatwień dostępu, zobacz [Modyfikatory dostępu](./access-modifiers.md).  
  
2. Zaimplementuj metodę rozszerzenia jako metodę statyczną o co najmniej takiej samej widoczności jak klasa zawierająca.  
  
3. Pierwszy parametr metody określa typ, na który działa metoda; musi być poprzedzony [tym](../../language-reference/keywords/this.md) modyfikatorem.  
  
4. W kodzie wywołującym dodaj dyrektywę, `using` aby określić obszar [nazw,](../../language-reference/keywords/namespace.md) który zawiera klasę metody rozszerzenia.  
  
5. Wywołaj metody tak, jakby były metody wystąpienia na typ.  
  
     Należy zauważyć, że pierwszy parametr nie jest określony przez kod wywołujący, ponieważ reprezentuje typ, na którym operator jest stosowany, a kompilator już zna typ obiektu. Musisz podać tylko argumenty dla `n`parametrów od 2 do .  
  
## <a name="example"></a>Przykład  
 Poniższy przykład implementuje metodę `WordCount` rozszerzenia `CustomExtensions.StringExtension` o nazwie w klasie. Metoda działa na <xref:System.String> klasie, która jest określona jako pierwszy parametr metody. Obszar `CustomExtensions` nazw jest importowany do obszaru nazw aplikacji, `Main` a metoda jest wywoływana wewnątrz metody.  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Metody rozszerzenia nie zawierają żadnych konkretnych luk w zabezpieczeniach. Nigdy nie można użyć do personifikacji istniejących metod typu, ponieważ wszystkie kolizje nazw są rozpoznawane na korzyść wystąpienia lub metody statycznej zdefiniowanej przez sam typ. Metody rozszerzenia nie mogą uzyskać dostępu do żadnych prywatnych danych w klasie rozszerzonej.  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Metody rozszerzeń](./extension-methods.md)
- [LINQ (zapytanie zintegrowane z językiem)](../../linq/linq-in-csharp.md)
- [Klasy statyczne i statyczni członkowie klas](./static-classes-and-static-class-members.md)
- [protected](../../language-reference/keywords/protected.md)
- [Wewnętrznego](../../language-reference/keywords/internal.md)
- [Publicznego](../../language-reference/keywords/public.md)
- [względem tego ruchu](../../language-reference/keywords/this.md)
- [Namespace](../../language-reference/keywords/namespace.md)
