---
title: "Porady: deklarowanie i użycie właściwości do odczytu i zapisu (C# przewodnik programowania w języku)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c17bdd05196f834b491c69f648bec0b7cb6e3cd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>Porady: deklarowanie i użycie właściwości do odczytu i zapisu (C# przewodnik programowania w języku)
Właściwości wygodniejszego publiczne elementy członkowskie danych bez zagrożenie niechronione, niekontrolowanego i niezweryfikowane dostęp do danych obiektu. Jest to realizowane przez *akcesorów*: specjalne metody przypisać i pobrać wartości z podstawowego elementu członkowskiego danych. [Ustawić](../../../csharp/language-reference/keywords/set.md) dostępu umożliwia członkom danych można przypisać i [uzyskać](../../../csharp/language-reference/keywords/get.md) akcesor pobiera wartości elementów członkowskich danych.  
  
 W tym przykładzie pokazano `Person` klasy, która ma dwie właściwości: `Name` (ciąg) i `Age` (int). Podaj zarówno właściwości `get` i `set` metody dostępu, więc są traktowane jako właściwości odczytu/zapisu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideObjects#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_1.cs)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 W poprzednim przykładzie `Name` i `Age` właściwości są [publicznego](../../../csharp/language-reference/keywords/public.md) i zawiera zarówno `get` i `set` metody dostępu. Dzięki temu dowolnego obiektu do odczytu i zapisu tych właściwości. Czasami jest pożądane, jednak do wykluczenia z jednej z metod dostępu. Pominięcie `set` dostępu, na przykład sprawia, że właściwość tylko do odczytu:  
  
 [!code-csharp[csProgGuideObjects#87](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_2.cs)]  
  
 Alternatywnie można ujawnić publicznie jedną metodę dostępu, ale innych prywatne lub chronione. Aby uzyskać więcej informacji, zobacz [asymetrycznego dostępności metody dostępu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
 Po zadeklarowaniu są właściwości, użyciem tak, jakby były pola klasy. Dzięki temu bardzo fizycznych składni, gdy zarówno pobieranie i ustawianie wartości właściwości, jak następujące instrukcje:  
  
 [!code-csharp[csProgGuideObjects#35](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_3.cs)]  
  
 Należy pamiętać, że we właściwości `set` metody a specjalne `value` zmienna jest dostępna. Ta zmienna uwzględnia wartość określonej przez użytkownika, na przykład:  
  
 [!code-csharp[csProgGuideObjects#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_4.cs)]  
  
 Zwróć uwagę, czysta składnia zwiększanie `Age` właściwość `Person` obiektu:  
  
 [!code-csharp[csProgGuideObjects#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_5.cs)]  
  
 Jeśli oddzielnych `set` i `get` metody zostały użyte do modelowania właściwości, równoważny kod może wyglądać następująco:  
  
```  
person.SetAge(person.GetAge() + 1);   
```  
  
 `ToString` Metoda zostanie przesłonięta w tym przykładzie:  
  
 [!code-csharp[csProgGuideObjects#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_6.cs)]  
  
 Zwróć uwagę, że `ToString` jawnie nie jest używany w programie. Domyślnie następuje jej wywoływanie `WriteLine` wywołania.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
