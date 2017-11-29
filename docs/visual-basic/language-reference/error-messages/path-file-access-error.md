---
title: "Błąd dostępu do ścieżki pliku"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c86d46c884617be152a5954426e9ddd6ef61651
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="pathfile-access-error"></a>Błąd dostępu do ścieżki/pliku
Podczas operacji dostępu do plików lub dostępu do dysku systemu operacyjnego nie można ustanowić połączenia między ścieżkę i nazwę pliku.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że specyfikacji pliku jest poprawnie sformatowana. Nazwa pliku może zawierać pełną (bezwzględna) lub względna ścieżka. Jest w pełni kwalifikowana ścieżka zaczyna się od nazwy dysku (jeśli znajduje się na innym dysku) i wyświetla jawne ścieżka od elementu głównego do pliku. Dowolną ścieżkę, która nie jest w pełni kwalifikowana jest względne wobec bieżącego dysku i katalogu.  
  
2.  Upewnij się, że nie próbował zapisać plik, który zastąpić istniejący plik tylko do odczytu. Jeśli jest to możliwe, zmień ten atrybut tylko do odczytu z pliku docelowego lub Zapisz plik z inną nazwą pliku.  
  
3.  Upewnij się, że nie próbując otworzyć plik tylko do odczytu w kolejnych `Output` lub `Append` tryb. Jeśli tak jest, otwórz plik w `Input` tryb lub zmień ten atrybut tylko do odczytu pliku.  
  
4.  Upewnij się, że nie próbował zmienić [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projektu bazy danych lub dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 [Error — typy](../../../visual-basic/programming-guide/language-features/error-types.md)
