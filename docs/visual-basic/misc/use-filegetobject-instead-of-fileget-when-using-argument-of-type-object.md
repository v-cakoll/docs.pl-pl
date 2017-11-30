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
ms.openlocfilehash: 996e8a50f90c738bbc64c200125a785c0e9bcd58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a>Użyj &#39; Filegetobject — &#39; zamiast &#39; Fileget — &#39; przy korzystaniu z argumentu typu &#39; obiekt &#39;
`FileGet` Metoda zawiera argument typu `Object`. `FileGetObject`powinien być używany zamiast `FileGet` Aby uniknąć niejednoznaczności.  
  
 Należy zauważyć, że funkcje oferowane przez `My.Computer.Filesystem` zapewnia większą łatwość użycia i wydajności niż albo `FileGet` lub `FileGetObject`.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Zastąp `FileGet` z `FileGetObject`.  
  
2.  Rzutowanie `Object` argument więcej określonego typu.  
  
## <a name="see-also"></a>Zobacz też  
 [NIE w kompilacji: Filegetobject — funkcja](http://msdn.microsoft.com/en-us/3eda786b-d1ee-4b44-9dd7-0ea6bff072c0)  
 [My.Computer.FileSystem — obiekt](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md)
