---
title: Zła nazwa lub numer pliku
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 903be68e71ad590b4b669545afd077175534ef4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585570"
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
