---
title: Próba zapisu poza końcem pliku
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: abd5f5c6e5df262d1deadd74f0a146a8d436ceb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="input-past-end-of-file"></a>Próba zapisu poza końcem pliku
Albo `Input` instrukcji jest odczytu z pliku, który jest pusty lub jeden w którym wszystkie dane są używane, lub użyto `EOF` funkcji przy użyciu pliku otwarte dostęp do danych binarnych.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Użyj `EOF` funkcji bezpośrednio przed `Input` instrukcji, aby wykryć koniec pliku.  
  
2.  Jeśli plik jest otwarty, aby uzyskać dostęp do danych binarnych, użyj `Seek` i `Loc`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileSystem.Input%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
