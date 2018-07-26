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
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37959988"
---
# <a name="static-c-reference"></a>static (odwołanie w C#)
Użyj `static` modyfikator, aby zadeklarować statyczną składową, która należy do samego typu, a nie do określonego obiektu. `static` Modyfikator mogą być używane z klasy, pola, metody, właściwości, operatory, zdarzenia i konstruktory, ale nie można używać z indeksatorów, finalizatory lub typów innych niż klasy. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## <a name="example"></a>Przykład  
 Następujące klasy jest zadeklarowana jako `static` i zawiera tylko `static` metody:  
  
 [!code-csharp[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_1.cs)]  
  
 Deklaracja stałej lub typu jest niejawnie statyczny element członkowski.  
  
 Statyczny element członkowski nie może być przywoływany przez wystąpienie. Zamiast tego jest przywoływany przez nazwę typu. Na przykład rozważmy następujące klasy:  
  
 [!code-csharp[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_2.cs)]  
  
 Aby odwołać się do statycznej składowej `x`, użyj w pełni kwalifikowanej nazwy `MyBaseC.MyStruct.x`, chyba że składowych jest możliwy z tym samym zakresie:  
  
```csharp  
Console.WriteLine(MyBaseC.MyStruct.x);  
```  
  
 Chociaż wystąpienia klasy zawiera osobną kopię wszystkie pola wystąpienia klasy, ma tylko jedną kopię każdego pola statyczne.  
  
 Nie jest możliwe użycie [to](../../../csharp/language-reference/keywords/this.md) można odwoływać się do metody statyczne lub właściwość metody dostępu.  
  
 Jeśli `static` — słowo kluczowe jest stosowany do klasy, wszystkie elementy członkowskie klasy muszą być statyczne.  
  
 Klasy i klas statycznych mogą mieć konstruktorów statycznych. Konstruktory statyczne są nazywane w pewnym momencie między po uruchomieniu programu i tworzenia wystąpienia klasy.  
  
> [!NOTE]
>  `static` — Słowo kluczowe podlega większym ograniczeniom niż w języku C++. Aby porównać ze słowem kluczowym C++, zobacz [klasy magazynu (C++)](/cpp/cpp/storage-classes-cpp#static).
  
 Aby zademonstrować statyczne elementy członkowskie, należy wziąć pod uwagę klasa, która reprezentuje pracowników firmy. Załóżmy, że klasa zawiera metodę, aby liczba pracowników i pola, do przechowywania liczby pracowników. Pola i metody nie należą do dowolnego wystąpienia pracownika. Zamiast tego należą do klasy firmy. W związku z tym powinny zostać zadeklarowane jako statyczne elementy członkowskie klasy.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie odczytuje nazwy i Identyfikatora nowych pracowników, zwiększa licznik pracowników za pomocą jednej i wyświetla informacje o nowych pracowników i liczba nowych pracowników. Dla uproszczenia ten program odczytuje bieżąca liczba pracowników przy użyciu klawiatury. W rzeczywistej aplikacji należy przeczytać te informacje z pliku.  
  
 [!code-csharp[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_3.cs)]  
  
## <a name="example"></a>Przykład  
 Ten przykład pokazuje, że mimo że można zainicjować pole statyczne za pomocą innego pola statyczne niezgłoszonych, wyniki będą niezdefiniowane aż jawnie przypisać wartości do pola statycznego.  
  
 [!code-csharp[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_4.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)  
 [Klasy statyczne i statyczne elementy członkowskie klas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
