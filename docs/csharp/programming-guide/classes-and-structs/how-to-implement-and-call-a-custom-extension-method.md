---
title: "Porady: implementowanie i wywołanie niestandardowej metody rozszerzenia (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a277412c69d26f20721381d9cfa839c7f082f2f2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a>Porady: implementowanie i wywołanie niestandardowej metody rozszerzenia (Przewodnik programowania w języku C#)
W tym temacie pokazano, jak wdrożyć własne metody rozszerzenia dla dowolnego typu .NET. Kod klienta można użyć metody rozszerzenia Dodawanie odwołania do pliku DLL zawierającego je i dodawanie [przy użyciu](../../../csharp/language-reference/keywords/using-directive.md) dyrektywy, który określa przestrzeń nazw, w którym zdefiniowano metody rozszerzenia.  
  
## <a name="to-define-and-call-the-extension-method"></a>Aby zdefiniować i wywołanie metody rozszerzenia  
  
1.  Definiowanie statycznego [klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) zawiera metody rozszerzenia.  
  
     Klasa musi być widoczny dla kodu klienta. Aby uzyskać więcej informacji o regułach ułatwień dostępu, zobacz [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
2.  Zaimplementuj metodę rozszerzenie jako metoda statyczna z co najmniej taką samą widoczność jak klasa zawierająca.  
  
3.  Pierwszy parametr metody Określa typ, metoda operuje na; musi być poprzedzony literą [to](../../../csharp/language-reference/keywords/this.md) modyfikator.  
  
4.  W kodu wywołującego dodać `using` dyrektywy do określenia [przestrzeń nazw](../../../csharp/language-reference/keywords/namespace.md) zawiera klasę — metoda rozszerzenia.  
  
5.  Wywołanie metody, tak jakby były to wystąpienie metody w typie.  
  
     Należy zauważyć, że pierwszy parametr nie zostanie określony przez wywołanie kodu, ponieważ reprezentuje ona typu, dla którego stosowana jest operator i kompilator zna już typ obiektu. Musisz podać argumenty parametrów 2 za pośrednictwem `n`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład implementuje metodę rozszerzenia o nazwie `WordCount` w `CustomExtensions.StringExtension` klasy. Metoda działa na <xref:System.String> klasy, która jest określony jako pierwszego parametru metody. `CustomExtensions` Przestrzeni nazw jest importowany do przestrzeni nazw aplikacji, a metoda jest wywoływana wewnątrz `Main` metody.  
  
 [!code-csharp[csProgGuideExtensionMethods#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-and-call-a-custom-extension-method_1.cs)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby uruchomić ten kod, skopiuj i wklej go do języka Visual C# console aplikacji projekt, który został utworzony w [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)]. Domyślnie ten projekt jest przeznaczony dla wersji 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], i zawiera odwołania do System.Core.dll i `using` dyrektywy dla System.Linq. Jeśli co najmniej jeden z tych wymagań brakuje z projektu, należy je dodać ręcznie.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Metody rozszerzenia udostępniają nie luk. One nigdy nie można personifikować istniejących metod typu, ponieważ wszystkie konflikty nazw są rozpoznawane na rzecz wystąpienia lub statycznej metody zdefiniowane przez samego typu. Metody rozszerzenia nie dostęp do danych prywatnych rozszerzoną klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Metody rozszerzeń](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [LINQ (zapytania o języku zintegrowanym)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [Klasy statyczne i statyczne elementy członkowskie klas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [this](../../../csharp/language-reference/keywords/this.md)  
 [namespace](../../../csharp/language-reference/keywords/namespace.md)
