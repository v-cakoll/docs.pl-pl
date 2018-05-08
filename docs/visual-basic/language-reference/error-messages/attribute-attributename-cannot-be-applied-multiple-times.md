---
title: Atrybut &#39; &lt;attributename&gt; &#39; nie można zastosować wiele razy
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: df97a4e391406661db98eb1c958c0e12e45b6c49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a>Atrybut &#39; &lt;attributename&gt; &#39; nie można zastosować wiele razy
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
