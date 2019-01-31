---
title: Element „<eventname>” jest zdarzeniem i nie można go wywołać bezpośrednio
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 4e27d9ce788ae7b9741c0cb80da776959748b8b9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272730"
---
# <a name="eventname-is-an-event-and-cannot-be-called-directly"></a>"\<eventname >" jest zdarzeniem i nie można wywołać bezpośrednio
"<`eventname`>" jest zdarzeniem i dlatego nie można wywołać bezpośrednio. Użyj `RaiseEvent` instrukcję, aby wywołać zdarzenie.  
  
 Wywołanie procedury określa zdarzenie dla nazwy procedury. Program obsługi zdarzeń jest procedurą samego zdarzenia jest jednak sygnalizowanie urządzenia, które muszą być zgłaszane i obsługi.  
  
 **Identyfikator błędu:** BC32022  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Użyj `RaiseEvent` instrukcję w celu zasygnalizowania zdarzenia i wywoływać procedury lub procedury, które go obsłużyć.  
  
## <a name="see-also"></a>Zobacz także
- [RaiseEvent, instrukcja](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
