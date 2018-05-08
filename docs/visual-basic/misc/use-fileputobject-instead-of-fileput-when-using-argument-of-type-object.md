---
title: Użyj &#39;FilePutObject&#39; zamiast &#39;FilePut&#39; przy korzystaniu z argumentu typu &#39;obiektu&#39;
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 529352d98c175981c20861205ce04c8a2ebcdca9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a>Użyj &#39;FilePutObject&#39; zamiast &#39;FilePut&#39; przy korzystaniu z argumentu typu &#39;obiektu&#39;
`FilePut` Metoda zawiera argument typu `Object`. `FilePutObject` powinien być używany zamiast `FilePut` Aby uniknąć niejednoznaczności.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zastąp `FilePut` z `FilePutObject`.  
  
-   Rzutowanie `Object` argument więcej określonego typu.  
  
-   Użyj funkcji dostępnych w `My.Computer.FileSystem` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
   
 [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [My.Computer.FileSystem.WriteAllBytes](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
