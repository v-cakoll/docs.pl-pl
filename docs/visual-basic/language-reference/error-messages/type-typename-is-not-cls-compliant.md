---
title: "Typ &lt;typename&gt; nie jest zgodne ze specyfikacją CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords: BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d45da3b061dff0f82c1155daf5724033261bbdaa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="type-lttypenamegt-is-not-cls-compliant"></a>Typ &lt;typename&gt; nie jest zgodne ze specyfikacją CLS
Zmienną, właściwością lub funkcji, zwracany jest zadeklarowana z typem danych, który nie jest zgodne ze specyfikacją CLS.  
  
 Dla aplikacji, aby było zgodne z [niezależność od języka i elementy niezależne od języka](https://msdn.microsoft.com/library/12a7a7h3) (ze specyfikacją CLS), należy użyć tylko typów zgodnych ze specyfikacją CLS.  
  
 Następujące [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] typy danych nie są zgodne ze specyfikacją CLS:  
  
-   [SByte — typ danych](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [Uinteger — typ danych](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [Ulong — typ danych](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [Ushort — typ danych](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 **Identyfikator błędu:** BC40041  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli aplikacja musi być zgodne ze specyfikacją CLS, Zmień typ danych tego elementu do najbliższego typu zgodne ze specyfikacją CLS. Na przykład zamiast z `UInteger` można użyć `Integer` Jeśli nie potrzebujesz zakres wartości powyżej 2 147 483 647. Jeśli potrzebujesz rozszerzonej zakresu, można zastąpić `UInteger` z `Long`.  
  
-   Jeśli aplikacja nie musi być zgodne ze specyfikacją CLS, jest konieczne wprowadzanie zmian. Należy pamiętać o jego niezgodności jednak.  
  
## <a name="see-also"></a>Zobacz też  
 [\<PAVE za pośrednictwem > Pisanie kodu zgodne ze specyfikacją CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
