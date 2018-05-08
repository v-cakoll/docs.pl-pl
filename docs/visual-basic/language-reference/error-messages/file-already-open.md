---
title: Plik jest już otwarty
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 75a08b411a4afd7ea8e11953f1d465b082faa712
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="file-already-open"></a>Plik jest już otwarty
Czasami pliku muszą zostać zamknięte przed inne `FileOpen` lub można wykonać innych operacji. Wśród możliwych przyczyn tego błędu są:  
  
-   Tryb sekwencyjnych dane wyjściowe `FileOpen` operacja została wykonana dla pliku, który jest już otwarty  
  
-   Oświadczenie odnosi się do otwartego pliku.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Zamknij plik przed wykonaniem instrukcji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
