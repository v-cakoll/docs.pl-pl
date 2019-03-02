---
title: 'Instrukcje: Implementowanie i wywołanie niestandardowej metody rozszerzenia - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: e4b77bf0a44ce58db632e0c58982dba7178f9272
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57203431"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a>Instrukcje: Implementowanie i wywołanie niestandardowej metody rozszerzenia (C# Programming Guide)
W tym temacie pokazano, jak można implementować własne metody rozszerzenia dla dowolnego typu platformy .NET. Kod klienta można użyć metody rozszerzenia przez dodanie odwołania do biblioteki DLL, która je zawiera i dodawanie [przy użyciu](../../../csharp/language-reference/keywords/using-directive.md) dyrektywę, który określa obszar nazw, w którym zdefiniowano metody rozszerzenia.  
  
## <a name="to-define-and-call-the-extension-method"></a>Aby zdefiniować i wywołanie metody rozszerzenia  
  
1.  Definiowanie statycznego [klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) zawiera metody rozszerzenia.  
  
     Klasy muszą być widoczne dla kodu klienta. Aby uzyskać więcej informacji o regułach ułatwień dostępu, zobacz [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
2.  Implementuje metody rozszerzenia jako metody statycznej z co najmniej taką samą widoczność jak klasa zawierająca.  
  
3.  Pierwszy parametr metody Określa typ, który działa metody; musi być poprzedzony znakiem [to](../../../csharp/language-reference/keywords/this.md) modyfikator.  
  
4.  W wywoływanym kodzie Dodaj `using` dyrektywy, aby określić [przestrzeni nazw](../../../csharp/language-reference/keywords/namespace.md) zawierający klasę metody rozszerzenia.  
  
5.  Tak, jakby były metodami wystąpień w typie, należy wywołać metodę.  
  
     Pamiętaj, że pierwszy parametr nie jest określony przez wywołanie kodu, ponieważ reprezentuje on typ, na którym jest stosowany operator kompilator wie już typ obiektu. Musisz podać argumenty dla parametrów 2 za pośrednictwem `n`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład implementuje metodę rozszerzenia o nazwie `WordCount` w `CustomExtensions.StringExtension` klasy. Metoda działa na <xref:System.String> klasy, która jest określony jako pierwszy parametr metody. `CustomExtensions` Przestrzeni nazw jest importowany do przestrzeni nazw aplikacji, a metoda jest wywoływana wewnątrz `Main` metody.  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby uruchomić ten kod, skopiuj i wklej go do programu Visual C# projekt aplikacji konsoli, która została utworzona w programie Visual Studio. Domyślnie ten projekt jest przeznaczony dla wersji 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], i ma odwołania do System.Core.dll i `using` dyrektywy dla System.Linq. Jeśli co najmniej jeden z tych wymagań brakuje z projektu, możesz je dodać ręcznie.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Metody rozszerzenia udostępniają nie luk w zabezpieczeniach określone. One nigdy nie można dokonać personifikacji istniejących metod w danym typie ponieważ wszystkich konfliktów nazw są rozpoznawane na rzecz wystąpienia lub statycznej metody zdefiniowane przez samego typu. Metody rozszerzenia nie może uzyskać dostęp do wszelkich danych prywatnych w rozszerzona klasa.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Metody rozszerzeń](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [LINQ (Language-Integrated Query)](../../../csharp/linq/linq-in-csharp.md)
- [Klasy statyczne i statyczne elementy członkowskie klas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [protected](../../../csharp/language-reference/keywords/protected.md)
- [internal](../../../csharp/language-reference/keywords/internal.md)
- [public](../../../csharp/language-reference/keywords/public.md)
- [this](../../../csharp/language-reference/keywords/this.md)
- [namespace](../../../csharp/language-reference/keywords/namespace.md)
