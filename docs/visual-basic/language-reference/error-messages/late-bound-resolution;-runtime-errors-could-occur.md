---
title: "Rozpoznanie późnego wiązania; mogą wystąpić błędy podczas wykonywania"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8d01164914b484ef689654f048a8743f3c2eb669
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a>Rozpoznanie późnego wiązania; mogą wystąpić błędy podczas wykonywania
Obiekt jest przypisany do zmiennej zadeklarowany za [Object — typ danych](../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Gdy zadeklarować zmiennej jako `Object`, należy wykonać kompilator *późne wiązanie*, co powoduje, że dodatkowe operacje w czasie wykonywania. Prezentuje ona potencjalne błędy czasu wykonywania przez aplikację. Na przykład w przypadku przypisania <xref:System.Windows.Forms.Form> do `Object` zmiennej, a następnie spróbuj uzyskać dostępu do <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> zgłasza wyjątek środowiska uruchomieniowego, właściwości, <xref:System.MemberAccessException> ponieważ <xref:System.Windows.Forms.Form> klasy nie ujawnia `NameTable` właściwości.  
  
 Jeśli należy zadeklarować zmienną określonego typu, kompilator może wykonywać *wczesne wiązanie* w czasie kompilacji. Powoduje to lepszą wydajność, kontroli dostępu do elementów członkowskich z określonego typu i zwiększenia czytelności kodu.  
  
 Domyślnie ten komunikat jest ostrzeżenie. Aby uzyskać informacje na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42017  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli to możliwe należy zadeklarować zmienną określonego typu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wczesne i późne powiązania](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [Deklaracja zmiennej obiektu](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
