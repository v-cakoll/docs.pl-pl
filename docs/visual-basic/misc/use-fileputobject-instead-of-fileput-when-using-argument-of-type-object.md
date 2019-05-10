---
title: Użyj "FilePutObject" zamiast "FilePut, jeśli korzystasz z argumentu typu"Object"
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: bf1f50d0d8eb9b0b8518075b0e48f40645a02a25
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913213"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a>Użyj "FilePutObject" zamiast "FilePut, jeśli korzystasz z argumentu typu"Object"
`FilePut` Metoda zawiera argument typu `Object`. `FilePutObject` powinny być używane zamiast `FilePut` Aby uniknąć niejednoznaczności.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Zastąp `FilePut` z `FilePutObject`.  
  
- Rzutowanie `Object` argument do bardziej określonego typu.  
  
- Użyj funkcji dostępnych w `My.Computer.FileSystem` obiektu.  
  
## <a name="see-also"></a>Zobacz także

- [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [My.Computer.FileSystem.WriteAllBytes](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
