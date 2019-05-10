---
title: Liczba porządkowa nie jest prawidłowa
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 740243c744a7ba5391659894812a00d80555fd80
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665665"
---
# <a name="ordinal-is-not-valid"></a>Liczba porządkowa nie jest prawidłowa
Wywołania do biblioteki dołączanej (dynamicznie DLL) wskazane Użyj numeru zamiast nazwy procedury przy użyciu `#num` składni. Ten błąd ma następujące możliwe przyczyny:  
  
- Próba konwersji `#num` wyrażenie numeru porządkowego nie powiodło się.  
  
- `#num` Określonego nie określa żadnej funkcji w bibliotece DLL.  
  
- Biblioteka typów ma nieprawidłową deklarację skutkuje wewnętrzne korzystanie z nieprawidłową liczbą porządkową.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Upewnij się, że wyrażenie reprezentuje prawidłową liczbę, lub wywołaj procedurę według nazwy.  
  
2. Upewnij się, że `#num` określa prawidłowe funkcję w bibliotece DLL.  
  
3. Izolowanie po wywołaniu procedury, które powoduje problem, zakomentowując kodu. Zapis `Declare` poufności informacji dotyczące procedury i raport problem z dostawcą biblioteki typów.  
  
## <a name="see-also"></a>Zobacz także

- [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)
