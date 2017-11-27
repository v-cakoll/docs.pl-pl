---
title: "Wiodące &#39;. &#39; i &#39;! &#39; może wystąpić tylko wewnątrz &#39; Z &#39; — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords: BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 961f2d737123ab68b200d5fc7658cb81291a5de6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="leading-3939-or-3939-can-only-appear-inside-a-39with39-statement"></a>Wiodące &#39;. &#39; i &#39;! &#39; może wystąpić tylko wewnątrz &#39; Z &#39; — Instrukcja
Kropki (.) lub wykrzyknika (!) nie jest który wewnątrz `With` bloku odbywa się bez wyrażenie po lewej stronie. Dostęp do elementu członkowskiego (`.`) i dostęp do elementu członkowskiego słownika (`!`) wymagają wyrażenie określające element, który zawiera element członkowski. Musi występować od razu po lewej stronie metody dostępu lub jako element docelowy `With` blok zawierający dostęp do elementu członkowskiego.  
  
 **Identyfikator błędu:** BC30157  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że `With` bloku jest poprawnie sformatowana.  
  
2.  W przypadku nie `With` bloków, Dodaj wyrażenie w lewo metody dostępu, która ocenia zdefiniowanego elementu zawierający element członkowski.  
  
## <a name="see-also"></a>Zobacz też  
 [Znaki specjalne w Code](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 [Z... End With — instrukcja](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
