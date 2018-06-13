---
title: Nie można uzyskać pełnej nazwy systemu operacyjnego z powodu błędu wewnętrznego
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: f85ca5f7f325cb0dd2b8fc55d3f90f6abdfd4a7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33635080"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>Nie można uzyskać pełnej nazwy systemu operacyjnego z powodu błędu wewnętrznego
Nie można uzyskać pełnej nazwy systemu operacyjnego z powodu błędu wewnętrznego. Może to być spowodowane WMI nie istniejący na bieżącym komputerze.  
  
 Wywołanie `My.Computer.Info.OSFullName` właściwości nie powiodło się. Możliwą przyczyną tego błędu jest to, czy Instrumentacja zarządzania Windows (WMI) nie jest zainstalowany na bieżącym komputerze.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Dodaj `Try...Catch` bloku wokół wywołanie `My.Computer.Info.OSFullName` właściwości.  
  
2.  Aby uzyskać więcej informacji na temat usługi WMI i sposobu instalacji, przejdź do i wyszukaj "Windows Management Instrumentation Core".  
  
## <a name="see-also"></a>Zobacz też  
 [My.Computer.Info.OSFullName](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)  
 [Wyjątek i obsługa błędów w języku Visual Basic](http://msdn.microsoft.com/library/3e351e73-cf23-40ab-8b60-05794160529e)  
 [Try...Catch...Finally, instrukcja](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
