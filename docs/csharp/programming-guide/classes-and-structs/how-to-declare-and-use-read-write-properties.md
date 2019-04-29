---
title: 'Instrukcje: Deklarowanie i użycie właściwości odczyt/zapis - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: b4dc9364e64f7ebfd495671b852b98d8f56c80b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646465"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>Instrukcje: Deklarowanie i użycie właściwości odczyt/zapis (C# Programming Guide)
Właściwości zapewniają wygodne publiczne elementy członkowskie danych bez ryzyka związane z niechronionych, niekontrolowane i niezweryfikowanych dostęp do danych obiektu. Jest to realizowane za pośrednictwem *Akcesory*: specjalne metody, które przypisać i pobierania wartości z bazowego elementu danych. [Ustaw](../../../csharp/language-reference/keywords/set.md) dostępu umożliwia członkom danych można przypisać i [uzyskać](../../../csharp/language-reference/keywords/get.md) akcesor pobiera wartości elementów członkowskich danych.  
  
 W tym przykładzie pokazano `Person` klasy, która ma dwie właściwości: `Name` (ciąg) i `Age` (int). Obie te właściwości zapewniają `get` i `set` metod dostępu, dzięki czemu są one traktowane jako właściwości odczytu/zapisu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 W poprzednim przykładzie `Name` i `Age` właściwości są [publicznych](../../../csharp/language-reference/keywords/public.md) i zawiera zarówno `get` i `set` metody dostępu. Umożliwia to dowolnego obiektu odczytywać i zapisywać te właściwości. Czasami jest pożądane, jednak do wykluczenia z jednej z metod dostępu. Pominięcie `set` dostępu, na przykład sprawia, że właściwość tylko do odczytu:  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 Alternatywnie można publicznie udostępnić jedną metodę dostępu, ale inne prywatnych lub chronionych. Aby uzyskać więcej informacji, zobacz [asymetrycznego dostępności metody dostępu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
 Po właściwości są deklarowane, mogą one używane tak, jakby były one pola klasy. Umożliwia to bardzo fizycznych składni, gdy zarówno pobierania i ustawiania wartości właściwości, tak jak w następujących instrukcji:  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 Należy pamiętać, że we właściwości `set` typu specjalne `value` zmienna jest dostępna. Ta zmienna zawiera wartość, którą użytkownik określił, na przykład:  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 Zwróć uwagę, czysta składnia zwiększanie `Age` właściwość `Person` obiektu:  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 Jeśli jest to oddzielne `set` i `get` metody były używane do modelowania właściwości, równoważny kod może wyglądać następująco:  
  
```csharp  
person.SetAge(person.GetAge() + 1);   
```  
  
 `ToString` Metoda zostanie przesłonięta w tym przykładzie:  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 Należy zauważyć, że `ToString` jawnie nie jest używany w programie. Jest wywoływana, domyślnie `WriteLine` wywołania.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
