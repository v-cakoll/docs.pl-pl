---
title: Wznowienie bez błędu
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 5e45f713a433365b4bbc8286154a3b877b08ec59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597878"
---
# <a name="resume-without-error"></a>Wznowienie bez błędu
A `Resume` instrukcji znajdowały się poza kodu obsługi błędu lub kod przeskoki do obsługi błędów, nawet jeśli nie było żadnych błędów.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Przenieś `Resume` instrukcji do obsługi błędów lub usuń go.  
  
2.  Dlatego przeskoki do etykiet nie może wystąpić między procedurami, wyszukaj procedury dla etykiety, który identyfikuje program obsługi błędów. Jeśli okaże się zduplikowane etykiety określony jako element docelowy `GoTo` instrukcji, która nie jest `On Error GoTo` instrukcji, zmienić etykietę wiersza, aby uzgodnić z jej celem.  
  
## <a name="see-also"></a>Zobacz też  
 [Resume, instrukcja](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [On Error, instrukcja](../../../visual-basic/language-reference/statements/on-error-statement.md)
