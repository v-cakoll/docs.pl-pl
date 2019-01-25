---
title: Liczba porządkowa nie jest prawidłowa
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 351b7ee7f1cfc5199d878c33965770693227ccc4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618966"
---
# <a name="ordinal-is-not-valid"></a>Liczba porządkowa nie jest prawidłowa
Wywołania do biblioteki dołączanej (dynamicznie DLL) wskazane Użyj numeru zamiast nazwy procedury przy użyciu `#num` składni. Ten błąd ma następujące możliwe przyczyny:  
  
-   Próba konwersji `#num` wyrażenie numeru porządkowego nie powiodło się.  
  
-   `#num` Określonego nie określa żadnej funkcji w bibliotece DLL.  
  
-   Biblioteka typów ma nieprawidłową deklarację skutkuje wewnętrzne korzystanie z nieprawidłową liczbą porządkową.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że wyrażenie reprezentuje prawidłową liczbę, lub wywołaj procedurę według nazwy.  
  
2.  Upewnij się, że `#num` określa prawidłowe funkcję w bibliotece DLL.  
  
3.  Izolowanie po wywołaniu procedury, które powoduje problem, zakomentowując kodu. Zapis `Declare` poufności informacji dotyczące procedury i raport problem z dostawcą biblioteki typów.  
  
## <a name="see-also"></a>Zobacz także
- [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)
