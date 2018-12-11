---
title: Jak inicjowanie słownika przy użyciu inicjatora kolekcji - C# Programming Guide
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 42deee85b3a425531ddadfa96cfaff6d342d1221
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243884"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Jak inicjowanie słownika przy użyciu inicjatora kolekcji (C# Programming Guide)

Element <xref:System.Collections.Generic.Dictionary%602> zawiera kolekcję par klucz/wartość. Jego <xref:System.Collections.Generic.Dictionary%602.Add*> metoda przyjmuje dwa parametry: jeden dla klucza i jeden dla wartości. Aby zainicjować <xref:System.Collections.Generic.Dictionary%602>, lub dowolnej kolekcji którego `Add` metoda przyjmuje kilka parametrów, należy ująć każdego zestawu parametrów w nawiasach klamrowych, jak pokazano w poniższym przykładzie.

## <a name="example"></a>Przykład

W poniższym przykładzie kodu <xref:System.Collections.Generic.Dictionary%602> jest inicjowany za pomocą wystąpienia typu `StudentName`.  
  
[!code-csharp[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]

Należy pamiętać, dwie pary nawiasów klamrowych w każdym elemencie w kolekcji. Najbardziej nawiasów klamrowych, należy ująć Inicjator obiektu `StudentName`, i najbardziej zewnętrznej nawiasów klamrowych ująć inicjator dla pary klucz/wartość, która zostanie dodana do `students` <xref:System.Collections.Generic.Dictionary%602>. Na koniec całej kolekcji inicjatora słownika jest ujęte w nawiasy klamrowe.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Aby uruchomić ten kod, skopiuj i Wklej klasy Visual C# projekt aplikacji konsoli, która została utworzona w programie Visual Studio. Domyślnie ten projekt jest przeznaczony dla wersji 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], i ma odwołania do System.Core.dll i przy użyciu dyrektywy dla System.Linq. Jeśli co najmniej jeden z tych wymagań brakuje z projektu, możesz je dodać ręcznie.

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
