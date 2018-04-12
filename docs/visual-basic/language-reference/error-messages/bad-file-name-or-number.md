---
title: Zła nazwa lub numer pliku
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3d7c8bae3df0e75a1c4f9afacdff681a553503d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="bad-file-name-or-number"></a>Zła nazwa lub numer pliku
Wystąpił błąd podczas próby uzyskania dostępu do określonego pliku. Wśród możliwych przyczyn tego błędu są:  
  
-   Oświadczenie odnosi się do pliku za pomocą nazwy pliku i numer, który nie został określony w `FileOpen` instrukcji lub która została określona w `FileOpen` instrukcji, jednak podano następnie zamknięte.  
  
-   Oświadczenie odnosi się do pliku z numerem, który znajduje się poza zakresem numerów plików.  
  
-   Oświadczenie odnosi się do nazwy pliku lub liczba, która jest nieprawidłowa.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że nazwa pliku jest określona w `FileOpen` instrukcji. Należy pamiętać, że jeśli zostanie wywołany `FileClose` instrukcji bez argumentów, może spowodować niezamierzoną zamknięciu wszystkich otwartych plików.  
  
2.  Jeśli kod jest generowany numerów plików algorithmically, upewnij się, że numery są prawidłowe.  
  
3.  Sprawdź nazwy pliku, aby upewnić się, że są one zgodne z konwencjami systemu operacyjnego.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>  
 [Visual Basic — konwencje nazewnictwa](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
