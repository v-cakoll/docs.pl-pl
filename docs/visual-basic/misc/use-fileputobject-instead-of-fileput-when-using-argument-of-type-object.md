---
title: Użyj "FilePutObject" zamiast "FilePut, jeśli korzystasz z argumentu typu"Object"
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 3d793151905c61ee12eccdfdb5e9567a4924bb35
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725561"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a>Użyj "FilePutObject" zamiast "FilePut, jeśli korzystasz z argumentu typu"Object"
`FilePut` Metoda zawiera argument typu `Object`. `FilePutObject` powinny być używane zamiast `FilePut` Aby uniknąć niejednoznaczności.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zastąp `FilePut` z `FilePutObject`.  
  
-   Rzutowanie `Object` argument do bardziej określonego typu.  
  
-   Użyj funkcji dostępnych w `My.Computer.FileSystem` obiektu.  
  
## <a name="see-also"></a>Zobacz także

- [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [My.Computer.FileSystem.WriteAllBytes](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
