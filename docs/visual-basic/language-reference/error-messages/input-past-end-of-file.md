---
title: Próba zapisu poza końcem pliku
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: 29a9b5ce3c3f8e6a02b52beda1338fd699143570
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491340"
---
# <a name="input-past-end-of-file"></a>Próba zapisu poza końcem pliku
Albo `Input` instrukcji jest odczytu z pliku, który jest pusty lub w którym wszystkie dane są używane, lub możesz użyć `EOF` funkcji przy użyciu pliku otwarty dostęp do danych binarnych.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Użyj `EOF` funkcji tuż przed `Input` instrukcję, aby wykrywać koniec pliku.  
  
2.  Jeśli plik jest otwarty, aby uzyskać dostęp do danych binarnych, należy użyć `Seek` i `Loc`.  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.FileSystem.Input%2A>
- <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
