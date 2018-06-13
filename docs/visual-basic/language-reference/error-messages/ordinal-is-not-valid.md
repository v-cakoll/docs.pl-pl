---
title: Liczba porządkowa nie jest prawidłowa
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 12d73b33e3c025b40c98d84e3507af7be1e1e91a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593606"
---
# <a name="ordinal-is-not-valid"></a>Liczba porządkowa nie jest prawidłowa
Wskazane jest używany numer zamiast nazwę procedury wywołania do biblioteki dołączanej (dynamicznie DLL) przy użyciu `#num` składni. Ten błąd ma następujące możliwe przyczyny:  
  
-   Próba konwersji `#num` wyrażenie numeru porządkowego nie powiodło się.  
  
-   `#num` Określony nie określa żadnych funkcji w bibliotece DLL.  
  
-   Biblioteki typów ma nieprawidłową deklaracją, co powoduje wewnętrzne korzystanie z nieprawidłową liczbą porządkową.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że wyrażenie reprezentuje prawidłową liczbę lub wywołania tej procedury według nazwy.  
  
2.  Upewnij się, że `#num` identyfikuje prawidłowe funkcji w bibliotece DLL.  
  
3.  Izolowanie wywoływania przyczyną problemu przez komentarzy kodu. Zapis `Declare` instrukcji dla procedury i raportu problem z dostawcą biblioteki typów.  
  
## <a name="see-also"></a>Zobacz też  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)
