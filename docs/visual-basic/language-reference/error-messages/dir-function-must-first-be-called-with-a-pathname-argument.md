---
title: '&#39;Dir&#39; należy najpierw wywołać funkcję z &#39;PathName&#39; argumentu'
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: f7e9ef9cc6309f24ae9f8963e910b41180c029b7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518491"
---
# <a name="39dir39-function-must-first-be-called-with-a-39pathname39-argument"></a>&#39;Dir&#39; należy najpierw wywołać funkcję z &#39;PathName&#39; argumentu
Początkowe wywołanie `Dir` nie ma funkcji `PathName` argumentu. Pierwsze wywołanie `Dir` musi zawierać `PathName`, ale kolejne wywołania `Dir` nie trzeba podawać parametrów, aby pobrać następny element.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Podaj `PathName` argumentu w wywołaniu funkcji.  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
