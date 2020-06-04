---
title: Element „<elementname>" jest przestarzały (ostrzeżenie w języku Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
ms.openlocfilehash: 7914bc859966e17f3da41c9a13a01573b31baf91
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409676"
---
# <a name="elementname-is-obsolete-visual-basic-warning"></a>Element „\<elementname>" jest przestarzały (ostrzeżenie w języku Visual Basic)
Instrukcja próbuje uzyskać dostęp do elementu programistycznego, który został oznaczony <xref:System.ObsoleteAttribute> atrybutem i dyrektywą, aby traktować go jako ostrzeżenie.  
  
 Można oznaczyć dowolny element programistyczny jako nieużywany przez zastosowanie <xref:System.ObsoleteAttribute> do niego. W takim przypadku można ustawić <xref:System.ObsoleteAttribute.IsError%2A> właściwość atrybutu na `True` lub `False` . Jeśli ustawisz ją na `True` , kompilator traktuje próbę użycia elementu jako błąd. Jeśli ustawisz ją na `False` lub Zezwól na ustawienie domyślne `False` , kompilator generuje ostrzeżenie w przypadku próby użycia elementu.  
  
 Domyślnie ten komunikat jest ostrzeżeniem, ponieważ <xref:System.ObsoleteAttribute.IsError%2A> Właściwość <xref:System.ObsoleteAttribute> jest `False` . Aby uzyskać więcej informacji na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędów, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40008  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że odwołanie do kodu źródłowego jest poprawnie sprawdzane jako nazwa elementu.  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd atrybutów](../../programming-guide/concepts/attributes/index.md)
