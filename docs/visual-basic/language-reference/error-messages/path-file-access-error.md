---
title: Błąd dostępu do ścieżki pliku
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: 83ce8615b173a6f5835347ebc561a793655ec8f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="pathfile-access-error"></a>Błąd dostępu do ścieżki/pliku
Podczas operacji dostępu do plików lub dostępu do dysku systemu operacyjnego nie można ustanowić połączenia między ścieżkę i nazwę pliku.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że specyfikacji pliku jest poprawnie sformatowana. Nazwa pliku może zawierać pełną (bezwzględna) lub względna ścieżka. Jest w pełni kwalifikowana ścieżka zaczyna się od nazwy dysku (jeśli znajduje się na innym dysku) i wyświetla jawne ścieżka od elementu głównego do pliku. Dowolną ścieżkę, która nie jest w pełni kwalifikowana jest względne wobec bieżącego dysku i katalogu.  
  
2.  Upewnij się, że nie próbował zapisać plik, który zastąpić istniejący plik tylko do odczytu. Jeśli jest to możliwe, zmień ten atrybut tylko do odczytu z pliku docelowego lub Zapisz plik z inną nazwą pliku.  
  
3.  Upewnij się, że nie próbując otworzyć plik tylko do odczytu w kolejnych `Output` lub `Append` tryb. Jeśli tak jest, otwórz plik w `Input` tryb lub zmień ten atrybut tylko do odczytu pliku.  
  
4.  Upewnij się, że nie próbował zmienić projekt Visual Basic w bazie danych lub dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy błędów](../../../visual-basic/programming-guide/language-features/error-types.md)
