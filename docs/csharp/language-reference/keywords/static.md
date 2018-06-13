---
title: static (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: b7e2981c8832d6ac1744c102d5bde55bbe25c256
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33287270"
---
# <a name="static-c-reference"></a>static (odwołanie w C#)
Użyj `static` modyfikator Aby zadeklarować statyczny element członkowski, który należy do samego typu, a nie z określonym obiektem. `static` Modyfikatora można używać z klasami, pola, metody, właściwości, operatory, zdarzeń i konstruktorów, ale nie można użyć z indeksatorów, finalizatory lub typu innego niż klasy. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statycznych elementów członkowskich klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## <a name="example"></a>Przykład  
 Następujące klasy jest zadeklarowany jako `static` i zawiera tylko `static` metod:  
  
 [!code-csharp[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_1.cs)]  
  
 Deklaracja stałej lub typu jest niejawnie statycznego elementu członkowskiego.  
  
 Statyczny element członkowski nie można odwoływać się za pomocą wystąpienia. Zamiast tego odwołuje się do za pomocą nazwy typu. Rozważmy na przykład następującej klasy:  
  
 [!code-csharp[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_2.cs)]  
  
 Aby odwołać się do statycznego elementu członkowskiego `x`, użyj w pełni kwalifikowanej nazwy, `MyBaseC.MyStruct.x`, chyba że jest dostępny z tym samym zakresie:  
  
```csharp  
Console.WriteLine(MyBaseC.MyStruct.x);  
```  
  
 Gdy wystąpienie klasy zawiera osobną kopię wszystkie pola wystąpienia klasy, istnieje tylko jedna kopia każdego pola statycznego.  
  
 Nie jest możliwe użycie [to](../../../csharp/language-reference/keywords/this.md) do odwołania statycznej metody lub właściwości metody dostępu.  
  
 Jeśli `static` — słowo kluczowe jest stosowane do klasy, wszystkie elementy członkowskie klasy musi być statyczna.  
  
 Klasy i klasy statyczne mogą mieć konstruktorów statycznych. Konstruktory statyczne są nazywane w pewnym momencie między podczas uruchamiania programu i tworzenia wystąpienia klasy.  
  
> [!NOTE]
>  `static` — Słowo kluczowe więcej ma ograniczoną użycia niż w języku C++. Aby porównać ze słowem kluczowym języka C++, zobacz [klasy magazynu (C++)](/cpp/cpp/storage-classes-cpp#static).
  
 Aby zademonstrować statycznych elementów członkowskich, należy wziąć pod uwagę klasa, która reprezentuje pracowników firmy. Załóżmy, że klasa zawiera metody liczba pracowników i pola do przechowywania liczba pracowników. Zarówno metoda, jak i pole nie należą do dowolnego wystąpienia pracownika. Zamiast tego należą do klasy firmy. W związku z tym powinny zostać zadeklarowane jako statyczne elementy członkowskie klasy.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie odczytuje nazwę i identyfikator nowego pracownika, zwiększa licznik pracowników przez jedną i wyświetla informacje o nowych pracowników i nowa liczba pracowników. Dla uproszczenia ten program odczytuje bieżącą liczbę pracowników z klawiatury. W rzeczywistej aplikacji należy przeczytać te informacje z pliku.  
  
 [!code-csharp[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_3.cs)]  
  
## <a name="example"></a>Przykład  
 Ten przykład przedstawia, że chociaż pola statycznego można zainicjować za pomocą innego pola statycznego niezgłoszonych, wyniki będą Niezdefiniowany dopóki jawnie przypisać wartości do pola statycznego.  
  
 [!code-csharp[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_4.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)  
 [Klasy statyczne i statyczne elementy członkowskie klas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
