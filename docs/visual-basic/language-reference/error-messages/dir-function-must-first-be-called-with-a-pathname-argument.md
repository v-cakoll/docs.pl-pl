---
title: Należy najpierw wywołać funkcję „Dir” z argumentem „PathName”
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 828c715d9aaceef17d030113e7eda302f025ca9d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55282597"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a>Należy najpierw wywołać funkcję „Dir” z argumentem „PathName”
Początkowe wywołanie `Dir` nie ma funkcji `PathName` argumentu. Pierwsze wywołanie `Dir` musi zawierać `PathName`, ale kolejne wywołania `Dir` nie trzeba podawać parametrów, aby pobrać następny element.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Podaj `PathName` argumentu w wywołaniu funkcji.  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
