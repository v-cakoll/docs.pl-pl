---
title: Jak deklarować i używać właściwości odczytu zapisu — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 5b880cfc3ace197a3bad2f707cf55543dbe7b78e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714931"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>Jak deklarować i używać właściwości odczytu zapisu (C# Przewodnik programowania)
Właściwości zapewniają wygodę publicznych członków danych bez ryzyka związanego z niechronionym, niekontrolowanym i niezweryfikowanym dostępem do danych obiektu. Jest to realizowane za pośrednictwem metod *dostępu*: specjalne metody, które przypisują i pobierają wartości z bazowego elementu członkowskiego danych. Metoda dostępu [Set](../../language-reference/keywords/set.md) umożliwia składowe danych, a metoda dostępu [Get](../../language-reference/keywords/get.md) pobiera wartości elementu członkowskiego danych.  
  
 Ten przykład pokazuje klasę `Person`, która ma dwie właściwości: `Name` (String) i `Age` (int). Obie właściwości zapewniają `get` i `set` metod dostępu, więc są uznawane za właściwości odczytu i zapisu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a>Skuteczne programowanie  
 W poprzednim przykładzie właściwości `Name` i `Age` są [publiczne](../../language-reference/keywords/public.md) i obejmują zarówno `get` jak i `set` metodę dostępu. Dzięki temu każdy obiekt może odczytywać i zapisywać te właściwości. Jednak czasami pożądane jest wyłączenie jednego z metod dostępu. Z pominięciem metody dostępu `set`, na przykład, powoduje, że właściwość jest tylko do odczytu:  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 Alternatywnie można uwidocznić jeden akcesor publicznie, ale drugi prywatny lub chroniony. Aby uzyskać więcej informacji, zobacz [ułatwienia dostępu asymetryczny](./restricting-accessor-accessibility.md).  
  
 Po zadeklarowaniu właściwości można ich używać tak, jakby były polami klasy. Pozwala to na bardzo naturalną składnię podczas pobierania i ustawiania wartości właściwości, jak w następujących instrukcjach:  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 Należy zauważyć, że w metodzie `set` właściwość jest dostępna specjalna `value` zmienna. Ta zmienna zawiera wartość określoną przez użytkownika, na przykład:  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 Zwróć uwagę na czystą składnię zwiększającą Właściwość `Age` w obiekcie `Person`:  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 Jeśli do właściwości modelu użyto oddzielnych metod `set` i `get`, odpowiedni kod może wyglądać następująco:  
  
```csharp  
person.SetAge(person.GetAge() + 1);   
```  
  
 Metoda `ToString` została przesłonięta w tym przykładzie:  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 Zwróć uwagę, że `ToString` nie jest jawnie używana w programie. Jest ona wywoływana domyślnie przez wywołania `WriteLine`.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Właściwości](./properties.md)
- [Klasy i struktury](./index.md)
