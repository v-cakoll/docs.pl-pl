---
title: Nie można wielokrotnie zastosować atrybutu „<attributename>”.
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: f2f4dc428a247275f9919c4a8b6e6944a558eef0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968224"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a>Nie można wielokrotnie zastosować atrybutu "\<AttributeName >"

Ten atrybut może być stosowany tylko raz. Atrybut `AttributeUsage` określa, czy atrybut może być stosowany więcej niż jeden raz.  
  
 **Identyfikator błędu:** BC30663  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Upewnij się, że atrybut jest stosowany tylko raz.  
  
2. Jeśli używasz niestandardowych atrybutów, Rozważ zmianę ich atrybutu `AttributeUsage`, aby zezwolić na użycie wielu atrybutów, jak w poniższym przykładzie.  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.AttributeUsageAttribute>
- [Tworzenie atrybutów niestandardowych](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [AttributeUsage](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
