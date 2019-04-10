---
title: Zła nazwa lub numer pliku
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 2e5d4a3ddd66df85dc4758e22b36ac1ed495659a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322163"
---
# <a name="bad-file-name-or-number"></a>Zła nazwa lub numer pliku
Wystąpił błąd podczas próby uzyskania dostępu do określonego pliku. Wśród możliwych przyczyn tego błędu są:  
  
-   Oświadczenie odnosi się do pliku przy użyciu nazwy pliku lub numeru, który nie został określony w `FileOpen` instrukcji lub która została określona w `FileOpen` instrukcji, jednak podano wartość następnie zamknięty.  
  
-   Oświadczenie odnosi się do pliku z numerem, który znajduje się poza zakresem numerów plików.  
  
-   Oświadczenie odnosi się do nazwy pliku lub numer, który jest nieprawidłowy.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Upewnij się, że nazwa pliku jest określona w `FileOpen` instrukcji. Należy pamiętać, że po wywołaniu `FileClose` instrukcji bez argumentów, może przypadkowo zamknięto wszystkie otwarte pliki.  
  
2. Jeśli Twój kod generuje algorithmically liczby plików, upewnij się, że cyfry są prawidłowe.  
  
3. Sprawdź nazwy pliku, aby upewnić się, że są one zgodne z konwencjami systemu operacyjnego.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [Visual Basic — Konwencje nazewnictwa](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
