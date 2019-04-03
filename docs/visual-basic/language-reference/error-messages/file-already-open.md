---
title: Plik jest już otwarty
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: e565dbd6352a8f76290f3f58d62e2e14a18ef45f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823509"
---
# <a name="file-already-open"></a>Plik jest już otwarty
Czasami pliku muszą zostać zamknięte przed inny `FileOpen` lub może wystąpić inna operacja. Wśród możliwe przyczyny tego błędu są:  
  
-   Tryb sekwencyjne dane wyjściowe `FileOpen` operacja została wykonana dla pliku, który jest już otwarty  
  
-   Oświadczenie odnosi się do otwartego pliku.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Zamknij plik przed wykonaniem instrukcji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
