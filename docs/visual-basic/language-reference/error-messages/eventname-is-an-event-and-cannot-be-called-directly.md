---
title: '&#39;&lt;eventName&gt; &#39; jest zdarzeniem i nie można wywołać bezpośrednio'
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 3efd8c18497ce288e16659db4ca4693d5a3e6acc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582005"
---
# <a name="39lteventnamegt39-is-an-event-and-cannot-be-called-directly"></a>&#39;&lt;eventName&gt; &#39; jest zdarzeniem i nie można wywołać bezpośrednio
"<`eventname`>" jest zdarzeniem i dlatego nie można wywołać bezpośrednio. Użyj `RaiseEvent` instrukcję, aby wywołać zdarzenie.  
  
 Wywołanie procedury określa zdarzenie dla nazwy procedury. Program obsługi zdarzeń jest procedurą samego zdarzenia jest jednak sygnalizowanie urządzenia, które muszą być zgłaszane i obsługi.  
  
 **Identyfikator błędu:** BC32022  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Użyj `RaiseEvent` instrukcję w celu zasygnalizowania zdarzenia i wywoływać procedury lub procedury, które go obsłużyć.  
  
## <a name="see-also"></a>Zobacz także
- [RaiseEvent, instrukcja](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
