---
title: Kodowanie nie można ustawić na wartość Nothing
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 99dbd1a068cabca7f57b6d5e8dd13e1069aede65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691336"
---
# <a name="encoding-cannot-be-set-to-nothing"></a>Kodowanie nie można ustawić na wartość Nothing
Podjęto próbę odczytu z lub zapisu w pliku nie powiodło się, ponieważ parametr `encoding` został ustawiony na `Nothing` , ale wymaga prawidłowej wartości.  
  
 <xref:System.Text.Encoding> Służy do określenia, jakie szyfrowanie do użycia podczas zapisywania do pliku. Wartość domyślna to UTF-8.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Podaj prawidłową wartość dla `encoding` parametru.  
  
## <a name="see-also"></a>Zobacz także
- [Kodowanie pliku](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
- [Odczyt z plików](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Zapisywanie w plikach](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [My.Computer.FileSystem.ReadAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [My.Computer.FileSystem.WriteAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
