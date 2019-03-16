---
title: Określono nieprawidłową nazwę dziennika zdarzeń
ms.date: 07/20/2015
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
ms.openlocfilehash: 2b9c934272d0f3392c845dcd2f0062a98dc50c7b
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "58032270"
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a>Określono nieprawidłową nazwę dziennika zdarzeń
Nieprawidłowa nazwa została określona dla dziennika zdarzeń. Zazwyczaj jest to wynik nieprawidłowe znaki w nazwę, nazwę pustego pliku lub nazwę pliku, który jest za długi.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli określona nazwa jest więcej niż 8 znaków, upewnij się, że nie występuje konflikt z nazwami innych dzienników zdarzeń. Pierwsze osiem znaków są oceniane podczas ustalania, czy nazwa jest unikatowa.  
  
-   Jeśli dostarczenie ścieżki, upewnij się, że jest analizowany poprawnie.  
  
-   Sprawdź, czy istnieją nie nieprawidłowe znaki w nazwie. Znaki, których nie można używać w nazwie pliku obejmują `<`, `>`, `:`, `"`, `/`, `\`, i `|`.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Analizowanie ścieżek pliku](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
- [Instrukcje: Zmienianie nazwy pliku](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
