---
ms.openlocfilehash: 4e81087431091dfa4d5432d5ea5e2b665be2b130
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774404"
---
### <a name="listtforeach-can-throw-exception-when-modifying-list-item"></a>Lista\<T >. ForEach może zgłosić wyjątek podczas modyfikowania elementu listy

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5, moduł wyliczający <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> zgłosi wyjątek <xref:System.InvalidOperationException?displayProperty=name>, jeśli element kolekcji wywołującej zostanie zmodyfikowany. Wcześniej nie zgłaszał wyjątku, ale mogło to prowadzić do sytuacji wyścigu.|
|Sugestia|Najlepiej nie poprawiać kodu, aby nie modyfikować list podczas wyliczania ich elementów, ponieważ to nigdy nie jest bezpieczna operacja. Aby przywrócić poprzednie zachowanie, można określić platformę docelową aplikacji jako program .NET Framework 4.0.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType></li></ul>|
