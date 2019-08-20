---
title: 'Instrukcje: Deklarowanie i używanie właściwości odczytu zapisu C# — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 010c3d4c1ae976091b5382f00a982400746f6436
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596931"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>Instrukcje: Deklarowanie i używanie właściwości odczytu zapisuC# (Przewodnik programowania)
Właściwości zapewniają wygodę publicznych członków danych bez ryzyka związanego z niechronionym, niekontrolowanym i niezweryfikowanym dostępem do danych obiektu. Jest to realizowane za pośrednictwem metod *dostępu*: specjalne metody, które przypisują i pobierają wartości z bazowego elementu członkowskiego danych. Metoda dostępu [Set](../../language-reference/keywords/set.md) umożliwia składowe danych, a metoda dostępu [Get](../../language-reference/keywords/get.md) pobiera wartości elementu członkowskiego danych.  
  
 Ten przykład pokazuje `Person` klasę, która ma dwie właściwości: `Name` (String) i `Age` (int). Obie właściwości zapewniają `get` i `set` metody dostępu, więc są uznawane za właściwości odczytu i zapisu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 W poprzednim `Name` przykładzie właściwości i `Age` są [publiczne](../../language-reference/keywords/public.md) i zawierają `get` `set` metodę dostępu a i. Dzięki temu każdy obiekt może odczytywać i zapisywać te właściwości. Jednak czasami pożądane jest wyłączenie jednego z metod dostępu. Z `set` pominięciem metody dostępu, na przykład, powoduje, że właściwość jest tylko do odczytu:  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 Alternatywnie można uwidocznić jeden akcesor publicznie, ale drugi prywatny lub chroniony. Aby uzyskać więcej informacji, zobacz [ułatwienia dostępu asymetryczny](./restricting-accessor-accessibility.md).  
  
 Po zadeklarowaniu właściwości można ich używać tak, jakby były polami klasy. Pozwala to na bardzo naturalną składnię podczas pobierania i ustawiania wartości właściwości, jak w następujących instrukcjach:  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 Należy pamiętać, że w `set` metodzie właściwości `value` jest dostępna specjalna zmienna. Ta zmienna zawiera wartość określoną przez użytkownika, na przykład:  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 Zwróć uwagę na czystą składnię zwiększającą `Age` Właściwość `Person` obiektu:  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 Jeśli do `set` właściwości `get` modelu użyto oddzielnych metod i, odpowiedni kod może wyglądać następująco:  
  
```csharp  
person.SetAge(person.GetAge() + 1);   
```  
  
 `ToString` Metoda została przesłonięta w tym przykładzie:  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 Należy zauważyć `ToString` , że nie jest on jawnie używany w programie. Jest wywoływana domyślnie przez `WriteLine` wywołania.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Właściwości](./properties.md)
- [Klasy i struktury](./index.md)
