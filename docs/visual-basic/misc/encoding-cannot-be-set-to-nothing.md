---
title: Nie można ustawić wartości Nothing dla kodowania
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 41565d1aa3b69f6ad92d4bbf2b2f2170014aef87
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394482"
---
# <a name="encoding-cannot-be-set-to-nothing"></a>Nie można ustawić wartości Nothing dla kodowania
Próba odczytu z pliku lub zapisu do niego nie powiodła się, ponieważ parametr został `encoding` ustawiony na `Nothing` wartość, ale wymaga prawidłowej wartości.  
  
 <xref:System.Text.Encoding>służy do określania kodowania, które ma być używane podczas zapisywania w pliku. Domyślnym ustawieniem jest UTF-8.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Podaj prawidłową wartość `encoding` parametru.  
  
## <a name="see-also"></a>Zobacz też

- [Kodowanie pliku](../developing-apps/programming/drives-directories-files/file-encodings.md)
- [Odczyt z plików](../developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Zapisywanie w plikach](../developing-apps/programming/drives-directories-files/writing-to-files.md)
- [My. Computer. FileSystem. ReadAllText obiektu](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [My. Computer. FileSystem. WriteAllText —](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
