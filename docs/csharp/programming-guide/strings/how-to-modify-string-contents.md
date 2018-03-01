---
title: "Porady: modyfikowanie zawartości ciągu (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- strings [C#], modifying
ms.assetid: b6c20bba-ce22-43d7-ad1b-5ce65f714055
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b0810d5722c2c32f7884187bb2e3fc5a039825c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-string-contents-c-programming-guide"></a>Porady: modyfikowanie zawartości ciągu (Przewodnik programowania w języku C#)
Ponieważ ciągi są *niezmienialnych*, nie jest możliwe (bez użycia niebezpiecznego kodu) Aby zmodyfikować wartość ciągu obiektu po jego utworzeniu. Jednak istnieje wiele sposobów, aby zmodyfikować wartość ciągu i zapisać wynik w nowym obiekcie string. <xref:System.String?displayProperty=nameWithType> Klasa udostępnia metody, które pracują na dane wejściowe ciągu i zwraca nowy obiekt ciągu. W wielu przypadkach nowego obiektu można przypisać do zmiennej, która przechowywać oryginalnego ciągu. <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> Klasa udostępnia dodatkowe metody, które działają w podobny sposób. <xref:System.Text.StringBuilder?displayProperty=nameWithType> Klasa udostępnia buforu znak, który można modyfikować "w miejscu." Należy wywołać <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> metodę, aby utworzyć nowy obiekt ciągu zawierający bieżącą zawartość buforu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia różne sposoby Zamień lub usuń podciągów w określonym ciągu.  
  
 [!code-csharp[csProgGuideStrings#28](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_1.cs)]  
  
## <a name="example"></a>Przykład  
 Aby uzyskać dostęp do poszczególnych znaków w ciągu przy użyciu notacji tablicy, można użyć <xref:System.Text.StringBuilder> obiektu, który overloads `[]` operatora, aby zapewnić dostęp do buforu wewnętrznego znaków. Możesz również przekonwertować ciągu do tablicy znaków, za pomocą <xref:System.String.ToCharArray%2A> metody. W poniższym przykładzie użyto `ToCharArray` do utworzenia tablicy. Niektóre elementy tej tablicy następnie są modyfikowane. Ciąg konstruktora, który przyjmuje wartość typu char tablicy jako parametr wejściowy jest następnie wywoływana w celu utworzenia nowych parametrów.  
  
 [!code-csharp[csProgGuideStrings#24](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_2.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład jest dostępna dla tych bardzo rzadko sytuacje, w których można zmodyfikować ciąg w miejscu przy użyciu niebezpiecznego kodu w sposób podobny do tablic char w stylu języka C. W przykładzie przedstawiono sposób dostępu do poszczególnych znaków "w miejscu" za pomocą fixed — słowo kluczowe. Ilustruje też jedną możliwe ubocznym niebezpieczne operacje na ciągach będącą wynikiem sposób kompilatora C# wewnętrznie przechowuje ciągi (stażystów). Ogólnie rzecz biorąc możesz nie powinni używać tej metody, chyba że jest bezwzględnie konieczne.  
  
 [!code-csharp[csProgGuideStrings#29](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_3.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Ciągi](../../../csharp/programming-guide/strings/index.md)
