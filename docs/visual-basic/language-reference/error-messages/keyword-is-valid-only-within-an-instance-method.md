---
title: "&#39; &lt;— słowo kluczowe&gt;&#39; jest prawidłowy tylko wewnątrz metody wystąpienia"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords: BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a61314c036cec0fd1412a9c844a610fbd1401add
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="39ltkeywordgt39-is-valid-only-within-an-instance-method"></a>&#39; &lt;— słowo kluczowe&gt;&#39; jest prawidłowy tylko wewnątrz metody wystąpienia
`Me`, `MyClass`, I `MyBase` słowa kluczowe odwoływać się do wystąpień określonej klasy. Nie można ich używać w udostępnionej `Function` lub `Sub` procedury.  
  
 **Identyfikator błędu:** BC30043  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Usuń słowo kluczowe z procedury lub usuń `Shared` — słowo kluczowe z deklaracji procedury.  
  
## <a name="see-also"></a>Zobacz też  
 [Przypisanie zmiennej obiektu](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Me, My, MyBase i MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
