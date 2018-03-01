---
title: "Próba zapisu poza końcem pliku"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 27de462d5d28ee09107d75afe8269e7401c4dc39
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
