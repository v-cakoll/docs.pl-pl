---
title: Należy najpierw wywołać funkcję „Dir” z argumentem „PathName”
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: d255b8dddd098835764f72b8a166eaa08b0353df
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767893"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a>Należy najpierw wywołać funkcję „Dir” z argumentem „PathName”
Początkowe wywołanie `Dir` nie ma funkcji `PathName` argumentu. Pierwsze wywołanie `Dir` musi zawierać `PathName`, ale kolejne wywołania `Dir` nie trzeba podawać parametrów, aby pobrać następny element.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Podaj `PathName` argumentu w wywołaniu funkcji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
