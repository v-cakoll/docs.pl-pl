---
title: "Słowa kluczowe jako nazwy elementów w Code (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f410a0eaac0dcc034d406a89ed1d01a8f228a583
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a>Słowa kluczowe jako nazwy elementów w Code (Visual Basic)
Każdy element program — takie jak zmienna, klasa lub element członkowski — może mieć taką samą nazwę jak ograniczeniami — słowo kluczowe. Na przykład można utworzyć zmiennej o nazwie `Loop`. Jednak aby odwołać się do używanej wersji — który ma taką samą nazwę jak ograniczeniami `Loop` — słowo kluczowe — należy poprzedzić ciągu pełnej kwalifikacji lub została ujęta w nawiasy kwadratowe (`[ ]`), jak pokazano na poniższym przykładzie.  
  
 [!code-vb[VbVbcnConventions#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/keywords-as-element-names-in-code_1.vb)]  
  
 Wykonaj jedną z nich, a następnie Visual Basic założono użycie wewnętrznej `Loop` — słowo kluczowe i tworzy błąd, jak w poniższym przykładzie:  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 Podczas odwoływania się do formularzy i kontrolek i gdy służy nawiasy kwadratowe deklarowanie zmiennej lub definiujący procedurę o tej samej nazwie jako ograniczeniami — słowo kluczowe. Można go łatwo Pamiętaj, aby zakwalifikować nazwy lub obejmują nawiasów kwadratowych, w związku z tym spowodują one błędów w kodzie i utrudnić odczytu. Z tego powodu zalecamy nie używać ograniczeniami słowa kluczowe jako nazwy elementów programu. Jednak jeśli przyszłych wersjach programu Visual Basic definiuje new — słowo kluczowe powodujący konflikt z istniejącym formularzu lub nazwa formantu, następnie służy ta technika podczas aktualizowania kodu do pracy z nową wersją.  
  
> [!NOTE]
>  Program może również obejmować nazwy elementów udostępnione przez innych zestawów występujących w odwołaniach. Jeśli te nazwy w konflikcie z ograniczeniami słów kluczowych, następnie umieszczenie nawiasy kwadratowe wokół nich spowoduje Visual Basic zinterpretować je jako określonych elementów.  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Basic — konwencje nazewnictwa](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [Struktura programu i konwencje związane z kodami](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
