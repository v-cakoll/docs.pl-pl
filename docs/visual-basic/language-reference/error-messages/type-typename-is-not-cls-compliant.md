---
title: "Typ &lt;typename&gt; nie jest zgodne ze specyfikacją CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 36a49ccf7d2185c26ef8d23eebea216cc193d951
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="type-lttypenamegt-is-not-cls-compliant"></a>Typ &lt;typename&gt; nie jest zgodne ze specyfikacją CLS
Zmienną, właściwością lub funkcji, zwracany jest zadeklarowana z typem danych, który nie jest zgodne ze specyfikacją CLS.  
  
 Dla aplikacji, aby było zgodne z [niezależność od języka i elementy niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (ze specyfikacją CLS), należy użyć tylko typów zgodnych ze specyfikacją CLS.  
  
 Następujące [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] typy danych nie są zgodne ze specyfikacją CLS:  
  
-   [SByte, typ danych](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger, typ danych](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong, typ danych](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort, typ danych](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 **Identyfikator błędu:** BC40041  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli aplikacja musi być zgodne ze specyfikacją CLS, Zmień typ danych tego elementu do najbliższego typu zgodne ze specyfikacją CLS. Na przykład zamiast z `UInteger` można użyć `Integer` Jeśli nie potrzebujesz zakres wartości powyżej 2 147 483 647. Jeśli potrzebujesz rozszerzonej zakresu, można zastąpić `UInteger` z `Long`.  
  
-   Jeśli aplikacja nie musi być zgodne ze specyfikacją CLS, jest konieczne wprowadzanie zmian. Należy pamiętać o jego niezgodności jednak.