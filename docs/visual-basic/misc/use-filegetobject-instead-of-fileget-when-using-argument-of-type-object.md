---
title: "Użyj &#39; Filegetobject — &#39; zamiast &#39; Fileget — &#39; przy korzystaniu z argumentu typu &#39; obiekt &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 090b8088-895a-482a-9362-606596bac304
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c5be466a8a0339bdb57818755d85a26d632d774
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a>Użyj &#39; Filegetobject — &#39; zamiast &#39; Fileget — &#39; przy korzystaniu z argumentu typu &#39; obiekt &#39;
`FileGet` Metoda zawiera argument typu `Object`. `FileGetObject`powinien być używany zamiast `FileGet` Aby uniknąć niejednoznaczności.  
  
 Należy zauważyć, że funkcje oferowane przez `My.Computer.Filesystem` zapewnia większą łatwość użycia i wydajności niż albo `FileGet` lub `FileGetObject`.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Zastąp `FileGet` z `FileGetObject`.  
  
2.  Rzutowanie `Object` argument więcej określonego typu.  
  
## <a name="see-also"></a>Zobacz też  
   
 [My.Computer.FileSystem —](xref:Microsoft.VisualBasic.FileIO.FileSystem)
