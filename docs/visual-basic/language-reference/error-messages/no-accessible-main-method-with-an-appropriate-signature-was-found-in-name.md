---
title: "Brak dostępnego &#39; Main &#39; metody z odpowiednim podpisem został znaleziony w &#39; &lt;nazwa&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6a2d66c860b72bd3ef59c02f548ac563fab6b8c
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a>Brak dostępnego &#39; Main &#39; metody z odpowiednim podpisem został znaleziony w &#39; &lt;nazwa&gt;&#39;
Aplikacje wiersza poleceń musi mieć `Sub Main` zdefiniowane. `Main`musi być zadeklarowany jako `Public Shared` , jeśli jest on zdefiniowany w klasie lub jako `Public` Jeśli zdefiniowany w module.  
  
 **Identyfikator błędu:** BC30737  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zdefiniuj `Public Sub Main` procedury dla projektu. Zadeklaruj ją jako `Shared` tylko wtedy, gdy należy zdefiniować wewnątrz klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura programu w języku Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
