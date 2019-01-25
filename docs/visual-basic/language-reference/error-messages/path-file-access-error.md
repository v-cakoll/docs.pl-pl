---
title: Błąd dostępu do ścieżki / pliku
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: 53f021faa9e4ae69a71d825ca823e1180421afc6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522482"
---
# <a name="pathfile-access-error"></a>Błąd dostępu do ścieżki/pliku
Podczas operacji uzyskiwania dostępu do plików lub dostępu do dysku systemu operacyjnego nie można ustanowić połączenia między ścieżkę i nazwę pliku.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że specyfikacja plików jest poprawnie sformatowana. Nazwa pliku może zawierać w pełni kwalifikowana (bezwzględny) lub względny ścieżki. W pełni kwalifikowana ścieżka zaczyna się od nazwy dysku (Jeśli ścieżka znajduje się na innym dysku) i wyświetla jawna ścieżka z katalogu głównego, do pliku. Dowolną ścieżkę, która nie jest w pełni kwalifikowany jest określana względem bieżącego dysku i katalogu.  
  
2.  Upewnij się, że użytkownik nie podjęła próby zapisania pliku, który zastąpi istniejący plik tylko do odczytu. Jeśli jest to możliwe, zmień atrybut tylko do odczytu pliku docelowego lub zapisać plik pod inną nazwą pliku.  
  
3.  Upewnij się, że nie podjęła próby otwarcia pliku tylko do odczytu w kolejnych `Output` lub `Append` trybu. Jeśli jest to możliwe, otwórz plik w `Input` tryb lub zmień atrybut tylko do odczytu pliku.  
  
4.  Upewnij się, że nie podjęła próby zmiany w projektach Visual Basic w bazie danych lub dokumentu.  
  
## <a name="see-also"></a>Zobacz także
- [Typy błędów](../../../visual-basic/programming-guide/language-features/error-types.md)
