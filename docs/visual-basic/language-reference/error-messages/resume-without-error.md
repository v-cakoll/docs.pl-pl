---
title: "Wznowienie bez błędu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f86361b1e5310359288a97c5f41f017a344c30b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="resume-without-error"></a>Wznowienie bez błędu
A `Resume` instrukcji znajdowały się poza kodu obsługi błędu lub kod przeskoki do obsługi błędów, nawet jeśli nie było żadnych błędów.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Przenieś `Resume` instrukcji do obsługi błędów lub usuń go.  
  
2.  Dlatego przeskoki do etykiet nie może wystąpić między procedurami, wyszukaj procedury dla etykiety, który identyfikuje program obsługi błędów. Jeśli okaże się zduplikowane etykiety określony jako element docelowy `GoTo` instrukcji, która nie jest `On Error GoTo` instrukcji, zmienić etykietę wiersza, aby uzgodnić z jej celem.  
  
## <a name="see-also"></a>Zobacz też  
 [Resume — instrukcja](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [On Error — instrukcja](../../../visual-basic/language-reference/statements/on-error-statement.md)
