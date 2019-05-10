---
title: Plik jest już otwarty
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 8ec878e04b0128c997c5be51d2c714d55abcde8c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665119"
---
# <a name="file-already-open"></a>Plik jest już otwarty
Czasami pliku muszą zostać zamknięte przed inny `FileOpen` lub może wystąpić inna operacja. Wśród możliwe przyczyny tego błędu są:  
  
- Tryb sekwencyjne dane wyjściowe `FileOpen` operacja została wykonana dla pliku, który jest już otwarty  
  
- Oświadczenie odnosi się do otwartego pliku.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Zamknij plik przed wykonaniem instrukcji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
