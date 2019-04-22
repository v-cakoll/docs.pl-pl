---
title: Plik jest już otwarty
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 401801c7c9072ce11f9eafdb84f2b377669ae545
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770363"
---
# <a name="file-already-open"></a>Plik jest już otwarty
Czasami pliku muszą zostać zamknięte przed inny `FileOpen` lub może wystąpić inna operacja. Wśród możliwe przyczyny tego błędu są:  
  
-   Tryb sekwencyjne dane wyjściowe `FileOpen` operacja została wykonana dla pliku, który jest już otwarty  
  
-   Oświadczenie odnosi się do otwartego pliku.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Zamknij plik przed wykonaniem instrukcji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
