---
title: Nie można wielokrotnie zastosować atrybutu „<attributename>”.
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 14145f165adf5ccd20298a70ca5596488b488b0c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409962"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a>Nie można wielokrotnie zastosować atrybutu „\<attributename>”.

Ten atrybut może być stosowany tylko raz. Ten `AttributeUsage` atrybut określa, czy atrybut może być stosowany więcej niż jeden raz.  
  
 **Identyfikator błędu:** BC30663  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Upewnij się, że atrybut jest stosowany tylko raz.  
  
2. Jeśli używasz niestandardowych atrybutów, Rozważ zmianę ich `AttributeUsage` atrybutu w celu zezwolenia na użycie wielu atrybutów, jak w poniższym przykładzie.  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.AttributeUsageAttribute>
- [Tworzenie atrybutów niestandardowych](../../programming-guide/concepts/attributes/creating-custom-attributes.md)
- [AttributeUsage](../../programming-guide/concepts/attributes/attributeusage.md)
