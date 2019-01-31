---
title: 'Pierwsza instrukcja tego elementu „Sub New” musi być jawnym wywołaniem elementu „MyBase.New” lub „MyClass.New”, ponieważ element „<constructorname>” w klasie bazowej „<baseclassname>” elementu „<derivedclassname>” jest oznaczony jako przestarzały: „<errormessage>"'
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: 31f92d1e52e50b2a87fd6a6af6e3c87292f4437f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268798"
---
# <a name="first-statement-of-this-sub-new-must-be-an-explicit-call-to-mybasenew-or-myclassnew-because-the-constructorname-in-the-base-class-baseclassname-of-derivedclassname-is-marked-obsolete-errormessage"></a>Pierwsza instrukcja tego elementu "Sub New" musi być jawnym wywołaniem elementu "MyBase.New" lub "MyClass.New", ponieważ "\<constructorname >" w klasie bazowej\<baseclassname > "z"\<derivedclassname > "jest oznaczony jako przestarzały:"\< komunikat o błędzie > "
Konstruktor klasy nie jawnie wywołać konstruktora klasy bazowej i Konstruktor niejawne klasy bazowej jest oznaczona za pomocą <xref:System.ObsoleteAttribute> atrybut i dyrektywy traktowanie jej jako błąd.  
  
 Jeśli konstruktor klasy pochodnej nie wywołać konstruktora klasy bazowej, Visual Basic spróbuje go wygenerować wywołanie niejawne konstruktor bez parametrów klasy bazowej. Jeśli jest dostępny żaden konstruktor nie w klasie bazowej, który można wywołać bez argumentów, Visual Basic nie można wygenerować wywołanie niejawne. W tym przypadku wymaganego konstruktora jest oznaczona za pomocą <xref:System.ObsoleteAttribute> atrybutu, więc języka Visual Basic nie można wywołać go.  
  
 Możesz oznaczyć dowolnego elementu programistycznego jako nie jest już używana przez zastosowanie <xref:System.ObsoleteAttribute> do niego. Jeśli to zrobisz, możesz ustawić atrybutu <xref:System.ObsoleteAttribute.IsError%2A> właściwości albo `True` lub `False`. Jeśli ustawisz na `True`, kompilator traktuje próba użycia elementu jako błąd. Jeśli ustawisz na `False`, lub pozwól, aby go domyślnie `False`, kompilator generuje ostrzeżenie, jeśli próba użycia elementu.  
  
 **Identyfikator błędu:** BC30920  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź komunikat o błędzie w cudzysłowach i podjąć odpowiednie działania.  
  
2.  Obejmują wywołania `MyBase.New()` lub `MyClass.New()` jako pierwsza instrukcja `Sub New` w klasie pochodnej.  
  
## <a name="see-also"></a>Zobacz także
- [Omówienie atrybuty](../../../visual-basic/programming-guide/concepts/attributes/index.md)

