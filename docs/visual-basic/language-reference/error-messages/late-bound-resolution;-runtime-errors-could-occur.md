---
title: Rozpoznanie późnego wiązania; mogą wystąpić błędy podczas wykonywania
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: 4fe79c74b6ff634223a4f10d8c5dc54bb77571cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921150"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a>Rozpoznanie późnego wiązania; mogą wystąpić błędy podczas wykonywania
Obiekt jest przypisany do zmiennej, zadeklarowanej będzie [Object — typ danych](../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Kiedy Deklarujesz zmienną `Object`, kompilator musi wykonać *późnym wiązaniu*, co powoduje, że dodatkowe operacje w czasie wykonywania. Udostępnia ona również aplikację, aby potencjalne błędy czasu wykonywania. Na przykład, jeśli przypisujesz <xref:System.Windows.Forms.Form> do `Object` zmiennej, a następnie spróbuj uzyskać dostęp do <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> właściwości, środowisko wykonawcze zgłasza <xref:System.MemberAccessException> ponieważ <xref:System.Windows.Forms.Form> klasy nie ujawnia `NameTable` właściwości.  
  
 Jeśli zadeklarujesz zmienną określonego typu, kompilator będzie mógł wykonać *wczesne powiązania* w czasie kompilacji. Skutkuje to lepszą wydajność i kontrolowany dostęp do elementów członkowskich z określonego typu i zwiększenia czytelności kodu.  
  
 Domyślnie ta wiadomość jest ostrzeżenie. Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42017  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Jeśli to możliwe należy zadeklarować zmienną określonego typu.  
  
## <a name="see-also"></a>Zobacz także

- [Wczesne i późne powiązania](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [Deklaracja zmiennej obiektu](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
