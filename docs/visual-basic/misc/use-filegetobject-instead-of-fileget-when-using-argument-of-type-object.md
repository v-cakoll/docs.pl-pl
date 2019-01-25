---
title: Użyj "Filegetobject —" zamiast "FileGet", jeśli korzystasz z argumentu typu "Object"
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 60eaabc686070aced908116728f06d4e82b5cecb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723397"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a>Użyj "Filegetobject —" zamiast "FileGet", jeśli korzystasz z argumentu typu "Object"
`FileGet` Metoda zawiera argument typu `Object`. `FileGetObject` powinny być używane zamiast `FileGet` Aby uniknąć niejednoznaczności.  
  
 Należy zauważyć, że funkcje oferowane przez `My.Computer.Filesystem` oferuje większą łatwość użycia i wydajności niż albo `FileGet` lub `FileGetObject`.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Zastąp `FileGet` z `FileGetObject`.  
  
2.  Rzutowanie `Object` argument do bardziej określonego typu.  
  
## <a name="see-also"></a>Zobacz także

- [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
