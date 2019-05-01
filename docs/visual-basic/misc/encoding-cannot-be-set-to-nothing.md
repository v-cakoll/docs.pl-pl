---
title: Kodowanie nie można ustawić na wartość Nothing
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 30b0b4a29fbdf931aa62263b75d1fa946e87b145
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970329"
---
# <a name="encoding-cannot-be-set-to-nothing"></a>Kodowanie nie można ustawić na wartość Nothing
Podjęto próbę odczytu z lub zapisu w pliku nie powiodło się, ponieważ parametr `encoding` został ustawiony na `Nothing` , ale wymaga prawidłowej wartości.  
  
 <xref:System.Text.Encoding> Służy do określenia, jakie szyfrowanie do użycia podczas zapisywania do pliku. Wartość domyślna to UTF-8.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Podaj prawidłową wartość dla `encoding` parametru.  
  
## <a name="see-also"></a>Zobacz także

- [Kodowanie pliku](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
- [Odczyt z plików](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Zapisywanie w plikach](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [My.Computer.FileSystem.ReadAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [My.Computer.FileSystem.WriteAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
