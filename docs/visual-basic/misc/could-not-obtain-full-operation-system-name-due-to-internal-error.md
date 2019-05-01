---
title: Nie można uzyskać pełnej nazwy systemu operacyjnego z powodu błędu wewnętrznego
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: ecbed5b59d36b1984c0b0ae161821ea99d28e090
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970589"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>Nie można uzyskać pełnej nazwy systemu operacyjnego z powodu błędu wewnętrznego
Nie można uzyskać pełnej nazwy systemu operacyjnego z powodu błędu wewnętrznego. Może to być spowodowane przez usługę WMI nie istnieje na bieżącej maszynie.  
  
 Wywołanie `My.Computer.Info.OSFullName` właściwości nie powiodło się. Możliwą przyczyną tego błędu jest, jeśli Instrumentacji zarządzania Windows (WMI) nie jest zainstalowany na bieżącym komputerze.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Dodaj `Try...Catch` bloku wokół wywołania `My.Computer.Info.OSFullName` właściwości.  
  
2. Aby uzyskać więcej informacji dotyczących usługi WMI i sposobach jego instalacji przejdź do i wyszukaj frazę "Podstawowy Instrumentacji zarządzania Windows".  
  
## <a name="see-also"></a>Zobacz także

- [My.Computer.Info.OSFullName](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [Obsługa i zgłaszanie wyjątków na platformie .NET](../../standard/exceptions/index.md)
- [Try...Catch...Finally, instrukcja](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
