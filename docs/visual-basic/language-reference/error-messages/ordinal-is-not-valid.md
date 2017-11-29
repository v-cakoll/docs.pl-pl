---
title: "Liczba porządkowa nie jest prawidłowa"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d31d0fba19cc16004c0b56786af30603d0c509ea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
 [DECLARE — instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)
