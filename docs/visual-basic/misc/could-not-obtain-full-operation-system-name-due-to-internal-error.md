---
title: Nie można uzyskać pełnej nazwy systemu operacyjnego z powodu błędu wewnętrznego
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: 6a0e24743c861ba92fc284a84fa4ef26e2ee48a8
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "58022750"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>Nie można uzyskać pełnej nazwy systemu operacyjnego z powodu błędu wewnętrznego
Nie można uzyskać pełnej nazwy systemu operacyjnego z powodu błędu wewnętrznego. Może to być spowodowane przez usługę WMI nie istnieje na bieżącej maszynie.  
  
 Wywołanie `My.Computer.Info.OSFullName` właściwości nie powiodło się. Możliwą przyczyną tego błędu jest, jeśli Instrumentacji zarządzania Windows (WMI) nie jest zainstalowany na bieżącym komputerze.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Dodaj `Try...Catch` bloku wokół wywołania `My.Computer.Info.OSFullName` właściwości.  
  
2.  Aby uzyskać więcej informacji dotyczących usługi WMI i sposobach jego instalacji przejdź do i wyszukaj frazę "Podstawowy Instrumentacji zarządzania Windows".  
  
## <a name="see-also"></a>Zobacz także

- [My.Computer.Info.OSFullName](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [Obsługa i zgłaszanie wyjątków na platformie .NET](../../standard/exceptions/index.md)
- [Try...Catch...Finally, instrukcja](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
