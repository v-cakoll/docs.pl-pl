---
title: Użyj &#39;filegetobject —&#39; zamiast &#39;fileget —&#39; przy korzystaniu z argumentu typu &#39;obiektu&#39;
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 2edb80f6df95774e0ea5a7b51e57925845d7ba75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a>Użyj &#39;filegetobject —&#39; zamiast &#39;fileget —&#39; przy korzystaniu z argumentu typu &#39;obiektu&#39;
`FileGet` Metoda zawiera argument typu `Object`. `FileGetObject` powinien być używany zamiast `FileGet` Aby uniknąć niejednoznaczności.  
  
 Należy zauważyć, że funkcje oferowane przez `My.Computer.Filesystem` zapewnia większą łatwość użycia i wydajności niż albo `FileGet` lub `FileGetObject`.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Zastąp `FileGet` z `FileGetObject`.  
  
2.  Rzutowanie `Object` argument więcej określonego typu.  
  
## <a name="see-also"></a>Zobacz też  
   
 [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
