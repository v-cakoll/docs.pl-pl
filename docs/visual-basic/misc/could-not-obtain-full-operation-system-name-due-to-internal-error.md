---
title: Nie można uzyskać pełnej nazwy systemu operacyjnego z powodu błędu wewnętrznego
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: 67e8fb5e906800d28bf15714463b7ff6ae585693
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402281"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>Nie można uzyskać pełnej nazwy systemu operacyjnego z powodu błędu wewnętrznego
Nie można uzyskać pełnej nazwy systemu operacyjnego z powodu błędu wewnętrznego. Może to być spowodowane tym, że usługa WMI nie jest istniejąca na bieżącym komputerze.  
  
 Wywołanie `My.Computer.Info.OSFullName` właściwości nie powiodło się. Możliwą przyczyną tego błędu jest to, że Instrumentacja zarządzania Windows (WMI) nie jest zainstalowana na bieżącym komputerze.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Dodaj `Try...Catch` blok wokół wywołania `My.Computer.Info.OSFullName` właściwości.  
  
2. Aby uzyskać więcej informacji na temat usługi WMI i sposobu jej instalowania, przejdź do i wyszukaj ciąg "Instrumentacja zarządzania Windows Core".  
  
## <a name="see-also"></a>Zobacz też

- [My. Computer. info. OSFullName](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [Obsługa i zgłaszanie wyjątków w programie .NET](../../standard/exceptions/index.md)
- [Try...Catch...Finally, instrukcja](../language-reference/statements/try-catch-finally-statement.md)
