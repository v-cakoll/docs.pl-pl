---
title: Nie można wielokrotnie zastosować atrybutu „<attributename>”.
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 62e84d174e4e218472eda9b7c08ed677e0140438
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278710"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a>Atrybut "\<attributename >" nie można zastosować wiele razy
Ten atrybut można zastosować tylko raz. `AttributeUsage` Atrybut określa, czy atrybut można zastosować więcej niż raz.  
  
 **Identyfikator błędu:** BC30663  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że ten atrybut jest stosowany tylko raz.  
  
2.  Jeśli używasz atrybutów niestandardowych, które utworzono, należy rozważyć zmianę ich `AttributeUsage` atrybutu, aby zezwolić na użycie wielu atrybutu, podobnie jak w poniższym przykładzie.  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.AttributeUsageAttribute>
- [Tworzenie atrybutów niestandardowych](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [AttributeUsage](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
