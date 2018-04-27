---
title: 'Porady: inicjowanie słownika przy użyciu inicjatora kolekcji (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
caps.latest.revision: 10
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9f014e92167d92f7daebcfb4c2e1d54f69ee2575
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Porady: inicjowanie słownika przy użyciu inicjatora kolekcji (Przewodnik programowania w języku C#)
A <xref:System.Collections.Generic.Dictionary`2> zawiera kolekcję par klucz/wartość. Jego <xref:System.Collections.Generic.Dictionary`2.Add*> metoda przyjmuje dwa parametry: jeden dla klucza i jeden dla wartości. Aby zainicjować <xref:System.Collections.Generic.Dictionary`2>, lub kolekcji których `Add` metoda przyjmuje kilka parametrów, ujmij każdego zestawu parametrów w nawiasach klamrowych, jak pokazano w poniższym przykładzie.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu <xref:System.Collections.Generic.Dictionary`2> jest inicjowany z wystąpień typu `StudentName`.  
  
 [!code-csharp[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 Należy zwrócić uwagę dwie pary nawiasów klamrowych w każdym elementem kolekcji. Najbardziej nawiasów klamrowych ujmij inicjatora obiektu dla `StudentName`, i nawiasy peryferyjnych ujmij inicjator dla pary klucza/wartości, który zostanie dodany do `students` <xref:System.Collections.Generic.Dictionary`2>. Na koniec całą kolekcję inicjatora słownika jest ujęta w nawiasy klamrowe.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby uruchomić ten kod, skopiuj i Wklej klasy w projektach Visual C# console aplikacji utworzony w programie Visual Studio. Domyślnie ten projekt jest przeznaczony dla wersji 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], i zawiera odwołania do System.Core.dll i przy użyciu dyrektywy dla System.Linq. Jeśli co najmniej jeden z tych wymagań brakuje z projektu, należy je dodać ręcznie.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
