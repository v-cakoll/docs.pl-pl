---
title: "&#39; &lt;elementname&gt;&#39; jest przestarzałe (ostrzeżenie Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords: BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bd6580da794255a3324021a284816ef9700beee7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="39ltelementnamegt39-is-obsolete-visual-basic-warning"></a>&#39; &lt;elementname&gt;&#39; jest przestarzałe (ostrzeżenie Visual Basic)
Instrukcja próbuje uzyskać dostęp elementu programistycznego, które zostały oznaczone <xref:System.ObsoleteAttribute> atrybut i dyrektywy traktować go jako ostrzeżenia.  
  
 Można zaznaczyć dowolny element programowania jako nie jest już używana przez zastosowanie <xref:System.ObsoleteAttribute> do niego. Jeśli to zrobisz, można ustawić atrybutu <xref:System.ObsoleteAttribute.IsError%2A> właściwości albo `True` lub `False`. Jeśli zostanie ustawiona `True`, kompilator traktuje próba użycia elementu jako błąd. Jeśli zostanie ustawiona `False`, lub pozwól mu domyślnie `False`, kompilator generuje ostrzeżenie, jeśli próba użycia elementu.  
  
 Domyślnie ten komunikat jest ostrzeżenie, ponieważ <xref:System.ObsoleteAttribute.IsError%2A> właściwość <xref:System.ObsoleteAttribute> jest `False`. Aby uzyskać więcej informacji na temat ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40008  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że odwołanie do kodu źródłowego jest poprawnie pisownię nazwy elementu.  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty — omówienie](../../../visual-basic/programming-guide/concepts/attributes/index.md)
