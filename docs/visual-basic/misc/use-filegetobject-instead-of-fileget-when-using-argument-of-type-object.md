---
title: Użyj "Filegetobject —" zamiast "FileGet", jeśli korzystasz z argumentu typu "Object"
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: ddbe187ed1210d238448a5ff3feaee18beea1def
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2018
ms.locfileid: "53768014"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a>Użyj "Filegetobject —" zamiast "FileGet", jeśli korzystasz z argumentu typu "Object"
`FileGet` Metoda zawiera argument typu `Object`. `FileGetObject` powinny być używane zamiast `FileGet` Aby uniknąć niejednoznaczności.  
  
 Należy zauważyć, że funkcje oferowane przez `My.Computer.Filesystem` oferuje większą łatwość użycia i wydajności niż albo `FileGet` lub `FileGetObject`.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Zastąp `FileGet` z `FileGetObject`.  
  
2.  Rzutowanie `Object` argument do bardziej określonego typu.  
  
## <a name="see-also"></a>Zobacz też  
   
 [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
