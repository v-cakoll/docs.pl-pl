---
title: Należy najpierw wywołać funkcję „Dir” z argumentem „PathName”
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: d255b8dddd098835764f72b8a166eaa08b0353df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803457"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a>Należy najpierw wywołać funkcję „Dir” z argumentem „PathName”
Początkowe wywołanie `Dir` nie ma funkcji `PathName` argumentu. Pierwsze wywołanie `Dir` musi zawierać `PathName`, ale kolejne wywołania `Dir` nie trzeba podawać parametrów, aby pobrać następny element.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Podaj `PathName` argumentu w wywołaniu funkcji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
