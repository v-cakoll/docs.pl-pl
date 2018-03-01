---
title: "&#39; Dir &#39; należy najpierw wywołać funkcję w z &#39; Nazwa ścieżki &#39; argument"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 843918fe9cb0b9dece076b5dc1373c3571588caa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="39dir39-function-must-first-be-called-with-a-39pathname39-argument"></a>&#39; Dir &#39; należy najpierw wywołać funkcję w z &#39; Nazwa ścieżki &#39; argument
Wywołanie początkowej `Dir` nie ma funkcji `PathName` argumentu. W pierwszym wywołaniu `Dir` musi zawierać `PathName`, ale kolejnych wywołań `Dir` nie trzeba podawać parametry do pobrania następnej.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Podaj `PathName` argument w wywołaniu funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
