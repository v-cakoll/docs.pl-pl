---
title: Element „<elementname>" jest przestarzały (ostrzeżenie w języku Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
ms.openlocfilehash: c6d927ef6681838d8a77a0c6018eb6bbe30913e8
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255865"
---
# <a name="elementname-is-obsolete-visual-basic-warning"></a>"\<elementname >" jest przestarzały (ostrzeżenie Visual Basic)
Instrukcja próbuje uzyskać dostęp elementu programistycznego, które zostały oznaczone do <xref:System.ObsoleteAttribute> atrybut i dyrektywy traktowanie jej jako ostrzeżenie.  
  
 Możesz oznaczyć dowolnego elementu programistycznego jako nie jest już używana przez zastosowanie <xref:System.ObsoleteAttribute> do niego. Jeśli to zrobisz, możesz ustawić atrybutu <xref:System.ObsoleteAttribute.IsError%2A> właściwości albo `True` lub `False`. Jeśli ustawisz na `True`, kompilator traktuje próba użycia elementu jako błąd. Jeśli ustawisz na `False`, lub pozwól, aby go domyślnie `False`, kompilator generuje ostrzeżenie, jeśli próba użycia elementu.  
  
 Domyślnie ten komunikat jest to ostrzeżenie, ponieważ <xref:System.ObsoleteAttribute.IsError%2A> właściwość <xref:System.ObsoleteAttribute> jest `False`. Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40008  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że odwołanie do kodu źródłowego jest poprawnie pisownia nazwy elementu.  
  
## <a name="see-also"></a>Zobacz także
- [Omówienie atrybuty](../../../visual-basic/programming-guide/concepts/attributes/index.md)
