---
title: "Użyj &#39; FilePutObject &#39; zamiast &#39; FilePut &#39; przy korzystaniu z argumentu typu &#39; obiekt &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5612c2bd4dc08f767643d2cd865a2ba1a8210c15
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a>Użyj &#39; FilePutObject &#39; zamiast &#39; FilePut &#39; przy korzystaniu z argumentu typu &#39; obiekt &#39;
`FilePut` Metoda zawiera argument typu `Object`. `FilePutObject`powinien być używany zamiast `FilePut` Aby uniknąć niejednoznaczności.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zastąp `FilePut` z `FilePutObject`.  
  
-   Rzutowanie `Object` argument więcej określonego typu.  
  
-   Użyj funkcji dostępnych w `My.Computer.FileSystem` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
   
 [My.Computer.FileSystem —](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [My.Computer.FileSystem.WriteAllBytes](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
