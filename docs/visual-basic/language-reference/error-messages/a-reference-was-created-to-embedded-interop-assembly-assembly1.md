---
title: "Utworzono odwołanie do osadzonego zestawu międzyoperacyjnego &#39; &lt;zestaw1&gt;&#39; z powodu pośredniego odwołania do tego zestawu z zestawu &#39;&lt; assembly2&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bc2fbb044fc839aa24abf3dc1ea864457efb0653
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-39ltassembly1gt39-because-of-an-indirect-reference-to-that-assembly-from-assembly-39ltassembly2gt39"></a>Utworzono odwołanie do osadzonego zestawu międzyoperacyjnego &#39; &lt;zestaw1&gt;&#39; z powodu pośredniego odwołania do tego zestawu z zestawu &#39;&lt; assembly2&gt;&#39;
Utworzono odwołanie do osadzonego zestawu międzyoperacyjnego "\<zestaw1 >" z powodu pośredniego odwołania do tego zestawu z zestawu "\<assembly2 >". Rozważ zmianę właściwości "Osadź typy międzyoperacyjne" na jednym z zestawów.  
  
 Dodano odwołanie do zestawu (zestaw1), który ma `Embed Interop Types` ustawioną właściwość `True`. To instruuje kompilator, aby osadzić typu międzyoperacyjnego informacje z tego zestawu. Jednak kompilator nie można osadzić typu międzyoperacyjnego informacje z tego zestawu, ponieważ inny zestaw czy zdefiniowano odwołania (assembly2) również odwołuje się do tego zestawu (zestaw1) i ma `Embed Interop Types` ustawioną właściwość `False`.  
  
> [!NOTE]
>  Ustawienie `Embed Interop Types` właściwości na odwołanie do zestawu `True` jest odpowiednikiem odwołanie do zestawu przy użyciu `/link` opcji dla kompilatora wiersza polecenia.  
  
 **Identyfikator błędu:** BC40059  
  
### <a name="to-address-this-warning"></a>W celu rozwiązania tego ostrzeżenia  
  
-   Aby osadzić typu międzyoperacyjnego informacje dla obu zestawów, ustaw `Embed Interop Types` właściwości na wszystkich odwołań do zestaw1 do `True`.  
  
-   Aby usunąć to ostrzeżenie, można ustawić `Embed Interop Types` właściwości zestaw1 do `False`. W takim przypadku informacje typu międzyoperacyjnego są udostępniane przez podstawowy zestaw międzyoperacyjny (PIA).  
  
## <a name="see-also"></a>Zobacz też  
 [/ Link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md)  
 [Programowanie za pomocą podstawowe zestawy międzyoperacyjne](http://msdn.microsoft.com/en-us/306fa1d6-0703-4004-9e93-d0a57f1be81e)
