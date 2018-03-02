---
title: "Porady: wyszukiwanie ciągów za pomocą wyrażeń regularnych (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with RegEx
ms.assetid: dcab2150-a4a2-4fe4-87e3-83b83b58d84a
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c851c57b44f1343816b905db002e530121fb6c0a
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="how-to-search-strings-using-regular-expressions-c-programming-guide"></a>Porady: wyszukiwanie ciągów za pomocą wyrażeń regularnych (Przewodnik programowania w języku C#)
<xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> Klasa może być używana do wyszukiwania ciągów. Te wyszukiwania można dostosować w zakresie w złożoności pełnego wykorzystania wyrażeń regularnych z bardzo proste. Poniżej przedstawiono dwa przykłady ciąg wyszukiwania przy użyciu <xref:System.Text.RegularExpressions.Regex> klasy. Aby uzyskać więcej informacji, zobacz [wyrażeń regularnych programu .NET Framework](https://msdn.microsoft.com/library/hs600312).  
  
## <a name="example"></a>Przykład  
 Następujący kod jest aplikacja konsolowa, która wykonuje proste wyszukiwanie bez uwzględniania wielkości liter ciągów w tablicy. Statyczna metoda <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> wykonuje wyszukiwanie podany ciąg do wyszukania i ciąg, który zawiera wzorzec wyszukiwania. W takim przypadku trzeci argument jest służy do wskazania, wielkość liter powinna być ignorowana. Aby uzyskać więcej informacji, zobacz <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.  
  
 [!code-csharp[csProgGuideStrings#17](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_1.cs)]  
  
## <a name="example"></a>Przykład  
 Następujący kod jest aplikacja konsolowa, która używa wyrażeń regularnych do walidacji format każdego ciągu w tablicy. Wymaga weryfikacji każdy ciąg formę numeru telefonu, w którym trzech grup cyfr są oddzielone kreskami, najpierw dwie grupy zawiera trzy cyfry i trzecia grupa zawiera cztery cyfry. Jest to zrobić za pomocą wyrażenia regularnego `^\\d{3}-\\d{3}-\\d{4}$`. Aby uzyskać więcej informacji, zobacz [język wyrażeń regularnych — podręczny wykaz](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c).  
  
 [!code-csharp[csProgGuideStrings#18](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_2.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Ciągi](../../../csharp/programming-guide/strings/index.md)  
 [.NET framework — nieprawidłowe wyrażenia](https://msdn.microsoft.com/library/hs600312)  
 [Język wyrażeń regularnych — podręczny wykaz](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c)
