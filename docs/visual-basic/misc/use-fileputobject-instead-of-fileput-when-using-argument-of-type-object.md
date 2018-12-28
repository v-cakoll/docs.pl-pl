---
title: Użyj "FilePutObject" zamiast "FilePut, jeśli korzystasz z argumentu typu"Object"
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: df7d7c54992984bcb1684e41f60ae8361a3aed03
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2018
ms.locfileid: "53774228"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a>Użyj "FilePutObject" zamiast "FilePut, jeśli korzystasz z argumentu typu"Object"
`FilePut` Metoda zawiera argument typu `Object`. `FilePutObject` powinny być używane zamiast `FilePut` Aby uniknąć niejednoznaczności.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zastąp `FilePut` z `FilePutObject`.  
  
-   Rzutowanie `Object` argument do bardziej określonego typu.  
  
-   Użyj funkcji dostępnych w `My.Computer.FileSystem` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
   
 [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [My.Computer.FileSystem.WriteAllBytes](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
