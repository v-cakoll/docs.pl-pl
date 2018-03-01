---
title: "&#39; Moduł &#39; instrukcje mogą wystąpić tylko na poziomie pliku lub przestrzeni nazw"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 61fe12fbd7d20e6cd2b6bc464e7fc3293150213b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="39module39-statements-can-occur-only-at-file-or-namespace-level"></a>&#39; Moduł &#39; instrukcje mogą wystąpić tylko na poziomie pliku lub przestrzeni nazw
`Module`Instrukcje muszą występować na początku pliku źródłowego natychmiast po `Option` i `Imports` instrukcje, atrybutami globalnymi i deklaracje przestrzeni nazw, ale przed wszystkimi innymi deklaracjami.  
  
 **Identyfikator błędu:** BC30617  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Przenieś `Module` instrukcji na początku pliku deklaracji ani źródła przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 [Module — instrukcja](../../../visual-basic/language-reference/statements/module-statement.md)
