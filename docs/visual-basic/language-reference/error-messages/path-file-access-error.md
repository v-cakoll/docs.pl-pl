---
title: Błąd dostępu do ścieżki pliku
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bff3ec554a594e99bc65e5cd8df28a056dcc1ebd
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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
