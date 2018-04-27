---
title: 'Pierwsza instrukcja tego &#39;Sub New&#39; musi być jawnym wywołaniem &#39;MyBase.New&#39; lub &#39;MyClass.New&#39; ponieważ &#39; &lt;constructorname&gt; &#39; w klasie podstawowej &#39; &lt;baseclassname&gt; &#39; z &#39; &lt;derivedclassname&gt; &#39; jest oznaczony jako przestarzały: &#39; &lt;komunikat o błędzie&gt;&#39;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7690c9dcdb97e63959d2f0e31791d55ee7b09ffc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a>Pierwsza instrukcja tego &#39;Sub New&#39; musi być jawnym wywołaniem &#39;MyBase.New&#39; lub &#39;MyClass.New&#39; ponieważ &#39; &lt;constructorname&gt; &#39; w klasie podstawowej &#39; &lt;baseclassname&gt; &#39; z &#39; &lt;derivedclassname&gt; &#39; jest oznaczony jako przestarzały: &#39; &lt;komunikat o błędzie&gt;&#39;
Konstruktor klasy nie wywołuje jawnie konstruktora klasy podstawowej i konstruktora klasy podstawowej niejawne jest oznaczony atrybutem <xref:System.ObsoleteAttribute> atrybut i dyrektywy traktować go jako błąd.  
  
 Gdy konstruktora klasy pochodnej nie wywołuje konstruktor klasy podstawowej, Visual Basic próbuje wygenerować niejawne wywołanie konstruktora bez parametrów klasy podstawowej. Jeśli nie będzie dostępny żaden konstruktor nie w klasie podstawowej, który można wywołać bez argumentów, Visual Basic nie można wygenerować niejawne wywołania. W takim przypadku wymagany Konstruktor jest oznaczony atrybutem <xref:System.ObsoleteAttribute> atrybutu, Visual Basic nie można jej wywołać.  
  
 Można zaznaczyć dowolny element programowania jako nie jest już używana przez zastosowanie <xref:System.ObsoleteAttribute> do niego. Jeśli to zrobisz, można ustawić atrybutu <xref:System.ObsoleteAttribute.IsError%2A> właściwości albo `True` lub `False`. Jeśli zostanie ustawiona `True`, kompilator traktuje próba użycia elementu jako błąd. Jeśli zostanie ustawiona `False`, lub pozwól mu domyślnie `False`, kompilator generuje ostrzeżenie, jeśli próba użycia elementu.  
  
 **Identyfikator błędu:** BC30920  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź komunikat błędu w cudzysłowie i podejmij odpowiednią akcję.  
  
2.  Obejmują wywołania `MyBase.New()` lub `MyClass.New()` jako pierwsza instrukcja `Sub New` w klasie pochodnej.  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty — omówienie](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
