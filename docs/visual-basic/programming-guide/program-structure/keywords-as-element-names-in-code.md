---
title: Słowa kluczowe jako nazwy elementów w Code (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: 53c3172e8518115d001c23be2430fbc87ae1b60f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652581"
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
