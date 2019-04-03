---
title: Próba zapisu poza końcem pliku
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: 63b099144b9da601a7b52a738f5a3173097ae257
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813161"
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
