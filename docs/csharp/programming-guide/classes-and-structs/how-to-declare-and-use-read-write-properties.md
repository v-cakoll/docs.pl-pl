---
title: Jak deklarować i używać właściwości odczytu zapisu - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 4b9db5f15746ab9a1f42239150c6783154723371
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170289"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>Jak zadeklarować i używać właściwości odczytu zapisu (Przewodnik programowania C#)
Właściwości zapewniają wygodę publicznych elementów członkowskich danych bez ryzyka związanego z niechronionym, niekontrolowanym i niezweryfikowanym dostępem do danych obiektu. Jest to realizowane za pomocą *akcesorów:* specjalne metody, które przypisują i pobierają wartości z podstawowego elementu członkowskiego danych. [Set](../../language-reference/keywords/set.md) akcesor umożliwia członków danych, które mają być przypisane, a [get](../../language-reference/keywords/get.md) akcesor pobiera wartości elementów członkowskich danych.  
  
 W tym `Person` przykładzie przedstawiono klasę, `Name` która ma `Age` dwie właściwości: (ciąg) i (int). Obie właściwości `get` zapewniają `set` i akcesorów, więc są one uważane za właściwości odczytu/zapisu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 W poprzednim przykładzie `Name` i `Age` właściwości są [publiczne](../../language-reference/keywords/public.md) i `get` obejmują `set` zarówno a, jak i akcesor. Dzięki temu każdy obiekt do odczytu i zapisu tych właściwości. Czasami pożądane jest jednak wykluczenie jednego z akcesorów. Pomijanie akcesor, `set` na przykład sprawia, że właściwość tylko do odczytu:  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 Alternatywnie można udostępnić jeden akcesor publicznie, ale inne prywatne lub chronione. Aby uzyskać więcej informacji, zobacz [Dostępność asymetrycznego dostępu](./restricting-accessor-accessibility.md).  
  
 Po zadeklarowaniu właściwości mogą być używane tak, jakby były polami klasy. Pozwala to na bardzo naturalną składnię, gdy zarówno uzyskanie i ustawienie wartości właściwości, jak w następujących instrukcjach:  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 Należy zauważyć, `set` że w `value` metodzie właściwości dostępna jest specjalna zmienna. Ta zmienna zawiera wartość określoną przez użytkownika, na przykład:  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 Zwróć uwagę na czystą składnię zwiększania `Age` właściwości na `Person` obiekcie:  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 Jeśli `set` oddzielne `get` i metody zostały użyte do modelu właściwości, równoważny kod może wyglądać tak:  
  
```csharp  
person.SetAge(person.GetAge() + 1);
```  
  
 Metoda `ToString` jest zastąpiona w tym przykładzie:  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 Zwróć `ToString` uwagę, że nie jest jawnie używany w programie. Jest wywoływana domyślnie `WriteLine` przez wywołania.  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Właściwości](./properties.md)
- [Klasy i struktury](./index.md)
