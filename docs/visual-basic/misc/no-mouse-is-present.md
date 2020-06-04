---
title: Żadna mysz nie jest obecna
ms.date: 07/20/2015
f1_keywords:
- vbrMouse_NoMouseIsPresent
ms.assetid: 4472fd57-4217-4463-9d3c-dc4a8fe88f1b
ms.openlocfilehash: 748661cae35292968aae989789a96d1df855b6ce
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84376127"
---
# <a name="no-mouse-is-present"></a>Żadna mysz nie jest obecna
Jedna z właściwości `My.Computer.Mouse` obiektu została wywołana, ale na komputerze nie jest zainstalowany mysz ani port myszy.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Dodaj `Try...Catch` blok wokół wywołania właściwości `My.Computer.Mouse` obiektu.  
  
     oraz  
  
- Zainstaluj myszą na komputerze.  
  
## <a name="see-also"></a>Zobacz też

- [My. Computer. Mouse](xref:Microsoft.VisualBasic.Devices.Mouse)
- [Obsługa i zgłaszanie wyjątków w programie .NET](../../standard/exceptions/index.md)
- [Try...Catch...Finally, instrukcja](../language-reference/statements/try-catch-finally-statement.md)
