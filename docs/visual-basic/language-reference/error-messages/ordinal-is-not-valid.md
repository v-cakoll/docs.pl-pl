---
title: Liczba porządkowa nie jest prawidłowa
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: f3207c2cc237ae22c295c2b3ed56f18601625226
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822278"
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
