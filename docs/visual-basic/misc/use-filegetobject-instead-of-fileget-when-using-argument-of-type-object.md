---
title: Użyj "Filegetobject —" zamiast "FileGet", jeśli korzystasz z argumentu typu "Object"
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: fdad64a4b35aa792c996d25a9fd72a9ce1126fbd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022548"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a>Użyj "Filegetobject —" zamiast "FileGet", jeśli korzystasz z argumentu typu "Object"
`FileGet` Metoda zawiera argument typu `Object`. `FileGetObject` powinny być używane zamiast `FileGet` Aby uniknąć niejednoznaczności.  
  
 Należy zauważyć, że funkcje oferowane przez `My.Computer.Filesystem` oferuje większą łatwość użycia i wydajności niż albo `FileGet` lub `FileGetObject`.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Zastąp `FileGet` z `FileGetObject`.  
  
2. Rzutowanie `Object` argument do bardziej określonego typu.  
  
## <a name="see-also"></a>Zobacz także

- [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
