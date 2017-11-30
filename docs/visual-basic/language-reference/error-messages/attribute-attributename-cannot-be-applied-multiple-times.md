---
title: "Atrybut &#39; &lt;attributename&gt;&#39; nie można zastosować wiele razy"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords: BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 216cf54fd164ca95b6378517a679b5b54183559f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a>Atrybut &#39; &lt;attributename&gt;&#39; nie można zastosować wiele razy
Ten atrybut można zastosować tylko raz. `AttributeUsage` Atrybut określa, czy atrybut można zastosować więcej niż raz.  
  
 **Identyfikator błędu:** BC30663  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że ten atrybut jest stosowana tylko raz.  
  
2.  Jeśli korzystasz z atrybutów niestandardowych, które utworzono, należy rozważyć zmianę ich `AttributeUsage` atrybutu aby umożliwić użycie atrybutu wiele, podobnie jak w poniższym przykładzie.  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.AttributeUsageAttribute>  
 [Tworzenie atrybutów niestandardowych](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [AttributeUsage](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
