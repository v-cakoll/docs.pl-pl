---
title: 'Pierwsza instrukcja tego &#39;Sub New&#39; musi być jawnym wywołaniem &#39;MyBase.New&#39; lub &#39;MyClass.New&#39; ponieważ &#39; &lt;constructorname&gt; &#39; w klasie bazowej &#39; &lt;baseclassname&gt; &#39; z &#39; &lt;derivedclassname&gt; &#39; jest oznaczony jako przestarzały: &#39; &lt;komunikat o błędzie&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: 9d07a68fd8d9790178427c512375323f23f46772
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566782"
---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a>Pierwsza instrukcja tego &#39;Sub New&#39; musi być jawnym wywołaniem &#39;MyBase.New&#39; lub &#39;MyClass.New&#39; ponieważ &#39; &lt;constructorname&gt; &#39; w klasie bazowej &#39; &lt;baseclassname&gt; &#39; z &#39; &lt;derivedclassname&gt; &#39; jest oznaczony jako przestarzały: &#39; &lt;komunikat o błędzie&gt;&#39;
Konstruktor klasy nie jawnie wywołać konstruktora klasy bazowej i Konstruktor niejawne klasy bazowej jest oznaczona za pomocą <xref:System.ObsoleteAttribute> atrybut i dyrektywy traktowanie jej jako błąd.  
  
 Jeśli konstruktor klasy pochodnej nie wywołać konstruktora klasy bazowej, Visual Basic spróbuje go wygenerować wywołanie niejawne konstruktor bez parametrów klasy bazowej. Jeśli jest dostępny żaden konstruktor nie w klasie bazowej, który można wywołać bez argumentów, Visual Basic nie można wygenerować wywołanie niejawne. W tym przypadku wymaganego konstruktora jest oznaczona za pomocą <xref:System.ObsoleteAttribute> atrybutu, więc języka Visual Basic nie można wywołać go.  
  
 Możesz oznaczyć dowolnego elementu programistycznego jako nie jest już używana przez zastosowanie <xref:System.ObsoleteAttribute> do niego. Jeśli to zrobisz, możesz ustawić atrybutu <xref:System.ObsoleteAttribute.IsError%2A> właściwości albo `True` lub `False`. Jeśli ustawisz na `True`, kompilator traktuje próba użycia elementu jako błąd. Jeśli ustawisz na `False`, lub pozwól, aby go domyślnie `False`, kompilator generuje ostrzeżenie, jeśli próba użycia elementu.  
  
 **Identyfikator błędu:** BC30920  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź komunikat o błędzie w cudzysłowach i podjąć odpowiednie działania.  
  
2.  Obejmują wywołania `MyBase.New()` lub `MyClass.New()` jako pierwsza instrukcja `Sub New` w klasie pochodnej.  
  
## <a name="see-also"></a>Zobacz także
- [Omówienie atrybuty](../../../visual-basic/programming-guide/concepts/attributes/index.md)

