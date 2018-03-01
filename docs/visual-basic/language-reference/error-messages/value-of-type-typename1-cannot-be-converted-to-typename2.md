---
title: "Wartość typu &#39; &lt;typename1&gt;&#39; nie można przekonwertować na &#39;&lt; typename2&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b583c4272dd6e964de99fb14d2795152c655f3aa
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39"></a>Wartość typu &#39; &lt;typename1&gt;&#39; nie można przekonwertować na &#39;&lt; typename2&gt;&#39;
Wartości typu "\<typename1 >' nie można przekonwertować na"\<typename2 > ". Niezgodność typów przyczyną może być połączenie odwołania pliku z odwołaniem projektu do zestawu "\<assemblyname >". Spróbuj zamienić odwołanie pliku do "\<ścieżka_pliku >" w projekcie "\<projectname1 >" na odwołanie projektu do "\<projectname2 >".  
  
 W sytuacji, gdy projekt sprawia, że zarówno odwołanie do projektu i odwołanie do pliku kompilator nie może zagwarantować, że jeden typ można przekonwertować na inny.  
  
 Poniższy pseudo-kod przedstawia sytuację, której może wygenerować tego błędu.  
  
 `' ================ Visual Basic project P1 ================`  
  
 `'        P1 makes a PROJECT REFERENCE to project P2`  
  
 `'        and a FILE REFERENCE to project P3.`  
  
 `Public commonObject As P3.commonClass`  
  
 `commonObject = P2.getCommonClass()`  
  
 `' ================ Visual Basic project P2 ================`  
  
 `'        P2 makes a PROJECT REFERENCE to project P3`  
  
 `Public Function getCommonClass() As P3.commonClass`  
  
 `Return New P3.commonClass`  
  
 `End Function`  
  
 `' ================ Visual Basic project P3 ================`  
  
 `Public Class commonClass`  
  
 `End Class`  
  
 Projekt `P1` wykonuje odwołanie pośrednie projektu do projektu `P2` do projektu `P3`, a także bezpośrednie odwołanie do pliku `P3`. Deklaracja `commonObject` używa odwołanie pliku do `P3`, podczas gdy wywołanie `P2.getCommonClass` używa odwołanie projektu do `P3`.  
  
 Problem w tej sytuacji jest, że odwołanie do pliku Określa ścieżkę i nazwę pliku dla pliku wyjściowego `P3` (zazwyczaj p3.dll), gdy projekt odwołuje się do identyfikacji projektu źródłowego (`P3`) według nazwy projektu. W związku z tym kompilator nie może zagwarantować, że typ `P3.commonClass` pochodzi z tego samego kodu źródłowego za pomocą dwóch różnych odwołań.  
  
 Ta sytuacja zwykle występuje, gdy projekt odwołań i mieszane odwołania do pliku. Na powyższej ilustracji, problem może nie wystąpić, jeśli `P1` wprowadzone bezpośrednie odwołanie do `P3` zamiast odwołania pliku.  
  
 **Identyfikator błędu:** BC30955  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zmień odwołanie pliku do projektu odwołanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersje typów w języku Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project)  
 
