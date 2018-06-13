---
title: '&#39;Dir&#39; należy najpierw wywołać funkcję z &#39;PathName&#39; argumentu'
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 3a271d7c2c2f7b98bae8f3f6fa9b67b65e3548f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585463"
---
# <a name="39dir39-function-must-first-be-called-with-a-39pathname39-argument"></a>&#39;Dir&#39; należy najpierw wywołać funkcję z &#39;PathName&#39; argumentu
Wywołanie początkowej `Dir` nie ma funkcji `PathName` argumentu. W pierwszym wywołaniu `Dir` musi zawierać `PathName`, ale kolejnych wywołań `Dir` nie trzeba podawać parametry do pobrania następnej.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Podaj `PathName` argument w wywołaniu funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
